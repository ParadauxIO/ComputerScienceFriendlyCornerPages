# ThreeNumbersTest
```java
import org.junit.jupiter.api.Assertions;
import org.junit.jupiter.api.Test;

public class ThreeNumbersTest {

//    Used to generate test cases

//    private static int randomNumber(int min, int max) {
//        Random random = new Random();
//        return random.nextInt(max - min) + min;
//    }


//    public static void main(String[] args) {
//        int a, b, c;
//        for (int i = 0; i != 20; i++) { }
//    }

    @Test
    public void medianOfTest() {
        System.out.println("medianOf: Positive Cases");
        Assertions.assertEquals(ThreeNumbers.medianOf(125, 300, 88), 125);
        Assertions.assertEquals(ThreeNumbers.medianOf(272, 58, 324), 272);
        Assertions.assertEquals(ThreeNumbers.medianOf(410, 174, 310), 310);
        Assertions.assertEquals(ThreeNumbers.medianOf(376, 109, 25), 109);
        Assertions.assertEquals(ThreeNumbers.medianOf(23, 162, 102), 102);
        Assertions.assertEquals(ThreeNumbers.medianOf(487, 258, 147), 258);
        Assertions.assertEquals(ThreeNumbers.medianOf(78, 40, 386), 78);
        Assertions.assertEquals(ThreeNumbers.medianOf(487, 192, 87), 192);
        Assertions.assertEquals(ThreeNumbers.medianOf(305, 172, 80), 172);
        Assertions.assertEquals(ThreeNumbers.medianOf(56, 266, 314), 266);

        System.out.println("medianOf: Negative and Positive Cases");
        Assertions.assertEquals(ThreeNumbers.medianOf(13, -189, -372), -189);
        Assertions.assertEquals(ThreeNumbers.medianOf(53, -321, -6), -6);
        Assertions.assertEquals(ThreeNumbers.medianOf(-153, -14, -322), -153);
        Assertions.assertEquals(ThreeNumbers.medianOf(-283, 458, -270), -270);
        Assertions.assertEquals(ThreeNumbers.medianOf(-442, -486, 461), -442);

        System.out.println("medianOf: Large Value Cases");
        Assertions.assertEquals(ThreeNumbers.medianOf(-70017893, -182636475, -480588388), -182636475);
        Assertions.assertEquals(ThreeNumbers.medianOf(-97804133, -157935532, -439131110), -157935532);
        Assertions.assertEquals(ThreeNumbers.medianOf(-468062807, -426040222, -107435830), -426040222);

    }

    @Test
    public void averageOfTest() {
        System.out.println("averageOf: Positive Cases");
        Assertions.assertEquals(ThreeNumbers.averageOf(127, 482, 449), 352.6666666666667d);
        Assertions.assertEquals(ThreeNumbers.averageOf(73, 145, 79), 99.0d);
        Assertions.assertEquals(ThreeNumbers.averageOf(171, 99, 268), 179.33333333333334d);
        Assertions.assertEquals(ThreeNumbers.averageOf(56, 398, 61), 171.66666666666666d);
        Assertions.assertEquals(ThreeNumbers.averageOf(353, 136, 147), 212.0d);
        Assertions.assertEquals(ThreeNumbers.averageOf(332, 308, 293), 311.0d);

        System.out.println("averageOf: Positive and Negative Cases");
        Assertions.assertEquals(ThreeNumbers.averageOf(420, 448, 497), 455.0d);
        Assertions.assertEquals(ThreeNumbers.averageOf(143, 324, 484), 317.0d);
        Assertions.assertEquals(ThreeNumbers.averageOf(92, -391, 327), 9.333333333333334d);
        Assertions.assertEquals(ThreeNumbers.averageOf(308, 133, 103), 181.33333333333334d);
        Assertions.assertEquals(ThreeNumbers.averageOf(-436, 163, 354), 27.0d);
        Assertions.assertEquals(ThreeNumbers.averageOf(-424, 166, 100), -52.666666666666664d);

        System.out.println("averageOf: Large Value Cases");
        Assertions.assertEquals(ThreeNumbers.averageOf(-365273786, 420108715, -217543304),
                -5.4236125E7);
        Assertions.assertEquals(ThreeNumbers.averageOf(384915057, -449492980, -412322920),
                -1.5896694766666666E8);
        Assertions.assertEquals(ThreeNumbers.averageOf(352264751, 363162248, 287516303),
                3.34314434E8);
    }

    @Test
    public void countOfNumbersGreaterThanTheAverageTest() {
        System.out.println("countOfNumbersGreaterThanTheAverage: Positive Cases");
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(127, 482, 449), 2);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(73, 145, 79), 1);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(171, 99, 268), 1);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(56, 398, 61), 1);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(353, 136, 147), 1);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(332, 308, 293), 1);

        System.out.println("countOfNumbersGreaterThanTheAverage: Positive and Negative Cases");
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(420, 448, 497), 1);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(143, 324, 484), 2);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(92, -391, 327), 2);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(308, 133, 103), 1);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(-436, 163, 354), 2);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(-424, 166, 100), 2);

        System.out.println("countOfNumbersGreaterThanTheAverage: Large Value Cases");
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(-365273786,
                420108715, -217543304), 1);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(384915057,
                -449492980, -412322920),1);
        Assertions.assertEquals(ThreeNumbers.countOfNumbersGreaterThanTheAverage(352264751,
                363162248, 287516303),2);
    }

    @Test
    public void getFormattedOutputStringTest() {
        System.out.println("countOfNumbersGreaterThanTheAverage: True Cases");
        Assertions.assertEquals("The median of your numbers is 267, and 2 of them are"
                + " greater than their average.", ThreeNumbers.getFormattedOutputString(267,
                2));
        Assertions.assertEquals("The median of your numbers is 244, and 1 of them is"
                + " greater than their average.", ThreeNumbers.getFormattedOutputString(244,
                1));
        Assertions.assertEquals("The median of your numbers is 289, and 2 of them are"
                + " greater than their average.", ThreeNumbers.getFormattedOutputString(289,
                2));
        Assertions.assertEquals("The median of your numbers is 181, and 0 of them is"
                + " greater than their average.", ThreeNumbers.getFormattedOutputString(181,
                0));

    }
}
```