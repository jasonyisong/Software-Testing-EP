# Software-Testing-EP

Study Notes - Maynooth Universtiy SOFTWARE TESTING (CS265) by Dr. Joe Timoney

# Equivalence Partitions

- ST ACTIVITIES

1. Analysis of SW / spec that informs the test
2. Identify test coverage items
3. Identify test cases
4. Verify test design to ensure completeness
5. Implementation of tests
6. Execution of tests
7. Examination of test results

# 1. Analysis of SW / spec that informs the test

| Parameter    | Equivalence Partition |         |
|--------------|-----------------------|---------|
| Deposit      | (*)Long.MIN_VALUE..0  | Input   |
|              | 1..100                |         |
|              | 101..1000             |         |
|              | 1001..Long.MAX_VALUE  |         |

| Parameter    | Equivalence Patition  |         |
|--------------|-----------------------|---------|
| Return Value | 0                     | Output  |
|              | 0.30%                 |         |
|              | 0.50%                 |         |
|              | 0.70%                 |         |


# 2. Identify test coverage items

| TCI  | Parameter    | Equivalence Partition | Test Case              |
|------|--------------|-----------------------|------------------------|
| EP1* | Deposit      | (*)Long.MIN_VALUE..0  | To be completed later  |
| EP2  |              | 1..100                |                        |
| EP3  |              | 101..1000             |                        |
| EP4  |              | 1001..Long.MAX_VALUE  |                        |
| EP5  | Return Value | 0                     |                        |
| EP6  |              | 0.30%                 |                        |
| EP7  |              | 0.50%                 |                        |
| EP8  |              | 0.70%                 |                        |


# 3. Identify test cases

| Case | Parameter    | Equivalence Partition | Test  |
|------|--------------|-----------------------|-------|
| EP1* | Deposit      | (*)Long.MIN_VALUE..0  |       |
| EP2  |              | 1..100                |       |
| EP3  |              | 101..1000             |       |
| EP4  |              | 1001..Long.MAX_VALUE  |       |
| EP5  | Return Value | 0                     |       |
| EP6  |              | 0.30%                 |       |
| EP7  |              | 0.50%                 |       |
| EP8  |              | 0.70%                 |       |

| Parameter    | Equivalence Partition | Equivalence Value  |
|--------------|-----------------------|--------------------|
| Deposit      | (*)Long.MIN_VALUE..0  | -100               |
|              | 1..100                | 50                 |
|              | 101..1000             | 150                |
|              | 1001..Long.MAX_VALUE  | 2000               |
| Return Value | 0                     | 0                  |
|              | 0.30%                 | 0.30%              |
|              | 0.50%                 | 0.50%              |
|              | 0.70%                 | 0.70%              |


| ID   | TCI Covered | Inputs<br/>Equivalence Value | Exp. Result<br/>Return Value  |
|------|-------------|-------------------|---------------|
| T1.1 | EP2,6       | 50                | 0.30%         |
| T1.2 | EP3,7       | 150               | 0.50%         |
| T1.3 | EP4,8       | 2000              | 0.70%         |



# 4. Verify test design to ensure completeness
# 5. Implementation of tests
# 6. Execution of tests
# 7. Examination of test results
