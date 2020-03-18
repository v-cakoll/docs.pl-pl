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
# <a name="indexers"></a><span data-ttu-id="63dd2-103">Indexers (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="63dd2-103">Indexers</span></span>

<span data-ttu-id="63dd2-104">*Indeksatory* są podobne do właściwości.</span><span class="sxs-lookup"><span data-stu-id="63dd2-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="63dd2-105">Na wiele sposobów indeksatory opierają się na tych samych funkcjach języka, co [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="63dd2-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="63dd2-106">Indeksatory włączyć właściwości *indeksowane:* właściwości odwołuje się przy użyciu jednego lub więcej argumentów.</span><span class="sxs-lookup"><span data-stu-id="63dd2-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="63dd2-107">Te argumenty zapewniają indeks do niektórych kolekcji wartości.</span><span class="sxs-lookup"><span data-stu-id="63dd2-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="63dd2-108">Składnia indeksatora</span><span class="sxs-lookup"><span data-stu-id="63dd2-108">Indexer Syntax</span></span>

<span data-ttu-id="63dd2-109">Dostęp do indeksatora za pomocą nazwy zmiennej i nawiasów kwadratowych.</span><span class="sxs-lookup"><span data-stu-id="63dd2-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="63dd2-110">Argumenty indeksatora można umieścić wewnątrz nawiasów:</span><span class="sxs-lookup"><span data-stu-id="63dd2-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="63dd2-111">Indeksatory deklarujesz używając słowa kluczowego `this` jako nazwy właściwości i deklarując argumenty w nawiasach kwadratowych.</span><span class="sxs-lookup"><span data-stu-id="63dd2-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="63dd2-112">Ta deklaracja będzie zgodna z użyciem pokazanym w poprzednim akapicie:</span><span class="sxs-lookup"><span data-stu-id="63dd2-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="63dd2-113">W tym przykładzie początkowym można zobaczyć relację między składnią właściwości i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="63dd2-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="63dd2-114">Ta analogia przenosi większość reguł składni dla indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="63dd2-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="63dd2-115">Indeksatory mogą mieć dowolne prawidłowe modyfikatory dostępu (publiczne, chronione wewnętrzne, chronione, wewnętrzne, prywatne lub prywatne chronione).</span><span class="sxs-lookup"><span data-stu-id="63dd2-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="63dd2-116">Mogą być zapieczętowane, wirtualne lub abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="63dd2-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="63dd2-117">Podobnie jak w przypadku właściwości, można określić różne modyfikatory dostępu dla get i set akcesorów w indeksatorze.</span><span class="sxs-lookup"><span data-stu-id="63dd2-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="63dd2-118">Można również określić indeksatory tylko do odczytu (pomijając set akcesor) lub indeksatory tylko do zapisu (pomijając get akcesor).</span><span class="sxs-lookup"><span data-stu-id="63dd2-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="63dd2-119">Możesz zastosować prawie wszystko, czego uczysz się od pracy z właściwościami do indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="63dd2-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="63dd2-120">Jedynym wyjątkiem od tej reguły są *właściwości implementowane automatycznie*.</span><span class="sxs-lookup"><span data-stu-id="63dd2-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="63dd2-121">Kompilator nie zawsze może wygenerować poprawny magazyn dla indeksatora.</span><span class="sxs-lookup"><span data-stu-id="63dd2-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="63dd2-122">Obecność argumentów do odwoływania się do elementu w zestawie elementów odróżnia indeksatory od właściwości.</span><span class="sxs-lookup"><span data-stu-id="63dd2-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="63dd2-123">Można zdefiniować wiele indeksatorów dla typu, tak długo, jak listy argumentów dla każdego indeksatora jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="63dd2-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="63dd2-124">Przyjrzyjmy się różne scenariusze, w których można użyć jednego lub więcej indeksatorów w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="63dd2-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span>

## <a name="scenarios"></a><span data-ttu-id="63dd2-125">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="63dd2-125">Scenarios</span></span>

