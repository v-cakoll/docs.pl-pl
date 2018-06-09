---
title: LINQ (zapytania zintegrowane Language)
description: Dowiedz się, jak LINQ udostępnia interfejsów API i możliwości podczas badania poziom języka C# i VB jako sposobu pisania kodu obszerne, deklaratywne.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 31b0a7b9e11d46e6453d9fcad87e7beadba9a1e3
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251093"
---
# <a name="linq-language-integrated-query"></a>LINQ (zapytania zintegrowane Language)

## <a name="what-is-it"></a>Co to?

LINQ zapewnia możliwości podczas badania poziom języka i [funkcja wyższego rzędu](https://en.wikipedia.org/wiki/Higher-order_function) interfejsu API języka C# i VB jako sposobu pisania kodu obszerne, deklaratywne.

Składnia zapytania poziom języka:

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

Przy użyciu tego samego przykład `IEnumerable<T>` interfejsu API:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a>LINQ jest Expressive

Wyobraź sobie listę zwierząt domowych, ale chcesz przekształcać je do słownika, w której będzie można uzyskać dostęp pet bezpośrednio przez jego `RFID` wartość.

Tradycyjny imperatywnych kodu:

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

Za kod jest nie, aby utworzyć nową `Dictionary<int, Pet>` i Dodaj do niej przy użyciu pętli, to można przekonwertować istniejącej listy do słownika! LINQ zachowuje zamiar, natomiast nie jest konieczne kodu.

Odpowiednik wyrażenia LINQ:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

Kod za pomocą LINQ jest przydatna, ponieważ jego evens pola gry między celem i kodu podczas wnioskowania dla programisty. Podwyższenie innego jest skrócenia kodu. Wyobraź sobie zmniejszanie dużych części codebase poprzez 1/3, jak wykonać powyżej. Funkcja pretty słodkich transakcji, prawy?

## <a name="linq-providers-simplify-data-access"></a>Dostawcy LINQ uprościć dostęp do danych

Znaczące fragmentu oprogramowania limit wszystko, co dotyczy tego postępowania z danymi z określonego źródła (baz danych, JSON, XML itp.). Często ten proces obejmuje uczenie nowy interfejs API dla każdego źródła danych, które mogą być irytujące. LINQ ułatwia to abstrakcyjność wspólne elementy dostępu do danych w składni zapytania, który jest taki sam, niezależnie od tego źródła danych, możesz wybrać.

Rozważ następujące opcje: znajdowanie wszystkich elementów XML z wartością określony atrybut.

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

Pisanie kodu ręcznie przechodzenia dokument XML, aby wykonać to zadanie będzie znacznie trudniejsze.

Interakcja z XML nie jest jedyną operacją, której można zrobić za pomocą dostawcy LINQ. [LINQ do SQL](../../docs/framework/data/adonet/sql/linq/index.md) jest dość bez systemu operacyjnego kości obiektów relacyjnych mapowania (ORM) dla bazy danych MSSQL. [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) Biblioteka zapewnia wydajne przechodzenie dokumentu JSON za pomocą LINQ. Ponadto, jeśli nie ma bibliotekę, która obsługuje, co jest potrzebne, można również [zapisać własnego dostawcę LINQ](https://msdn.microsoft.com/library/Bb546158.aspx)!

## <a name="why-use-the-query-syntax"></a>Dlaczego warto używać składni zapytania?

Jest to pytanie, które często pojawia się. Po wszystkich, ten,

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

jest znacznie bardziej zwięzłe niż to:

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

Składnia interfejsu API nie jest tylko bardziej zwięzły sposób na czy składnia zapytania?

Nie. Składnia zapytania umożliwia wykorzystanie **let** klauzuli, dzięki czemu można wprowadzić i powiązać zmiennej w zakresie wyrażenie, używając w kolejnej części wyrażenia. Odtwarzanie tego samego kodu przy użyciu składni interfejsu API jest możliwe, ale najprawdopodobniej doprowadzi do kodu, który jest trudny do odczytania.

Dlatego begs to pytanie, **możesz po prostu użyj składni zapytania?**

Odpowiedzi na to pytanie jest **tak** Jeśli...

*   Istniejące ścieżki bazowej kodu już używa składni zapytania
*   W ramach zapytania z powodu złożoności konieczne zmiennych o zasięgu
*   Preferowane jest składnia zapytania i go nie niekorzystnie wpłynąć na baza kodu

Odpowiedzi na to pytanie jest **nie** Jeśli...

*   Istniejące ścieżki bazowej kodu już używa składni interfejsu API
*   Użytkownik nie ma potrzeby do zmiennych o zasięgu w zapytaniach
*   Preferowane jest składnia interfejsu API i go nie niekorzystnie wpłynąć na baza kodu

## <a name="essential-samples"></a>Przykłady podstawowych

Naprawdę kompleksowe przykłady interfejsów LINQ, można znaleźć [101 przykłady interfejsów LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Poniżej przedstawiono szybki pokaz niektórych podstawowych części LINQ. Jest to w żaden sposób kompleksowe, jak LINQ udostępnia znacznie więcej funkcji niż co to jest pokazywane w tym miejscu.

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

*   Związek między dwoma zestawami (za pomocą niestandardowych komparatora):

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

*   Część wspólną między dwoma zestawami:

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   Kolejność:

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   Na koniec bardziej zaawansowane próbki: Określanie, czy wartości właściwości dwa wystąpienia tego samego typu są takie same (Borrowed i zmodyfikowanych z [tego wpisu StackOverflow](http://stackoverflow.com/a/844855)):

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

## <a name="plinq"></a>PLINQ

PLINQ lub równoległe LINQ jest aparatem przetwarzania równoległego wyrażenia LINQ. Innymi słowy regularne wyrażenia LINQ może być trivially zarządzana z przetwarzaniem na dowolną liczbę wątków. Jest to realizowane za pośrednictwem wywołania `AsParallel()` przed wyrażeniem.

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

Ten kod będzie partycji `facebookUsers` przez wątki systemowe w razie potrzeby podsumowania całkowita podobne w każdym wątku równolegle, Suma wyników obliczone przez każdy wątek i projektu na ciąg nieuprzywilejowany tego wyniku.

W postaci diagramu:

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

Działania równoległego zadania procesora, które można łatwo wyrazić za pomocą LINQ (innymi słowy, są czystych funkcji i nie skutków po stronie) jest doskonałym kandydatem do PLINQ. Dla zadania, które _czy_ ma skutków ubocznych, należy rozważyć użycie [Biblioteka zadań równoległych](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Dodatkowe zasoby:

*   [101 przykłady interfejsów LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   [Linqpad](https://www.linqpad.net/), Plac zabaw dla środowiska i zapytań bazy danych aparatu dla C# / f # / VB.
*   [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), książkę elektroniczną do uczenia implementowania LINQ do obiektów
