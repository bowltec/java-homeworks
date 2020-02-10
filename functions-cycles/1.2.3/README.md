## Задача 3. Календарь

### Описание
Вы планируете задачи своей команды на неделю, а значит, что хорошо бы было использовать календарь для этого. Нужно написать программу, которая будет выводить календарь в консоль.

### Функционал программы
1. Вывод года и месяца (запрашивать какие-либо данные не нужно, год и месяц используем текущие).
2. Вывод дней недели и чисел текущего месяца.

### Пример
```
Март 2019
Пн Вт Ср Чт Пт Сб Вс
            1  2  3
4  5  6  7  8  9  10
11 12 13 14 15 16 17
18 19 20 21 22 23 24
25 26 27 28 29 30 31
```
### Реализация
1. Создадим новый repl на сайте [repl.it](https://repl.it/repls), как написано в инструкции к выполнению домашней работы, и зададим название `homework1.2.3`.

2. В файле `Main.java` написан следующий код:

```
class Main {
  public static void main(String[] args) {
    System.out.println("Hello world!");
  }
}
``` 

Весь код выполнения задачи нужно писать вместо `System.out.println("Hello world!");`, эту строку нужно удалить.

```
  public static void main(String[] args) {
    System.out.println("Hello world!"); //Код сюда
  }
```

3. Выведем текущий год и месяц в консоль (год и месяц константы, задаем в коде программы, не запрашивая ввод значений от пользователя).

```
System.out.println("Март 2019");
```

4. Выведем дни недели до цикла. Для этого воспользуемся хорошо известным методом `System.out.println`.

```
System.out.println("Пн Вт Ср ...");
```

5. Для вывода отступа (дней предыдущего месяца), а также вывода чисел нужно использовать метод `System.out.print(" ")`.

`System.out.print()` — не переводит указатель на новую строку после вывода в консоль.
`System.out.println()` — переводит указатель на новую строку после вывода в консоль. 

6. Для решения задачи потребуется два, вложенных один в другой, цикла `for`.

```
for (int i = 0; i < ...; i++) {
    for (int j = ...) {
        System.out.print(...);  
  }
}
```

7. Завершить работу программы.