<span data-ttu-id="63dd2-126">Można zdefiniować *indeksatory* w typie, gdy jego modele interfejsu API niektóre kolekcji, gdzie można zdefiniować argumenty do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="63dd2-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="63dd2-127">Indeksatory mogą lub nie mogą być mapowane bezpośrednio do typów kolekcji, które są częścią platformy .NET core.</span><span class="sxs-lookup"><span data-stu-id="63dd2-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="63dd2-128">Typ może mieć inne obowiązki oprócz modelowania kolekcji.</span><span class="sxs-lookup"><span data-stu-id="63dd2-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="63dd2-129">Indeksatory umożliwiają podanie interfejsu API, który pasuje do abstrakcji typu bez ujawniania wewnętrznych szczegółów, w jaki sposób wartości dla tej abstrakcji są przechowywane lub obliczane.</span><span class="sxs-lookup"><span data-stu-id="63dd2-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="63dd2-130">Przejdźmy przez niektóre typowe scenariusze korzystania z *indeksatorów*.</span><span class="sxs-lookup"><span data-stu-id="63dd2-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="63dd2-131">Można uzyskać dostęp do [przykładowego folderu dla indeksatorów](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="63dd2-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="63dd2-132">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="63dd2-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="63dd2-133">Tablice i wektory</span><span class="sxs-lookup"><span data-stu-id="63dd2-133">Arrays and Vectors</span></span>

<span data-ttu-id="63dd2-134">Jednym z najbardziej typowych scenariuszy tworzenia indeksatorów jest, gdy typ modeli tablicy lub wektora.</span><span class="sxs-lookup"><span data-stu-id="63dd2-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="63dd2-135">Indeksatora można utworzyć w celu modelowania uporządkowanej listy danych.</span><span class="sxs-lookup"><span data-stu-id="63dd2-135">You can create an indexer to model an ordered list of data.</span></span>

<span data-ttu-id="63dd2-136">Zaletą tworzenia własnego indeksatora jest to, że można zdefiniować magazyn dla tej kolekcji do własnych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="63dd2-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="63dd2-137">Wyobraź sobie scenariusz, w którym typ modeli danych historycznych, który jest zbyt duży, aby załadować do pamięci na raz.</span><span class="sxs-lookup"><span data-stu-id="63dd2-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="63dd2-138">Należy załadować i rozładować sekcje kolekcji na podstawie użycia.</span><span class="sxs-lookup"><span data-stu-id="63dd2-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="63dd2-139">W poniższym przykładzie modele to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="63dd2-139">The example following models this behavior.</span></span> <span data-ttu-id="63dd2-140">Raportuje, ile punktów danych istnieje.</span><span class="sxs-lookup"><span data-stu-id="63dd2-140">It reports on how many data points exist.</span></span> <span data-ttu-id="63dd2-141">Tworzy strony do przechowywania sekcji danych na żądanie.</span><span class="sxs-lookup"><span data-stu-id="63dd2-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="63dd2-142">Usuwa strony z pamięci, aby zrobić miejsce dla stron potrzebnych przez nowsze żądania.</span><span class="sxs-lookup"><span data-stu-id="63dd2-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="63dd2-143">Można wykonać ten projekt idiom do modelu wszelkiego rodzaju kolekcji, gdzie istnieją dobre powody, aby nie załadować cały zestaw danych do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="63dd2-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="63dd2-144">Należy zauważyć, że `Page` klasa jest prywatną klasą zagnieżdżoną, która nie jest częścią interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="63dd2-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="63dd2-145">Te szczegóły są ukryte przed użytkownikami tej klasy.</span><span class="sxs-lookup"><span data-stu-id="63dd2-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="63dd2-146">Słowniki</span><span class="sxs-lookup"><span data-stu-id="63dd2-146">Dictionaries</span></span>

