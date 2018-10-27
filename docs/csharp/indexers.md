---
title: Indeksatory
description: Dowiedz się więcej o C# indeksatory i sposób implementacji indeksowane właściwości, które są właściwościami wskazywane za pomocą jednego lub więcej argumentów.
ms.date: 06/20/2016
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: a13163cb6bd835dfdd16c83c905c134eb8a86e7d
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2018
ms.locfileid: "50041144"
---
# <a name="indexers"></a>Indeksatory

*Indeksatory* są podobne do właściwości. Na wiele sposobów indeksatory kompilacji na te same funkcje języka jako [właściwości](properties.md). Włącz indeksatory *indeksowane* właściwości: właściwości, do których odwołuje się przy użyciu jednego lub więcej argumentów. Te argumenty zawierają indeksu do niektórych kolekcji wartości.

## <a name="indexer-syntax"></a>Składnia indeksatora

Indeksator dostępu za pomocą nazwy zmiennej i nawiasami kwadratowymi. Możesz umieścić argumenty indeksatora w nawiasie:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Można zadeklarować indeksatorów za pomocą `this` słowa kluczowego jako nazwy właściwości i deklarowanie argumentów w nawiasy kwadratowe. Ta deklaracja będzie odpowiadać użycia pokazano w poprzednim akapicie:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

W tym przykładzie początkowej można zobaczyć relację pomiędzy składni dla właściwości i indeksatorów. Ten sposób analogiczny niesie ze sobą za pośrednictwem większość reguł dotyczących składni dla indeksatorów. Indeksatory może mieć żadnych modyfikatorów dostępu nie jest ważna (publicznych, chronionych wewnętrznych, chronione, wewnętrzne, prywatne lub prywatnych chronionych). Mogą one sealed, wirtualne ani abstrakcyjne. Podobnie jak w przypadku właściwości, można określić modyfikatorów różny dostęp do pobierania i zestawu metod dostępu w indeksatorze.
Możesz również określić indeksatory tylko do odczytu (pomijając metody dostępu set) lub indeksatory tylko do zapisu (pomijając metody dostępu get).

Można zastosować prawie wszystko, czego nauczysz się praca z właściwości w celu indeksatorów. Jedynym wyjątkiem od tej reguły jest *automatycznie implementowane właściwości*. Kompilator nie zawsze Generuj poprawny magazyn dla indeksatora.

Obecność argumenty, które odwołuje się do elementu w zestawie elementów odróżnia indeksatory od właściwości. Można zdefiniować wiele indeksatorów w danym typie tak długo, jak wykazy argumentów dla każdego indeksatora jest unikatowa. Przyjrzyjmy się różne scenariusze których można użyć co najmniej jeden indeksatorów w definicji klasy. 

## <a name="scenarios"></a>Scenariusze

Należy zdefiniować *indeksatory* w danego typu, gdy jej interfejsu API modeli niektóre kolekcji, w którym zdefiniuj argumenty do tej kolekcji. Twoje indeksatory mogą lub nie mogą być mapowane bezpośrednio do typów kolekcji, które są częścią platformy .NET core framework. Danego typu może mieć inne obowiązki oprócz modelowania kolekcji.
Indeksatory umożliwiają interfejsu API, który odpowiada abstrakcji danego typu bez narażania wewnętrzny szczegóły jak przechowywane lub obliczonych wartości dla tego abstrakcji.

