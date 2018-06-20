---
title: Indeksatory
description: Dowiedz się więcej o języku C# indeksatory i sposobu wdrażania indeksowane właściwości, które są właściwościami odwoływać się przy użyciu co najmniej jeden argument.
ms.date: 06/20/2016
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 012213a4cdf8b70ec919639a082d5700228dde6b
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207498"
---
# <a name="indexers"></a><span data-ttu-id="f06d1-103">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="f06d1-103">Indexers</span></span>

<span data-ttu-id="f06d1-104">*Indeksatory* są podobne do właściwości.</span><span class="sxs-lookup"><span data-stu-id="f06d1-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="f06d1-105">Na wiele sposobów indeksatory kompilacji na te same funkcje języka jako [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="f06d1-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="f06d1-106">Włącz indeksatory *indeksowane* właściwości: właściwości odwoływać się przy użyciu co najmniej jeden argument.</span><span class="sxs-lookup"><span data-stu-id="f06d1-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="f06d1-107">Tych argumentów Podaj indeksu w pewnej kolekcji wartości.</span><span class="sxs-lookup"><span data-stu-id="f06d1-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="f06d1-108">Składnia indeksatora</span><span class="sxs-lookup"><span data-stu-id="f06d1-108">Indexer Syntax</span></span>

<span data-ttu-id="f06d1-109">Indeksator dostępu za pomocą nazwy zmiennej i nawiasy kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="f06d1-109">You access an indexer through a variable name and square brackets .</span></span> <span data-ttu-id="f06d1-110">Możesz umieścić argumenty indeksatora w nawiasie:</span><span class="sxs-lookup"><span data-stu-id="f06d1-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="f06d1-111">Można zadeklarować indeksatorów przy użyciu `this` słowa kluczowego jako nazwy właściwości i typ deklarujący argumenty w nawiasach kwadratowych.</span><span class="sxs-lookup"><span data-stu-id="f06d1-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="f06d1-112">Ta deklaracja spowoduje dopasowanie użycia pokazano powyżej:</span><span class="sxs-lookup"><span data-stu-id="f06d1-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="f06d1-113">W tym przykładzie początkowej można zobaczyć relację pomiędzy składni dla właściwości i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="f06d1-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="f06d1-114">Prowadzi to odpowiednio do większości składni reguł dla indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="f06d1-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="f06d1-115">Indeksatory może mieć modyfikatorów żadnych prawomocny dostęp (publicznych, chronionych wewnętrznych, chronione, wewnętrzne, prywatne lub prywatny chroniony).</span><span class="sxs-lookup"><span data-stu-id="f06d1-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="f06d1-116">Mogą być zapieczętowane, wirtualne lub abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="f06d1-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="f06d1-117">Podobnie jak w przypadku właściwości, można określić modyfikatorów dostępu różnych GET i ustaw accesssors w indeksatora.</span><span class="sxs-lookup"><span data-stu-id="f06d1-117">As with properties, you can specify different access modifiers for the get and set accesssors in an indexer.</span></span>
<span data-ttu-id="f06d1-118">Indeksatory tylko do odczytu (na przykład, pomijając metody dostępu set) lub tylko do zapisu indeksatory mogą określać również (, pomijając metody dostępu get).</span><span class="sxs-lookup"><span data-stu-id="f06d1-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="f06d1-119">Możesz zastosować prawie wszystko, czego możesz dowiedzieć się, Praca z właściwości indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="f06d1-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="f06d1-120">Jedynym wyjątkiem od tej reguły jest *automatycznie implementowane właściwości*.</span><span class="sxs-lookup"><span data-stu-id="f06d1-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="f06d1-121">Kompilator nie może wygenerować zawsze poprawny magazyn dla indeksatora.</span><span class="sxs-lookup"><span data-stu-id="f06d1-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="f06d1-122">Obecność argumentów, aby odwołać się do elementu w zestawie elementów odróżnia indeksatory od właściwości.</span><span class="sxs-lookup"><span data-stu-id="f06d1-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="f06d1-123">Można zdefiniować wiele indeksatorów w typie, tak długo, jak argument wymieniono dla każdego indeksatora jest unikatowy.</span><span class="sxs-lookup"><span data-stu-id="f06d1-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="f06d1-124">Przyjrzyjmy różnych scenariuszy których można użyć co najmniej jeden indeksatorów w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="f06d1-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span> 