<span data-ttu-id="63dd2-147">Innym typowym scenariuszem jest, gdy trzeba modelować słownika lub mapy.</span><span class="sxs-lookup"><span data-stu-id="63dd2-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="63dd2-148">W tym scenariuszu jest, gdy typ przechowuje wartości na podstawie klucza, zazwyczaj klucze tekstowe.</span><span class="sxs-lookup"><span data-stu-id="63dd2-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="63dd2-149">W tym przykładzie tworzy słownik, który mapuje argumenty wiersza polecenia do [wyrażeń lambda,](delegates-overview.md) które zarządzają tymi opcjami.</span><span class="sxs-lookup"><span data-stu-id="63dd2-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="63dd2-150">W poniższym przykładzie przedstawiono `ArgsActions` dwie klasy: klasę, `Action` która mapuje `ArgsProcessor` opcję wiersza polecenia na pełnomocnika i która używa `ArgsActions` do wykonania każdej z nich, `Action` gdy napotka tę opcję.</span><span class="sxs-lookup"><span data-stu-id="63dd2-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="63dd2-151">W tym przykładzie `ArgsAction` kolekcja mapuje ściśle do podstawowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="63dd2-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="63dd2-152">Określa, `get` czy dana opcja została skonfigurowana.</span><span class="sxs-lookup"><span data-stu-id="63dd2-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="63dd2-153">Jeśli tak, zwraca `Action` skojarzony z tą opcją.</span><span class="sxs-lookup"><span data-stu-id="63dd2-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="63dd2-154">Jeśli nie, `Action` zwraca, że nic nie robi.</span><span class="sxs-lookup"><span data-stu-id="63dd2-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="63dd2-155">Publiczny akcesor `set` nie obejmuje akcesora.</span><span class="sxs-lookup"><span data-stu-id="63dd2-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="63dd2-156">Zamiast tego projekt przy użyciu publicznej metody ustawiania opcji.</span><span class="sxs-lookup"><span data-stu-id="63dd2-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="63dd2-157">Mapy wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="63dd2-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="63dd2-158">Można utworzyć indeksatory, które używają wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="63dd2-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="63dd2-159">Ponadto te argumenty nie są ograniczone do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="63dd2-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="63dd2-160">Spójrzmy na dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="63dd2-160">Let's look at two examples.</span></span>

<span data-ttu-id="63dd2-161">Pierwszy przykład pokazuje klasę, która generuje wartości dla zestawu Mandelbrot.</span><span class="sxs-lookup"><span data-stu-id="63dd2-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="63dd2-162">Aby uzyskać więcej informacji na temat matematyki za zestaw, przeczytaj [ten artykuł](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="63dd2-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span>
<span data-ttu-id="63dd2-163">Indeksator używa dwóch podwaja do zdefiniowania punktu w X, Y płaszczyzny.</span><span class="sxs-lookup"><span data-stu-id="63dd2-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="63dd2-164">Get akcesor oblicza liczbę iteracji, dopóki punkt nie zostanie określony jako nie w zestawie.</span><span class="sxs-lookup"><span data-stu-id="63dd2-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="63dd2-165">Jeśli zostanie osiągnięta maksymalna iteracji, punkt znajduje się w zestawie, a wartość maksymalizacji klasy jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="63dd2-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="63dd2-166">(Obrazy generowane przez komputer spopularyzowane dla zestawu Mandelbrot definiują kolory dla liczby iteracji niezbędnych do określenia, że punkt znajduje się poza zestawem.</span><span class="sxs-lookup"><span data-stu-id="63dd2-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="63dd2-167">Zestaw Mandelbrot definiuje wartości w każdej współrzędnej (x,y) dla wartości liczb rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="63dd2-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="63dd2-168">Który definiuje słownik, który może zawierać nieskończoną liczbę wartości.</span><span class="sxs-lookup"><span data-stu-id="63dd2-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="63dd2-169">W związku z tym nie ma magazynu za zestaw.</span><span class="sxs-lookup"><span data-stu-id="63dd2-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="63dd2-170">Zamiast tego ta klasa oblicza wartość dla każdego `get` punktu, gdy kod wywołuje akcesor.</span><span class="sxs-lookup"><span data-stu-id="63dd2-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="63dd2-171">Nie jest używany podstawowy magazyn.</span><span class="sxs-lookup"><span data-stu-id="63dd2-171">There's no underlying storage used.</span></span>

