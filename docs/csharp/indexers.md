---
title: Indexers (Indeksatory)
description: Poznaj indeksatory języka C# i sposób implementowania właściwości indeksowanych, które są właściwościami, do których odwołuje się jeden lub więcej argumentów.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: e9b1cb18157982f068f1c1e4546e637f2bd707cb
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394701"
---
# <a name="indexers"></a>Indexers (Indeksatory)

*Indeksatory* są podobne do właściwości. Na wiele sposobów Indeksatory są kompilowane przy użyciu tych samych funkcji językowych, co [Właściwości](properties.md). Indeksatory włączają *indeksowane* właściwości: właściwości, których dotyczy odwołanie, przy użyciu co najmniej jednego argumentu. Te argumenty zapewniają indeks do pewnej kolekcji wartości.

## <a name="indexer-syntax"></a>Składnia indeksatora

Dostęp do indeksatora można uzyskać za pomocą nazwy zmiennej i nawiasów kwadratowych. Argumenty indeksatora są umieszczane w nawiasach:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Indeksatory są deklarowane przy użyciu `this` słowa kluczowego jako nazwy właściwości i deklarując argumenty w nawiasach kwadratowych. Ta deklaracja będzie zgodna z użyciem przedstawionym w poprzednim akapicie:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Z tego początkowego przykładu można zobaczyć relacje między składnią właściwości i indeksatorów. To analogowe przechodzenie przez większość reguł składni indeksatorów. Indeksatory mogą mieć wszelkie prawidłowe Modyfikatory dostępu (publiczne, chronione wewnętrznie, chronione, wewnętrzne, prywatne lub prywatne chronione). Mogą być zapieczętowane, wirtualne lub abstrakcyjne. Podobnie jak w przypadku właściwości, można określić różne Modyfikatory dostępu dla metod dostępu get i Set w indeksatorze.
Można również określić indeksatory tylko do odczytu (poprzez pominięcie metody dostępu set) lub indeksatory tylko do zapisu (przez pominięcie metody dostępu get).

Możesz zastosować niemal wszystkie informacje o pracy z właściwościami indeksatorów. Jedynym wyjątkiem od tej reguły są *zaimplementowane właściwości*. Kompilator nie zawsze może generować prawidłowy magazyn dla indeksatora.

Obecność argumentów odwołujących się do elementu w zestawie elementów odróżnia indeksatory od właściwości. Można zdefiniować wiele indeksatorów dla typu, tak długo, jak listy argumentów dla każdego indeksatora są unikatowe. Zapoznaj się z różnymi scenariuszami, w których możesz użyć co najmniej jednego indeksatora w definicji klasy.

## <a name="scenarios"></a>Scenariusze

Można zdefiniować *indeksatory* w typie, gdy jego interfejs API modeluje pewne kolekcje, w których zdefiniowano argumenty tej kolekcji. Indeksatory mogą lub nie mogą być mapowane bezpośrednio do typów kolekcji, które są częścią programu .NET Core Framework. Typ może mieć inne obowiązki oprócz modelowania kolekcji.
Indeksatory umożliwiają udostępnienie interfejsu API, który jest zgodny z abstrakcyjnym typem, bez uwidaczniania wewnętrznych informacji o sposobie przechowywania lub obliczania wartości dla tego abstrakcji.