## <a name="scenarios"></a><span data-ttu-id="f06d1-125">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="f06d1-125">Scenarios</span></span>

<span data-ttu-id="f06d1-126">Należy zdefiniować *indeksatory* w danego typu, gdy jej interfejsu API modele pewnej kolekcji miejscu należy określić argumenty do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f06d1-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="f06d1-127">Twoje indeksatory mogą lub nie mogą być mapowane bezpośrednio do typów kolekcji, które są częścią programu .NET framework core.</span><span class="sxs-lookup"><span data-stu-id="f06d1-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="f06d1-128">Danego typu może mieć inne obowiązki oprócz modelowania kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f06d1-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="f06d1-129">Indeksatory umożliwiają stosowanie odpowiadającego danego typu abstrakcji bez narażania wewnętrzny szczegóły jak przechowywane lub obliczanej wartości dla tego abstrakcji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="f06d1-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="f06d1-130">Przejdźmy niektóre typowe scenariusze dotyczące korzystania z *indeksatory*.</span><span class="sxs-lookup"><span data-stu-id="f06d1-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="f06d1-131">Dostęp można uzyskać [przykładowy folder dla indeksatorów](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="f06d1-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="f06d1-132">Instrukcje pobrania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="f06d1-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="f06d1-133">Tablice i wektorów</span><span class="sxs-lookup"><span data-stu-id="f06d1-133">Arrays and Vectors</span></span>

<span data-ttu-id="f06d1-134">Jest jednym z najbardziej typowych scenariuszy tworzenia indeksatorów, gdy modele danego typu tablicy lub wektora.</span><span class="sxs-lookup"><span data-stu-id="f06d1-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="f06d1-135">Można utworzyć indeksatora do modelowania uporządkowaną listę danych.</span><span class="sxs-lookup"><span data-stu-id="f06d1-135">You can create an indexer to model an ordered list of data.</span></span> 

<span data-ttu-id="f06d1-136">Zaletą tworzenia własnych indeksatora jest zdefiniować magazynu dla tej kolekcji, w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="f06d1-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="f06d1-137">Wyobraź sobie scenariusz, w którym danego typu modeli danych historycznych, który jest zbyt duży, aby załadować do pamięci na raz.</span><span class="sxs-lookup"><span data-stu-id="f06d1-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="f06d1-138">Musisz ładowanie i zwalnianie sekcje kolekcji na podstawie użycia.</span><span class="sxs-lookup"><span data-stu-id="f06d1-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="f06d1-139">Poniższy przykład modele tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="f06d1-139">The example following models this behavior.</span></span> <span data-ttu-id="f06d1-140">Raporty na liczbę punktów danych istnieje.</span><span class="sxs-lookup"><span data-stu-id="f06d1-140">It reports on how many data points exist.</span></span> <span data-ttu-id="f06d1-141">Tworzy stron do przechowywania części danych na żądanie.</span><span class="sxs-lookup"><span data-stu-id="f06d1-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="f06d1-142">Usuwa stron z pamięci, aby zwolnić miejsce dla strony wymagany przez nowszą żądania.</span><span class="sxs-lookup"><span data-stu-id="f06d1-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="f06d1-143">Idiom tego projektu do modelowania dowolny rodzaj kolekcji można wykonać w przypadku, gdy istnieją powody nie można załadować cały zestaw danych do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f06d1-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="f06d1-144">Zwróć uwagę, że `Page` klasa jest klasą zagnieżdżonych prywatnych nie jest częścią interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="f06d1-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="f06d1-145">Te szczegóły są ukryte przed wszyscy użytkownicy tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f06d1-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="f06d1-146">słowników</span><span class="sxs-lookup"><span data-stu-id="f06d1-146">Dictionaries</span></span>

