---
title: Indeksatory
description: Dowiedz się więcej o C# indeksatory i sposób implementacji indeksowane właściwości, które są właściwościami wskazywane za pomocą jednego lub więcej argumentów.
ms.date: 06/20/2016
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: a13163cb6bd835dfdd16c83c905c134eb8a86e7d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197603"
---
# <a name="indexers"></a><span data-ttu-id="692af-103">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="692af-103">Indexers</span></span>

<span data-ttu-id="692af-104">*Indeksatory* są podobne do właściwości.</span><span class="sxs-lookup"><span data-stu-id="692af-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="692af-105">Na wiele sposobów indeksatory kompilacji na te same funkcje języka jako [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="692af-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="692af-106">Włącz indeksatory *indeksowane* właściwości: właściwości, do których odwołuje się przy użyciu jednego lub więcej argumentów.</span><span class="sxs-lookup"><span data-stu-id="692af-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="692af-107">Te argumenty zawierają indeksu do niektórych kolekcji wartości.</span><span class="sxs-lookup"><span data-stu-id="692af-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="692af-108">Składnia indeksatora</span><span class="sxs-lookup"><span data-stu-id="692af-108">Indexer Syntax</span></span>

<span data-ttu-id="692af-109">Indeksator dostępu za pomocą nazwy zmiennej i nawiasami kwadratowymi.</span><span class="sxs-lookup"><span data-stu-id="692af-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="692af-110">Możesz umieścić argumenty indeksatora w nawiasie:</span><span class="sxs-lookup"><span data-stu-id="692af-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="692af-111">Można zadeklarować indeksatorów za pomocą `this` słowa kluczowego jako nazwy właściwości i deklarowanie argumentów w nawiasy kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="692af-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="692af-112">Ta deklaracja będzie odpowiadać użycia pokazano w poprzednim akapicie:</span><span class="sxs-lookup"><span data-stu-id="692af-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="692af-113">W tym przykładzie początkowej można zobaczyć relację pomiędzy składni dla właściwości i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="692af-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="692af-114">Ten sposób analogiczny niesie ze sobą za pośrednictwem większość reguł dotyczących składni dla indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="692af-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="692af-115">Indeksatory może mieć żadnych modyfikatorów dostępu nie jest ważna (publicznych, chronionych wewnętrznych, chronione, wewnętrzne, prywatne lub prywatnych chronionych).</span><span class="sxs-lookup"><span data-stu-id="692af-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="692af-116">Mogą one sealed, wirtualne ani abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="692af-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="692af-117">Podobnie jak w przypadku właściwości, można określić modyfikatorów różny dostęp do pobierania i zestawu metod dostępu w indeksatorze.</span><span class="sxs-lookup"><span data-stu-id="692af-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="692af-118">Możesz również określić indeksatory tylko do odczytu (pomijając metody dostępu set) lub indeksatory tylko do zapisu (pomijając metody dostępu get).</span><span class="sxs-lookup"><span data-stu-id="692af-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="692af-119">Można zastosować prawie wszystko, czego nauczysz się praca z właściwości w celu indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="692af-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="692af-120">Jedynym wyjątkiem od tej reguły jest *automatycznie implementowane właściwości*.</span><span class="sxs-lookup"><span data-stu-id="692af-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="692af-121">Kompilator nie zawsze Generuj poprawny magazyn dla indeksatora.</span><span class="sxs-lookup"><span data-stu-id="692af-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="692af-122">Obecność argumenty, które odwołuje się do elementu w zestawie elementów odróżnia indeksatory od właściwości.</span><span class="sxs-lookup"><span data-stu-id="692af-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="692af-123">Można zdefiniować wiele indeksatorów w danym typie tak długo, jak wykazy argumentów dla każdego indeksatora jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="692af-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="692af-124">Przyjrzyjmy się różne scenariusze których można użyć co najmniej jeden indeksatorów w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="692af-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span> 

