# PerniciousNumbersTest

```java
import org.junit.jupiter.api.Assertions;
import org.junit.jupiter.api.Test;

public class PerniciousNumbersTest {

    @Test
    public void isPerniciousTest() {
        System.out.println("isPernicious: false");
        Assertions.assertFalse(PerniciousNumbers.isPernicious(0));
        Assertions.assertFalse(PerniciousNumbers.isPernicious(8));
        Assertions.assertFalse(PerniciousNumbers.isPernicious(1));
        Assertions.assertFalse(PerniciousNumbers.isPernicious(1));

        System.out.println("isPernicious: true");
        Assertions.assertTrue(PerniciousNumbers.isPernicious(3));
        Assertions.assertTrue(PerniciousNumbers.isPernicious(5));
        Assertions.assertTrue(PerniciousNumbers.isPernicious(80));
        Assertions.assertTrue(PerniciousNumbers.isPernicious(100));
    }



    @Test
    public void isPrimeTest() {
        System.out.println("isPrime: true");
        Assertions.assertTrue(PerniciousNumbers.isPrime(2));
        Assertions.assertTrue(PerniciousNumbers.isPrime(3));
        Assertions.assertTrue(PerniciousNumbers.isPrime(5));
        Assertions.assertTrue(PerniciousNumbers.isPrime(7));
        Assertions.assertTrue(PerniciousNumbers.isPrime(11));
        Assertions.assertTrue(PerniciousNumbers.isPrime(3));
        Assertions.assertTrue(PerniciousNumbers.isPrime(17));
        Assertions.assertTrue(PerniciousNumbers.isPrime(19));
        Assertions.assertTrue(PerniciousNumbers.isPrime(23));
        Assertions.assertTrue(PerniciousNumbers.isPrime(29));
        Assertions.assertTrue(PerniciousNumbers.isPrime(31));
        Assertions.assertTrue(PerniciousNumbers.isPrime(37));

        System.out.println("isPrime: false (negative)");
        Assertions.assertFalse(PerniciousNumbers.isPrime(-1));
        Assertions.assertFalse(PerniciousNumbers.isPrime(-2));
        Assertions.assertFalse(PerniciousNumbers.isPrime(-4));
        Assertions.assertFalse(PerniciousNumbers.isPrime(-5));
        Assertions.assertFalse(PerniciousNumbers.isPrime(-7));

        System.out.println("isPrime: false (positive)");
        Assertions.assertFalse(PerniciousNumbers.isPrime(1));
        Assertions.assertFalse(PerniciousNumbers.isPrime(0));
        Assertions.assertFalse(PerniciousNumbers.isPrime(6));
        Assertions.assertFalse(PerniciousNumbers.isPrime(648));
        Assertions.assertFalse(PerniciousNumbers.isPrime(15));
    }

    @Test
    public void countBinaryOnesTest() {
        Assertions.assertEquals(PerniciousNumbers.countBinaryOnes(0), 0);
        Assertions.assertEquals(PerniciousNumbers.countBinaryOnes(1), 1);
        Assertions.assertEquals(PerniciousNumbers.countBinaryOnes(3), 2);
        Assertions.assertEquals(PerniciousNumbers.countBinaryOnes(6), 2);
        Assertions.assertEquals(PerniciousNumbers.countBinaryOnes(12), 2);
        Assertions.assertEquals(PerniciousNumbers.countBinaryOnes(14), 3);
        Assertions.assertEquals(PerniciousNumbers.countBinaryOnes(19), 3);
        Assertions.assertEquals(PerniciousNumbers.countBinaryOnes(21), 3);
    }

    @Test
    public void getBinaryString() {
        Assertions.assertEquals(PerniciousNumbers.getBinaryString(0), "0");
        Assertions.assertEquals(PerniciousNumbers.getBinaryString(1), "1");
        Assertions.assertEquals(PerniciousNumbers.getBinaryString(-5), "-101");
        Assertions.assertEquals(PerniciousNumbers.getBinaryString(-50),"-110010");
        Assertions.assertEquals(PerniciousNumbers.getBinaryString(-100), "-1100100");
        Assertions.assertEquals(PerniciousNumbers.getBinaryString(100), "1100100");
    }

}
```




