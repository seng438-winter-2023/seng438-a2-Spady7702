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

// including the input partitions you have designed

# 3 Test cases developed
    
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

# 4 How the team work/effort was divided and managed

For this lab the group decided to divide themselves into pairs of two to develop the test. Brenek and Ben worked on the test for Range, while Jack and Arion worked on the test for DataUtilities. The group worked on the lab report together. 

# 5 Difficulties encountered, challenges overcome, and lessons learned

Text…

# 6 Comments/feedback on the lab itself

The lab was enjoyable as it allowed us to review unit testing. All of us have used JUnit in past courses, however we have not used it recently so it was nice to have a lab that walked us through writing a unit test, before we wrote one ourselves. Additionally, the lab gave very clear instructions on what we were supposed to do which was very helpul. The brief tutorial section on eclipse was also appreciated as most of us just used Visual Studio in the past. 
