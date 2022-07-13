# T-Evos

T-Evos: A Large-Scale Longitudinal Study on CI Test Execution and Coverage Evolution

## Description

T-Evos is a dataset on test result and coverage evolution, covering 8,093 consecutive commits across 12 open-source Java projects.

We present the 12 studied open-source Java projects below. Note that we also shared three additional projects (i.e., commons-lang, commons-collections and joda-time) for tranparency of our project selection process, but they are not included in our study.

| Projects               | Purpose | Testing practices | Start date for CI configuration on GitHub | CI configuration commit |
|------------------------|----------|----------|----------|----------|
| commons-cli            | command line arguments and options parser | unit testing | Nov 17, 2016 |[b486fbd](https://github.com/apache/commons-cli/commit/b486fbd) |
| commons-codec          | encoding utility | unit testing | Nov 16, 2016 | [1491a45](https://github.com/apache/commons-codec/commit/1491a45) |
| commons-compress       | compression and archiving | unit, integration testing | Nov 16, 2016 | [db8bdf6](https://github.com/apache/commons-compress/commit/db8bdf6) |
| commons-csv            | csv reading and writing | unit, performance testing | Nov 17, 2016 | [fbc11c2](https://github.com/apache/commons-csv/commit/fbc11c2) |
| commons-math           | math and stats computation | unit testing | Dec 3, 2015 | [7d32a99](https://github.com/apache/commons-math/commit/7d32a99) |
| gson                   | JSON serializer/deserializer | unit, functional, performance testing, fuzzing | Jun 18, 2015 | [cd38056](https://github.com/google/gson/commit/cd38056) |
| jackson-core           | data parser and generator | unit, performance testing, fuzzing | Feb 17, 2014 | [4a2c548](https://github.com/FasterXML/jackson-core/commit/4a2c548) |
| jackson-dataformat-xml | XML encoder | unit, functional testing, fuzzing | Feb 27, 2015  | [2c4b875](https://github.com/FasterXML/jackson-dataformat-xml/commit/2c4b875) |
| jfreechart             | chart drawing | unit testing | Oct 2, 2020* | [4eff8cf](https://github.com/jfree/jfreechart/commit/4eff8cf) |
| junit4                 | testing framework | unit, functional testing | Dec 13, 2013 | [26e5df2](https://github.com/junit-team/junit4/commit/26e5df2) |
| jsoup                  | HTML fetching, extracting, and data manipulation | unit testing | May 14, 2014 | [3475eaf](https://github.com/jhy/jsoup/commit/3475eaf) |
| fastjson               | JSON parser and generator | unit, functional testing | Apr 16, 2016 | [071aa91](https://github.com/alibaba/fastjson/commit/071aa91) |


## Data summary
We summarize the dataset below.

| Projects               | Total LOC | Test LOC (%) | Date range | Studied commits | Compiled commits  |
|------------------------|----------|----------|----------|----------|----------|
| commons-cli            | 12.2k | 4.3k (35%) | (2002/06/10, 2020/09/19) | 965   | 558 |
| commons-codec          | 30.9k | 14.6k (47%)| (2012/08/20, 2020/10/11) | 1,000 | 709 |
| commons-compress       | 65.8k | 23.1k (35%)| (2017/01/07, 2020/10/13) | 1,000 | 337 |
| commons-csv            | 10.3k | 7.2k (70%) | (2013/03/20, 2020/10/03) | 1,000 | 936 |
| commons-math           | 199.2k| 76.0k (38%)| (2015/04/26, 2020/08/10) | 1,000 | 551 |
| gson                   | 38.4k | 15.2k (40%)| (2011/03/29, 2020/05/13) | 1,000 | 942 |
| jackson-core           | 50.8k | 19.0k (37%)| (2014/12/05, 2019/12/30) | 1,000 | 453 |
| jackson-dataformat-xml | 564.7k| 7.6k (1%)  | (2014/11/12, 2020/10/16) | 1,000 | 203 |
| jfreechart             | 159.1k| 40.0k (25%)| (2013/08/15, 2020/03/10) | 1,000 | 439 |
| junit4                 | 37.9k | 20.4k (54%)| (2013/02/05, 2021/02/13) | 1,000 | 997 |
| jsoup                  | 86.8k | 9.4k (11%) | (2011/07/02, 2020/03/07) | 1,000 | 990 |
| fastjson               | 354.6k| 138.0k (39%)| (2018/09/03, 2021/04/05)| 1,000 | 978 |


## Structure
We present T-Evos repository structure below.

```
│
├── project1
│   ├── build_logs 
│   │   └── 0303dc_out.txt			(build logs)
│   │ 
│   ├── active_tests 
│   │   └── 0303dc.json				(list of active tests)
│   │ 
│   ├── test_status 
│   │   ├── test_status.csv			(per-commit test status)
│   │ 	    (or)
│   │   └── 0303dc.csv
│   │
│   └─ test_status.csv				(overall test status)
│
├── deflaker
│   └─ flaky_tests.csv				(list of flaky tests, and the commits that detect them)
│
└─ ...
```


## Potential research directions


**Studying and understanding quality issues in test code**: Our findings indicate that there may be pre-existing issues causing test cases to fail. Future studies may use our dataset to further study the quality of test code throughout software evolution.

**Studying code coverage evolution**: Future studies may use our dataset to study the evolution of test failures that do not involve any coverage change. Future studies may investigate whether there exists any correlation between the increased coverage and faster failure resolution time. It is also interesting to investigate whether better coverage helps to detect and resolve the failures.  

**Studying the roles of test cases that failed repetitively**: The same test failure may be resolved but the same test case may fail again multiple times during the evolution due to other reasons. Our dataset may be used to study the characteristics of such test cases, and whether it is possible to help developers enhance the quality of both the test code and the tested source code to prevent future bugs.  

**Studying how code change history may assist fault localization and program repair techniques**: As there exist many automated testing techniques that leverage code coverage (i.e., fault localization and program repair techniques), future studies may use our dataset to propose new or enhance current techniques. Future studies may mine the past code coverage data to complement the decrease in coverage. In addition, future studies may analyze the code changes that we collected in the dataset and examine how recent code changes contribute to test failures. Future studies might even use our dataset for benchmarking automated testing techniques.  

**Studying how build configurations may affect test result**: Future studies may analyze the build logs to study how the quality of the build scripts contributes to test failures. 