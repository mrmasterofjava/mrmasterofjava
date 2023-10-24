import java.util.Random;

public class lab1 {
    public static void main(String[] args) {
        short[] p = new short[9];
        double[] x = new double[16];
        double[][] e = new double[9][16];

        // Заполнение массива p чётными числами от 2 до 18
        int value = 2;
        for (int i = 0; i < 9; i++) {
            p[i] = (short) value;
            value += 2;
        }

        // Заполнение массива x случайными числами от -12.0 до 4.0
        Random random = new Random();
        for (int i = 0; i < 16; i++) {
            x[i] = -12.0 + random.nextDouble() * 16.0;
        }

        // Вычисление значений для массива e
        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 16; j++) {
                double xValue = x[j];
                if (p[i] == 2) {
                    e[i][j] = Math.atan(Math.E - Math.abs(xValue)) / Math.sqrt(3);
                } else if (p[i] == 8 || p[i] == 10 || p[i] == 16 || p[i] == 18) {
                    e[i][j] = Math.cbrt((0.5 - Math.cos(xValue) * Math.pow(2 * xValue, 2)) * Math.pow(xValue, 1 / 4) / Math.pow(xValue, 2));
                } else {
                    e[i][j] = Math.tan(Math.log(Math.pow(Math.tan(xValue), 2)));
                }
            }
        }

        // Вывод массива e с тремя знаками после запятой
        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 16; j++) {
                System.out.printf("%.3f\t", e[i][j]);
            }
            System.out.println();      
        }
    }
}