## <a name="scenarios"></a><span data-ttu-id="692af-125">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="692af-125">Scenarios</span></span>

<span data-ttu-id="692af-126">Należy zdefiniować *indeksatory* w danego typu, gdy jej interfejsu API modeli niektóre kolekcji, w którym zdefiniuj argumenty do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="692af-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="692af-127">Twoje indeksatory mogą lub nie mogą być mapowane bezpośrednio do typów kolekcji, które są częścią platformy .NET core framework.</span><span class="sxs-lookup"><span data-stu-id="692af-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="692af-128">Danego typu może mieć inne obowiązki oprócz modelowania kolekcji.</span><span class="sxs-lookup"><span data-stu-id="692af-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="692af-129">Indeksatory umożliwiają interfejsu API, który odpowiada abstrakcji danego typu bez narażania wewnętrzny szczegóły jak przechowywane lub obliczonych wartości dla tego abstrakcji.</span><span class="sxs-lookup"><span data-stu-id="692af-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="692af-130">Przejdźmy teraz przez niektóre typowe scenariusze za pomocą *indeksatory*.</span><span class="sxs-lookup"><span data-stu-id="692af-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="692af-131">Możesz uzyskać dostęp [przykładowy folder dla indeksatorów](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="692af-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="692af-132">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="692af-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="692af-133">Tablice i wektory</span><span class="sxs-lookup"><span data-stu-id="692af-133">Arrays and Vectors</span></span>

<span data-ttu-id="692af-134">Jest jednym z najbardziej typowych scenariuszy, do tworzenia indeksatorów, gdy typu modele tablicy lub wektora.</span><span class="sxs-lookup"><span data-stu-id="692af-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="692af-135">Można utworzyć indeksator do modelowania uporządkowaną listę danych.</span><span class="sxs-lookup"><span data-stu-id="692af-135">You can create an indexer to model an ordered list of data.</span></span> 

<span data-ttu-id="692af-136">Zaletą tworzenia własnych indeksatora jest zdefiniować magazynu dla tej kolekcji, w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="692af-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="692af-137">Wyobraź sobie scenariusz, w którym typu modele danych historycznych, który jest zbyt duży, aby załadować do pamięci na raz.</span><span class="sxs-lookup"><span data-stu-id="692af-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="692af-138">Należy załadować i rozładować sekcje kolekcji na podstawie użycia.</span><span class="sxs-lookup"><span data-stu-id="692af-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="692af-139">Poniższy przykład modeluje zachowania.</span><span class="sxs-lookup"><span data-stu-id="692af-139">The example following models this behavior.</span></span> <span data-ttu-id="692af-140">Raportuje, na ile punktów danych istnieje.</span><span class="sxs-lookup"><span data-stu-id="692af-140">It reports on how many data points exist.</span></span> <span data-ttu-id="692af-141">Tworzy strony do przechowywania części danych na żądanie.</span><span class="sxs-lookup"><span data-stu-id="692af-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="692af-142">Usuwa stron z pamięci, aby zwolnić miejsce dla stron wymagane przez nowszą żądań.</span><span class="sxs-lookup"><span data-stu-id="692af-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="692af-143">Można wykonać tego idiomu projektu do modelowania dowolny rodzaj kolekcji w przypadku, gdy istnieje wiele powodów, nie można załadować cały zestaw danych do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="692af-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="692af-144">Należy zauważyć, że `Page` klasa jest klasą zagnieżdżoną prywatnych nie jest częścią interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="692af-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="692af-145">Te informacje są ukryte przed wszyscy użytkownicy tej klasy.</span><span class="sxs-lookup"><span data-stu-id="692af-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="692af-146">słowniki</span><span class="sxs-lookup"><span data-stu-id="692af-146">Dictionaries</span></span>

