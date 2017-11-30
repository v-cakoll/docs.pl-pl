---
title: Indeksatory
description: "Dowiedz się więcej o języku C# indeksatory i sposobu wdrażania indeksowane właściwości, które są właściwościami odwoływać się przy użyciu co najmniej jeden argument."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 32e090524f414ef93b8481a8ad356b313191d8b9
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2017
---
# <a name="indexers"></a>Indeksatory

*Indeksatory* są podobne do właściwości. Na wiele sposobów indeksatory kompilacji na te same funkcje języka jako [właściwości](properties.md). Włącz indeksatory *indeksowane* właściwości: właściwości odwoływać się przy użyciu co najmniej jeden argument. Tych argumentów Podaj indeksu w pewnej kolekcji wartości.

## <a name="indexer-syntax"></a>Składnia indeksatora

Indeksator dostępu za pomocą nazwy zmiennej i nawiasy kwadratowe. Możesz umieścić argumenty indeksatora w nawiasie:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Można zadeklarować indeksatorów przy użyciu `this` słowa kluczowego jako nazwy właściwości i typ deklarujący argumenty w nawiasach kwadratowych. Ta deklaracja spowoduje dopasowanie użycia pokazano powyżej:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

W tym przykładzie początkowej można zobaczyć relację pomiędzy składni dla właściwości i indeksatorów. Prowadzi to odpowiednio do większości składni reguł dla indeksatorów. Indeksatory może mieć modyfikatorów żadnych prawomocny dostęp (publicznych, chronionych wewnętrznych, chronione, wewnętrzne, prywatne lub prywatny chroniony). Mogą być zapieczętowane, wirtualne lub abstrakcyjne. Podobnie jak w przypadku właściwości, można określić modyfikatorów dostępu różnych GET i ustaw accesssors w indeksatora.
Indeksatory tylko do odczytu (na przykład, pomijając metody dostępu set) lub tylko do zapisu indeksatory mogą określać również (, pomijając metody dostępu get).

Możesz zastosować prawie wszystko, czego możesz dowiedzieć się, Praca z właściwości indeksatorów. Jedynym wyjątkiem od tej reguły jest *automatycznie implementowane właściwości*. Kompilator nie może wygenerować zawsze poprawny magazyn dla indeksatora.

Obecność argumentów, aby odwołać się do elementu w zestawie elementów odróżnia indeksatory od właściwości. Można zdefiniować wiele indeksatorów w typie, tak długo, jak argument wymieniono dla każdego indeksatora jest unikatowy. Przyjrzyjmy różnych scenariuszy których można użyć co najmniej jeden indeksatorów w definicji klasy. 

## <a name="scenarios"></a>Scenariusze

Należy zdefiniować *indeksatory* w danego typu, gdy jej interfejsu API modele pewnej kolekcji miejscu należy określić argumenty do tej kolekcji. Twoje indeksatory mogą lub nie mogą być mapowane bezpośrednio do typów kolekcji, które są częścią programu .NET framework core. Danego typu może mieć inne obowiązki oprócz modelowania kolekcji.
Indeksatory umożliwiają stosowanie odpowiadającego danego typu abstrakcji bez narażania wewnętrzny szczegóły jak przechowywane lub obliczanej wartości dla tego abstrakcji interfejsu API.