<span data-ttu-id="f06d1-147">Inny typowy scenariusz polega, gdy trzeba modelu słownika lub mapy.</span><span class="sxs-lookup"><span data-stu-id="f06d1-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="f06d1-148">Ten scenariusz jest w przypadku danego typu przechowuje wartości oparte na kluczu, zwykle klucze tekstu.</span><span class="sxs-lookup"><span data-stu-id="f06d1-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="f06d1-149">W tym przykładzie tworzy słownik mapujący argumenty wiersza polecenia do [wyrażenia lambda](delegates-overview.md) który Zarządzanie tych opcji.</span><span class="sxs-lookup"><span data-stu-id="f06d1-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="f06d1-150">W poniższym przykładzie przedstawiono dwie klasy: `ArgsActions` klasa, która mapuje opcji wiersza polecenia, aby `Action` delegować i `ArgsProcessor` używającą `ArgsActions` do wykonania poszczególnych `Action` po napotkaniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="f06d1-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="f06d1-151">W tym przykładzie `ArgsAction` kolekcji ściśle Mapowana kolekcja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="f06d1-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="f06d1-152">`get` Określa, czy dany opcji został skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="f06d1-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="f06d1-153">Jeśli tak, zwraca `Action` skojarzone z tej opcji.</span><span class="sxs-lookup"><span data-stu-id="f06d1-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="f06d1-154">Jeśli nie, zwraca `Action` nie działają.</span><span class="sxs-lookup"><span data-stu-id="f06d1-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="f06d1-155">Nie ma publicznego akcesora `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="f06d1-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="f06d1-156">Zamiast projektu za pomocą metody publicznej do ustawiania opcji.</span><span class="sxs-lookup"><span data-stu-id="f06d1-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="f06d1-157">Mapy wielowymiarowych</span><span class="sxs-lookup"><span data-stu-id="f06d1-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="f06d1-158">Można utworzyć indeksatory korzystających z wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="f06d1-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="f06d1-159">Ponadto tych argumentów nie są ograniczone do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="f06d1-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="f06d1-160">Oto dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="f06d1-160">Let's look at two examples.</span></span>   

<span data-ttu-id="f06d1-161">W pierwszym przykładzie klasy, które generuje wartości z zestawu Mandelbrot.</span><span class="sxs-lookup"><span data-stu-id="f06d1-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="f06d1-162">Aby uzyskać więcej informacji na matematyce za zestaw odczytu [w tym artykule](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="f06d1-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span> <span data-ttu-id="f06d1-163">Indeksator używa dwóch symulacyjnych, aby zdefiniować punkt w X, Y płaszczyzny.</span><span class="sxs-lookup"><span data-stu-id="f06d1-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="f06d1-164">Metoda dostępu get oblicza liczba iteracji, dopóki nie stwierdzono, że punkt nie może być w zestawie.</span><span class="sxs-lookup"><span data-stu-id="f06d1-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="f06d1-165">Jeśli zostanie osiągnięta maksymalna liczba iteracji, punkt znajduje się w zestawie, i jest zwracana wartość maxIterations tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f06d1-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="f06d1-166">(Obrazy generowane komputera popularized zestawu Mandelbrot zdefiniowanie kolorów liczba iteracji, które są niezbędne do określenia, czy punkt znajduje się poza zestaw.</span><span class="sxs-lookup"><span data-stu-id="f06d1-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="f06d1-167">Zestaw Mandelbrot definiuje wartości w każdym folderu (x, y) koordynować rzeczywiste wartości liczbowe.</span><span class="sxs-lookup"><span data-stu-id="f06d1-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="f06d1-168">Definiuje słownik, który może zawierać nieograniczoną liczbę wartości.</span><span class="sxs-lookup"><span data-stu-id="f06d1-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="f06d1-169">Dlatego nie jest Brak magazynu poza zestaw.</span><span class="sxs-lookup"><span data-stu-id="f06d1-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="f06d1-170">Zamiast tego należy ta klasa oblicza wartość dla każdego punktu, gdy kod wywołuje `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="f06d1-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="f06d1-171">Nie ma żadnych powiązany magazyn używany.</span><span class="sxs-lookup"><span data-stu-id="f06d1-171">There's no underlying storage used.</span></span>

