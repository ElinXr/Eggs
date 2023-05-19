import java.util.ArrayList;
import java.util.List;

// Имплементация на шаблона Singleton за Великденския заек
public class EasterBunny {
    private static EasterBunny instance;

    private EasterBunny() {}

    public static EasterBunny getInstance() {
        if (instance == null) {
            instance = new EasterBunny();
        }
        return instance;
    }

    public void prepareEggs() {
        MagicBag bag = new MagicBag();

        // Използване на шаблона Factory (Abstract Factory) за създаване на яйцата
        EggFactory eggFactory = new EggFactory();
        List<Egg> eggs = eggFactory.createEggs(bag);

        Basket basket = new Basket();

        for (Egg egg : eggs) {
            // Използване на шаблона Decorator за украсяване на яйцата
            ColoredEgg coloredEgg = new ColoredEgg(egg);
            StickeredEgg decoratedEgg = new StickeredEgg(coloredEgg);

            basket.addEgg(decoratedEgg);

            if (basket.getEggCount() > 5) {
                // Използване на шаблона Observer за съобщаване на пиленцата
                Chicks.getInstance().notify("Яйцата са готови");
            }
        }
    }
}

// Имплементация на шаблона Factory (Abstract Factory) за създаване на различни видове яйца
public interface EggFactory {
    List<Egg> createEggs(MagicBag bag);
}

public class QuailEggFactory implements EggFactory {
    @Override
    public List<Egg> createEggs(MagicBag bag) {
        return bag.createQuailEggs();
    }
}

public class ChickenEggFactory implements EggFactory {
    @Override
    public List<Egg> createEggs(MagicBag bag) {
        return bag.createChickenEggs();
    }
}

public class DinosaurEggFactory implements EggFactory {
    @Override
    public List<Egg> createEggs(MagicBag bag) {
        return bag.createDinosaurEggs();
    }
}

// Имплементация на шаблона Decorator за украсяване на яйцата
public abstract class DecoratedEgg extends Egg {
    protected Egg egg;
}

public class ColoredEgg extends DecoratedEgg {
    private List<String> decorations;

    public ColoredEgg(Egg egg) {
        this.egg = egg;
        this.decorations = new ArrayList<>();
    }

    public void addColor(String color) {
        decorations.add("Цвят: " + color);
    }

    @Override
    public String toString() {
        return egg.toString() + ", " + String.join(", ", decorations);
    }
}

public class StickeredEgg extends DecoratedEgg {
    private List<String> stickers;

    public StickeredEgg(Egg egg) {
        this.egg = egg;
        this.stickers = new ArrayList<>();
    }

    public void addSticker(String sticker) {
        stickers.add("Стикер: " + sticker);
    }

    @Override
    public String toString() {
        return egg.toString() + ", " + String.join(", ", stickers);
    }
}

// Имплементация на шаблона Observer за пиленцата
public class Chicks {
    private static Chicks instance;
    private List<Observer> observers;

    private Chicks() {
        observers = new ArrayList<>();
    }

    public static Chicks getInstance() {
        if (instance == null) {
            instance = new Chicks();
        }
        return instance;
    }

    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    public void notifyObservers(String message) {
        for (Observer observer : observers) {
            observer.update(message);
        }
    }

    public interface Observer {
        void update(String message);
    }
}

// Имплементация на MagicBag за създаване на яйца
public class MagicBag {
    public List<Egg> createQuailEggs() {
        List<Egg> eggs = new ArrayList<>();
        // Логика за създаване на пъдпъдъчи яйца
        return eggs;
    }

    public List<Egg> createChickenEggs() {
        List<Egg> eggs = new ArrayList<>();
        // Логика за създаване на кокошо яйца
        return eggs;
    }

    public List<Egg> createDinosaurEggs() {
        List<Egg> eggs = new ArrayList<>();
        // Логика за създаване на динозавърски яйца
        return eggs;
    }
}

// Имплементация на кошница за яйца
public class Basket {
    private List<Egg> eggs;

    public Basket() {
        eggs = new ArrayList<>();
    }

    public void addEgg(Egg egg) {
        eggs.add(egg);
    }

    public int getEggCount() {
        return eggs.size();
    }
}
