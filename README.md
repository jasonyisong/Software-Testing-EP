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

# EP design case - example

The bank customer enters how much money is deposited (represented as an integer) in a bank savings account. Based on the amount of money, the different interest rates are displayed:

a) 0.3% interest rate if the amount is between €1 and €100.

b) 0.5% interest rate if the amount is between €101 and €1000. 

c) 0.7% interest rate if the amount is above €1000.

The initial balance of the account is €0 because of a lack of information. The deposited amount must be a positive number. Any error leads to a return value of 0. 

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
| T1.4 | EP1*,5      | -100              | 0             |


# 4. Verify test design to ensure completeness

| TCI  | Parameter    | Equivalence Partition | Test Case  |
|------|--------------|-----------------------|------------|
| EP1* | Deposit      | (*)Long.MIN_VALUE..0  | T1.4       |
| EP2  |              | 1..100                | T1.1       |
| EP3  |              | 101..1000             | T1.2       |
| EP4  |              | 1001..Long.MAX_VALUE  | T1.3       |
| EP5  | Return Value | 0                     | T1.4       |
| EP6  |              | 0.30%                 | T1.1       |
| EP7  |              | 0.50%                 | T1.2       |
| EP8  |              | 0.70%                 | T1.3       |

# 5. Implementation of tests
# 6. Execution of tests

```java
package cs265;

import org.testng.annotations.Test;
import static org.testng.Assert.assertEquals;
import org.testng.annotations.DataProvider;

public class InterestCalculatorTest {

	// test data
	private static Object[][] testData = new Object[][] {
			// id, variable1, variable2, ... variableN, expected
		    {"T1.1",	   50,		 0.003},
		    {"T1.2",  	  150, 		 0.005},
		    {"T1.3", 	 2000, 		 0.007}, 
		    {"T1.4", 	 -100,    	     0},
	};

	@DataProvider(name = "data")
	public Object[][] getTestData() {
		return testData;
	}

	@Test(dataProvider = "data")
	public void test(String id, double variable1,  double expected) {
		 assertEquals(InterestCalculator.interestRate(variable1), expected);
	}
}
```

# 7. Examination of test results
