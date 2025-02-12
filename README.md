[Pattern] Write a program that looks for a pattern in a sentence. The program searches for a pattern using two methods: the first one compares words using the equals string function, the second method checks whether the subsequent characters of the word are the same as the subsequent characters of the pattern. Both methods display information such as whether the pattern exists and how many times, e.g. "True.3" (boolean and int types).

Code:

import java.util.Scanner;


public class Wzorzec {


   public static void main(String[] args) {
       Scanner sc = new Scanner(System.in);


       System.out.print("Podaj zdanie: ");
       String wyraz = sc.nextLine();


       System.out.print("Podaj wzorzec: ");
       String szukane = sc.nextLine();


       boolean szukanie = wyraz.contains(szukane);
       System.out.println("Czy wyraz zawiera '" + szukane + "'? " + szukanie);




       String[] podzielone = wyraz.split(" ");
       int wystapienieSlow = 0;
       for (String slowo : podzielone) {
           if (slowo.equals(szukane)) {
               wystapienieSlow++;
           }
       }
       boolean znaleziono = wystapienieSlow > 0;
       System.out.println("Split >>> Czy '" + szukane + "' jest w tablicy słów? " + znaleziono + ". Wystąpiło ono: " + wystapienieSlow + " razy.");




       int wystapieniePodciagow = metoda2(wyraz, szukane);
       System.out.println("Znaki >>> Wzorzec '" + szukane + "' występuje on: " + wystapieniePodciagow + " razy.");
   }


   public static int metoda2(String tekst, String wzorzec) {
       int licznik = 0;
       int dlugoscTekstu = tekst.length();
       int dlugoscWzorca = wzorzec.length();


       for (int i = 0; i <= dlugoscTekstu - dlugoscWzorca; i++) {
           if (tekst.substring(i, i + dlugoscWzorca).equals(wzorzec)) {
               licznik++;
           }
       }


       return licznik;
   }
}