<span data-ttu-id="692af-147">Inny typowy scenariusz polega, gdy trzeba modelu obiekt dictionary lub mapy.</span><span class="sxs-lookup"><span data-stu-id="692af-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="692af-148">Ten scenariusz jest, jeśli danego typu przechowuje wartości na podstawie klucza, zazwyczaj klucze tekstu.</span><span class="sxs-lookup"><span data-stu-id="692af-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="692af-149">W tym przykładzie tworzy słownik mapujący argumenty wiersza polecenia do [wyrażeń lambda](delegates-overview.md) zarządzające tych opcji.</span><span class="sxs-lookup"><span data-stu-id="692af-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="692af-150">W poniższym przykładzie przedstawiono dwóch klas: `ArgsActions` klasa, która mapuje opcję wiersza polecenia, aby `Action` delegować i `ArgsProcessor` , który używa `ArgsActions` do wykonania każdego `Action` po napotkaniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="692af-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="692af-151">W tym przykładzie `ArgsAction` kolekcji ściśle mapuje do podstawowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="692af-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="692af-152">`get` Decyduje, jeśli skonfigurowano danej opcji.</span><span class="sxs-lookup"><span data-stu-id="692af-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="692af-153">Jeśli tak, zwraca `Action` skojarzone z tej opcji.</span><span class="sxs-lookup"><span data-stu-id="692af-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="692af-154">Jeśli nie, zwraca `Action` , nic nie robi.</span><span class="sxs-lookup"><span data-stu-id="692af-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="692af-155">Nie ma publicznej metody dostępu `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="692af-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="692af-156">Zamiast projektu za pomocą publicznej metody do ustawiania opcji.</span><span class="sxs-lookup"><span data-stu-id="692af-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="692af-157">Wielowymiarowe mapy</span><span class="sxs-lookup"><span data-stu-id="692af-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="692af-158">Możesz tworzyć indeksatory, korzystających z wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="692af-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="692af-159">Oprócz tych argumentów nie są ograniczone do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="692af-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="692af-160">Przyjrzyjmy się dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="692af-160">Let's look at two examples.</span></span>   

<span data-ttu-id="692af-161">W pierwszym przykładzie pokazano klasę, która generuje wartości z zestawu Mandelbrot.</span><span class="sxs-lookup"><span data-stu-id="692af-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="692af-162">Aby uzyskać więcej informacji na matematyce za zestaw odczytu [w tym artykule](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="692af-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span> <span data-ttu-id="692af-163">Indeksator używa dwóch wartości podwójnej precyzji, aby zdefiniować punkt x, Y płaszczyzny.</span><span class="sxs-lookup"><span data-stu-id="692af-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="692af-164">Metody dostępu get oblicza liczbę iteracji, dopóki punkt zostanie uznane za nie może być w zestawie.</span><span class="sxs-lookup"><span data-stu-id="692af-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="692af-165">Jeśli zostanie osiągnięta maksymalna liczba iteracji, punkt znajduje się w zestawie i zwracana jest wartość maxIterations tej klasy.</span><span class="sxs-lookup"><span data-stu-id="692af-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="692af-166">(Obrazy wygenerowanego przez komputer spopularyzowany dla zestawu Mandelbrot zdefiniowanie kolorów liczba iteracji, które są niezbędne w celu ustalenia, czy punkt znajduje się poza zestaw.</span><span class="sxs-lookup"><span data-stu-id="692af-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="692af-167">Zestaw Mandelbrot definiuje wartości w każdym folderu (x, y) koordynować rzeczywiste wartości liczbowe.</span><span class="sxs-lookup"><span data-stu-id="692af-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="692af-168">Definiuje słownik, który może zawierać nieograniczoną liczbę wartości.</span><span class="sxs-lookup"><span data-stu-id="692af-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="692af-169">Dlatego jest Brak magazynu poza zestaw.</span><span class="sxs-lookup"><span data-stu-id="692af-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="692af-170">Zamiast tego należy ta klasa oblicza wartość dla każdego punktu, gdy kod wywołuje `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="692af-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="692af-171">Nie ma żadnych magazynu.</span><span class="sxs-lookup"><span data-stu-id="692af-171">There's no underlying storage used.</span></span>

