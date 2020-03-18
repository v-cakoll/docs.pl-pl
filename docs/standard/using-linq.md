---
title: LINQ (zapytanie zintegrowane językowe)
description: Dowiedz się, jak LINQ zapewnia możliwości wykonywania zapytań na poziomie języka i interfejsu API do języka C# i Visual Basic jako sposób pisania wyraziste, deklaratywne kodu.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: eafd8f78c3d8de1ba064021111f869571d5a570f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160329"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="1dc16-103">LINQ (zapytanie zintegrowane językowe)</span><span class="sxs-lookup"><span data-stu-id="1dc16-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="1dc16-104">co to jest?</span><span class="sxs-lookup"><span data-stu-id="1dc16-104">What is it?</span></span>

<span data-ttu-id="1dc16-105">LINQ zapewnia możliwości wykonywania zapytań na poziomie języka i interfejs API [funkcji wyższego rzędu](https://en.wikipedia.org/wiki/Higher-order_function) do języka C# i Visual Basic jako sposób pisania wyrazistego, deklaratywnego kodu.</span><span class="sxs-lookup"><span data-stu-id="1dc16-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="1dc16-106">Składnia kwerend na poziomie języka:</span><span class="sxs-lookup"><span data-stu-id="1dc16-106">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

```vb
Dim linqExperts = From p in programmers
                  Where p.IsNewToLINQ
                  Select New LINQExpert(p)
```

<span data-ttu-id="1dc16-107">Ten sam `IEnumerable<T>` przykład przy użyciu interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="1dc16-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="1dc16-108">LINQ jest wyrazisty</span><span class="sxs-lookup"><span data-stu-id="1dc16-108">LINQ is Expressive</span></span>

<span data-ttu-id="1dc16-109">Wyobraź sobie, że masz listę zwierząt domowych, ale chcesz przekształcić go w `RFID` słownik, w którym możesz uzyskać dostęp do zwierzaka bezpośrednio według jego wartości.</span><span class="sxs-lookup"><span data-stu-id="1dc16-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="1dc16-110">Tradycyjny kod imperatywu:</span><span class="sxs-lookup"><span data-stu-id="1dc16-110">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

```vb
Dim petLookup = New Dictionary(Of Integer, Pet)()

For Each pet in pets
    petLookup.Add(pet.RFID, pet)
Next
```

<span data-ttu-id="1dc16-111">Intencją kodu nie jest tworzenie `Dictionary<int, Pet>` nowego i dodawanie do niego za pośrednictwem pętli, jest konwersja istniejącej listy do słownika!</span><span class="sxs-lookup"><span data-stu-id="1dc16-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="1dc16-112">LINQ zachowuje intencji, podczas gdy kod imperatywnie nie.</span><span class="sxs-lookup"><span data-stu-id="1dc16-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="1dc16-113">Równoważne wyrażenie LINQ:</span><span class="sxs-lookup"><span data-stu-id="1dc16-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="1dc16-114">Kod przy użyciu LINQ jest cenne, ponieważ wyrównuje pole gry między intencji i kodu podczas rozumowania jako programista.</span><span class="sxs-lookup"><span data-stu-id="1dc16-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="1dc16-115">Kolejnym bonusem jest zwięzłość kodu.</span><span class="sxs-lookup"><span data-stu-id="1dc16-115">Another bonus is code brevity.</span></span> <span data-ttu-id="1dc16-116">Wyobraź sobie zmniejszenie dużych części bazy kodu o 1/3, jak to się robi powyżej.</span><span class="sxs-lookup"><span data-stu-id="1dc16-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="1dc16-117">Całkiem słodka oferta, prawda?</span><span class="sxs-lookup"><span data-stu-id="1dc16-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="1dc16-118">Dostawcy LINQ upraszczają dostęp do danych</span><span class="sxs-lookup"><span data-stu-id="1dc16-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="1dc16-119">Dla znacznego fragmentu oprogramowania w środowisku naturalnym, wszystko kręci się wokół radzenia sobie z danymi z niektórych źródeł (bazy danych, JSON, XML, itp.).</span><span class="sxs-lookup"><span data-stu-id="1dc16-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="1dc16-120">Często wiąże się to z uczeniem się nowego interfejsu API dla każdego źródła danych, co może być denerwujące.</span><span class="sxs-lookup"><span data-stu-id="1dc16-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="1dc16-121">LINQ upraszcza to przez abstrakcję typowych elementów dostępu do danych do składni kwerendy, która wygląda tak samo bez względu na to, które źródło danych wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="1dc16-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="1dc16-122">Należy wziąć pod uwagę następujące czynności: znalezienie wszystkich elementów XML z określoną wartością atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1dc16-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

```vb
Public Shared Function FindAllElementsWithAttribute(documentRoot As XElement, elementName As String,
                                           attributeName As String, value As String) As IEnumerable(Of XElement)
    Return From el In documentRoot.Elements(elementName)
           Where el.Element(attributeName).ToString() = value
           Select el
End Function

```

<span data-ttu-id="1dc16-123">Pisanie kodu do ręcznego przechodzenia przez dokument XML w celu wykonania tego zadania byłoby znacznie trudniejsze.</span><span class="sxs-lookup"><span data-stu-id="1dc16-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="1dc16-124">Interakcja z XML nie jest jedyną rzeczą, którą możesz zrobić z dostawcami LINQ.</span><span class="sxs-lookup"><span data-stu-id="1dc16-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="1dc16-125">[Linq do SQL](../../docs/framework/data/adonet/sql/linq/index.md) jest dość gołymi kości object-relational Mapper (ORM) dla bazy danych serwera MSSQL.</span><span class="sxs-lookup"><span data-stu-id="1dc16-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="1dc16-126">Biblioteka [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) zapewnia wydajną przejście dokumentu JSON przez LINQ.</span><span class="sxs-lookup"><span data-stu-id="1dc16-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="1dc16-127">Ponadto, jeśli nie ma biblioteki, która robi to, czego potrzebujesz, możesz również [napisać własnego dostawcę LINQ!](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="1dc16-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="1dc16-128">Dlaczego warto korzystać ze składni kwerendy?</span><span class="sxs-lookup"><span data-stu-id="1dc16-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="1dc16-129">To jest pytanie, które często pojawia się.</span><span class="sxs-lookup"><span data-stu-id="1dc16-129">This is a question which often comes up.</span></span> <span data-ttu-id="1dc16-130">Po tym wszystkim, to,</span><span class="sxs-lookup"><span data-stu-id="1dc16-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="1dc16-131">jest o wiele bardziej zwięzły niż to:</span><span class="sxs-lookup"><span data-stu-id="1dc16-131">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

```vb
Dim filteredItems = From item In myItems
                    Where item.Foo
                    Select item
```

<span data-ttu-id="1dc16-132">Czy składnia interfejsu API nie jest tylko bardziej zwięzłym sposobem wykonywania składni kwerendy?</span><span class="sxs-lookup"><span data-stu-id="1dc16-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="1dc16-133">Nie.</span><span class="sxs-lookup"><span data-stu-id="1dc16-133">No.</span></span> <span data-ttu-id="1dc16-134">Składnia kwerendy umożliwia użycie **let** klauzuli, która pozwala na wprowadzenie i powiązanie zmiennej w zakresie wyrażenia, używając go w kolejnych fragmentach wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1dc16-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="1dc16-135">Odtwarzanie tego samego kodu tylko składni interfejsu API można zrobić, ale najprawdopodobniej doprowadzi do kodu, który jest trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="1dc16-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="1dc16-136">Więc to nasuwa pytanie, **należy po prostu użyć składni kwerendy?**</span><span class="sxs-lookup"><span data-stu-id="1dc16-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="1dc16-137">Odpowiedź na to pytanie **brzmi: tak,** jeśli...</span><span class="sxs-lookup"><span data-stu-id="1dc16-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="1dc16-138">Istniejąca baza kodu już używa składni kwerendy</span><span class="sxs-lookup"><span data-stu-id="1dc16-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="1dc16-139">Należy zakres zmiennych w ramach zapytań ze względu na złożoność</span><span class="sxs-lookup"><span data-stu-id="1dc16-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="1dc16-140">Wolisz składnię zapytania i nie odwróci ona uwagi od bazy kodu</span><span class="sxs-lookup"><span data-stu-id="1dc16-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="1dc16-141">Odpowiedź na to pytanie **brzmi: nie,** jeśli...</span><span class="sxs-lookup"><span data-stu-id="1dc16-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="1dc16-142">Istniejąca baza kodu korzysta już ze składni interfejsu API</span><span class="sxs-lookup"><span data-stu-id="1dc16-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="1dc16-143">Nie musisz zakres zmiennych w kwerendach</span><span class="sxs-lookup"><span data-stu-id="1dc16-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="1dc16-144">Wolisz składnię interfejsu API i nie odwróci ona uwagi od bazy kodu</span><span class="sxs-lookup"><span data-stu-id="1dc16-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="1dc16-145">Podstawowe próbki</span><span class="sxs-lookup"><span data-stu-id="1dc16-145">Essential Samples</span></span>

<span data-ttu-id="1dc16-146">Aby uzyskać naprawdę wyczerpującą listę próbek LINQ, odwiedź [101 próbek LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span><span class="sxs-lookup"><span data-stu-id="1dc16-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="1dc16-147">Poniżej znajduje się szybki pokaz niektórych podstawowych elementów LINQ.</span><span class="sxs-lookup"><span data-stu-id="1dc16-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="1dc16-148">Nie jest to w żaden sposób kompleksowe, ponieważ LINQ zapewnia znacznie więcej funkcjonalności niż to, co jest tutaj prezentowane.</span><span class="sxs-lookup"><span data-stu-id="1dc16-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="1dc16-149">Chleb i masło `Where` `Select`- `Aggregate`, i :</span><span class="sxs-lookup"><span data-stu-id="1dc16-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list.
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax.
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B.
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax.
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings.
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

```vb
' Filtering a list.
Dim germanShepards = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepard)

' Using the query syntax.
Dim queryGermanShepards = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepard
                          Select dog

' Mapping a list from type A to type B.
Dim cats = dogs.Select(Function(dog) dog.TurnIntoACat())

' Using the query syntax.
Dim queryCats = From dog In dogs
                Select dog.TurnIntoACat()

' Summing the lengths of a set of strings.
Dim seed As Integer = 0
Dim sumOfStrings As Integer = strings.Aggregate(seed, Function(s1, s2) s1.Length + s2.Length)
```

* <span data-ttu-id="1dc16-150">Spłaszczanie listy list:</span><span class="sxs-lookup"><span data-stu-id="1dc16-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* <span data-ttu-id="1dc16-151">Unia między dwoma zestawami (z niestandardowym komparatorem):</span><span class="sxs-lookup"><span data-stu-id="1dc16-151">Union between two sets (with custom comparator):</span></span>

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
        // Default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels.
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

```vb
Public Class DogHairLengthComparer
  Inherits IEqualityComparer(Of Dog)

  Public Function Equals(a As Dog,b As Dog) As Boolean
      If a Is Nothing AndAlso b Is Nothing Then
          Return True
      ElseIf (a Is Nothing AndAlso b IsNot Nothing) OrElse (a IsNot Nothing AndAlso b Is Nothing) Then
          Return False
      Else
          Return a.HairLengthType = b.HairLengthType
      End If
  End Function

  Public Function GetHashCode(d As Dog) As Integer
      ' Default hashcode is enough here, as these are simple objects.
      Return d.GetHashCode()
  End Function
End Class

...

' Gets all the short-haired dogs between two different kennels.
Dim allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, New DogHairLengthComparer())
```

* <span data-ttu-id="1dc16-152">Przecięcie dwóch zestawów:</span><span class="sxs-lookup"><span data-stu-id="1dc16-152">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

```vb
' Gets the volunteers who spend share time with two humane societies.
Dim volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     New VolunteerTimeComparer())
```

* <span data-ttu-id="1dc16-153">Zamawiania:</span><span class="sxs-lookup"><span data-stu-id="1dc16-153">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

```vb
' Get driving directions, ordering by if it's toll-free before estimated driving time.
Dim results = DirectionsProcessor.GetDirections(start, end).
                OrderBy(Function(direction) direction.HasNoTolls).
                ThenBy(Function(direction) direction.EstimatedTime)
```

* <span data-ttu-id="1dc16-154">Na koniec bardziej zaawansowany przykład: określenie, czy wartości właściwości dwóch wystąpień tego samego typu są równe (Pożyczone i zmodyfikowane z [tego postu StackOverflow):](https://stackoverflow.com/a/844855)</span><span class="sxs-lookup"><span data-stu-id="1dc16-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

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

```vb
<System.Runtime.CompilerServices.Extension()>
Public Function PublicInstancePropertiesEqual(Of T As Class)(self As T, [to] As T, ParamArray ignore As String()) As Boolean
    If self Is Nothing OrElse [to] Is Nothing Then
        Return self Is [to]
    End If

    ' Selects the properties which have unequal values into a sequence of those properties.
    Dim unequalProperties = From [property] In GetType(T).GetProperties(BindingFlags.Public Or BindingFlags.Instance)
                            Where Not ignore.Contains([property].Name)
                            Let selfValue = [property].GetValue(self, Nothing)
                            Let toValue = [property].GetValue([to], Nothing)
                            Where Not Equals(selfValue, toValue) Select [property]
    Return Not unequalProperties.Any()
End Function
```

## <a name="plinq"></a><span data-ttu-id="1dc16-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="1dc16-155">PLINQ</span></span>

<span data-ttu-id="1dc16-156">PLINQ lub Parallel LINQ jest równoległym aparatem wykonywania wyrażeń LINQ.</span><span class="sxs-lookup"><span data-stu-id="1dc16-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="1dc16-157">Innymi słowy, regularne wyrażenie LINQ może być trywialnie równoległe w dowolnej liczbie wątków.</span><span class="sxs-lookup"><span data-stu-id="1dc16-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="1dc16-158">Odbywa się to za `AsParallel()` pomocą wywołania do przedstwa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1dc16-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="1dc16-159">Rozważ następujące źródła:</span><span class="sxs-lookup"><span data-stu-id="1dc16-159">Consider the following:</span></span>

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

```vb
Public Shared GetAllFacebookUserLikesMessage(facebookUsers As IEnumerable(Of FacebookUser)) As String
{
    Dim seed As UInt64 = 0

    Dim threadAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim threadResultAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim resultSelector As Func(Of Uint64, string) = Function(total) $"Facebook has {total} likes!"

    Return facebookUsers.AsParallel().
                        Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector)
}
```

<span data-ttu-id="1dc16-160">Ten kod `facebookUsers` będzie partycjonować między wątkami systemowym w razie potrzeby, podsumować całkowitą liczbę polubień w każdym wątku równolegle, zsumować wyniki obliczone przez każdy wątek i projektu, który wynik w miły ciąg.</span><span class="sxs-lookup"><span data-stu-id="1dc16-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="1dc16-161">W formie diagramu:</span><span class="sxs-lookup"><span data-stu-id="1dc16-161">In diagram form:</span></span>

![Diagram PLINQ](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="1dc16-163">Równoległe zadania związane z procesorem, które można łatwo wyrazić za pomocą LINQ (innymi słowy, są czystymi funkcjami i nie mają skutków ubocznych) są doskonałym kandydatem do PLINQ.</span><span class="sxs-lookup"><span data-stu-id="1dc16-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="1dc16-164">W przypadku _zadań,_ które mają efekt uboczny, należy rozważyć użycie [biblioteki równoległej zadania](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="1dc16-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="1dc16-165">Dalsze zasoby:</span><span class="sxs-lookup"><span data-stu-id="1dc16-165">Further Resources:</span></span>

* [<span data-ttu-id="1dc16-166">101 próbek LINQ</span><span class="sxs-lookup"><span data-stu-id="1dc16-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* <span data-ttu-id="1dc16-167">[Linqpad](https://www.linqpad.net/), środowisko plac zabaw i aparat zapytań bazy danych dla Języka C#/F#/Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dc16-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="1dc16-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), e-book do nauki, jak LINQ-to-obiekty są realizowane</span><span class="sxs-lookup"><span data-stu-id="1dc16-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
