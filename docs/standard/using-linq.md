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
# <a name="linq-language-integrated-query"></a>LINQ (zapytanie zintegrowane językowe)

## <a name="what-is-it"></a>co to jest?

LINQ zapewnia możliwości wykonywania zapytań na poziomie języka i interfejs API [funkcji wyższego rzędu](https://en.wikipedia.org/wiki/Higher-order_function) do języka C# i Visual Basic jako sposób pisania wyrazistego, deklaratywnego kodu.

Składnia kwerend na poziomie języka:

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

Ten sam `IEnumerable<T>` przykład przy użyciu interfejsu API:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a>LINQ jest wyrazisty

Wyobraź sobie, że masz listę zwierząt domowych, ale chcesz przekształcić go w `RFID` słownik, w którym możesz uzyskać dostęp do zwierzaka bezpośrednio według jego wartości.

Tradycyjny kod imperatywu:

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

Intencją kodu nie jest tworzenie `Dictionary<int, Pet>` nowego i dodawanie do niego za pośrednictwem pętli, jest konwersja istniejącej listy do słownika! LINQ zachowuje intencji, podczas gdy kod imperatywnie nie.

Równoważne wyrażenie LINQ:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

Kod przy użyciu LINQ jest cenne, ponieważ wyrównuje pole gry między intencji i kodu podczas rozumowania jako programista. Kolejnym bonusem jest zwięzłość kodu. Wyobraź sobie zmniejszenie dużych części bazy kodu o 1/3, jak to się robi powyżej. Całkiem słodka oferta, prawda?

## <a name="linq-providers-simplify-data-access"></a>Dostawcy LINQ upraszczają dostęp do danych

Dla znacznego fragmentu oprogramowania w środowisku naturalnym, wszystko kręci się wokół radzenia sobie z danymi z niektórych źródeł (bazy danych, JSON, XML, itp.). Często wiąże się to z uczeniem się nowego interfejsu API dla każdego źródła danych, co może być denerwujące. LINQ upraszcza to przez abstrakcję typowych elementów dostępu do danych do składni kwerendy, która wygląda tak samo bez względu na to, które źródło danych wybierzesz.

Należy wziąć pod uwagę następujące czynności: znalezienie wszystkich elementów XML z określoną wartością atrybutu.

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

Pisanie kodu do ręcznego przechodzenia przez dokument XML w celu wykonania tego zadania byłoby znacznie trudniejsze.

Interakcja z XML nie jest jedyną rzeczą, którą możesz zrobić z dostawcami LINQ. [Linq do SQL](../../docs/framework/data/adonet/sql/linq/index.md) jest dość gołymi kości object-relational Mapper (ORM) dla bazy danych serwera MSSQL. Biblioteka [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) zapewnia wydajną przejście dokumentu JSON przez LINQ. Ponadto, jeśli nie ma biblioteki, która robi to, czego potrzebujesz, możesz również [napisać własnego dostawcę LINQ!](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))

## <a name="why-use-the-query-syntax"></a>Dlaczego warto korzystać ze składni kwerendy?

To jest pytanie, które często pojawia się. Po tym wszystkim, to,

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

jest o wiele bardziej zwięzły niż to:

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

Czy składnia interfejsu API nie jest tylko bardziej zwięzłym sposobem wykonywania składni kwerendy?

Nie. Składnia kwerendy umożliwia użycie **let** klauzuli, która pozwala na wprowadzenie i powiązanie zmiennej w zakresie wyrażenia, używając go w kolejnych fragmentach wyrażenia. Odtwarzanie tego samego kodu tylko składni interfejsu API można zrobić, ale najprawdopodobniej doprowadzi do kodu, który jest trudny do odczytania.

Więc to nasuwa pytanie, **należy po prostu użyć składni kwerendy?**

Odpowiedź na to pytanie **brzmi: tak,** jeśli...

* Istniejąca baza kodu już używa składni kwerendy
* Należy zakres zmiennych w ramach zapytań ze względu na złożoność
* Wolisz składnię zapytania i nie odwróci ona uwagi od bazy kodu

Odpowiedź na to pytanie **brzmi: nie,** jeśli...

* Istniejąca baza kodu korzysta już ze składni interfejsu API
* Nie musisz zakres zmiennych w kwerendach
* Wolisz składnię interfejsu API i nie odwróci ona uwagi od bazy kodu

## <a name="essential-samples"></a>Podstawowe próbki

Aby uzyskać naprawdę wyczerpującą listę próbek LINQ, odwiedź [101 próbek LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Poniżej znajduje się szybki pokaz niektórych podstawowych elementów LINQ. Nie jest to w żaden sposób kompleksowe, ponieważ LINQ zapewnia znacznie więcej funkcjonalności niż to, co jest tutaj prezentowane.

* Chleb i masło `Where` `Select`- `Aggregate`, i :

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

* Unia między dwoma zestawami (z niestandardowym komparatorem):

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

* Przecięcie dwóch zestawów:

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

* Zamawiania:

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

* Na koniec bardziej zaawansowany przykład: określenie, czy wartości właściwości dwóch wystąpień tego samego typu są równe (Pożyczone i zmodyfikowane z [tego postu StackOverflow):](https://stackoverflow.com/a/844855)

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

PLINQ lub Parallel LINQ jest równoległym aparatem wykonywania wyrażeń LINQ. Innymi słowy, regularne wyrażenie LINQ może być trywialnie równoległe w dowolnej liczbie wątków. Odbywa się to za `AsParallel()` pomocą wywołania do przedstwa wyrażenia.

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

Ten kod `facebookUsers` będzie partycjonować między wątkami systemowym w razie potrzeby, podsumować całkowitą liczbę polubień w każdym wątku równolegle, zsumować wyniki obliczone przez każdy wątek i projektu, który wynik w miły ciąg.

W formie diagramu:

![Diagram PLINQ](./media/using-linq/plinq-diagram.png)

Równoległe zadania związane z procesorem, które można łatwo wyrazić za pomocą LINQ (innymi słowy, są czystymi funkcjami i nie mają skutków ubocznych) są doskonałym kandydatem do PLINQ. W przypadku _zadań,_ które mają efekt uboczny, należy rozważyć użycie [biblioteki równoległej zadania](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Dalsze zasoby:

* [101 próbek LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* [Linqpad](https://www.linqpad.net/), środowisko plac zabaw i aparat zapytań bazy danych dla Języka C#/F#/Visual Basic
* [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), e-book do nauki, jak LINQ-to-obiekty są realizowane
