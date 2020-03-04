---
title: LINQ (zapytanie zintegrowane z językiem)
description: Dowiedz się, w jaki sposób LINQ udostępnia funkcje zapytań na poziomie języka C# i interfejs API do i Visual Basic jako sposób pisania kodu, który jest bardziej wyraźny.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: eafd8f78c3d8de1ba064021111f869571d5a570f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160329"
---
# <a name="linq-language-integrated-query"></a>LINQ (zapytanie zintegrowane z językiem)

## <a name="what-is-it"></a>Co to jest?

LINQ udostępnia funkcje obsługi zapytań na poziomie języka i interfejs API [funkcji wyższej kolejności](https://en.wikipedia.org/wiki/Higher-order_function) do C# i Visual Basic jako sposób pisania kodu, który jest bardziej wyraźny.

Składnia zapytania na poziomie języka:

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

Ten sam przykład przy użyciu interfejsu API `IEnumerable<T>`:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a>LINQ jest wyraźne

Wyobraź sobie, że masz listę zwierząt domowych, ale chcesz ją przekonwertować na słownik, w którym możesz uzyskać dostęp do Pet bezpośrednio przez jego wartość `RFID`.

Tradycyjny, bezwzględny kod:

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

Zamiarem za kod nie jest utworzenie nowego `Dictionary<int, Pet>` i dodanie go do niego za pośrednictwem pętli. ma to na celu konwersję istniejącej listy do słownika. LINQ zachowuje zamiar, a sam kod nie jest.

Równoważne wyrażenie LINQ:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

Kod przy użyciu LINQ jest cenny, ponieważ nawet pole Play między intencją a kodem, gdy jest to programista. Kolejną premią jest zwięzłości kodu. Załóżmy, że zmniejszasz duże fragmenty kodu bazy danych o 1/3 jak powyżej. Dość słodkiej transakcji?

## <a name="linq-providers-simplify-data-access"></a>Dostawcy LINQ upraszczają dostęp do danych

Aby uzyskać znaczący fragment oprogramowania na świecie, wszystko to koncentruje się na danych z niektórych źródeł (baz danych, JSON, XML itp.). Często obejmuje to uczenie nowego interfejsu API dla każdego źródła danych, co może być irytujące. LINQ upraszcza to dzięki abstrakcyjnym typowym elementom dostępu do danych do składni zapytań, która wygląda tak samo niezależnie od wybranego źródła danych.

Rozważ następujące kwestie: znalezienie wszystkich elementów XML z określoną wartością atrybutu.

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

Pisanie kodu do ręcznego przechodzenia dokumentu XML w celu wykonania tego zadania byłoby znacznie trudniejsze.

Korzystanie z języka XML nie jest jedynym elementem, który można wykonywać za pomocą dostawców LINQ. [LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) to stosunkowo jednoskładnikowo-relacyjny obiekt mapowania (ORM) dla bazy danych serwera MSSQL. Biblioteka [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) zapewnia wydajną przechodzenie dokumentów JSON za pośrednictwem LINQ. Ponadto jeśli nie ma biblioteki, która robi to potrzebne, możesz również [napisać własnego dostawcę LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110)).

## <a name="why-use-the-query-syntax"></a>Dlaczego warto używać składni zapytania?

Jest to pytanie, które często się pojawia. Następnie,

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

jest znacznie bardziej zwięzły niż:

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

Czy składnia interfejsu API jest bardziej zwięzła, aby wykonać składnię zapytania?

Nie. Składnia zapytania umożliwia użycie klauzuli **Let** , która umożliwia wprowadzenie i powiązanie zmiennej w zakresie wyrażenia, przy użyciu jej w kolejnych fragmentach wyrażenia. Odtwarzanie tego samego kodu tylko przy użyciu składni interfejsu API można wykonać, ale najprawdopodobniej prowadzi to do kodu, który jest trudno odczytać.

W związku z tym begs pytanie, **czy wystarczy użyć składni zapytania?**

Odpowiedź na to pytanie ma **wartość tak** , jeśli...

* Istniejąca baza kodu używa już składni zapytania
* Należy określić zakres zmiennych w zapytaniach ze względu na złożoność
* Wolisz składnię zapytania i nie będzie ona przeszkadzać w kodzie bazowej

Odpowiedź na to pytanie **nie** dotyczy, jeśli...

* Istniejąca baza kodu używa już składni interfejsu API
* Nie ma potrzeby określania zakresu zmiennych w zapytaniach
* Wolisz składnię interfejsu API i nie będzie ona przeszkadzać w kodzie bazowym

## <a name="essential-samples"></a>Najważniejsze przykłady

Aby zapoznać się z prawdziwie obszerną listą przykładów LINQ, zobacz [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Poniżej znajduje się szybka Prezentacja niektórych najważniejszych fragmentów LINQ. Ta funkcja nie jest kompletna, ponieważ składnik LINQ zapewnia znacznie większą funkcjonalność niż to, co zostało przedstawione w tym miejscu.

* Chleb i masło `Where`, `Select`i `Aggregate`:

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

* Spłaszczanie listy list:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* Złożenie między dwoma zestawami (z niestandardowym komparatorem):

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

* Część wspólna między dwoma zestawami:

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

* Zamówienie

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

* Na koniec bardziej zaawansowaną próbkę: określenie, czy wartości właściwości dwóch wystąpień tego samego typu są równe (zapożyczone i zmodyfikowane z [tego StackOverflow post](https://stackoverflow.com/a/844855)):

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

## <a name="plinq"></a>PLINQ

PLINQ lub Parallel LINQ jest aparatem wykonywania równoległym dla wyrażeń LINQ. Inaczej mówiąc, regularne wyrażenie LINQ może być równolegle równoległe do dowolnej liczby wątków. Jest to realizowane za pośrednictwem wywołania `AsParallel()` poprzedzającego wyrażenie.

Rozważ następujące źródła:

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

Ten kod będzie dzielić na partycje `facebookUsers` między wątkami systemowymi, w razie potrzeby Sumuj łączną liczbę polubień w każdym wątku równolegle, Sumuj wyniki obliczone przez poszczególne wątki oraz projekt, który spowoduje powstanie ciągu znaków.

W formularzu diagramu:

![Diagram PLINQ](./media/using-linq/plinq-diagram.png)

Działania równoległego zadania związane z PROCESORem, które można łatwo wyrazić za pośrednictwem LINQ (innymi słowy, są czystymi funkcjami i nie mają efektów ubocznych) są doskonałym kandydatem do PLINQ. W przypadku zadań _, które mają_ efekt uboczny, należy rozważyć użycie [biblioteki zadań równoległych](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Dalsze zasoby:

* [Przykłady dla LINQ 101](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* [LINQPad](https://www.linqpad.net/), środowisko plac zabaw i aparat zapytań bazy danych dla C#/F#/Visual Basic
* [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/)— książka elektroniczna do uczenia się, jak jest implementowane LINQ-to-Objects