<span data-ttu-id="63dd2-172">Przyjrzyjmy się ostatniemu użyciu indeksatorów, gdzie indeksator przyjmuje wiele argumentów różnych typów.</span><span class="sxs-lookup"><span data-stu-id="63dd2-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="63dd2-173">Rozważmy program, który zarządza historycznymi danymi temperatury.</span><span class="sxs-lookup"><span data-stu-id="63dd2-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="63dd2-174">Ten indeksator używa miasta i daty, aby ustawić lub uzyskać wysokie i niskie temperatury dla tej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="63dd2-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="63dd2-175">W tym przykładzie tworzy indeksator, który mapuje dane pogodowe `string`na dwa różne argumenty: `DateTime`miasto (reprezentowane przez ) i datę (reprezentowaną przez ).</span><span class="sxs-lookup"><span data-stu-id="63dd2-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="63dd2-176">Magazyn wewnętrzny używa `Dictionary` dwóch klas do reprezentowania słownika dwuwymiarowego.</span><span class="sxs-lookup"><span data-stu-id="63dd2-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="63dd2-177">Publiczny interfejs API nie reprezentuje już podstawowego magazynu.</span><span class="sxs-lookup"><span data-stu-id="63dd2-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="63dd2-178">Zamiast tego funkcje języka indeksatorów umożliwia utworzenie interfejsu publicznego, który reprezentuje abstrakcji, mimo że podstawowego magazynu musi używać różnych typów kolekcji podstawowych.</span><span class="sxs-lookup"><span data-stu-id="63dd2-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="63dd2-179">Istnieją dwie części tego kodu, które mogą być nieznane niektórym deweloperom.</span><span class="sxs-lookup"><span data-stu-id="63dd2-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="63dd2-180">Te `using` dwa stwierdzenia:</span><span class="sxs-lookup"><span data-stu-id="63dd2-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="63dd2-181">utworzyć *alias* dla skonstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="63dd2-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="63dd2-182">Instrukcje te umożliwiają kod później użyć bardziej `DateMeasurements` opisowe `CityDateMeasurements` i nazwy `Dictionary<DateTime, Measurements>` zamiast `Dictionary<string, Dictionary<DateTime, Measurements> >`ogólnej budowy i .</span><span class="sxs-lookup"><span data-stu-id="63dd2-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span>
<span data-ttu-id="63dd2-183">Ta konstrukcja wymaga użycia w pełni kwalifikowanych nazw `=` typów po prawej stronie znaku.</span><span class="sxs-lookup"><span data-stu-id="63dd2-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="63dd2-184">Druga technika jest usunięcie części czasu `DateTime` dowolnego obiektu używanego do indeksowania do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="63dd2-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="63dd2-185">.NET nie zawiera typu tylko daty.</span><span class="sxs-lookup"><span data-stu-id="63dd2-185">.NET doesn't include a date-only type.</span></span>
<span data-ttu-id="63dd2-186">Deweloperzy `DateTime` używają tego typu, ale `Date` użyj `DateTime` właściwości, aby upewnić się, że każdy obiekt z tego dnia są równe.</span><span class="sxs-lookup"><span data-stu-id="63dd2-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="63dd2-187">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="63dd2-187">Summing Up</span></span>

<span data-ttu-id="63dd2-188">Indeksatory należy utworzyć w dowolnym momencie masz element podobny do właściwości w klasie, gdzie ta właściwość reprezentuje nie pojedynczą wartość, ale raczej kolekcję wartości, gdzie każdy pojedynczy element jest identyfikowany przez zestaw argumentów.</span><span class="sxs-lookup"><span data-stu-id="63dd2-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="63dd2-189">Te argumenty można jednoznacznie zidentyfikować, który element w kolekcji należy odwoływać.</span><span class="sxs-lookup"><span data-stu-id="63dd2-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="63dd2-190">Indeksatory rozszerzyć pojęcie [właściwości](properties.md), gdzie element członkowski jest traktowany jak element danych spoza klasy, ale jak metoda w środku.</span><span class="sxs-lookup"><span data-stu-id="63dd2-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the inside.</span></span> <span data-ttu-id="63dd2-191">Indeksatory zezwalają na znajdowanie pojedynczego elementu we właściwości reprezentującej zestaw elementów.</span><span class="sxs-lookup"><span data-stu-id="63dd2-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
