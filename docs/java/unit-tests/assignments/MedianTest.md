# MedianTest

This unit test uses a few methods from JUnit I haven't covered including `assertArrayEquals` which compares array value equality rather than reference equality and `assertNull` which is the same as `assertEquals(null, someMethod())` 

These unit tests also make use of a JUnit Delta which is basically a margin of error, as doubles are not in any way accurate, so we have to include a margin of error in our tests when comparing any form of floating point number. You provide a delta as a third argument to an `assertEquals` call. 

I also put the elements in the test in the correct order, So if the test fails `expected:` are the values your method SHOULD have returned, but it actually returned what is specified in `actual:` like so:

```
Test Median Computation with real-number arrays.

org.opentest4j.AssertionFailedError: 
Expected :-4.53
Actual   :-463.0
```

Here we can see that when `computeMedian` is given a real-number array, it returns the wrong value. It returned `-463.0` when in fact it should have returned `-4.53` 



```java
import org.junit.jupiter.api.Test;

import static org.junit.jupiter.api.Assertions.*;

/**
 * MedianTest by Rían Errity 12-12-2020
 * Assumes the following functions:
 * computeMedian(double[] array);
 * createSortedArray(double[] arrary);
 * computeRollingAverage(double[] array, int lastXNumbers);
 * convertToString(double[] array);
 * @implNote This does not make use of parameterised testing due to extensive use of Arrays.
 * @author Rían Errity <rian@paradaux.io>
 * @since 12-12-2020
 * */
class MedianTest {

    /**
     * This test uses a "delta" parameter in assertEquals as comparing equality isn't exactly
     * possible in java, as they are not accurate representations of floating-point numbers.
     * The delta value (third parameter) allows some "fuzz" or for the value to be off by that
     * factor.
     * */
    @Test
    void computeMedianTest() {

        System.out.println("Test Median Computation with positive real-number arrays.");
        double[] array = {1.3,2.3,2.3,2.6,6.7,8.9}; // 2.45
        assertEquals(2.45d, Median.computeMedian(array), 0.01d);

        System.out.println("Test Median Computation with negative real-number arrays.");
        array = new double[]{-6.7,-2.3,-1.3,-2.3,-2.6,-8.9}; // 1.8
        assertEquals(-2.45d, Median.computeMedian(array), 0.01d);

        System.out.println("Test Median Computation with real-number arrays.");
        array = new double[]{37478.46, 5853.14, 57478.47, 35742.24, 46742.36, -57356.36}; // 36610.35
        assertEquals(36610.35d, Median.computeMedian(array), 0.01d);

        array = new double[]{-6464,-463,-4.53,4574,5635}; // -4.53
        assertEquals(-4.53d, Median.computeMedian(array), 0.01d);

        System.out.println("Test Median Computation with empty array.");
        assertEquals(0d, Median.computeMedian(new double[0]));

        System.out.println("Test Median Computation with null.");
        assertEquals(0d, Median.computeMedian(null));
    }

    /**
     * If I were to use assertEquals here it would compare the array references here rather than the
     * values within the arrays themselves, which isn't what we're looking to do here. Hence the
     * existence of assertArrayEquals.
     * */
    @Test
    void createSortedArrayTest() {
        System.out.println("Testing Array Sorting with already sorted array.");
        double[] array  = {1, 4, 5, 6, 7, 8, 9, 10, 11, 12};
        assertArrayEquals(array, Median.createSortedArray(array));

        array = new double[]{1, 2, 3, 4, 5};
        assertArrayEquals(array, Median.createSortedArray(array));

        System.out.println("Testing Array Sorting with positive real-number arrays.");
        array = new double[]{1, 4, 5.5465, 6, 7.578, 8, 9.5857, 10, 11.175, 12};
        assertArrayEquals(new double[]{1, 4, 5.5465, 6, 7.578, 8, 9.5857, 10, 11.175, 12},
                Median.createSortedArray(array));

        System.out.println("Testing Array Sorting with random real-number arrays.");
        array = new double[]{0, 1, 43000, -5.5465, -60000, 7.578, 8, 999.5857, -10, 1111111.175,
                12};
        assertArrayEquals(new double[]{-60000, -10, -5.5465, 0, 1, 7.578, 8, 12, 999.5857, 43000,
                1111111.175}, Median.createSortedArray(array));

        array = new double[]{-1, 4, 5.5465, 6, 7.578, 0, -8, 9.5857, 10, -11.175, 12};
        assertArrayEquals(new double[]{-11.175, -8, -1, 0, 4, 5.5465, 6, 7.578, 9.5857, 10, 12},
                Median.createSortedArray(array));

        array = new double[]{-1, -4, -5.5465, -6, -7.578, -8, -9.5857, -10, -11.175, -12};
        assertArrayEquals(new double[]{-12, -11.175, -10, -9.5857, -8, -7.578, -6, -5.5465, -4, -1},
                Median.createSortedArray(array));

        System.out.println("Testing Array Sorting with large whole-number arrays.");
        array = new double[]{346652367, 452547235, 365457234, 346457543};
        assertArrayEquals(new double[]{346457543, 346652367, 365457234, 452547235},
                Median.createSortedArray(array));

        System.out.println("Testing Array Sorting with < 2 entries.");
        array = new double[]{2, 1};
        assertArrayEquals(new double[]{1, 2}, Median.createSortedArray(array));

        array = new double[]{1};
        assertArrayEquals(array, Median.createSortedArray(array));

        System.out.println("Testing Array Sorting with predominantly duplicate entries.");

        array = new double[]{1, 1, 2, 2, 2};
        assertArrayEquals(array, Median.createSortedArray(array));

        array = new double[]{2, 2, 2, 2, 2};
        assertArrayEquals(array, Median.createSortedArray(array));

        array = new double[]{2, 2, 2, 1, 0};
        assertArrayEquals(new double[]{0, 1, 2, 2, 2}, Median.createSortedArray(array));

        System.out.println("Testing Array Sorting with empty arrays.");

        array = new double[0];
        assertArrayEquals(array, Median.createSortedArray(array));

        array = new double[1];
        assertArrayEquals(array, Median.createSortedArray(array));

        System.out.println("Testing Array Sorting with null.");
        assertNull(Median.createSortedArray(null));
    }


    @Test
    void computeRollingAverageTest() {
        double[] array = {6.8, 5.3, -1.5, 5.9, 5.9};

        System.out.println("Testing Rolling average of last 7 numbers in a 5-number array");
        assertEquals(4.48d, Median.computeRollingAverage(array, 7), 0.01d);

        System.out.println("Testing Rolling average of last 5 numbers in a 5-number array");
        assertEquals(4.48d, Median.computeRollingAverage(array, 5), 0.01d);

        System.out.println("Testing Rolling average of last 3 numbers in a 5-number array");
        assertEquals(3.43d, Median.computeRollingAverage(array, 3), 0.01d);

        System.out.println("Testing Rolling average of last 2 numbers in a 5-number array");
        assertEquals(5.9d, Median.computeRollingAverage(array, 2), 0.01d);

        System.out.println("Testing Rolling average of the last number in a 5-number array");
        array = new double[]{6.8, 5.3, -1.5, 5.9, 5.9};
        assertEquals(5.9d, Median.computeRollingAverage(array, 1), 0.01d);

        System.out.println("Testing Rolling average of 0 entries in a 5-number array");
        array = new double[]{6.8, 5.3, -1.5, 5.9, 5.9};
        assertEquals(0d, Median.computeRollingAverage(array, 0));

    }

    @Test
    void convertToStringTest() {
        System.out.println("Testing convertToString with the assignment brief examples.");
        double[] array = {5.0};
        assertEquals("{ 5.0 }", Median.convertToString(array));

        array = new double[]{5.0, 3.0};
        assertEquals("{ 5.0, 3.0 }", Median.convertToString(array));

        array = new double[]{5.0, 3.0, 7.0};
        assertEquals("{ 5.0, 3.0, 7.0 }", Median.convertToString(array));

        array = new double[]{5.0, 3.0, 7.0, 99.0};
        assertEquals("{ 5.0, 3.0, 7.0, 99.0 }", Median.convertToString(array));

        array = new double[]{5.0, 3.0, 7.0, 99.0, 8.0};
        assertEquals("{ 5.0, 3.0, 7.0, 99.0, 8.0 }", Median.convertToString(array));

        System.out.println("Testing convertToString to see if it rounds to one decimal place.");

        array = new double[]{5.33, 3.25, 7.196, 99.835, 8.9258};
        assertEquals("{ 5.3, 3.3, 7.2, 99.8, 8.9 }", Median.convertToString(array));

        array = new double[]{-5.6363, 3.34673, 7.4742, 99.46873, 8.246432};
        assertEquals("{ -5.6, 3.3, 7.5, 99.5, 8.2 }", Median.convertToString(array));

        System.out.println("Testing convertToString with empty arrays.");

        array = new double[0];
        assertEquals("{ }", Median.convertToString(array));

        array = new double[16];
        assertEquals("{ 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 }", Median.convertToString(array));

        System.out.println("Testing convertToString with null.");

        assertEquals("{ }", Median.convertToString(null));
    }
}
```