Przejdźmy teraz przez niektóre typowe scenariusze za pomocą *indeksatory*. Możesz uzyskać dostęp [przykładowy folder dla indeksatorów](https://github.com/dotnet/samples/tree/master/csharp/indexers). Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Tablice i wektory

Jest jednym z najbardziej typowych scenariuszy, do tworzenia indeksatorów, gdy typu modele tablicy lub wektora. Można utworzyć indeksator do modelowania uporządkowaną listę danych. 

Zaletą tworzenia własnych indeksatora jest zdefiniować magazynu dla tej kolekcji, w zależności od potrzeb. Wyobraź sobie scenariusz, w którym typu modele danych historycznych, który jest zbyt duży, aby załadować do pamięci na raz. Należy załadować i rozładować sekcje kolekcji na podstawie użycia. Poniższy przykład modeluje zachowania. Raportuje, na ile punktów danych istnieje. Tworzy strony do przechowywania części danych na żądanie. Usuwa stron z pamięci, aby zwolnić miejsce dla stron wymagane przez nowszą żądań.

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

Można wykonać tego idiomu projektu do modelowania dowolny rodzaj kolekcji w przypadku, gdy istnieje wiele powodów, nie można załadować cały zestaw danych do kolekcji w pamięci. Należy zauważyć, że `Page` klasa jest klasą zagnieżdżoną prywatnych nie jest częścią interfejsu publicznego. Te informacje są ukryte przed wszyscy użytkownicy tej klasy.

### <a name="dictionaries"></a>słowniki

Inny typowy scenariusz polega, gdy trzeba modelu obiekt dictionary lub mapy. Ten scenariusz jest, jeśli danego typu przechowuje wartości na podstawie klucza, zazwyczaj klucze tekstu. W tym przykładzie tworzy słownik mapujący argumenty wiersza polecenia do [wyrażeń lambda](delegates-overview.md) zarządzające tych opcji. W poniższym przykładzie przedstawiono dwóch klas: `ArgsActions` klasa, która mapuje opcję wiersza polecenia, aby `Action` delegować i `ArgsProcessor` , który używa `ArgsActions` do wykonania każdego `Action` po napotkaniu tej opcji.

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

W tym przykładzie `ArgsAction` kolekcji ściśle mapuje do podstawowej kolekcji.
`get` Decyduje, jeśli skonfigurowano danej opcji. Jeśli tak, zwraca `Action` skojarzone z tej opcji. Jeśli nie, zwraca `Action` , nic nie robi. Nie ma publicznej metody dostępu `set` metody dostępu. Zamiast projektu za pomocą publicznej metody do ustawiania opcji.

### <a name="multi-dimensional-maps"></a>Wielowymiarowe mapy

Możesz tworzyć indeksatory, korzystających z wielu argumentów. Oprócz tych argumentów nie są ograniczone do tego samego typu. Przyjrzyjmy się dwa przykłady.   

W pierwszym przykładzie pokazano klasę, która generuje wartości z zestawu Mandelbrot. Aby uzyskać więcej informacji na matematyce za zestaw odczytu [w tym artykule](https://en.wikipedia.org/wiki/Mandelbrot_set). Indeksator używa dwóch wartości podwójnej precyzji, aby zdefiniować punkt x, Y płaszczyzny.
Metody dostępu get oblicza liczbę iteracji, dopóki punkt zostanie uznane za nie może być w zestawie. Jeśli zostanie osiągnięta maksymalna liczba iteracji, punkt znajduje się w zestawie i zwracana jest wartość maxIterations tej klasy. (Obrazy wygenerowanego przez komputer spopularyzowany dla zestawu Mandelbrot zdefiniowanie kolorów liczba iteracji, które są niezbędne w celu ustalenia, czy punkt znajduje się poza zestaw.

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
Definiuje słownik, który może zawierać nieograniczoną liczbę wartości. Dlatego jest Brak magazynu poza zestaw. Zamiast tego należy ta klasa oblicza wartość dla każdego punktu, gdy kod wywołuje `get` metody dostępu. Nie ma żadnych magazynu.

Przeanalizujmy ostatniego użycia jeden z indeksatorów, w której indeksator ma wiele argumentów o różnych typach. Należy wziąć pod uwagę program, który zarządza dane historyczne dotyczące temperatury. Ten indeksator używa miejscowość i datę można ustawiać ani pobierać wysokich i niskich temperatur wobec tej lokalizacji:

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

W tym przykładzie tworzy działanie indeksatora, który mapuje dane pogody na dwa różne argumenty: mieście (reprezentowane przez `string`) i daty (reprezentowane przez `DateTime`). Wewnętrzny magazyn korzysta z dwóch `Dictionary` klasy do reprezentowania dwuwymiarową słownika. Publiczny interfejs API nie jest już reprezentuje podstawowy magazyn. Zamiast funkcji języka, indeksatorów pozwala na tworzenie publiczny interfejs, który reprezentuje swoje abstrakcji, mimo że bazowego magazynu, należy użyć różne podstawowe typy kolekcji.

Istnieją dwie części ten kod, który może być nieznane dla niektórych programistów. Te dwa `using` instrukcji:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

Tworzenie *alias* dla zbudowany typ ogólny. Te instrukcje należy włączyć kod później użyć bardziej opisowe `DateMeasurements` i `CityDateMeasurements` nazwy zamiast ogólnych konstrukcja `Dictionary<DateTime, Measurements>` i `Dictionary<string, Dictionary<DateTime, Measurements> >`. Ta konstrukcja wymaga przy użyciu w pełni kwalifikowanych nazw typów na prawej krawędzi `=` logowania.

Drugi techniką jest paska Wyłącz fragmenty czas dowolnych `DateTime` obiekt używany do indeksowania w kolekcji. .NET framework nie zawiera typu tylko data.
Deweloperzy używają `DateTime` typu, ale użyj `Date` właściwość, aby upewnić się, że dowolne `DateTime` obiektu z tego samego dnia są takie same.

## <a name="summing-up"></a>Podsumowanie

Indeksatory należy utworzyć w dowolnym momencie ma elementu właściwości w klasie gdzie tę właściwość reprezentuje pojedynczą wartość, ale raczej zbiór wartości, gdzie poszczególnych elementów jest identyfikowany przez zestawu argumentów. Te argumenty może jednoznacznie zidentyfikować, który element w kolekcji, które powinny istnieć odwołania.
Indeksatory rozszerzenie pojęcia [właściwości](properties.md), której członkiem jest traktowany jak elementu danych z poza klasy, ale jak metoda po stronie. Indeksatory zezwalają na argumenty znaleźć pojedynczy element we właściwości, które reprezentuje zestaw elementów.
