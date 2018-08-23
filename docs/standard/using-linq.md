---
title: LINQ (Language Integrated Query)
description: Dowiedz się, jak LINQ zapewnia możliwości zapytań w poziomie języka i interfejs API języka C# i VB jako sposób pisania kodu ekspresyjna, deklaratywnego.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 4e6e361666b6b6ae36b7d4bf02af55a379c8e16e
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752134"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="7b3b2-103">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="7b3b2-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="7b3b2-104">Co to?</span><span class="sxs-lookup"><span data-stu-id="7b3b2-104">What is it?</span></span>

<span data-ttu-id="7b3b2-105">LINQ zapewnia możliwości zapytań w poziomie języka i [funkcja wyższego rzędu](https://en.wikipedia.org/wiki/Higher-order_function) interfejsu API języka C# i VB jako sposób pisania kodu ekspresyjna, deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="7b3b2-106">Składnia poziomu języka zapytań:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-106">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

<span data-ttu-id="7b3b2-107">Przy użyciu tego samego przykładu `IEnumerable<T>` interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a><span data-ttu-id="7b3b2-108">LINQ to Expressive</span><span class="sxs-lookup"><span data-stu-id="7b3b2-108">LINQ is Expressive</span></span>

<span data-ttu-id="7b3b2-109">Wyobraź sobie listę zwierząt domowych, ale chcesz przekonwertować ją do słownika, w którym możesz uzyskać dostęp pet bezpośrednio przez jego `RFID` wartość.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="7b3b2-110">Tradycyjne kodu imperatywnego:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-110">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

<span data-ttu-id="7b3b2-111">Za kod jest nie do tworzenia nowego `Dictionary<int, Pet>` i dodać do niego za pomocą pętli, to można przekonwertować istniejącej listy do słownika!</span><span class="sxs-lookup"><span data-stu-id="7b3b2-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="7b3b2-112">LINQ zachowuje zamiar, dlatego nie ma kodu imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="7b3b2-113">Równoważne wyrażenie LINQ:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

<span data-ttu-id="7b3b2-114">Kod za pomocą LINQ jest przydatne, ponieważ evens szans między intencji i kodu, podczas wnioskowania programistą.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="7b3b2-115">Podwyższenie innego jest zwięzłości kodu.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-115">Another bonus is code brevity.</span></span> <span data-ttu-id="7b3b2-116">Wyobraź sobie, zmniejszanie dużych fragmentów kodu poprzez 1/3 jako gotowe powyżej.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="7b3b2-117">Całkiem osiąganie słodkiego transakcji, odpowiednie?</span><span class="sxs-lookup"><span data-stu-id="7b3b2-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="7b3b2-118">Dostawcy LINQ uprościć dostęp do danych</span><span class="sxs-lookup"><span data-stu-id="7b3b2-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="7b3b2-119">Znaczne fragmenty oprogramowania na zewnątrz wszystko, czego dotyczy tego radzenia sobie z danymi z określonego źródła (baz danych, JSON, XML itp.).</span><span class="sxs-lookup"><span data-stu-id="7b3b2-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="7b3b2-120">Często ten proces obejmuje uczenie nowego interfejsu API dla każdego źródła danych, które mogą być irytujące.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="7b3b2-121">LINQ upraszcza to abstrakcyjność wspólne elementy dostęp do danych w składni zapytań, który wygląda tak samo niezależnie od tego źródła danych wybierz.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="7b3b2-122">Rozważ następujące opcje: znajdowanie wszystkich elementów XML z wartością konkretnego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

<span data-ttu-id="7b3b2-123">Pisanie kodu w celu ręcznego przechodzenia dokumentu XML, aby wykonać to zadanie będzie znacznie trudniejsze.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="7b3b2-124">Wchodzenie w interakcje z danymi XML nie jest jedyną czynnością, którą można zrobić za pomocą dostawców LINQ.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="7b3b2-125">[LINQ do SQL](../../docs/framework/data/adonet/sql/linq/index.md) jest dość bez kości obiektowo-relacyjny mapowania (ORM) dla bazy danych MSSQL.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="7b3b2-126">[JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) Biblioteka zapewnia wydajne przechodzenie dokumentów JSON za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="7b3b2-127">Ponadto, jeśli nie istnieje biblioteki, która obsługuje, czego potrzebujesz, możesz również [pisania własnego dostawcy LINQ](https://msdn.microsoft.com/library/Bb546158.aspx)!</span><span class="sxs-lookup"><span data-stu-id="7b3b2-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://msdn.microsoft.com/library/Bb546158.aspx)!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="7b3b2-128">Dlaczego warto używać składni zapytań?</span><span class="sxs-lookup"><span data-stu-id="7b3b2-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="7b3b2-129">Jest to pytanie, które często jest dostarczany w górę.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-129">This is a question which often comes up.</span></span> <span data-ttu-id="7b3b2-130">Gdy wszystkie ten,</span><span class="sxs-lookup"><span data-stu-id="7b3b2-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

<span data-ttu-id="7b3b2-131">jest znacznie bardziej zwięzłe niż to:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-131">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

<span data-ttu-id="7b3b2-132">Składnia interfejsu API nie jest po prostu bardziej zwarty sposób przeprowadzenia składnia zapytania?</span><span class="sxs-lookup"><span data-stu-id="7b3b2-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="7b3b2-133">Nie.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-133">No.</span></span> <span data-ttu-id="7b3b2-134">Składnia zapytań umożliwia użycie **umożliwiają** klauzula, która pozwala na wprowadzenie i powiązać zmiennej w zakresie wyrażenie, używając go w kolejnych częściach wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-134">The query syntax allows for the use the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="7b3b2-135">Odtwarzanie tego samego kodu przy użyciu składni interfejsu API może odbywać się, ale prawdopodobnie doprowadzi do kodu, który jest trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="7b3b2-136">Tak wymaga to pytanie, **należy po prostu użyć składni zapytania?**</span><span class="sxs-lookup"><span data-stu-id="7b3b2-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="7b3b2-137">Odpowiedź na to pytanie jest **tak** Jeśli...</span><span class="sxs-lookup"><span data-stu-id="7b3b2-137">The answer to this question is **yes** if...</span></span>

*   <span data-ttu-id="7b3b2-138">Istniejącej bazy kodu już używa składni zapytania</span><span class="sxs-lookup"><span data-stu-id="7b3b2-138">Your existing codebase already uses the query syntax</span></span>
*   <span data-ttu-id="7b3b2-139">Należy do zakresu zmiennych w ciągu zapytania z powodu złożoności</span><span class="sxs-lookup"><span data-stu-id="7b3b2-139">You need to scope variables within your queries due to complexity</span></span>
*   <span data-ttu-id="7b3b2-140">Preferuj składnia zapytania i jej nie będzie niekorzystnie wpłynąć na bazie kodu</span><span class="sxs-lookup"><span data-stu-id="7b3b2-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="7b3b2-141">Odpowiedź na to pytanie jest **nie** Jeśli...</span><span class="sxs-lookup"><span data-stu-id="7b3b2-141">The answer to this question is **no** if...</span></span>

*   <span data-ttu-id="7b3b2-142">Istniejącej bazy kodu już używa składni interfejsu API</span><span class="sxs-lookup"><span data-stu-id="7b3b2-142">Your existing codebase already uses the API syntax</span></span>
*   <span data-ttu-id="7b3b2-143">Użytkownik nie ma potrzeby do zakresu zmiennych w ciągu zapytania</span><span class="sxs-lookup"><span data-stu-id="7b3b2-143">You have no need to scope variables within your queries</span></span>
*   <span data-ttu-id="7b3b2-144">Preferuj składni interfejsu API i jego nie będzie niekorzystnie wpłynąć na bazie kodu</span><span class="sxs-lookup"><span data-stu-id="7b3b2-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="7b3b2-145">Podstawowe przykłady</span><span class="sxs-lookup"><span data-stu-id="7b3b2-145">Essential Samples</span></span>

<span data-ttu-id="7b3b2-146">Aby naprawdę pełną listę przykładów LINQ, odwiedź stronę [101 przykładów LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span><span class="sxs-lookup"><span data-stu-id="7b3b2-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="7b3b2-147">Poniżej przedstawiono szybki pokaz niektórych podstawowych rodzajów LINQ.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="7b3b2-148">To jest w żaden sposób nie wszechstronne LINQ zapewnia znacznie więcej funkcji niż co jest pokazywane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

*   <span data-ttu-id="7b3b2-149">Masła i chleb - `Where`, `Select`, i `Aggregate`:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

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

*   <span data-ttu-id="7b3b2-150">Spłaszczanie listę list:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   <span data-ttu-id="7b3b2-151">Związek między dwoma zestawami (przy użyciu niestandardowych komparator):</span><span class="sxs-lookup"><span data-stu-id="7b3b2-151">Union between two sets (with custom comparator):</span></span>

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
        return d.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

*   <span data-ttu-id="7b3b2-152">Część wspólną między dwoma zestawami:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-152">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   <span data-ttu-id="7b3b2-153">Określanie kolejności:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-153">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   <span data-ttu-id="7b3b2-154">Na koniec bardziej zaawansowany przykład: Określanie, czy wartości właściwości z dwóch wystąpień tego samego typu są równe (Borrowed i zmodyfikowane od [ten wpis w witrynie StackOverflow](http://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="7b3b2-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](http://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self == null || to == null)
    {
        return self == to;
    }
    
    // Selects the properties which have unequal values into a sequence of those properties.
    var unequalProperties = from property in typeof(T).GetProperties(BindingFlags.Public | BindingFlags.Instance)
                            where !ignore.Contains(property.Name)
                            let selfValue = property.GetValue(self, null)
                            let toValue = property.GetValue(to, null)
                            where !Equals(selfValue, toValue)
                            select property;
    return !unequalProperties.Any();
}
```

## <a name="plinq"></a><span data-ttu-id="7b3b2-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="7b3b2-155">PLINQ</span></span>

<span data-ttu-id="7b3b2-156">Program PLINQ lub równoległe LINQ jest aparatem wykonywania równoległego wyrażenia LINQ.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="7b3b2-157">Innymi słowy regularne wyrażenia LINQ może być przypadku przetwarzane równolegle w dowolnej liczbie wątków.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-157">In other words, a regular LINQ expressions can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="7b3b2-158">Jest to realizowane poprzez wywołanie `AsParallel()` przed wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="7b3b2-159">Rozważ następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-159">Consider the following:</span></span>

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

<span data-ttu-id="7b3b2-160">Ten kod będzie partycji `facebookUsers` na wątki systemowe zgodnie z potrzebami, sumują łączna liczba polubień na każdy wątek w sposób równoległy, Suma wyników obliczone przez każdego wątku i projektu wynik na ciąg dobre rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="7b3b2-161">W postaci diagramu:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-161">In diagram form:</span></span>

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="7b3b2-163">Równoległego zadania zależne od Procesora CPU, które mogą być łatwo wyrażone za pomocą LINQ (innymi słowy, czystej funkcji i mieć żadnych efektów ubocznych) są doskonałym kandydatem do PLINQ.</span><span class="sxs-lookup"><span data-stu-id="7b3b2-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="7b3b2-164">Dla zadań, które _czy_ ma efekt uboczny, należy rozważyć użycie [Biblioteka zadań równoległych](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="7b3b2-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="7b3b2-165">Dalsze zasoby:</span><span class="sxs-lookup"><span data-stu-id="7b3b2-165">Further Resources:</span></span>

*   [<span data-ttu-id="7b3b2-166">101 przykładów LINQ</span><span class="sxs-lookup"><span data-stu-id="7b3b2-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   <span data-ttu-id="7b3b2-167">[Linqpad](https://www.linqpad.net/), Plac zabaw dla środowiska i wykonywanie zapytań w bazie danych aparatu dla języków C# /F #/VB</span><span class="sxs-lookup"><span data-stu-id="7b3b2-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
*   <span data-ttu-id="7b3b2-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), e-book, prezentującą implementacji LINQ do obiektów</span><span class="sxs-lookup"><span data-stu-id="7b3b2-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
