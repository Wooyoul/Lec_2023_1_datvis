2023-1학기 데이터시각화</br></br>4주차 과제 예시 code
================
Wooyoul Na </br>

## 시작 전: package `dplyr` loading

``` r
## package loading
library(dplyr)
```

</br>  
</br>

## Question 1 : 남학생들의 시험 준비 여부(`test_prepare`)별 `math`, `reading`, `writing` 점수 평균 구하기

-   **step 1**. `filter()`를 이용하여 남학생(`gender=="male"`)만 선택

-   **step 2**. `group_by()`를 이용하여, `test_prepare`별로 작업 실시

-   **step 3**. `summarize()`를 이용하여, `math`, `reading`, `writing`
    평균 구하기

``` r
studperf %>% # 데이터
  filter(gender=="male") %>% # 남학생만 선택
  group_by(test_prepare) %>% # test_prepare 별로
  summarize(math_평균=mean(math),# math 평균
            reading_평균=mean(reading), # reading 평균
            writing_평균=mean(writing)) # writing 평균
```

    ## # A tibble: 2 x 4
    ##   test_prepare math_평균 reading_평균 writing_평균
    ##   <chr>            <dbl>        <dbl>        <dbl>
    ## 1 completed         72.3         70.2         69.8
    ## 2 none              66.7         62.8         59.6

</br>  
</br>

## Question 2 : 여학생들의 부모 학력(`parentEdu`)별 `math`, `reading`, `writing` 평균 구하기

-   **step 1**. `filter()`를 이용하여 남학생(`gender=="female"`)만 선택

-   **step 2**. `group_by()`를 이용하여, `parentEdu`별로 작업 실시

-   **step 3**. `summarize()`를 이용하여, `math`, `reading`, `writing`
    평균 구하기

``` r
studperf %>% # 데이터
  filter(gender=="female") %>% # 여학생만 선택
  group_by(parentEdu) %>% # parentEdu 별로
  summarize(math_평균=mean(math),# math 평균
            reading_평균=mean(reading), # reading 평균
            writing_평균=mean(writing)) # writing 평균
```

    ## # A tibble: 6 x 4
    ##   parentEdu        math_평균 reading_평균 writing_평균
    ##   <chr>                <dbl>        <dbl>        <dbl>
    ## 1 associate             65.2         74.1         74  
    ## 2 bachelor              68.3         77.3         78.4
    ## 3 high school           59.4         68.2         66.7
    ## 4 master                66.5         76.8         77.6
    ## 5 some college          65.4         73.6         74.1
    ## 6 some high school      59.3         69.1         68.3

</br>  
</br>

-   **참고** : 만약 최종학력(`parentEdu`) 순서대로 결과를 제시하고
    싶다면…?

    -   `character` 형으로 된 `parentEdu`를 `factor` 형으로 변환. 이 때,
        `levels` 옵션을 통해 각 범주의 순서를 지정.

``` r
studperf %>% # 데이터
  mutate(parentEdu = factor(parentEdu, levels=c(
    "some high school", "high school", "some college", "associate", 
    "bachelor", "master"
  ))) %>% # parentEdu를 factor형으로 변환. 이 때, 범주의 순서는 다음과 같이 지정
  filter(gender=="female") %>% # 여학생만 선택
  group_by(parentEdu) %>% # parentEdu 별로
  summarize(math_평균=mean(math),# math 평균
            reading_평균=mean(reading), # reading 평균
            writing_평균=mean(writing)) # writing 평균
```

    ## # A tibble: 6 x 4
    ##   parentEdu        math_평균 reading_평균 writing_평균
    ##   <fct>                <dbl>        <dbl>        <dbl>
    ## 1 some high school      59.3         69.1         68.3
    ## 2 high school           59.4         68.2         66.7
    ## 3 some college          65.4         73.6         74.1
    ## 4 associate             65.2         74.1         74  
    ## 5 bachelor              68.3         77.3         78.4
    ## 6 master                66.5         76.8         77.6

</br>  
</br>

## Question 3 : `test_prepare` 여부별 `total_sco4.5`의 평균과 표준편차 구하기

-   `total_sco4.5` : `math`, `reading`, `writing`의 총합 점수를 4.5점
    만점 단위로 환산한 변수

-   이 때, `math`, `reading`, `writing`의 총합 점수는 300점 만점으로
    간주

    -   **Step 1. `total_sco` 생성** : `math`, `reading`, `writing`의 합

    -   **Step 2. `total_sco4.5` 생성** : `total_sco`의 단위를 4.5점
        만점으로 바꿔 생성  

    -   **Step 3.** `summarize()`를 이용하여, `total_sco4.5`의
        평균(`mean()`) 및 표준편차(`sd()`)를 산출

``` r
studperf %>% # 데이터
  mutate(total_sco = math+reading+writing) %>% # 총합 점수 생성
  mutate(total_sco4.5 = 4.5*(total_sco/300)) %>% # 4.5점 만점으로 환산
  summarize(평균=mean(total_sco4.5),
              표준편차=sd(total_sco4.5)) # 평균, 표준편차 계산
```

    ##      평균  표준편차
    ## 1 3.04968 0.6415797
