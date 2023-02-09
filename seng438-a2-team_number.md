**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report \#2 – Requirements-Based Test Generation**

| Group \#:      |     |
| -------------- | --- |
| Student Names: |     |
|Brenek Spademan               |30060822    |
|Ben Leggett                |30114359     |
|Arion Hamel                |30112662     |
|Jack Rovere                |30085670     |

# 1 Introduction

Text…

# 2 Detailed description of unit test strategy

<h2>DataUtilities Testing | Jack & Arion </h2>

Before beginning testing we go through a setUp() process, in which we create a new Mockery object to mock Values2D and KeyedValues objects.

<h3>1. calculateColumnTotal(Values2D data, int column)</h3>
   
Each function utilizes as Values2D mock when summing the values in the column provided.

* First test: 'calculateColumnTotalForFourPositiveValues()' mocks a Values2D object as follows: {3.0, 2.5, 7.0, 10.5} in (0,0), (1,0), (2,0), and (3,0) respectively. The test method expects a sum of 23.0 to be returned.

* Second test: 'calculateColumnTotalForFourNegativeValues()' is similar to the test above, differing by only inputting negative values in the Values2D object. The mock Values2D object is as follows: {-1.0, -2.5, -7.0, -14.5} in (0,0), (1,0), (2,0), and (3,0) respectively. The test method expects a sum of -25.0 to be returned.

* Third test: 'exceptionThrownOnInvalidDataColumn()' provides an invalid Values2D argument. As per the documentation of calculateColumnTotal(), an 'InvalidParameterException' should be thrown. exceptionThrownOnInvalidDataColumn ensures that the proper exception is thrown from calculateColumnTotal().

We test both negative and positive numbers as a form of equivalence partitioning and boundary value analysis. 'exceptionThrownOnInvalidDataColumn()' involves use case testing, in a scenario where a user inputs incorrect data to the function. 

<h3>2. calculateRowTotal(Values2D data, int row)</h3>

Each function utilizes a Values2D mock when summing the values in the row provided.
   
* First test: 'calculateRowTotalForFourPositiveValues()' mocks a Values2D object as follows {3.5, 2.0, 7.5, 15.0} in (0, 0), (0, 1), (0, 2), and (0, 3) respectively. The test method expects a sum of 28.0 to be returned.

* Second test: 'calculateRowTotalForFourNegativeValues()' mocks a Values2D object as follows {-2.5, -5.5, -7.5, -15.0} in (0, 0), (0, 1), (0, 2), and (0, 3) respectively. The test method expects a sum of -30.5 to be returned.

* Third test: 'exceptionThrownOnInvalidDataRow()' provides an invalid Values2D argument. As per the documentation of calculateRowTotal(), an 'InvalidParameterException' should be thrown. exceptionThrownOnInvalidDataColumn ensures that the proper exception is thrown from calculateRowTotal().
    
We test both negative and positive numbers as a form of equivalence partitioning and boundary value analysis. 'exceptionThrownOnInvalidDataRow()' involves use case testing, in a scenario where a user inputs incorrect data to the function. 

Mocking in both 'calculateColumnTotal' and 'calculateRowTotal' is useful as we do not have to rely on the Values2D class as a dependency. We are able to manufacture our expected output, and test accordingly. However due to our strong control over the test cases, we may lead to overspecification of the test case; limiting the scope of our testing. Similarly, mocking increases the complexity of the test case, making it more difficult to understand for both users and developers. 

<h3>3. createNumberArray(double[] data)</h3>

There are no mocking objects used in the following test cases.

createNumberArray takes in an array of doubles, and creates an array of Number objects.

* First test: 'createEmptyNumberArray()' creates a 'double[] data' with no values inside. It is then passed towards DataUtilities.createNumberArray() as an argument. The test case expects 'createNumberArray()' to return an empty array of Number objects.

* Second test: 'createNumberArrayPositiveValues()' passes a 'double[] data' with values = {1.0, 2.0, 3.0, 4.0, 5.0} into DataUtilites.createNumberArray(). The test case expects 'createNumberArray()' to return an array of Number objects = {1.0, 2.0, 3.0, 4.0, 5.0}. 

* Third test: 'createNumberArrayNegativeValues()' passes a 'double[] data' with values = {-1.0, -2.0, -3.0, -4.0, -5.0}. It is then passed towards Data.Utilities.createNumberArray() as an argument. The test case expects 'createNumberArray()' to return an array of Number objects = {-1.0, -2.0, -3.0, -4.0, -5.0}.
    
