# JUnit
## 1) Junit Basics 
## 2) How to write unit testcase and test a software 
## 3) suites 
## 4) reporing

## 1) Junit Basics 

**What is Unit Testing**
*   Testing done by programmer on their own piece of code is called unit testing.
*   Testing means matching expected results with actual results.

**Features of JUnit**
*   JUnit has very rich annotations set to identify the test methods.
*   It provides assertions for testing expected results.
*   JUnit has test runners capability for running tests.
*   It allow us to write quality codes which can make the test results faster.
*   JUnit tests cases are relatively simple to write as compared to other Unit Testing frameworks.
*   JUnit tests can be run automatically and provides its own feedback.
*   JUnit tests can be organized into test suites containing test cases.
*   JUnit can show the Test Progress Bar which changes its color based on results. If it runs successful then it turns **green** and if test fails then it turns to **red**.

**Install junit**
*   apt-get update
*   apt-get install junit
*   apt-get remove junit


## 2) How to write unit testcase and test a software 

### Demo1
#### Source code
```java
package com.suresh.demos;

public class Calculator {
	public Calculator() {
		
	}
	public double add(int a,int b) {
		return a+b;
	}
	public double sub(int a,int b) {
		return a-b;
	}
}
```

#### Testing Code
```java
package com.suresh.demos;

import org.junit.Assert;
import org.junit.Test;

public class CalculatorTest {

	@Test
	public void testAdd() {
		Calculator calc = new Calculator();

		double result = calc.add(20, 10);
		Assert.assertEquals(30, result, 0);

	}

	public void testSub() {
		Calculator calc = new Calculator();

		double result = calc.sub(20, 10);
		Assert.assertEquals(10, result, 0);
	}
}
```


#### To compile and test it
```bash
mvn compile
mvn test
```



### Demo2 - Test Coverage / Conditional Testing
#### Source Code
```java
package com.suresh.demos;

public class Calculator {
	public Calculator() {
		
	}
	public double add(int a,int b) {
		if(a==100) {
			b = b + 10;	
		}
		else if(a == 200) {
			b = b + 20;
		}
			
		return a+b;
	}
	public double sub(int a,int b) {
		return a-b;
	}
}

```
#### Testing Code
```java
//Test Coverage - Conditional Testing
package com.suresh.demos;

import org.junit.Assert;
import org.junit.Test;

public class CalculatorTest {

	@Test
	public void testAdd() {
		Calculator calc = new Calculator();
	
		double result1 = calc.add(100, 10);
		Assert.assertEquals(120, result1, 0);
		
		double result2 = calc.add(200, 10);
		Assert.assertEquals(230, result2, 0);

	}

	public void testSub() {
		Calculator calc = new Calculator();

		double result = calc.sub(20, 10);
		Assert.assertEquals(10, result, 0);
	}
}
```
#### To compile and test it
```bash
mvn compile
mvn test
```

### Demo3 - @Before @After @BeforeClass and @AfterClass
#### Source Code
```java
package com.suresh.demos;

public class Calculator {
	public double add(int a,int b) {
		if(a==100) {
			b = b + 10;	
		}
		else if(a == 200) {
			b = b + 20;
		}
			
		return a+b;
	}
	public double sub(int a,int b) {
		return a-b;
	}
}
```

#### Testing Code
```java
//Before and After
package com.suresh.demos;

import org.junit.After;
import org.junit.AfterClass;
import org.junit.Assert;
import org.junit.Before;
import org.junit.BeforeClass;
import org.junit.Test;

public class CalculatorTest {
	
	Calculator calc = null;
	
	@BeforeClass
	public static void bfClass() {
		System.out.println("Before Class");
	}
	
	@AfterClass
	public static void afClass() {
		System.out.println("After Class");
	}
	
	@Before
	public void setupCalc() {
		System.out.println("Before");
		calc = new Calculator();
	}
	@After
	public void ClosingCalc() {
		System.out.println("After");
	}

	@Test
	public void testAdd() {
		System.out.println("add() test");
	
		double result1 = calc.add(100, 10);
		Assert.assertEquals(120, result1, 0);
		
		double result2 = calc.add(200, 10);
		Assert.assertEquals(230, result2, 0);	
	}
	@Test
	public void testSub() {
		System.out.println("sub() test");
		double result = calc.sub(20, 10);
		Assert.assertEquals(10, result, 0);
	}
}
```
#### To compile and test it
```bash
mvn compile
mvn test
```
## 3) suites 

### Demo4 - Suite 
>In Junit, test suite allows us to aggregate all test cases from multiple classes in one place and run it together.

> To run the suite test, you need to annotate a class using below-mentioned annotations:
*   @Runwith(Suite.class)
*   @SuiteClasses(test1.class,test2.class……)
    <br>OR<br>
*   @Suite.SuiteClasses ({test1.class, test2.class……})
#### Source Code
```java
//For Suite Class
package com.suresh.demos;

public class Calculator {

	public double add(int a,int b) {
		if(a==100) {
			b = b + 10;	
		}
		else if(a == 200) {
			b = b + 20;
		}
			
		return a+b;
	}
	public double sub(int a,int b) {
		return a-b;
	}
}
```

#### Testing Code
```java
package com.suresh.demos;

import org.junit.After;
import org.junit.AfterClass;
import org.junit.Assert;
import org.junit.Before;
import org.junit.BeforeClass;
import org.junit.Test;

public class CalculatorTest {

	@Test
	public void testAdd() {
		System.out.println("Calculator Test 2");
		Calculator calc = new Calculator();
		
		double result1 = calc.add(100, 10);
		Assert.assertEquals(120, result1, 0);
		
		double result2 = calc.add(200, 10);
		Assert.assertEquals(230, result2, 0);
		
	}
}
```
```java
package com.suresh.demos;

import org.junit.After;
import org.junit.AfterClass;
import org.junit.Assert;
import org.junit.Before;
import org.junit.BeforeClass;
import org.junit.Test;

public class CalculatorTest2 {

	@Test
	public void testAdd() {
		System.out.println("Calculator Test 2");
		Calculator calc = new Calculator();
		double result1 = calc.add(100, 20);
		Assert.assertEquals(130, result1, 0);
	}
}
```
```java
package com.suresh.demos;

import org.junit.runner.RunWith;
import org.junit.runners.Suite;

@RunWith(Suite.class)
@Suite.SuiteClasses({
	CalculatorTest.class,
	CalculatorTest2.class
})

public class SuiteClass {

}

```

#### Compile and Test
```bash
## test single test class
mvn clean test -Dtest=com.suresh.demos.CalculatorTest
OR
mvn -Dtest=com.suresh.demos.CalculatorTest test

mvn clean test -Dtest=com.suresh.demos.CalculatorTest2
mvn clean test -Dtest=com.suresh.demos.SuiteClass

## test single test method in a test class
mvn -Dtest=com.suresh.demos.CalculatorTest#testAdd test

```

## 4) reporing
*   JUnit helps us in validation our methods for functionality. But in some cases we have to see the report also for the test cases. 
*   In the process of developing reports, Maven plays an important role as it will make a text, XML and also HTML reports. 
*   All JUnit test cases with the details are printed in the reports

