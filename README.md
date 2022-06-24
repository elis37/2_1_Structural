# 2_1_Structural
Задача Калькулятор
Описание
В этом задании попрактикуемся с шаблоном Adapter (Адаптер). Ниже вам дан готовый класс калькулятора:

public  classCalculator {
 public Formula newFormula() {
 return new Formula();
 }

 public static  enumOperation {
 SUM, SUB, MULT, DIV, POW;
 }

 public   staticclassFormula {
 protected Double a, b, result;

 protected Formula() {}

 public Formula addOperand(double operand) {
 if (a == null) {
 a = operand;
 } else if (b == null) {
 b = operand;
 } else {
 throw new IllegalStateException("Formula is full of operands");
 }
 return this;
 }

   publicFormulacalculate(Operation op) {
 if (a == null // b == null)
 throw new IllegalStateException("Not enough operands!");
 switch (op) {
  caseSUM:
 result = a + b;
 break;
  caseSUB:
 result = a - b;
 break;
  caseMULT:
 result = a * b;
 break;
 case DIV:
 result = a / b;
 break;
 case POW:
 result = Math.pow(a, b);
 break;
 }
 return this;
 }

 public double result() {
 if (result == null)
 throw new IllegalStateException("Formula is not computed!");
 return result;
 }
 }
}
Пример использования этого класса:

Calculator calc = new Calculator();
System.out.println(
 calc.newFormula()
 .addOperand(5)
 .addOperand(15)
 .calculate(Calculator.Operation.MULT)
 .result()
);
Пользователю же нужен другой интерфейс для работы с калькулятором:

  publicinterfaceInts {
 int sum(int arg0, int arg1);
 int mult(int arg0, int arg1);
 int pow(int a, int b);
}
который он использует в main, например, вот так:

public static void main(String[] args) {
 Ints  = new IntsCalculator();
 System.out.println(intsCalc.sum(2, 2));
 System.out.println(intsCalc.sum(10, 22));
 System.out.println(intsCalc.pow(2, 10));
}
Вам надо написать класс IntsCalculator, который будет имплементировать интерфейс Ints, "под капотом" делая вычисления через класс Calculator.

Реализация
Создайте класс Calculator, скопируйте его готовый код выше.
Создайте интерфейс Ints, скопируйте его готовый код выше.
Создайте класс IntsCalculator, укажите что он имплементирует интерфейс Ints, реализуйте его методы через обращение к объекту класса Calculator:
public class IntsCalculator implements Ints {
 protected final  Calculatortarget;

 public IntsCalculator() { this.target = new Calculator(); }

 @Override
  public  intsum(int arg0, int arg1) {
 //считаем через target
 }

 @Override
  public int mult(int arg0, int arg1) {
 //считаем через target
 }

 @Override
  public int pow(int a, int b) {
 //считаем через target
 }
}
Создайте класс Main, продемонстрируйте использование и возможности вашего класса (например, как выше в условии), обращайтесь к нему как к объекту интерфейса Ints.
public class Main {
 public static void main(String[] args) {
 Ints calc = new IntsCalculator();
 //демонстрация
 }
}
Протестируйте работу программы. Не забывайте про правила форматирования кода (для автоформата можете выделить код в идее и нажать Ctrl+Alt+L).
