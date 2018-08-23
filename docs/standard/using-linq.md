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
# <a name="linq-language-integrated-query"></a>LINQ (Language Integrated Query)

## <a name="what-is-it"></a>Co to?

LINQ zapewnia możliwości zapytań w poziomie języka i [funkcja wyższego rzędu](https://en.wikipedia.org/wiki/Higher-order_function) interfejsu API języka C# i VB jako sposób pisania kodu ekspresyjna, deklaratywnego.

Składnia poziomu języka zapytań:

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

Przy użyciu tego samego przykładu `IEnumerable<T>` interfejsu API:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a>LINQ to Expressive

Wyobraź sobie listę zwierząt domowych, ale chcesz przekonwertować ją do słownika, w którym możesz uzyskać dostęp pet bezpośrednio przez jego `RFID` wartość.

Tradycyjne kodu imperatywnego:

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

Za kod jest nie do tworzenia nowego `Dictionary<int, Pet>` i dodać do niego za pomocą pętli, to można przekonwertować istniejącej listy do słownika! LINQ zachowuje zamiar, dlatego nie ma kodu imperatywnego.

Równoważne wyrażenie LINQ:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

Kod za pomocą LINQ jest przydatne, ponieważ evens szans między intencji i kodu, podczas wnioskowania programistą. Podwyższenie innego jest zwięzłości kodu. Wyobraź sobie, zmniejszanie dużych fragmentów kodu poprzez 1/3 jako gotowe powyżej. Całkiem osiąganie słodkiego transakcji, odpowiednie?

## <a name="linq-providers-simplify-data-access"></a>Dostawcy LINQ uprościć dostęp do danych

Znaczne fragmenty oprogramowania na zewnątrz wszystko, czego dotyczy tego radzenia sobie z danymi z określonego źródła (baz danych, JSON, XML itp.). Często ten proces obejmuje uczenie nowego interfejsu API dla każdego źródła danych, które mogą być irytujące. LINQ upraszcza to abstrakcyjność wspólne elementy dostęp do danych w składni zapytań, który wygląda tak samo niezależnie od tego źródła danych wybierz.

Rozważ następujące opcje: znajdowanie wszystkich elementów XML z wartością konkretnego atrybutu.

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

Pisanie kodu w celu ręcznego przechodzenia dokumentu XML, aby wykonać to zadanie będzie znacznie trudniejsze.

Wchodzenie w interakcje z danymi XML nie jest jedyną czynnością, którą można zrobić za pomocą dostawców LINQ. [LINQ do SQL](../../docs/framework/data/adonet/sql/linq/index.md) jest dość bez kości obiektowo-relacyjny mapowania (ORM) dla bazy danych MSSQL. [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) Biblioteka zapewnia wydajne przechodzenie dokumentów JSON za pomocą LINQ. Ponadto, jeśli nie istnieje biblioteki, która obsługuje, czego potrzebujesz, możesz również [pisania własnego dostawcy LINQ](https://msdn.microsoft.com/library/Bb546158.aspx)!

## <a name="why-use-the-query-syntax"></a>Dlaczego warto używać składni zapytań?

Jest to pytanie, które często jest dostarczany w górę. Gdy wszystkie ten,

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

jest znacznie bardziej zwięzłe niż to:

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

Składnia interfejsu API nie jest po prostu bardziej zwarty sposób przeprowadzenia składnia zapytania?

Nie. Składnia zapytań umożliwia użycie **umożliwiają** klauzula, która pozwala na wprowadzenie i powiązać zmiennej w zakresie wyrażenie, używając go w kolejnych częściach wyrażenia. Odtwarzanie tego samego kodu przy użyciu składni interfejsu API może odbywać się, ale prawdopodobnie doprowadzi do kodu, który jest trudny do odczytania.

Tak wymaga to pytanie, **należy po prostu użyć składni zapytania?**

Odpowiedź na to pytanie jest **tak** Jeśli...

*   Istniejącej bazy kodu już używa składni zapytania
*   Należy do zakresu zmiennych w ciągu zapytania z powodu złożoności
*   Preferuj składnia zapytania i jej nie będzie niekorzystnie wpłynąć na bazie kodu

Odpowiedź na to pytanie jest **nie** Jeśli...

*   Istniejącej bazy kodu już używa składni interfejsu API
*   Użytkownik nie ma potrzeby do zakresu zmiennych w ciągu zapytania
*   Preferuj składni interfejsu API i jego nie będzie niekorzystnie wpłynąć na bazie kodu

## <a name="essential-samples"></a>Podstawowe przykłady

Aby naprawdę pełną listę przykładów LINQ, odwiedź stronę [101 przykładów LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Poniżej przedstawiono szybki pokaz niektórych podstawowych rodzajów LINQ. To jest w żaden sposób nie wszechstronne LINQ zapewnia znacznie więcej funkcji niż co jest pokazywane w tym miejscu.

*   Masła i chleb - `Where`, `Select`, i `Aggregate`:

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

*   Spłaszczanie listę list:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   Związek między dwoma zestawami (przy użyciu niestandardowych komparator):

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

*   Część wspólną między dwoma zestawami:

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   Określanie kolejności:

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   Na koniec bardziej zaawansowany przykład: Określanie, czy wartości właściwości z dwóch wystąpień tego samego typu są równe (Borrowed i zmodyfikowane od [ten wpis w witrynie StackOverflow](http://stackoverflow.com/a/844855)):

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

## <a name="plinq"></a>PLINQ

Program PLINQ lub równoległe LINQ jest aparatem wykonywania równoległego wyrażenia LINQ. Innymi słowy regularne wyrażenia LINQ może być przypadku przetwarzane równolegle w dowolnej liczbie wątków. Jest to realizowane poprzez wywołanie `AsParallel()` przed wyrażeniem.

Rozważ następujące opcje:

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

Ten kod będzie partycji `facebookUsers` na wątki systemowe zgodnie z potrzebami, sumują łączna liczba polubień na każdy wątek w sposób równoległy, Suma wyników obliczone przez każdego wątku i projektu wynik na ciąg dobre rozwiązanie.

W postaci diagramu:

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

Równoległego zadania zależne od Procesora CPU, które mogą być łatwo wyrażone za pomocą LINQ (innymi słowy, czystej funkcji i mieć żadnych efektów ubocznych) są doskonałym kandydatem do PLINQ. Dla zadań, które _czy_ ma efekt uboczny, należy rozważyć użycie [Biblioteka zadań równoległych](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Dalsze zasoby:

*   [101 przykładów LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   [Linqpad](https://www.linqpad.net/), Plac zabaw dla środowiska i wykonywanie zapytań w bazie danych aparatu dla języków C# /F #/VB
*   [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), e-book, prezentującą implementacji LINQ do obiektów
