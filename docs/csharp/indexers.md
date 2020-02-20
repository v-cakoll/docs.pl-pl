---
title: Indexers (Indeksatory)
description: Dowiedz C# się więcej na temat indeksatorów i sposobu implementowania właściwości indeksowanych, które są właściwościami, do których odwołuje się jeden lub więcej argumentów.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 966483e80d8dd0421dce1b7fabdb0d443d73a0fc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450885"
---
# <a name="indexers"></a><span data-ttu-id="b7677-103">Indexers (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="b7677-103">Indexers</span></span>

<span data-ttu-id="b7677-104">*Indeksatory* są podobne do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b7677-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="b7677-105">Na wiele sposobów Indeksatory są kompilowane przy użyciu tych samych funkcji językowych, co [Właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="b7677-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="b7677-106">Indeksatory włączają *indeksowane* właściwości: właściwości, których dotyczy odwołanie, przy użyciu co najmniej jednego argumentu.</span><span class="sxs-lookup"><span data-stu-id="b7677-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="b7677-107">Te argumenty zapewniają indeks do pewnej kolekcji wartości.</span><span class="sxs-lookup"><span data-stu-id="b7677-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="b7677-108">Składnia indeksatora</span><span class="sxs-lookup"><span data-stu-id="b7677-108">Indexer Syntax</span></span>

<span data-ttu-id="b7677-109">Dostęp do indeksatora można uzyskać za pomocą nazwy zmiennej i nawiasów kwadratowych.</span><span class="sxs-lookup"><span data-stu-id="b7677-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="b7677-110">Argumenty indeksatora są umieszczane w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="b7677-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="b7677-111">Indeksatory deklaruje się za pomocą słowa kluczowego `this` jako nazwy właściwości i deklarując argumenty w nawiasach kwadratowych.</span><span class="sxs-lookup"><span data-stu-id="b7677-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="b7677-112">Ta deklaracja będzie zgodna z użyciem przedstawionym w poprzednim akapicie:</span><span class="sxs-lookup"><span data-stu-id="b7677-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="b7677-113">Z tego początkowego przykładu można zobaczyć relacje między składnią właściwości i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="b7677-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="b7677-114">To analogowe przechodzenie przez większość reguł składni indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="b7677-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="b7677-115">Indeksatory mogą mieć wszelkie prawidłowe Modyfikatory dostępu (publiczne, chronione wewnętrznie, chronione, wewnętrzne, prywatne lub prywatne chronione).</span><span class="sxs-lookup"><span data-stu-id="b7677-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="b7677-116">Mogą być zapieczętowane, wirtualne lub abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="b7677-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="b7677-117">Podobnie jak w przypadku właściwości, można określić różne Modyfikatory dostępu dla metod dostępu get i Set w indeksatorze.</span><span class="sxs-lookup"><span data-stu-id="b7677-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="b7677-118">Można również określić indeksatory tylko do odczytu (poprzez pominięcie metody dostępu set) lub indeksatory tylko do zapisu (przez pominięcie metody dostępu get).</span><span class="sxs-lookup"><span data-stu-id="b7677-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="b7677-119">Możesz zastosować niemal wszystkie informacje o pracy z właściwościami indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="b7677-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="b7677-120">Jedynym wyjątkiem od tej reguły są *zaimplementowane właściwości*.</span><span class="sxs-lookup"><span data-stu-id="b7677-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="b7677-121">Kompilator nie zawsze może generować prawidłowy magazyn dla indeksatora.</span><span class="sxs-lookup"><span data-stu-id="b7677-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="b7677-122">Obecność argumentów odwołujących się do elementu w zestawie elementów odróżnia indeksatory od właściwości.</span><span class="sxs-lookup"><span data-stu-id="b7677-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="b7677-123">Można zdefiniować wiele indeksatorów dla typu, tak długo, jak listy argumentów dla każdego indeksatora są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="b7677-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="b7677-124">Zapoznaj się z różnymi scenariuszami, w których możesz użyć co najmniej jednego indeksatora w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="b7677-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span> 

## <a name="scenarios"></a><span data-ttu-id="b7677-125">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="b7677-125">Scenarios</span></span>

<span data-ttu-id="b7677-126">Można zdefiniować *indeksatory* w typie, gdy jego interfejs API modeluje pewne kolekcje, w których zdefiniowano argumenty tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b7677-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="b7677-127">Indeksatory mogą lub nie mogą być mapowane bezpośrednio do typów kolekcji, które są częścią programu .NET Core Framework.</span><span class="sxs-lookup"><span data-stu-id="b7677-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="b7677-128">Typ może mieć inne obowiązki oprócz modelowania kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b7677-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="b7677-129">Indeksatory umożliwiają udostępnienie interfejsu API, który jest zgodny z abstrakcyjnym typem, bez uwidaczniania wewnętrznych informacji o sposobie przechowywania lub obliczania wartości dla tego abstrakcji.</span><span class="sxs-lookup"><span data-stu-id="b7677-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="b7677-130">Zapoznaj się z kilkoma typowymi scenariuszami dotyczącymi używania *indeksatorów*.</span><span class="sxs-lookup"><span data-stu-id="b7677-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="b7677-131">Możesz uzyskać dostęp do [przykładowego folderu dla indeksatorów](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="b7677-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="b7677-132">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b7677-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="b7677-133">Tablice i wektory</span><span class="sxs-lookup"><span data-stu-id="b7677-133">Arrays and Vectors</span></span>

<span data-ttu-id="b7677-134">Jednym z najpopularniejszych scenariuszy tworzenia indeksatorów jest to, że typ modeluje tablicę lub wektor.</span><span class="sxs-lookup"><span data-stu-id="b7677-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="b7677-135">Można utworzyć indeksator do modelowania uporządkowanej listy danych.</span><span class="sxs-lookup"><span data-stu-id="b7677-135">You can create an indexer to model an ordered list of data.</span></span> 

<span data-ttu-id="b7677-136">Zaletą tworzenia własnego indeksatora jest możliwość zdefiniowania magazynu dla tej kolekcji zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="b7677-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="b7677-137">Załóżmy, że Twój typ modeluje dane historyczne, które są zbyt duże do załadowania do pamięci jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="b7677-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="b7677-138">Należy załadować i zwolnić sekcje kolekcji na podstawie użycia.</span><span class="sxs-lookup"><span data-stu-id="b7677-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="b7677-139">W przykładzie poniżej przedstawiono model tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="b7677-139">The example following models this behavior.</span></span> <span data-ttu-id="b7677-140">Raport przedstawia liczbę istniejących punktów danych.</span><span class="sxs-lookup"><span data-stu-id="b7677-140">It reports on how many data points exist.</span></span> <span data-ttu-id="b7677-141">Tworzy strony do przechowywania sekcji danych na żądanie.</span><span class="sxs-lookup"><span data-stu-id="b7677-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="b7677-142">Usuwa strony z pamięci, aby zwolnić miejsce dla stron wymaganych przez nowsze żądania.</span><span class="sxs-lookup"><span data-stu-id="b7677-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="b7677-143">Można postępować zgodnie z idiom projektu, aby modelować dowolne sortowanie kolekcji, w której istnieją dobre powody, aby nie ładować całego zestawu danych do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b7677-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="b7677-144">Należy zauważyć, że Klasa `Page` jest prywatną klasą zagnieżdżoną, która nie jest częścią interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="b7677-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="b7677-145">Te szczegóły są ukryte dla wszystkich użytkowników tej klasy.</span><span class="sxs-lookup"><span data-stu-id="b7677-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="b7677-146">Słowniki</span><span class="sxs-lookup"><span data-stu-id="b7677-146">Dictionaries</span></span>

<span data-ttu-id="b7677-147">Inny typowy scenariusz jest konieczny do modelowania słownika lub mapy.</span><span class="sxs-lookup"><span data-stu-id="b7677-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="b7677-148">Ten scenariusz polega na tym, że typ przechowuje wartości w oparciu o klucz, zazwyczaj klucze tekstowe.</span><span class="sxs-lookup"><span data-stu-id="b7677-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="b7677-149">W tym przykładzie tworzony jest słownik, który mapuje argumenty wiersza polecenia na [wyrażenia lambda](delegates-overview.md) , które zarządzają tymi opcjami.</span><span class="sxs-lookup"><span data-stu-id="b7677-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="b7677-150">Poniższy przykład przedstawia dwie klasy: Klasa `ArgsActions`, która mapuje opcję wiersza polecenia do delegata `Action`, a `ArgsProcessor`, który używa `ArgsActions` do wykonywania każdego `Action`, gdy napotka tę opcję.</span><span class="sxs-lookup"><span data-stu-id="b7677-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="b7677-151">W tym przykładzie kolekcje `ArgsAction` są mapowane blisko źródłowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b7677-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="b7677-152">`get` określa, czy dana opcja została skonfigurowana.</span><span class="sxs-lookup"><span data-stu-id="b7677-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="b7677-153">Jeśli tak, zwraca `Action` skojarzona z tą opcją.</span><span class="sxs-lookup"><span data-stu-id="b7677-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="b7677-154">W przeciwnym razie zwraca `Action`, która nic nie robi.</span><span class="sxs-lookup"><span data-stu-id="b7677-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="b7677-155">Publiczna metoda dostępu nie obejmuje metody dostępu `set`.</span><span class="sxs-lookup"><span data-stu-id="b7677-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="b7677-156">Zamiast tego projekt przy użyciu metody publicznej służącej do ustawiania opcji.</span><span class="sxs-lookup"><span data-stu-id="b7677-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="b7677-157">Mapy wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="b7677-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="b7677-158">Można tworzyć indeksatory używające wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="b7677-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="b7677-159">Ponadto te argumenty nie są ograniczone do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="b7677-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="b7677-160">Przyjrzyjmy się dwóm przykładom.</span><span class="sxs-lookup"><span data-stu-id="b7677-160">Let's look at two examples.</span></span>   

<span data-ttu-id="b7677-161">Pierwszy przykład przedstawia klasę, która generuje wartości dla zestawu Mandelbrot.</span><span class="sxs-lookup"><span data-stu-id="b7677-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="b7677-162">Aby uzyskać więcej informacji na temat matematyki za zestawem, Przeczytaj [ten artykuł](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="b7677-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span> <span data-ttu-id="b7677-163">Indeksator używa dwóch podwaja do definiowania punktu w płaszczyźnie X, Y.</span><span class="sxs-lookup"><span data-stu-id="b7677-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="b7677-164">Metoda dostępu get oblicza liczbę iteracji do momentu, gdy punkt nie zostanie ustalony w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b7677-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="b7677-165">W przypadku osiągnięcia maksymalnej liczby iteracji punkt znajduje się w zestawie i zwracana jest wartość maxIterations klasy.</span><span class="sxs-lookup"><span data-stu-id="b7677-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="b7677-166">(Typowe obrazy wygenerowane przez komputer dla zestawu Mandelbrot definiują kolory dla liczby iteracji wymaganych do określenia, że punkt znajduje się poza zestawem.</span><span class="sxs-lookup"><span data-stu-id="b7677-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="b7677-167">Zestaw Mandelbrot definiuje wartości dla każdej współrzędnej (x, y) dla wartości liczb rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="b7677-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="b7677-168">Definiuje słownik, który może zawierać nieskończoną liczbę wartości.</span><span class="sxs-lookup"><span data-stu-id="b7677-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="b7677-169">W związku z tym nie istnieje magazyn związany z zestawem.</span><span class="sxs-lookup"><span data-stu-id="b7677-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="b7677-170">Zamiast tego Klasa oblicza wartość dla każdego punktu, gdy kod wywołuje metodę dostępu `get`.</span><span class="sxs-lookup"><span data-stu-id="b7677-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="b7677-171">Nie jest używany magazyn bazowy.</span><span class="sxs-lookup"><span data-stu-id="b7677-171">There's no underlying storage used.</span></span>

<span data-ttu-id="b7677-172">Sprawdźmy jedno z ostatniego użycia indeksatorów, gdzie indeksator przyjmuje wiele argumentów różnych typów.</span><span class="sxs-lookup"><span data-stu-id="b7677-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="b7677-173">Weź pod uwagę program, który zarządza danymi temperatury historycznej.</span><span class="sxs-lookup"><span data-stu-id="b7677-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="b7677-174">Ten indeksator używa miasta i daty, aby ustawić lub uzyskać górną i dolną temperaturę dla tej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="b7677-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="b7677-175">Ten przykład tworzy indeksator, który mapuje dane pogodowe na dwa różne argumenty: miasto (reprezentowane przez `string`) i datę (reprezentowane przez `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="b7677-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="b7677-176">Magazyn wewnętrzny używa dwóch `Dictionary` klas do reprezentowania dwuwymiarowego słownika.</span><span class="sxs-lookup"><span data-stu-id="b7677-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="b7677-177">Publiczny interfejs API nie reprezentuje już bazowego magazynu.</span><span class="sxs-lookup"><span data-stu-id="b7677-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="b7677-178">Zamiast tego funkcje językowe indeksatorów umożliwiają utworzenie interfejsu publicznego, który reprezentuje streszczenie, nawet jeśli podstawowy magazyn musi korzystać z różnych podstawowych typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b7677-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="b7677-179">Istnieją dwie części tego kodu, które mogą być nieznane dla niektórych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="b7677-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="b7677-180">Te dwie instrukcje `using`:</span><span class="sxs-lookup"><span data-stu-id="b7677-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="b7677-181">Utwórz *alias* dla konstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b7677-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="b7677-182">Te instrukcje umożliwiają późniejsze użycie bardziej opisowych `DateMeasurements` i nazw `CityDateMeasurements` zamiast ogólnej konstrukcji `Dictionary<DateTime, Measurements>` i `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="b7677-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span> <span data-ttu-id="b7677-183">Ta konstrukcja wymaga używania w pełni kwalifikowanych nazw typów po prawej stronie znaku `=`.</span><span class="sxs-lookup"><span data-stu-id="b7677-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="b7677-184">Druga Technika polega na rozdzieleniu części czasu dowolnego obiektu `DateTime` używanego do indeksowania kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b7677-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="b7677-185">Platforma .NET nie zawiera typu tylko daty.</span><span class="sxs-lookup"><span data-stu-id="b7677-185">.NET doesn't include a date-only type.</span></span>
<span data-ttu-id="b7677-186">Deweloperzy używają typu `DateTime`, ale używają właściwości `Date`, aby upewnić się, że każdy obiekt `DateTime` z tego dnia będzie równy.</span><span class="sxs-lookup"><span data-stu-id="b7677-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="b7677-187">Sumowanie</span><span class="sxs-lookup"><span data-stu-id="b7677-187">Summing Up</span></span>

<span data-ttu-id="b7677-188">Indeksatory należy tworzyć w dowolnym momencie, gdy istnieje element podobny do właściwości w klasie, gdzie ta właściwość reprezentuje nie pojedynczą wartość, ale raczej zbiór wartości, w których każdy indywidualny element jest identyfikowany przez zestaw argumentów.</span><span class="sxs-lookup"><span data-stu-id="b7677-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="b7677-189">Te argumenty mogą jednoznacznie identyfikować, do którego elementu w kolekcji należy się odwoływać.</span><span class="sxs-lookup"><span data-stu-id="b7677-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="b7677-190">Indeksatory zwiększają koncepcję [Właściwości](properties.md), gdzie element członkowski jest traktowany jak element danych spoza klasy, ale taki jak Metoda wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="b7677-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the inside.</span></span> <span data-ttu-id="b7677-191">Indeksatory umożliwiają argumentom znalezienie pojedynczego elementu we właściwości, która reprezentuje zestaw elementów.</span><span class="sxs-lookup"><span data-stu-id="b7677-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