Zapoznaj się z kilkoma typowymi scenariuszami dotyczącymi używania *indeksatorów*. Możesz uzyskać dostęp do [przykładowego folderu dla indeksatorów](https://github.com/dotnet/samples/tree/master/csharp/indexers). Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Tablice i wektory

Jednym z najpopularniejszych scenariuszy tworzenia indeksatorów jest to, że typ modeluje tablicę lub wektor. Można utworzyć indeksator do modelowania uporządkowanej listy danych.

Zaletą tworzenia własnego indeksatora jest możliwość zdefiniowania magazynu dla tej kolekcji zgodnie z potrzebami. Załóżmy, że Twój typ modeluje dane historyczne, które są zbyt duże do załadowania do pamięci jednocześnie. Należy załadować i zwolnić sekcje kolekcji na podstawie użycia. W przykładzie poniżej przedstawiono model tego zachowania. Raport przedstawia liczbę istniejących punktów danych. Tworzy strony do przechowywania sekcji danych na żądanie. Usuwa strony z pamięci, aby zwolnić miejsce dla stron wymaganych przez nowsze żądania.

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

Można postępować zgodnie z idiom projektu, aby modelować dowolne sortowanie kolekcji, w której istnieją dobre powody, aby nie ładować całego zestawu danych do kolekcji w pamięci. Należy zauważyć, że `Page` Klasa jest prywatną klasą zagnieżdżoną, która nie jest częścią interfejsu publicznego. Te szczegóły są ukryte dla wszystkich użytkowników tej klasy.

### <a name="dictionaries"></a>Słowniki

Inny typowy scenariusz jest konieczny do modelowania słownika lub mapy. Ten scenariusz polega na tym, że typ przechowuje wartości w oparciu o klucz, zazwyczaj klucze tekstowe. W tym przykładzie tworzony jest słownik, który mapuje argumenty wiersza polecenia na [wyrażenia lambda](delegates-overview.md) , które zarządzają tymi opcjami. W poniższym przykładzie przedstawiono dwie klasy: `ArgsActions` Klasa, która mapuje opcję wiersza polecenia na `Action` delegata, i `ArgsProcessor` używa `ArgsActions` do wykonywania każdej z nich `Action` podczas napotkania tej opcji.

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

W tym przykładzie `ArgsAction` Kolekcja kolekcji jest ściśle mapowana do źródłowej kolekcji.
`get`Określa, czy dana opcja została skonfigurowana. W takim przypadku zwraca `Action` skojarzoną z tą opcją. Jeśli nie, zwraca wartość `Action` , która nic nie robi. Publiczna metoda dostępu nie obejmuje `set` metody dostępu. Zamiast tego projekt przy użyciu metody publicznej służącej do ustawiania opcji.

### <a name="multi-dimensional-maps"></a>Mapy wielowymiarowe

Można tworzyć indeksatory używające wielu argumentów. Ponadto te argumenty nie są ograniczone do tego samego typu. Przyjrzyjmy się dwóm przykładom.

Pierwszy przykład przedstawia klasę, która generuje wartości dla zestawu Mandelbrot. Aby uzyskać więcej informacji na temat matematyki za zestawem, Przeczytaj [ten artykuł](https://en.wikipedia.org/wiki/Mandelbrot_set).
Indeksator używa dwóch podwaja do definiowania punktu w płaszczyźnie X, Y.
Metoda dostępu get oblicza liczbę iteracji do momentu, gdy punkt nie zostanie ustalony w zestawie. W przypadku osiągnięcia maksymalnej liczby iteracji punkt znajduje się w zestawie i zwracana jest wartość maxIterations klasy. (Typowe obrazy wygenerowane przez komputer dla zestawu Mandelbrot definiują kolory dla liczby iteracji wymaganych do określenia, że punkt znajduje się poza zestawem.

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

Zestaw Mandelbrot definiuje wartości dla każdej współrzędnej (x, y) dla wartości liczb rzeczywistych.
Definiuje słownik, który może zawierać nieskończoną liczbę wartości. W związku z tym nie istnieje magazyn związany z zestawem. Zamiast tego Klasa oblicza wartość dla każdego punktu, gdy kod wywołuje `get` metodę dostępu. Nie jest używany magazyn bazowy.

Sprawdźmy jedno z ostatniego użycia indeksatorów, gdzie indeksator przyjmuje wiele argumentów różnych typów. Weź pod uwagę program, który zarządza danymi temperatury historycznej. Ten indeksator używa miasta i daty, aby ustawić lub uzyskać górną i dolną temperaturę dla tej lokalizacji:

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

W tym przykładzie tworzony jest indeksator, który mapuje dane pogodowe na dwa różne argumenty: miasto (reprezentowane przez a `string` ) i datę (reprezentowane przez `DateTime` ). Magazyn wewnętrzny używa dwóch `Dictionary` klas do reprezentowania dwuwymiarowego słownika. Publiczny interfejs API nie reprezentuje już bazowego magazynu. Zamiast tego funkcje językowe indeksatorów umożliwiają utworzenie interfejsu publicznego, który reprezentuje streszczenie, nawet jeśli podstawowy magazyn musi korzystać z różnych podstawowych typów kolekcji.

Istnieją dwie części tego kodu, które mogą być nieznane dla niektórych deweloperów. Te dwie `using` dyrektywy:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

Utwórz *alias* dla konstruowanego typu ogólnego. Te instrukcje umożliwiają późniejsze użycie większej liczby opisów `DateMeasurements` i `CityDateMeasurements` nazw zamiast ogólnej konstrukcji `Dictionary<DateTime, Measurements>` i `Dictionary<string, Dictionary<DateTime, Measurements> >` .
Ta konstrukcja wymaga użycia w pełni kwalifikowanych nazw typów po prawej stronie `=` znaku.

Druga metoda polega na rozdzieleniu części czasu dowolnego `DateTime` obiektu używanego do indeksowania kolekcji. Platforma .NET nie zawiera typu tylko daty.
Deweloperzy używają `DateTime` typu, ale używają właściwości, `Date` Aby upewnić się, że każdy `DateTime` obiekt z tego dnia będzie równy.

## <a name="summing-up"></a>Sumowanie

Indeksatory należy tworzyć w dowolnym momencie, gdy istnieje element podobny do właściwości w klasie, gdzie ta właściwość reprezentuje nie pojedynczą wartość, ale raczej zbiór wartości, w których każdy indywidualny element jest identyfikowany przez zestaw argumentów. Te argumenty mogą jednoznacznie identyfikować, do którego elementu w kolekcji należy się odwoływać.
Indeksatory zwiększają koncepcję [Właściwości](properties.md), gdzie element członkowski jest traktowany jak element danych spoza klasy, ale taki jak Metoda wewnątrz. Indeksatory umożliwiają argumentom znalezienie pojedynczego elementu we właściwości, która reprezentuje zestaw elementów.
