---
title: LINQ (zapytania zintegrowane Language)
description: Dowiedz się, jak LINQ udostępnia interfejsów API i możliwości podczas badania poziom języka C# i VB jako sposobu pisania kodu obszerne, deklaratywne.
keywords: .NET, .NET Core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5ce6819abee90ceccc52a79f8bda794f2fd345fb
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="c609c-104">LINQ (zapytania zintegrowane Language)</span><span class="sxs-lookup"><span data-stu-id="c609c-104">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="c609c-105">Co to?</span><span class="sxs-lookup"><span data-stu-id="c609c-105">What is it?</span></span>

<span data-ttu-id="c609c-106">LINQ zapewnia możliwości podczas badania poziom języka i [funkcja wyższego rzędu](https://en.wikipedia.org/wiki/Higher-order_function) interfejsu API języka C# i VB jako sposobu pisania kodu obszerne, deklaratywne.</span><span class="sxs-lookup"><span data-stu-id="c609c-106">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="c609c-107">Składnia zapytania poziom języka:</span><span class="sxs-lookup"><span data-stu-id="c609c-107">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

<span data-ttu-id="c609c-108">Przy użyciu tego samego przykład `IEnumerable<T>` interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="c609c-108">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a><span data-ttu-id="c609c-109">LINQ jest Expressive</span><span class="sxs-lookup"><span data-stu-id="c609c-109">LINQ is Expressive</span></span>

<span data-ttu-id="c609c-110">Wyobraź sobie listę zwierząt domowych, ale chcesz przekształcać je do słownika, w której będzie można uzyskać dostęp pet bezpośrednio przez jego `RFID` wartość.</span><span class="sxs-lookup"><span data-stu-id="c609c-110">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="c609c-111">Tradycyjny imperatywnych kodu:</span><span class="sxs-lookup"><span data-stu-id="c609c-111">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

<span data-ttu-id="c609c-112">Za kod jest nie, aby utworzyć nową `Dictionary<int, Pet>` i Dodaj do niej przy użyciu pętli, to można przekonwertować istniejącej listy do słownika!</span><span class="sxs-lookup"><span data-stu-id="c609c-112">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="c609c-113">LINQ zachowuje zamiar, natomiast nie jest konieczne kodu.</span><span class="sxs-lookup"><span data-stu-id="c609c-113">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="c609c-114">Odpowiednik wyrażenia LINQ:</span><span class="sxs-lookup"><span data-stu-id="c609c-114">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

<span data-ttu-id="c609c-115">Kod za pomocą LINQ jest przydatna, ponieważ jego evens pola gry między celem i kodu podczas wnioskowania dla programisty.</span><span class="sxs-lookup"><span data-stu-id="c609c-115">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="c609c-116">Podwyższenie innego jest skrócenia kodu.</span><span class="sxs-lookup"><span data-stu-id="c609c-116">Another bonus is code brevity.</span></span> <span data-ttu-id="c609c-117">Wyobraź sobie zmniejszanie dużych części codebase poprzez 1/3, jak wykonać powyżej.</span><span class="sxs-lookup"><span data-stu-id="c609c-117">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="c609c-118">Funkcja pretty słodkich transakcji, prawy?</span><span class="sxs-lookup"><span data-stu-id="c609c-118">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="c609c-119">Dostawcy LINQ uprościć dostęp do danych</span><span class="sxs-lookup"><span data-stu-id="c609c-119">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="c609c-120">Znaczące fragmentu oprogramowania limit wszystko, co dotyczy tego postępowania z danymi z określonego źródła (baz danych, JSON, XML itp.).</span><span class="sxs-lookup"><span data-stu-id="c609c-120">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="c609c-121">Często ten proces obejmuje uczenie nowy interfejs API dla każdego źródła danych, które mogą być irytujące.</span><span class="sxs-lookup"><span data-stu-id="c609c-121">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="c609c-122">LINQ ułatwia to abstrakcyjność wspólne elementy dostępu do danych w składni zapytania, który jest taki sam, niezależnie od tego źródła danych, możesz wybrać.</span><span class="sxs-lookup"><span data-stu-id="c609c-122">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="c609c-123">Rozważ następujące opcje: znajdowanie wszystkich elementów XML z wartością określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="c609c-123">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

<span data-ttu-id="c609c-124">Pisanie kodu ręcznie przechodzenia dokument XML, aby wykonać to zadanie będzie znacznie trudniejsze.</span><span class="sxs-lookup"><span data-stu-id="c609c-124">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="c609c-125">Interakcja z XML nie jest jedyną operacją, której można zrobić za pomocą dostawcy LINQ.</span><span class="sxs-lookup"><span data-stu-id="c609c-125">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="c609c-126">[LINQ do SQL](../../docs/framework/data/adonet/sql/linq/index.md) jest dość bez systemu operacyjnego kości obiektów relacyjnych mapowania (ORM) dla bazy danych MSSQL.</span><span class="sxs-lookup"><span data-stu-id="c609c-126">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="c609c-127">[JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) Biblioteka zapewnia wydajne przechodzenie dokumentu JSON za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="c609c-127">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="c609c-128">Ponadto, jeśli nie ma bibliotekę, która obsługuje, co jest potrzebne, można również [zapisać własnego dostawcę LINQ](https://msdn.microsoft.com/library/Bb546158.aspx)!</span><span class="sxs-lookup"><span data-stu-id="c609c-128">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://msdn.microsoft.com/library/Bb546158.aspx)!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="c609c-129">Dlaczego warto używać składni zapytania?</span><span class="sxs-lookup"><span data-stu-id="c609c-129">Why Use the Query Syntax?</span></span>

<span data-ttu-id="c609c-130">Jest to pytanie, które często pojawia się.</span><span class="sxs-lookup"><span data-stu-id="c609c-130">This is a question which often comes up.</span></span> <span data-ttu-id="c609c-131">Po wszystkich, ten,</span><span class="sxs-lookup"><span data-stu-id="c609c-131">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

<span data-ttu-id="c609c-132">jest znacznie bardziej zwięzłe niż to:</span><span class="sxs-lookup"><span data-stu-id="c609c-132">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

<span data-ttu-id="c609c-133">Składnia interfejsu API nie jest tylko bardziej zwięzły sposób na czy składnia zapytania?</span><span class="sxs-lookup"><span data-stu-id="c609c-133">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="c609c-134">Nie.</span><span class="sxs-lookup"><span data-stu-id="c609c-134">No.</span></span> <span data-ttu-id="c609c-135">Składnia zapytania umożliwia wykorzystanie **let** klauzuli, dzięki czemu można wprowadzić i powiązać zmiennej w zakresie wyrażenie, używając w kolejnej części wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c609c-135">The query syntax allows for the use the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="c609c-136">Odtwarzanie tego samego kodu przy użyciu składni interfejsu API jest możliwe, ale najprawdopodobniej doprowadzi do kodu, który jest trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="c609c-136">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="c609c-137">Dlatego begs to pytanie, **możesz po prostu użyj składni zapytania?**</span><span class="sxs-lookup"><span data-stu-id="c609c-137">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="c609c-138">Odpowiedzi na to pytanie jest **tak** Jeśli...</span><span class="sxs-lookup"><span data-stu-id="c609c-138">The answer to this question is **yes** if...</span></span>

*   <span data-ttu-id="c609c-139">Istniejące ścieżki bazowej kodu już używa składni zapytania</span><span class="sxs-lookup"><span data-stu-id="c609c-139">Your existing codebase already uses the query syntax</span></span>
*   <span data-ttu-id="c609c-140">W ramach zapytania z powodu złożoności konieczne zmiennych o zasięgu</span><span class="sxs-lookup"><span data-stu-id="c609c-140">You need to scope variables within your queries due to complexity</span></span>
*   <span data-ttu-id="c609c-141">Preferowane jest składnia zapytania i go nie niekorzystnie wpłynąć na baza kodu</span><span class="sxs-lookup"><span data-stu-id="c609c-141">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="c609c-142">Odpowiedzi na to pytanie jest **nie** Jeśli...</span><span class="sxs-lookup"><span data-stu-id="c609c-142">The answer to this question is **no** if...</span></span>

*   <span data-ttu-id="c609c-143">Istniejące ścieżki bazowej kodu już używa składni interfejsu API</span><span class="sxs-lookup"><span data-stu-id="c609c-143">Your existing codebase already uses the API syntax</span></span>
*   <span data-ttu-id="c609c-144">Użytkownik nie ma potrzeby do zmiennych o zasięgu w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="c609c-144">You have no need to scope variables within your queries</span></span>
*   <span data-ttu-id="c609c-145">Preferowane jest składnia interfejsu API i go nie niekorzystnie wpłynąć na baza kodu</span><span class="sxs-lookup"><span data-stu-id="c609c-145">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="c609c-146">Przykłady podstawowych</span><span class="sxs-lookup"><span data-stu-id="c609c-146">Essential Samples</span></span>

<span data-ttu-id="c609c-147">Naprawdę kompleksowe przykłady interfejsów LINQ, można znaleźć [101 przykłady interfejsów LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span><span class="sxs-lookup"><span data-stu-id="c609c-147">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="c609c-148">Poniżej przedstawiono szybki pokaz niektórych podstawowych części LINQ.</span><span class="sxs-lookup"><span data-stu-id="c609c-148">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="c609c-149">Jest to w żaden sposób kompleksowe, jak LINQ udostępnia znacznie więcej funkcji niż co to jest pokazywane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="c609c-149">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

*   <span data-ttu-id="c609c-150">Masła i chleb - `Where`, `Select`, i `Aggregate`:</span><span class="sxs-lookup"><span data-stu-id="c609c-150">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

*   <span data-ttu-id="c609c-151">Spłaszczanie listę list:</span><span class="sxs-lookup"><span data-stu-id="c609c-151">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   <span data-ttu-id="c609c-152">Związek między dwoma zestawami (za pomocą niestandardowych komparatora):</span><span class="sxs-lookup"><span data-stu-id="c609c-152">Union between two sets (with custom comparator):</span></span>

```csharp
public class DogHairLengthComparer : IEqualityComparer<Dog>
{
    public bool Equals(Dog a, Dog b)
    {
        if (a == null && b == null)
        {
            return true;
        }
        else if ((a == null && b != null) ||
                 (a != null && b == null))
        {
            return false;
        }
        else
        {
            return a.HairLengthType == b.HairLengthType;
        }
    }

    public int GetHashCode(Dog d)
    {
        // default hashcode is enough here, as these are simple objects.
        return b.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

*   <span data-ttu-id="c609c-153">Część wspólną między dwoma zestawami:</span><span class="sxs-lookup"><span data-stu-id="c609c-153">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   <span data-ttu-id="c609c-154">Kolejność:</span><span class="sxs-lookup"><span data-stu-id="c609c-154">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   <span data-ttu-id="c609c-155">Na koniec bardziej zaawansowane próbki: Określanie, czy wartości właściwości dwa wystąpienia tego samego typu są takie same (Borrowed i zmodyfikowanych z [tego wpisu StackOverflow](http://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="c609c-155">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](http://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self != null && to != null)
    {
        var type = typeof(T);
        var ignoreList = new List<string>(ignore);

        // Selects the properties which have unequal values into a sequence of those properties.
        var unequalProperties = from pi in type.GetProperties(BindingFlags.Public | BindingFlags.Instance)
                                where !ignoreList.Contains(pi.Name)
                                let selfValue = type.GetProperty(pi.Name).GetValue(self, null)
                                let toValue = type.GetProperty(pi.Name).GetValue(to, null)
                                where selfValue != toValue && (selfValue == null || !selfValue.Equals(toValue))
                                select new { Prop = pi.Name, selfValue, toValue };
        return !unequalProperties.Any();
    }

    return self == to;
}
```

## <a name="plinq"></a><span data-ttu-id="c609c-156">PLINQ</span><span class="sxs-lookup"><span data-stu-id="c609c-156">PLINQ</span></span>

<span data-ttu-id="c609c-157">PLINQ lub równoległe LINQ jest aparatem przetwarzania równoległego wyrażenia LINQ.</span><span class="sxs-lookup"><span data-stu-id="c609c-157">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="c609c-158">Innymi słowy regularne wyrażenia LINQ może być trivially zarządzana z przetwarzaniem na dowolną liczbę wątków.</span><span class="sxs-lookup"><span data-stu-id="c609c-158">In other words, a regular LINQ expressions can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="c609c-159">Jest to realizowane za pośrednictwem wywołania `AsParallel()` przed wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="c609c-159">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="c609c-160">Rozważ następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="c609c-160">Consider the following:</span></span>

```csharp
public static string GetAllFacebookUserLikesMessage(IEnumerable<FacebookUser> facebookUsers)
{
    var seed = default(UInt64);

    Func<UInt64, UInt64, UInt64> threadAccumulator = (t1, t2) => t1 + t2;
    Func<UInt64, UInt64, UInt64> threadResultAccumulator = (t1, t2) => t1 + t2;
    Func<Uint64, string> resultSelector = total => $"Facebook has {total} likes!";

    return facebookUsers.AsParallel()
                        .Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector);
}
```

<span data-ttu-id="c609c-161">Ten kod będzie partycji `facebookUsers` przez wątki systemowe w razie potrzeby podsumowania całkowita podobne w każdym wątku równolegle, Suma wyników obliczone przez każdy wątek i projektu na ciąg nieuprzywilejowany tego wyniku.</span><span class="sxs-lookup"><span data-stu-id="c609c-161">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="c609c-162">W postaci diagramu:</span><span class="sxs-lookup"><span data-stu-id="c609c-162">In diagram form:</span></span>

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="c609c-164">Działania równoległego zadania procesora, które można łatwo wyrazić za pomocą LINQ (innymi słowy, są czystych funkcji i nie skutków po stronie) jest doskonałym kandydatem do PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c609c-164">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="c609c-165">Dla zadania, które _czy_ ma skutków ubocznych, należy rozważyć użycie [Biblioteka zadań równoległych](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="c609c-165">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="c609c-166">Dodatkowe zasoby:</span><span class="sxs-lookup"><span data-stu-id="c609c-166">Further Resources:</span></span>

*   [<span data-ttu-id="c609c-167">101 przykłady interfejsów LINQ</span><span class="sxs-lookup"><span data-stu-id="c609c-167">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   <span data-ttu-id="c609c-168">[Linqpad](https://www.linqpad.net/), Plac zabaw dla środowiska i zapytań bazy danych aparatu dla C# / f # / VB.</span><span class="sxs-lookup"><span data-stu-id="c609c-168">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
*   <span data-ttu-id="c609c-169">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), książkę elektroniczną do uczenia implementowania LINQ do obiektów</span><span class="sxs-lookup"><span data-stu-id="c609c-169">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
