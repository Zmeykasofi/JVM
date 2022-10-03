# "Понимание JVM"

```java
public class JvmComprehension {
    public static void main(String[] args) {
        int i = 1;                      // 1 В Stack Memory во фрейме main класса JvmComprehension создаём переменную i 
        // и присваеваем ей значение 1
        Object o = new Object();        // 2 В куче (heap) создаём объект типа Object, на который ссылается переменная 
        // Object о, созданная в Stack Memory во фрейме main класса JvmComprehension
        Integer ii = 2;                 // 3 В куче (heap) создаём объект типа Integer со значением 2, в Stack Memory 
        // во фрейме main класса JvmComprehension создаём переменную ii типа Integer, которая ссылается на созданный объект
        printAll(o, i, ii);             // 4 В Stack Memory создаём фрейм printAll с переменными о, i, ii
        System.out.println("finished"); // 7 В Stack Memory создаём фрейм println, принимающий ссылку типа String на 
        // объект из кучи (heap) со значением "finished". По завершении метода main сборщик мусора удалит объекты 
        // из кучи и фреймы из стека по завершении программы
    }
    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5 В куче (heap) создаём объект типа Integer со значением 700,
        // на который ссылается переменная uselessVar типа Integer, созданная в Stack Memory во фрейме printAll 
        System.out.println(o.toString() + i + ii);  // 6 В Stack Memory создаём фрейм println с переменными o, i, ii;
        // каждая переменная создаёт свой фрейм toString.
        // Полученная строка же сохраняется в куче, на которую будет ссылаться переменная типа String во фрейме println 
        // в Stack Memory. 
        // Сборщик мусора после завершения метода удаляет: фреймы toString переменных, фрейм println, объект, 
        // хранящий результат сложения строк.               
    }
}
```