<span data-ttu-id="692af-172">Przeanalizujmy ostatniego użycia jeden z indeksatorów, w której indeksator ma wiele argumentów o różnych typach.</span><span class="sxs-lookup"><span data-stu-id="692af-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="692af-173">Należy wziąć pod uwagę program, który zarządza dane historyczne dotyczące temperatury.</span><span class="sxs-lookup"><span data-stu-id="692af-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="692af-174">Ten indeksator używa miejscowość i datę można ustawiać ani pobierać wysokich i niskich temperatur wobec tej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="692af-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="692af-175">W tym przykładzie tworzy działanie indeksatora, który mapuje dane pogody na dwa różne argumenty: mieście (reprezentowane przez `string`) i daty (reprezentowane przez `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="692af-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="692af-176">Wewnętrzny magazyn korzysta z dwóch `Dictionary` klasy do reprezentowania dwuwymiarową słownika.</span><span class="sxs-lookup"><span data-stu-id="692af-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="692af-177">Publiczny interfejs API nie jest już reprezentuje podstawowy magazyn.</span><span class="sxs-lookup"><span data-stu-id="692af-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="692af-178">Zamiast funkcji języka, indeksatorów pozwala na tworzenie publiczny interfejs, który reprezentuje swoje abstrakcji, mimo że bazowego magazynu, należy użyć różne podstawowe typy kolekcji.</span><span class="sxs-lookup"><span data-stu-id="692af-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="692af-179">Istnieją dwie części ten kod, który może być nieznane dla niektórych programistów.</span><span class="sxs-lookup"><span data-stu-id="692af-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="692af-180">Te dwa `using` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="692af-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="692af-181">Tworzenie *alias* dla zbudowany typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="692af-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="692af-182">Te instrukcje należy włączyć kod później użyć bardziej opisowe `DateMeasurements` i `CityDateMeasurements` nazwy zamiast ogólnych konstrukcja `Dictionary<DateTime, Measurements>` i `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="692af-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span> <span data-ttu-id="692af-183">Ta konstrukcja wymaga przy użyciu w pełni kwalifikowanych nazw typów na prawej krawędzi `=` logowania.</span><span class="sxs-lookup"><span data-stu-id="692af-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="692af-184">Drugi techniką jest paska Wyłącz fragmenty czas dowolnych `DateTime` obiekt używany do indeksowania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="692af-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="692af-185">.NET framework nie zawiera typu tylko data.</span><span class="sxs-lookup"><span data-stu-id="692af-185">The .NET framework does not include a Date only type.</span></span>
<span data-ttu-id="692af-186">Deweloperzy używają `DateTime` typu, ale użyj `Date` właściwość, aby upewnić się, że dowolne `DateTime` obiektu z tego samego dnia są takie same.</span><span class="sxs-lookup"><span data-stu-id="692af-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="692af-187">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="692af-187">Summing Up</span></span>

<span data-ttu-id="692af-188">Indeksatory należy utworzyć w dowolnym momencie ma elementu właściwości w klasie gdzie tę właściwość reprezentuje pojedynczą wartość, ale raczej zbiór wartości, gdzie poszczególnych elementów jest identyfikowany przez zestawu argumentów.</span><span class="sxs-lookup"><span data-stu-id="692af-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="692af-189">Te argumenty może jednoznacznie zidentyfikować, który element w kolekcji, które powinny istnieć odwołania.</span><span class="sxs-lookup"><span data-stu-id="692af-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="692af-190">Indeksatory rozszerzenie pojęcia [właściwości](properties.md), której członkiem jest traktowany jak elementu danych z poza klasy, ale jak metoda po stronie.</span><span class="sxs-lookup"><span data-stu-id="692af-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the side.</span></span> <span data-ttu-id="692af-191">Indeksatory zezwalają na argumenty znaleźć pojedynczy element we właściwości, które reprezentuje zestaw elementów.</span><span class="sxs-lookup"><span data-stu-id="692af-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
