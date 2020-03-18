---
title: Indexers (Indeksatory)
description: Dowiedz się więcej o indeksatory C# i jak implementują właściwości indeksowane, które są właściwości, do których odwołuje się przy użyciu jednego lub więcej argumentów.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 8e583b8a7cedab61ea6fdd56587608907610b6b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145687"
---
# <a name="indexers"></a>Indexers (Indeksatory)

*Indeksatory* są podobne do właściwości. Na wiele sposobów indeksatory opierają się na tych samych funkcjach języka, co [właściwości](properties.md). Indeksatory włączyć właściwości *indeksowane:* właściwości odwołuje się przy użyciu jednego lub więcej argumentów. Te argumenty zapewniają indeks do niektórych kolekcji wartości.

## <a name="indexer-syntax"></a>Składnia indeksatora

Dostęp do indeksatora za pomocą nazwy zmiennej i nawiasów kwadratowych. Argumenty indeksatora można umieścić wewnątrz nawiasów:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Indeksatory deklarujesz używając słowa kluczowego `this` jako nazwy właściwości i deklarując argumenty w nawiasach kwadratowych. Ta deklaracja będzie zgodna z użyciem pokazanym w poprzednim akapicie:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

W tym przykładzie początkowym można zobaczyć relację między składnią właściwości i indeksatorów. Ta analogia przenosi większość reguł składni dla indeksatorów. Indeksatory mogą mieć dowolne prawidłowe modyfikatory dostępu (publiczne, chronione wewnętrzne, chronione, wewnętrzne, prywatne lub prywatne chronione). Mogą być zapieczętowane, wirtualne lub abstrakcyjne. Podobnie jak w przypadku właściwości, można określić różne modyfikatory dostępu dla get i set akcesorów w indeksatorze.
Można również określić indeksatory tylko do odczytu (pomijając set akcesor) lub indeksatory tylko do zapisu (pomijając get akcesor).

Możesz zastosować prawie wszystko, czego uczysz się od pracy z właściwościami do indeksatorów. Jedynym wyjątkiem od tej reguły są *właściwości implementowane automatycznie*. Kompilator nie zawsze może wygenerować poprawny magazyn dla indeksatora.

Obecność argumentów do odwoływania się do elementu w zestawie elementów odróżnia indeksatory od właściwości. Można zdefiniować wiele indeksatorów dla typu, tak długo, jak listy argumentów dla każdego indeksatora jest unikatowa. Przyjrzyjmy się różne scenariusze, w których można użyć jednego lub więcej indeksatorów w definicji klasy.

## <a name="scenarios"></a>Scenariusze

Można zdefiniować *indeksatory* w typie, gdy jego modele interfejsu API niektóre kolekcji, gdzie można zdefiniować argumenty do tej kolekcji. Indeksatory mogą lub nie mogą być mapowane bezpośrednio do typów kolekcji, które są częścią platformy .NET core. Typ może mieć inne obowiązki oprócz modelowania kolekcji.
Indeksatory umożliwiają podanie interfejsu API, który pasuje do abstrakcji typu bez ujawniania wewnętrznych szczegółów, w jaki sposób wartości dla tej abstrakcji są przechowywane lub obliczane.