<span data-ttu-id="f06d1-172">Przeanalizujmy jedno ostatniego Użycie indeksatorów, gdzie indeksatora przyjmuje wiele argumentów o różnych typach.</span><span class="sxs-lookup"><span data-stu-id="f06d1-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="f06d1-173">Należy wziąć pod uwagę program, który zarządza temperatury historycznych danych.</span><span class="sxs-lookup"><span data-stu-id="f06d1-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="f06d1-174">Ten indeksator używa miejscowość i Data ustawić lub pobrać temperatury wysoki i niski dla tej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="f06d1-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="f06d1-175">W tym przykładzie jest tworzony indeksatorze, który mapuje dane o pogodzie w dwóch różnych argumentów: Miejscowość (reprezentowane przez `string`) i datę (reprezentowane przez `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="f06d1-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="f06d1-176">Wewnętrzny magazyn korzysta z dwóch `Dictionary` klasy do reprezentowania dwuwymiarowa słownika.</span><span class="sxs-lookup"><span data-stu-id="f06d1-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="f06d1-177">Publiczny interfejs API reprezentuje nie jest już powiązany magazyn.</span><span class="sxs-lookup"><span data-stu-id="f06d1-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="f06d1-178">Zamiast funkcji języka indeksatory umożliwia utworzenie publiczny interfejs, który reprezentuje użytkownika abstrakcji, mimo że powiązany magazyn muszą używać różnych podstawowych typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f06d1-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="f06d1-179">Istnieją dwie części tego kodu, które mogą być nieznane niektórzy deweloperzy.</span><span class="sxs-lookup"><span data-stu-id="f06d1-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="f06d1-180">Te dwa `using` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="f06d1-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="f06d1-181">Utwórz *alias* do skonstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="f06d1-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="f06d1-182">Te instrukcje Włącz kod później używany bardziej opisowe `DateMeasurements` i `CityDateMeasurements` nazw zamiast ogólnego konstrukcji `Dictionary<DateTime, Measurements>` i `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="f06d1-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span> <span data-ttu-id="f06d1-183">Ta konstrukcja wymaga użycia pełni kwalifikowane nazwy typów w prawej części `=` logowania.</span><span class="sxs-lookup"><span data-stu-id="f06d1-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="f06d1-184">Drugi technika jest paska Wyłącz fragmenty czasu dowolnego `DateTime` obiekt używany do indeksu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f06d1-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="f06d1-185">.NET framework nie obejmuje jedynym typem daty.</span><span class="sxs-lookup"><span data-stu-id="f06d1-185">The .NET framework does not include a Date only type.</span></span>
<span data-ttu-id="f06d1-186">Deweloperzy za pomocą `DateTime` typu, ale użyj `Date` właściwość, aby upewnić się, że wszelkie `DateTime` obiektów z danego dnia są takie same.</span><span class="sxs-lookup"><span data-stu-id="f06d1-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="f06d1-187">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="f06d1-187">Summing Up</span></span>

<span data-ttu-id="f06d1-188">Należy utworzyć indeksatorów w dowolnym momencie ma elementu właściwości w klasie, w których tej właściwości reprezentuje pojedynczą wartość, ale raczej kolekcję wartości, w którym każdego elementu jest identyfikowany przez zestaw argumentów.</span><span class="sxs-lookup"><span data-stu-id="f06d1-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="f06d1-189">Tych argumentów można jednoznacznie zidentyfikować, który element w kolekcji ma być utworzone odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f06d1-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="f06d1-190">Indeksatory rozszerzenie pojęcia [właściwości](properties.md), której członkiem jest traktowany jak elementu danych z poza klasą, ale jak metody na stronie.</span><span class="sxs-lookup"><span data-stu-id="f06d1-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the side.</span></span> <span data-ttu-id="f06d1-191">Indeksatory zezwalają na argumenty można znaleźć pojedynczego elementu we właściwości, która reprezentuje zestaw elementów.</span><span class="sxs-lookup"><span data-stu-id="f06d1-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
