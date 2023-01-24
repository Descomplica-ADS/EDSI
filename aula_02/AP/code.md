**R e s p o s t a - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -**

*JAVA:*
```java
import javax.swing.JOptionPane;

public class AP2 {
    public double Average() {
        int i;
        double realNumber[], average, amount = 0;
        realNumber = new double [50];

        for (i = 0; i < realNumber.length; i++) {
            realNumber[i] = Double.parseDouble(JOptionPane.showInputDialog("Digite um valor real para calcular a média:"));

            amount += realNumber[i];
        }

        average = amount / realNumber.length;

        return average;
    }

    public static void main(String args[]) {
        AP2 exec = new AP2();

        double average = exec.Average();

        System.out.print("O método Average retornou como média: " + average);
        System.exit(0);
    }
}
```