We test both negative and positive numbers as a form of equivalence partitioning and boundary value analysis. createEmptyNumberArray() acts as a boundary value and use case test, evaluating how the function behaves with an unexpected input. 

<h3>4. createNumberArray2D(double[][] data)</h3>

There are no mocking objects used in the following test cases.

createNumberArray2D takes in a double (2D) array of doubles, and creates a 2D array of Number objects.

* First test: 'create2DEmptyNumberArray()' creates a 'double[][] data' with no values inside. It is then passed towards DataUtilities.createNumberArray2D() as an argument. The test case expects 'createNumberArray2D()' to return an empty 2D array of Number objects.

* Second test: 'create2DNumberArrayPositiveValues()' passes a 'double[][] data' with values = {{1.0, 2.0, 3.0, 4.0, 5.0}, {6.0, 7.0, 8.0}, {1.0}} into DataUtilites.createNumberArray2D(). The test case expects 'createNumberArray2D()' to return a 2D array of Number objects = {{1.0, 2.0, 3.0, 4.0, 5.0}, {6.0, 7.0, 8.0}, {1.0}}. 

* Third test: 'create2DNumberArrayNegativeValues()' passes a 'double[] data' with values = {{-1.0, -2.0, -3.0, -4.0, -5.0}, {-6.0, -7.0, -8.0}, {-1.0}}. It is then passed towards Data.Utilities.createNumberArray2D() as an argument. The test case expects 'createNumberArray2D()' to return a 2D array of Number objects = {{-1.0, -2.0, -3.0, -4.0, -5.0}, {-6.0, -7.0, -8.0}, {-1.0}}.
    
We test both negative and positive numbers as a form of equivalence partitioning and boundary value analysis. createEmptyNumberArray2D() acts as a boundary value and use case test, evaluating how the function behaves with an unexpected input. 

Neither createNumberArray or createNumberArray2D's tests utilize mocking, thus a discussion of mocking's benefits and drawbacks is not applicable. 

<h3>5. getCumulativePercentages(KeyedValues data)</h3>

Each test utilizes the KeyedValues mocking object created above. 

DataUtilities.getCumulativePercentages() receives a KeyedValues object - containing key/value pairs - and returns a KeyedValues object in which each key/value pair represents the cumulative percentage thus far of each key/value pair provided. 

* First test: 'exceptionThrownOnInvalidPercentageData()' passes an invalid argument to 'DataUtilites.getCumulativePercentages()'. Given the documentation of 'getCumulativePercentages()', the test case expects an 'InvalidParameterException' to be thrown. 

* Second test: 'cumulatePercentageForZeroValueKeyPairs()' creates a 'String[] names' with values = {"KeyOne", "KeyTwo", "KeyThree"} and a 'double[] values' with values = {0, 0, 0}. This simulates the data in a KeyedValues object as follows: (KeyOne, 0), (KeyTwo, 0), (KeyThree, 0). The test case expects 'getCumulativePercentages()' to return a NaN Divide by zero, as there should be a divide by zero error in calculating the cumulative percentage. 

* Third test: 'cumulatePercentageForPositiveValueKeyPairs()' creates a 'String[] names' with values = {"KeyOne", "KeyTwo", "KeyThree"} and a 'double[] values' with values = {5.0, 9.0, 2.0}. This simulates the data in a KeyedValues object as follows: (KeyOne, 5.0), (KeyTwo, 9.0), (KeyThree, 2.0). The test case expects 'getCumulativePercentages()' to return 0.3125 when queried for the value of the resultant KeyOne.

* Fourth test: 'cumulatePercentageForNegativeValueKeyPairs()' creates a 'String[] names' with values = {"KeyOne", "KeyTwo", "KeyThree"} and a 'double[] values' with values = {-5.0, -9.0, -2.0}. This simulates the data in a KeyedValues object as follows: (KeyOne, -.50), (KeyTwo, -9.0), (KeyThree, -2.0). The test case expects 'getCumulativePercentages()' to return 0.3125 when queried for the value of the resultant KeyOne.
    
