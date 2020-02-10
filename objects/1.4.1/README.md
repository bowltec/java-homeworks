## Задача 1. Добавление новой задачи в TaskManager

### Описание
Мы продолжаем улучшать наш Task Manager для нашей любимой команды!
Напишем программу для упрощения ввода менеджером данных о задаче. При добавлении задачи менеджер Иван вводит следующий текст: "Добавить картинку на главный экран приветствия, задача начинается в 15 и заканчивается в 19" (минуты учитывать пока не будем). 
Нужно найти в этом тексте время (часы) после выражения "начинается в" и "заканчивается в", рассчитать разницу между ними, и, если результат вычисления будет отрицательным или равным нулю, — завершить выполнение программы и вывести сообщение: "Формат введенных данных неверный".  

### Функционал программы
1. Возможность ввода из консоли текста задачи и времени;
2. Распознавание времени начала начали задачи и времени завершения задачи;
3. Расчет времени на выполнение задачи и вывод на экран.

### Примеры
#### Пример 1
```
Введите название задачи и время на ее выполнение:
"Добавить картинку на главный экран приветствия, задача начинается в 15 и заканчивается в 19" <нажмите enter>
"На задачу потребуется: 4 ч."
```
#### Пример 2
```
Введите название задачи и время на ее выполнение:
"Изменить заголовок главного экрана, задача начинается в 11 и заканчивается в 8" <нажмите enter>
"Формат введенных данных неверный"
```

### Процесс реализации
1. Создадим новый repl на сайте [repl.it](https://repl.it/repls), как написано в инструкции к выполнению домашней работы, и зададим название `homework1.4.1`.

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

3. Для начала нужно считать данные для разбора. Объявим в методе `main` ссылку на новый объект `Scanner scanner = new Scanner(System.in)` (где System.in — это стандартный поток ввода, в нашем случае console).

Для того чтобы прочитать значения, нужно вызвать у объекта `scanner.next()`, но, так этот метод считывает каждое новое значение через пробел, лучше использовать другой метод этого класса — `scanner.nextLine()`, он считает всю строку целиком.
Сохраним результат его выполнения в переменную, которую назовем `input`. 
    ```
    public static void main(String[] args) throws Exception {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();
        //TODO
    }
    ```

4. Находим время начала задачи. Для этого в введенной пользователем строке нужно определить позицию начала выражения `начинается в `. Для определения вхождения нам поможет метод класса `String - indexOf`. Сами же искомые строку вынесем в переменные – они нам понадобиться не один раз.
  - Определение позиции начала подстроки:
    ```
    String STARTS_AT = "начинается в "; // обратите внимание на пробел в конце!
    String ENDS_AT = "заканчивается в ";
    int startPos = input.indexOf(STARTS_AT); // вернёт позицию буквы "н" из "начинается в"
    startPos = startPos + STARTS_AT.length(); // если к позиции "н" прибавить длинну строки "начинается в "
                                              // то мы окажемя после "в " – как раз там где начинается число!
    ```
  - Находим числа после этого выражения. Для этого используем метод класса String — substring(int beginIndex, int endIndex). Он принимает на вход начальную и конечную позиции для извлечения подстроки. Начальной позицией будет последний символ выражения "начинается в", а конечной — startPos + 2 символа (количество цифр в часах). 
    ```
    String startTimeString = input.substring(startPos, startPos + 2);
    ```
  - Получаем строку `startTimeString`, в которой возможны пробелы. Для удаления начальных и конечных пробелов в Java у класса строк реализован метод `trim`.
    ```
    startTimeString = startTimeString.trim();
    ```
  - Последний шаг для нахождения часов — это преобразовать их в числовой тип, например, в int. Воспользуемся методом `Integer.parse`, который принимает на вход число в виде строки и возвращает int.
    ```
    int startTime = Integer.parseInt(startTimeString);
    ```

5. На этом шаге нам нужно найти число `endTime`, для этого нужно повторить операции над `input` (все как в пункте 2), только искать время после подстроки "заканчивается в ". Только в данном случае обратите внимание на ситуацию когда мы в качестве времени окончания введём одну цифру, например "бла бла бла заканчивается в 8". Здесь нам поможет то что мы можем не передавать в функцию substring второй параметр – `input.substring(endPos)`, она вернет всё что осталось до конца строки.

6. Рассчитываем количество между началом и завершением. Если результат вычисления меньше нуля, то выводим ошибку.

7. Выводим полученный результат в консоль.

8. Done! 