Przejdźmy przez niektóre typowe scenariusze korzystania z *indeksatorów*. Można uzyskać dostęp do [przykładowego folderu dla indeksatorów](https://github.com/dotnet/samples/tree/master/csharp/indexers). Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Tablice i wektory

Jednym z najbardziej typowych scenariuszy tworzenia indeksatorów jest, gdy typ modeli tablicy lub wektora. Indeksatora można utworzyć w celu modelowania uporządkowanej listy danych.

Zaletą tworzenia własnego indeksatora jest to, że można zdefiniować magazyn dla tej kolekcji do własnych potrzeb. Wyobraź sobie scenariusz, w którym typ modeli danych historycznych, który jest zbyt duży, aby załadować do pamięci na raz. Należy załadować i rozładować sekcje kolekcji na podstawie użycia. W poniższym przykładzie modele to zachowanie. Raportuje, ile punktów danych istnieje. Tworzy strony do przechowywania sekcji danych na żądanie. Usuwa strony z pamięci, aby zrobić miejsce dla stron potrzebnych przez nowsze żądania.

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

Można wykonać ten projekt idiom do modelu wszelkiego rodzaju kolekcji, gdzie istnieją dobre powody, aby nie załadować cały zestaw danych do kolekcji w pamięci. Należy zauważyć, że `Page` klasa jest prywatną klasą zagnieżdżoną, która nie jest częścią interfejsu publicznego. Te szczegóły są ukryte przed użytkownikami tej klasy.

### <a name="dictionaries"></a>Słowniki

Innym typowym scenariuszem jest, gdy trzeba modelować słownika lub mapy. W tym scenariuszu jest, gdy typ przechowuje wartości na podstawie klucza, zazwyczaj klucze tekstowe. W tym przykładzie tworzy słownik, który mapuje argumenty wiersza polecenia do [wyrażeń lambda,](delegates-overview.md) które zarządzają tymi opcjami. W poniższym przykładzie przedstawiono `ArgsActions` dwie klasy: klasę, `Action` która mapuje `ArgsProcessor` opcję wiersza polecenia na pełnomocnika i która używa `ArgsActions` do wykonania każdej z nich, `Action` gdy napotka tę opcję.

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

W tym przykładzie `ArgsAction` kolekcja mapuje ściśle do podstawowej kolekcji.
Określa, `get` czy dana opcja została skonfigurowana. Jeśli tak, zwraca `Action` skojarzony z tą opcją. Jeśli nie, `Action` zwraca, że nic nie robi. Publiczny akcesor `set` nie obejmuje akcesora. Zamiast tego projekt przy użyciu publicznej metody ustawiania opcji.

### <a name="multi-dimensional-maps"></a>Mapy wielowymiarowe

Można utworzyć indeksatory, które używają wielu argumentów. Ponadto te argumenty nie są ograniczone do tego samego typu. Spójrzmy na dwa przykłady.

Pierwszy przykład pokazuje klasę, która generuje wartości dla zestawu Mandelbrot. Aby uzyskać więcej informacji na temat matematyki za zestaw, przeczytaj [ten artykuł](https://en.wikipedia.org/wiki/Mandelbrot_set).
Indeksator używa dwóch podwaja do zdefiniowania punktu w X, Y płaszczyzny.
Get akcesor oblicza liczbę iteracji, dopóki punkt nie zostanie określony jako nie w zestawie. Jeśli zostanie osiągnięta maksymalna iteracji, punkt znajduje się w zestawie, a wartość maksymalizacji klasy jest zwracana. (Obrazy generowane przez komputer spopularyzowane dla zestawu Mandelbrot definiują kolory dla liczby iteracji niezbędnych do określenia, że punkt znajduje się poza zestawem.

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

Zestaw Mandelbrot definiuje wartości w każdej współrzędnej (x,y) dla wartości liczb rzeczywistych.
Który definiuje słownik, który może zawierać nieskończoną liczbę wartości. W związku z tym nie ma magazynu za zestaw. Zamiast tego ta klasa oblicza wartość dla każdego `get` punktu, gdy kod wywołuje akcesor. Nie jest używany podstawowy magazyn.

Przyjrzyjmy się ostatniemu użyciu indeksatorów, gdzie indeksator przyjmuje wiele argumentów różnych typów. Rozważmy program, który zarządza historycznymi danymi temperatury. Ten indeksator używa miasta i daty, aby ustawić lub uzyskać wysokie i niskie temperatury dla tej lokalizacji:

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

W tym przykładzie tworzy indeksator, który mapuje dane pogodowe `string`na dwa różne argumenty: `DateTime`miasto (reprezentowane przez ) i datę (reprezentowaną przez ). Magazyn wewnętrzny używa `Dictionary` dwóch klas do reprezentowania słownika dwuwymiarowego. Publiczny interfejs API nie reprezentuje już podstawowego magazynu. Zamiast tego funkcje języka indeksatorów umożliwia utworzenie interfejsu publicznego, który reprezentuje abstrakcji, mimo że podstawowego magazynu musi używać różnych typów kolekcji podstawowych.

Istnieją dwie części tego kodu, które mogą być nieznane niektórym deweloperom. Te `using` dwa stwierdzenia:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

utworzyć *alias* dla skonstruowanego typu ogólnego. Instrukcje te umożliwiają kod później użyć bardziej `DateMeasurements` opisowe `CityDateMeasurements` i nazwy `Dictionary<DateTime, Measurements>` zamiast `Dictionary<string, Dictionary<DateTime, Measurements> >`ogólnej budowy i .
Ta konstrukcja wymaga użycia w pełni kwalifikowanych nazw `=` typów po prawej stronie znaku.

Druga technika jest usunięcie części czasu `DateTime` dowolnego obiektu używanego do indeksowania do kolekcji. .NET nie zawiera typu tylko daty.
Deweloperzy `DateTime` używają tego typu, ale `Date` użyj `DateTime` właściwości, aby upewnić się, że każdy obiekt z tego dnia są równe.

## <a name="summing-up"></a>Podsumowanie

Indeksatory należy utworzyć w dowolnym momencie masz element podobny do właściwości w klasie, gdzie ta właściwość reprezentuje nie pojedynczą wartość, ale raczej kolekcję wartości, gdzie każdy pojedynczy element jest identyfikowany przez zestaw argumentów. Te argumenty można jednoznacznie zidentyfikować, który element w kolekcji należy odwoływać.
Indeksatory rozszerzyć pojęcie [właściwości](properties.md), gdzie element członkowski jest traktowany jak element danych spoza klasy, ale jak metoda w środku. Indeksatory zezwalają na znajdowanie pojedynczego elementu we właściwości reprezentującej zestaw elementów.