We test both negative and positive numbers as a form of equivalence partitioning and boundary value analysis. exceptionThrownOnInvalidPercentageData() acts as a boundary value and use case test, evaluating how the function behaves with an unexpected input, and ensuring an 'InvalidParameterException' is properly thrown. Similarly 'cumulatePercentageForZeroValueKeyPairs()' is a boundary value and use case test, as it provides an unusual input that should provide an error if handled properly. 

Mocking in 'getCumulativepercentages()' was useful in isolated the test component and functionality being testing. We effectively eliminated the KeyedValues class dependency, and were able to manufacture our expected output, and test accordingly. However the tests became significantly more complex and may not accurately reflect the behaviour of the code in a real-world scenario. Using KeyedValues objects may produce differing results. 

# 3 Test cases developed

<h2><what> Testing | Brenek & Ben </h2>
	
    package org.jfree.data.test;
    
    import static org.junit.Assert.*;
    import org.jfree.data.Range;
    import org.junit.*;

    public class RangeTest {
        private Range exampleRange;
        @BeforeClass 
        public static void setUpBeforeClass() throws Exception {
        }

        @Before
        public void setUp() throws Exception { exampleRange = new Range(-1, 1);
        }


        @Test
        public void centralValueShouldBeZero() {
            assertEquals("The central value of -1 and 1 should be 0",
            0, exampleRange.getCentralValue(), .000000001d);
        }

        @Test
        public void lowerBoundShouldBeNegativeOne() {
            assertEquals("The lower bound of -1 and 1 should be -1", -1, exampleRange.getLowerBound(), .000000001d);
        }

        @Test
        public void upperBoundShouldBeOne() {
            assertEquals("The upper bound of -1 and 1 should be 1", 1, exampleRange.getUpperBound(), .000000001d);
        }

        @Test
        public void lengthShouldBeTwo() {
            assertEquals("The length of -1 and 1 should be 2", 2, exampleRange.getLength(), .000000001d);
        }

        @Test
        public void rangeContainsZero() {
            assertEquals("The range of -1 and 1 should contain 0", true, exampleRange.contains(0));
        }

        @Test
        public void rangeDoesNotContainTwo() {
            assertEquals("The range of -1 and 1 should not contain 2", false, exampleRange.contains(2));
        }

        @After
        public void tearDown() throws Exception {
        }

        @AfterClass
        public static void tearDownAfterClass() throws Exception {
        }
    }
    