Przejdźmy niektóre typowe scenariusze dotyczące korzystania z *indeksatory*. Dostęp można uzyskać [przykładowy folder dla indeksatorów](https://github.com/dotnet/docs/tree/master/samples/csharp/indexers). Instrukcje pobrania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Tablice i wektorów

Jest jednym z najbardziej typowych scenariuszy tworzenia indeksatorów, gdy modele danego typu tablicy lub wektora. Można utworzyć indeksatora do modelowania uporządkowaną listę danych. 

Zaletą tworzenia własnych indeksatora jest zdefiniować magazynu dla tej kolekcji, w zależności od potrzeb. Wyobraź sobie scenariusz, w którym danego typu modeli danych historycznych, który jest zbyt duży, aby załadować do pamięci na raz. Musisz ładowanie i zwalnianie sekcje kolekcji na podstawie użycia. Poniższy przykład modele tego zachowania. Raporty na liczbę punktów danych istnieje. Tworzy stron do przechowywania części danych na żądanie. Usuwa stron z pamięci, aby zwolnić miejsce dla strony wymagany przez nowszą żądania.

```csharp
public class DataSamples
{
    private class Page
    {
        private readonly List<Measurements> pageData = new List<Measurements>();
        private readonly int startingIndex;
        private readonly int length;
        private bool dirty;
        private DateTime lastAccess;

        public Page(int startingIndex, int length)
        {
            this.startingIndex = startingIndex;
            this.length = length;
            lastAccess = DateTime.Now;

            // This stays as random stuff:
            var generator = new Random();
            for(int i=0; i < length; i++)
            {
                var m = new Measurements
                {
                    HiTemp = generator.Next(50, 95),
                    LoTemp = generator.Next(12, 49),
                    AirPressure = 28.0 + generator.NextDouble() * 4
                };
                pageData.Add(m);
            }
        }
        public bool HasItem(int index) =>
            ((index >= startingIndex) &&
            (index < startingIndex + length));

        public Measurements this[int index]
        {
            get
            {
                lastAccess = DateTime.Now;
                return pageData[index - startingIndex];
            }
            set
            {
                pageData[index - startingIndex] = value;
                dirty = true;
                lastAccess = DateTime.Now;
            }
        }

        public bool Dirty => dirty;
        public DateTime LastAccess => lastAccess;
    }

    private readonly int totalSize;
    private readonly List<Page> pagesInMemory = new List<Page>();

    public DataSamples(int totalSize)
    {
        this.totalSize = totalSize;
    }

    public Measurements this[int index]
    {
        get
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");

            var page = updateCachedPagesForAccess(index);
            return page[index];
        }
        set
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");
            var page = updateCachedPagesForAccess(index);

            page[index] = value;
        }
    }

    private Page updateCachedPagesForAccess(int index)
    {
        foreach (var p in pagesInMemory)
        {
            if (p.HasItem(index))
            {
                return p;
            }
        }
        var startingIndex = (index / 1000) * 1000;
        var newPage = new Page(startingIndex, 1000);
        addPageToCache(newPage);
        return newPage;
    }

    private void addPageToCache(Page p)
    {
        if (pagesInMemory.Count > 4)
        {
            // remove oldest non-dirty page:
            var oldest = pagesInMemory
                .Where(page => !page.Dirty)
                .OrderBy(page => page.LastAccess)
                .FirstOrDefault();
            // Note that this may keep more than 5 pages in memory
            // if too much is dirty
            if (oldest != null)
                pagesInMemory.Remove(oldest);
        }
        pagesInMemory.Add(p);
    }
}
```

Idiom tego projektu do modelowania dowolny rodzaj kolekcji można wykonać w przypadku, gdy istnieją powody nie można załadować cały zestaw danych do kolekcji w pamięci. Zwróć uwagę, że `Page` klasa jest klasą zagnieżdżonych prywatnych nie jest częścią interfejs publiczny. Te szczegóły są ukryte przed wszyscy użytkownicy tej klasy.

### <a name="dictionaries"></a>słowników

Inny typowy scenariusz polega, gdy trzeba modelu słownika lub mapy. Ten scenariusz jest w przypadku danego typu przechowuje wartości oparte na kluczu, zwykle klucze tekstu. W tym przykładzie tworzy słownik mapujący argumenty wiersza polecenia do [wyrażenia lamdba](delegates-overview.md) który Zarządzanie tych opcji. W poniższym przykładzie przedstawiono dwie klasy: `ArgsActions` klasa, która mapuje opcji wiersza polecenia, aby `Action` delegować i `ArgsProcessor` używającą `ArgsActions` do wykonania poszczególnych `Action` po napotkaniu tej opcji.

```csharp
public class ArgsProcessor
{
    private readonly ArgsActions actions;

    public ArgsProcessor(ArgsActions actions)
    {
        this.actions = actions;
    }

    public void Process(string[] args)
    {
        foreach(var arg in args)
        {
            actions[arg]?.Invoke();
        }
    }

}
public class ArgsActions
{
    readonly private Dictionary<string, Action> argsActions = new Dictionary<string, Action>();

    public Action this[string s]
    {
        get
        {
            Action action;
            Action defaultAction = () => {} ;
            return argsActions.TryGetValue(s, out action) ? action : defaultAction;
        }
    }

    public void SetOption(string s, Action a)
    {
        argsActions[s] = a;
    }
}
```

W tym przykładzie `ArgsAction` kolekcji ściśle Mapowana kolekcja źródłowa.
`get` Określa, czy dany opcji został skonfigurowany. Jeśli tak, zwraca `Action` skojarzone z tej opcji. Jeśli nie, zwraca `Action` nie działają. Nie ma publicznego akcesora `set` metody dostępu. Zamiast projektu za pomocą metody publicznej do ustawiania opcji.

### <a name="multi-dimensional-maps"></a>Mapy wielowymiarowych

Można utworzyć indeksatory korzystających z wielu argumentów. Ponadto tych argumentów nie są ograniczone do tego samego typu. Oto dwa przykłady.   

W pierwszym przykładzie klasy, które generuje wartości z zestawu Mandelbrot. Aby uzyskać więcej informacji na matematyce za zestaw odczytu [w tym artykule](https://en.wikipedia.org/wiki/Mandelbrot_set). Indeksator używa dwóch symulacyjnych, aby zdefiniować punkt w X, Y płaszczyzny.
Metoda dostępu get oblicza liczba iteracji, dopóki nie stwierdzono, że punkt nie może być w zestawie. Jeśli zostanie osiągnięta maksymalna liczba iteracji, punkt znajduje się w zestawie, i jest zwracana wartość maxIterations tej klasy. (Obrazy generowane komputera popularized zestawu Mandelbrot zdefiniowanie kolorów liczba iteracji, które są niezbędne do określenia, czy punkt znajduje się poza zestaw.

```csharp
public class Mandelbrot
{
    readonly private int maxIterations;

    public Mandelbrot(int maxIterations)
    {
        this.maxIterations = maxIterations;
    }

    public int this [double x, double y]
    {
        get
        {
            var iterations = 0;
            var x0 = x;
            var y0 = y;

            while ((x*x + y * y < 4) &&
                (iterations < maxIterations))
            {
                var newX = x * x - y * y + x0;
                y = 2 * x * y + y0;
                x = newX;
                iterations++;
            }
            return iterations;
        }
    }
}
```

Zestaw Mandelbrot definiuje wartości w każdym folderu (x, y) koordynować rzeczywiste wartości liczbowe.
Definiuje słownik, który może zawierać nieograniczoną liczbę wartości. Dlatego nie jest Brak magazynu poza zestaw. Zamiast tego należy ta klasa oblicza wartość dla każdego punktu, gdy kod wywołuje `get` metody dostępu. Nie ma żadnych powiązany magazyn używany.

Przeanalizujmy jedno ostatniego Użycie indeksatorów, gdzie indeksatora przyjmuje wiele argumentów o różnych typach. Należy wziąć pod uwagę program, który zarządza temperatury historycznych danych. Ten indeksator używa miejscowość i Data ustawić lub pobrać temperatury wysoki i niski dla tej lokalizacji:

```csharp
using DateMeasurements = 
    System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = 
    System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;

public class HistoricalWeatherData
{
    readonly CityDataMeasurements storage = new CityDataMeasurements();

    public Measurements this[string city, DateTime date]
    {
        get
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
                throw new ArgumentOutOfRangeException(nameof(city), "City not found");

            // strip out any time portion:
            var index = date.Date;
            var measure = default(Measurements);
            if (cityData.TryGetValue(index, out measure))
                return measure;
            throw new ArgumentOutOfRangeException(nameof(date), "Date not found");
        }
        set
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
            {
                cityData = new DateMeasurements();
                storage.Add(city, cityData);
            }

            // Strip out any time portion:
            var index = date.Date;
            cityData[index] = value;
        }
    }
}
```

W tym przykładzie jest tworzony indeksatorze, który mapuje dane o pogodzie w dwóch różnych argumentów: Miejscowość (reprezentowane przez `string`) i datę (reprezentowane przez `DateTime`). Wewnętrzny magazyn korzysta z dwóch `Dictionary` klasy do reprezentowania dwuwymiarowa słownika. Publiczny interfejs API reprezentuje nie jest już powiązany magazyn. Zamiast funkcji języka indeksatory umożliwia utworzenie publiczny interfejs, który reprezentuje użytkownika abstrakcji, mimo że powiązany magazyn muszą używać różnych podstawowych typów kolekcji.

Istnieją dwie części tego kodu, które mogą być nieznane niektórzy deweloperzy. Te dwa `using` instrukcji:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

Utwórz *alias* do skonstruowanego typu ogólnego. Te instrukcje Włącz kod później używany bardziej opisowe `DateMeasurements` i `CityDateMeasurements` nazw zamiast ogólnego konstrukcji `Dictionary<DateTime, Measurements>` i `Dictionary<string, Dictionary<DateTime, Measurements> >`. Ta konstrukcja wymaga użycia pełni kwalifikowane nazwy typów w prawej części `=` logowania.

Drugi technika jest paska Wyłącz fragmenty czasu dowolnego `DateTime` obiekt używany do indeksu w kolekcji. .NET framework nie obejmuje jedynym typem daty.
Deweloperzy za pomocą `DateTime` typu, ale użyj `Date` właściwość, aby upewnić się, że wszelkie `DateTime` obiektów z danego dnia są takie same.

## <a name="summing-up"></a>Podsumowanie

Należy utworzyć indeksatorów w dowolnym momencie ma elementu właściwości w klasie, w których tej właściwości reprezentuje pojedynczą wartość, ale raczej kolekcję wartości, w którym każdego elementu jest identyfikowany przez zestaw argumentów. Tych argumentów można jednoznacznie zidentyfikować, który element w kolekcji ma być utworzone odwołanie.
Indeksatory rozszerzenie pojęcia [właściwości](properties.md), której członkiem jest traktowany jak elementu danych z poza klasą, ale jak metody na stronie. Indeksatory zezwalają na argumenty można znaleźć pojedynczego elementu we właściwości, która reprezentuje zestaw elementów.
