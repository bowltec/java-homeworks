## Задача 1. Автор программы

### Описание
Нужно написать программу для вывода имени ее разработчика в консоль.

### Функционал программы
1. Вывод сообщения в консоли "Имя разработчика".

### Пример
Пример 1
```
John Smith
```
Пример 2
```
Петров Николай
```

### Реализация
1. Создадим в блокноте текстовый файл `Main.java`.
2. Добавим в этот файл метод `main` со следующим кодом (нужно заменить имя "Петров Николай" на свое):

```
public class Main {
    public static void main(String[] args) {
        System.out.println("Петров Николай");  
    }
}
``` 
3. Скомпилируем программу, для этого нужно вызвать программу `javac`:
```
    javac Main.java
```
Результат получим байт-код файл `Main.class`

4. Запустим программу:
```
    java Main
```
Получим вывод:
```
    "Петров Николай"
```
5. Задача выполнена.