<h2>DataUtilities Testing | Jack & Arion </h2>
   
	private Mockery mockingContext;
	private Values2D values;
	private KeyedValues kValues;
	
	@BeforeClass
	public static void setUpBeforeClass() throws Exception {}
	
	@Before
	public void setUp() throws Exception {
		mockingContext = new Mockery();
		values = mockingContext.mock(Values2D.class);
		kValues = mockingContext.mock(KeyedValues.class);
	}
	
	@Test
	public void calculateColumnTotalForFourPositiveValues() {
		mockingContext.checking(new Expectations() {
			{
				one(values).getRowCount();
				will(returnValue(4));
				one(values).getValue(0, 0);
				will(returnValue(3.0));
				one(values).getValue(1, 0);
				will(returnValue(2.5));
				one(values).getValue(2, 0);
				will(returnValue(7.0));
				one(values).getValue(3, 0);
				will(returnValue(10.5));
			}
		});
		
		double result = DataUtilities.calculateColumnTotal(values, 0);
		
		assertEquals("Result should equal 23.0", 23.0, result, .000000001d);
	}
	
	@Test
	public void calculateColumnTotalForFourNegativeValues() {
		mockingContext.checking(new Expectations() {
			{
				one(values).getRowCount();
				will(returnValue(4));
				one(values).getValue(0, 0);
				will(returnValue(-1.0));
				one(values).getValue(1, 0);
				will(returnValue(-2.5));
				one(values).getValue(2, 0);
				will(returnValue(-7.0));
				one(values).getValue(3, 0);
				will(returnValue(-14.5));
			}
		});
		
		double result = DataUtilities.calculateColumnTotal(values, 0);
		
		assertEquals("Result should equal -25.0", -25.0, result, .000000001d);
	}
	
	@Test
	public void exceptionThrownOnInvalidDataColumn() {
		boolean correctExceptionThrown = false;
		try {
			DataUtilities.calculateColumnTotal(null, 0);
		} catch (Exception e) {
			correctExceptionThrown = e instanceof InvalidParameterException;
		}
		assertTrue("Program expected to throw InvalidParameterException", correctExceptionThrown);
	}
	
	@Test
	public void calculateRowTotalForFourPositiveValues() {
		mockingContext.checking(new Expectations() {
			{
				one(values).getColumnCount();
				will(returnValue(4));
				one(values).getValue(0, 0);
				will(returnValue(3.5));
				one(values).getValue(0, 1);
				will(returnValue(2.0));
				one(values).getValue(0, 2);
				will(returnValue(7.5));
				one(values).getValue(0, 3);
				will(returnValue(15.0));
			}
		});
		
		double result = DataUtilities.calculateRowTotal(values, 0);
		
		assertEquals("Result should equal 28.0", 28.0, result, .000000001d);
	}
	
	@Test
	public void calculateRowTotalForFourNegativeValues() {
		mockingContext.checking(new Expectations() {
			{
				one(values).getColumnCount();
				will(returnValue(4));
				one(values).getValue(0, 0);
				will(returnValue(-2.5));
				one(values).getValue(0, 1);
				will(returnValue(-5.5));
				one(values).getValue(0, 2);
				will(returnValue(-7.5));
				one(values).getValue(0, 3);
				will(returnValue(-15.0));
			}
		});
		
		double result = DataUtilities.calculateRowTotal(values, 0);
		
		assertEquals("Result should equal -30.5", -30.5, result, .000000001d);
	}
	
	@Test
	public void exceptionThrownOnInvalidDataRow() {
		boolean correctExceptionThrown = false;
		try {
			DataUtilities.calculateRowTotal(null, 0);
		} catch (Exception e) {
			correctExceptionThrown = e instanceof InvalidParameterException;
		}
		assertTrue("Program expected to throw InvalidParameterException", correctExceptionThrown);
	}
	
	@Test
	public void createEmptyNumberArray() {
		double[] data = {};
		
		Number[] result = DataUtilities.createNumberArray(data);
		Number[] expected = {};
		
		assertTrue("Number array created with incorrect values", Arrays.equals(expected, result));
	}
	
	@Test
	public void createNumberArrayPositiveValues() {
		double[] data = {1.0, 2.0, 3.0, 4.0, 5.0};
		
		Number[] result = DataUtilities.createNumberArray(data);
		Number[] expected = {1.0, 2.0, 3.0, 4.0, 5.0};
		
		assertTrue("Number array created with incorrect values", Arrays.equals(expected, result));
	}
	
	@Test
	public void createNumberArrayNegativeValues() {
		double[] data = {-1.0, -2.0, -3.0, -4.0, -5.0};
		
		Number[] result = DataUtilities.createNumberArray(data);
		Number[] expected = {-1.0, -2.0, -3.0, -4.0, -5.0};
		
		assertTrue("Number array created with incorrect values", Arrays.equals(expected, result));
	}
	
	@Test
	public void createEmpty2DNumberArray() {
		double[][] data = {};
		
		Number[][] result = DataUtilities.createNumberArray2D(data);
		Number[][] expected = {};
		
		assertTrue("2D Number array created with incorrect values", Arrays.equals(expected, result));
	}
	
	@Test
	public void create2DNumberArrayPositiveValues() {
		double[][] data = {{1.0, 2.0, 3.0, 4.0, 5.0}, {6.0, 7.0, 8.0}, {1.0}};
		
		Number[][] result = DataUtilities.createNumberArray2D(data);
		Number[][] expected = {{1.0, 2.0, 3.0, 4.0, 5.0}, {6.0, 7.0, 8.0}, {1.0}};
		
		assertTrue("2D Number array created with incorrect values", Arrays.equals(expected, result));
	}
	
	@Test
	public void create2DNumberArrayNegativeValues() {
		double[][] data = {{-1.0, -2.0, -3.0, -4.0, -5.0}, {-6.0, -7.0, -8.0}, {-1.0}};
		
		Number[][] result = DataUtilities.createNumberArray2D(data);
		Number[][] expected = {{-1.0, -2.0, -3.0, -4.0, -5.0}, {-6.0, -7.0, -8.0}, {-1.0}};
		
		assertTrue("2D Number array created with incorrect values", Arrays.equals(expected, result));
	}
	
	@Test
	public void exceptionThrownOnInvalidPercentageData() {
		boolean correctExceptionThrown = false;
		try {
			DataUtilities.getCumulativePercentages(null);
		} catch (Exception e) {
			correctExceptionThrown = e instanceof InvalidParameterException;
		}
		assertTrue("Program expected to throw InvalidParameterException", correctExceptionThrown);
	}
	
	@Test
	public void cumulatePercentageForZeroValueKeyPairs() {
		mockingContext.checking(new Expectations() {
			{
				final int KEY_AMOUNT = 3;
				String[] names = {"KeyOne", "KeyTwo", "KeyThree"};
				double[] values = {0, 0, 0};
				for (int i = 0; i < KEY_AMOUNT; i++) {
					allowing(kValues).getValue(i);
					will(returnValue(values[i]));
					allowing(kValues).getKey(i);
					will(returnValue(names[i]));
				}
				allowing(kValues).getItemCount();
				will(returnValue(KEY_AMOUNT));
				allowing(kValues).getKeys();
				will(returnEnumeration(Arrays.asList(names)));
			}
		});
		
		KeyedValues result = DataUtilities.getCumulativePercentages(kValues);
		assertEquals("Result should be NaN, divide by zero", Double.NaN, result.getValue("KeyOne"));
	}
	
	@Test 
	public void cumulatePercentageForPositiveValueKeyPairs() {
		mockingContext.checking(new Expectations() {
			{
				final int KEY_AMOUNT = 3;
				String[] names = {"KeyOne", "KeyTwo", "KeyThree"};
				double[] values = {5.0, 9.0, 2.0};
				for (int i = 0; i < KEY_AMOUNT; i++) {
					allowing(kValues).getValue(i);
					will(returnValue(values[i]));
					allowing(kValues).getKey(i);
					will(returnValue(names[i]));
				}
				allowing(kValues).getItemCount();
				will(returnValue(KEY_AMOUNT));
				allowing(kValues).getKeys();
				will(returnEnumeration(Arrays.asList(names)));
			}
		});
		
		KeyedValues result = DataUtilities.getCumulativePercentages(kValues);
		assertEquals("Result should equal 0.3125", 0.3125, result.getValue("KeyOne").doubleValue(), .000000001d);
	}
	
	@Test 
	public void cumulatePercentageForNegativeValueKeyPairs() {
		mockingContext.checking(new Expectations() {
			{
				final int KEY_AMOUNT = 3;
				String[] names = {"KeyOne", "KeyTwo", "KeyThree"};
				double[] values = {-5.0, -9.0, -2.0};
				for (int i = 0; i < KEY_AMOUNT; i++) {
					allowing(kValues).getValue(i);
					will(returnValue(values[i]));
					allowing(kValues).getKey(i);
					will(returnValue(names[i]));
				}
				allowing(kValues).getItemCount();
				will(returnValue(KEY_AMOUNT));
				allowing(kValues).getKeys();
				will(returnEnumeration(Arrays.asList(names)));
			}
		});
		
		KeyedValues result = DataUtilities.getCumulativePercentages(kValues);
		assertEquals("Result should equal 0.3125", 0.3125, result.getValue("KeyOne").doubleValue(), .000000001d);
	}
	
	
	@After
        public void tearDown() throws Exception {}

    @AfterClass
        public static void tearDownAfterClass() throws Exception {}
	}

# 4 How the team work/effort was divided and managed
							       
<h2>Brenek & Ben</h2>

<h2>Jack & Arion</h2>

Jack and Arion handled the DataUtilities test cases. Jack was responsible for utilizing jMock, JUnit tests and Eclipse to implement the test cases. Arion created the test plan and aided Jack where possible in the implementation of the plan. Ben and Brenek did one mocking test each to learn the functionality of mocking in JUnit as well. 

# 5 Difficulties encountered, challenges overcome, and lessons learned

<h2>Jack & Arion</h2> 

Jack and Arion encountered difficulties figuring out the semantics behind jMock while attempting to mock Values2D and KeyedValues objects in their tests. Eventually they learned the proper syntax and gained valuable experience in jMock. 

# 6 Comments/feedback on the lab itself

The lab was enjoyable as it allowed us to review unit testing. All of us have used JUnit in past courses, however we have not used it recently so it was nice to have a lab that walked us through writing a unit test, before we wrote one ourselves. Additionally, the lab gave very clear instructions on what we were supposed to do which was very helpul. The brief tutorial section on eclipse was also appreciated as most of us just used Visual Studio in the past. 
