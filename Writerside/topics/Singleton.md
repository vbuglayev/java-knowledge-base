# Singleton

Creational design pattern that lets you ensure that a class has only one instance, while providing a global access point to this instance.

## Thread Safe Singleton

```Java
public final class Singleton {
    private static volatile Singleton instance;

    private Singleton() {}

    public static Singleton getInstance() {
        Singleton result = instance;
        if (result != null) {
            return result;
        }
        synchronized(Singleton.class) {
            if (instance == null) {
                instance = new Singleton();
            }
            return instance;
        }
    }
}
```

## Enum Singleton

```Java
public enum Singleton {
    INSTANCE;

    public void execute (String arg) {
        // perform operations here
    }
}
```