---
title: Iteratory
description: Dowiedz się, jak za pomocą wbudowanych Iteratory C# oraz tworzenie własnych metody iteracyjne niestandardowych.
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 403a286e9b1168b9e913b3cb2764e7fe262017d4
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="iterators"></a>Iteratory

Niemal wszystkie programy, jaki ma niektóre trzeba Iterowanie przez kolekcję. Będzie pisania kodu, który sprawdza, czy każdy element w kolekcji. 

Utworzysz także metody iteracyjne, które metod, które tworzy iteratora dla elementów tej klasy. Te mogą służyć do:

+ Wykonuje akcję na każdego elementu w kolekcji.
+ Wyliczanie kolekcji niestandardowej.
+ Rozszerzanie [LINQ](linq/index.md) lub innych bibliotek.
+ Tworzenie potoku danych, w którym dane przepływają wydajnie za pośrednictwem metody iteracyjne.

W języku C# udostępnia funkcje dla obu tych scenariuszy. Ten artykuł zawiera omówienie tych funkcji.

Ten samouczek ma wiele kroków. Po każdym kroku możesz uruchomić aplikację i wyświetlany jest postęp. Możesz również [wyświetlić lub pobrać przykład wypełnionego](https://github.com/dotnet/samples/blob/master/csharp/iterators) dla tego tematu. Instrukcje pobrania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Iterowanie za pomocą instrukcji foreach

Wyliczanie kolekcji jest prosty: `foreach` — słowo kluczowe wylicza kolekcję wykonywania osadzona instrukcja raz dla każdego elementu w kolekcji:
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

To wszystko jest do niego. Aby przejść przez całą zawartość kolekcji, `foreach` instrukcja jest potrzebna. `foreach` Instrukcja nie jest magic, mimo że. Opiera się na dwóch interfejsach zdefiniowany w bibliotece programu .NET core w celu wygenerowania kodu niezbędne w celu wykonania iteracji w kolekcji: `IEnumerable<T>` i `IEnumerator<T>`. Ten mechanizm jest co omówiono bardziej szczegółowo poniżej.

Z tych interfejsów również mają odpowiedniki nieogólnego: `IEnumerable` i `IEnumerator`. [Ogólnego](programming-guide/generics/index.md) wersje są preferowane dla nowoczesnego kodu.

## <a name="enumeration-sources-with-iterator-methods"></a>Wyliczenie źródeł za pomocą metody iteracyjne

Inny wspaniałych funkcji języka C# umożliwia tworzenie metody, które utworzyć źródło wyliczania. Są one określane jako *metody iteracyjne*. Iterator — metoda definiuje sposób generowania obiektów w sekwencji na żądanie. Możesz użyć `yield return` kontekstowe słowa kluczowe, aby określić metodę iteratora. 

Można zapisać tę metodę w celu utworzenia sekwencji liczb całkowitych od 0 do 9:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

Powyższy kod przedstawia różne `yield return` instrukcje, aby wyróżnić fakt, że można używać wielu odrębny `yield return` instrukcje w metodzie iteracyjnej.
Można (i często nie) użyć innych konstrukcji językowych, aby uprościć kod metody iteracyjnej. Definicja metody poniżej tworzy dokładnie tej samej sekwencji liczb:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

Nie trzeba określić jednego lub drugiego. Może mieć tyle `yield return` instrukcje odpowiednio do potrzeb metodę:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
    
    index = 100;
    while (index++ < 110)
        yield return index;
}
```

To jest podstawowa składnia. Zastanówmy się przykład rzeczywistych, w którym możesz zapisać metodę iteratora. Wyobraź sobie w projekcie IoT i czujników urządzenia generować bardzo duże strumienia danych. Aby uzyskać pewne pojęcie o danych, może być napisanie metody, która przykłady każdego elementu danych w n-ty. Ta metoda małych iteratora wykonuje lewy:

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

Istnieje jeden ważne ograniczenia metody iteracyjne: nie może zawierać zarówno `return` instrukcji i `yield return` instrukcji w tej samej metody. Następujące nie zostanie skompilowany:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    // generates a compile time error: 
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;  
}
```

To ograniczenie jest zazwyczaj problem. Masz do wyboru przy użyciu `yield return` w metodzie lub rozdzielić wiele metod oryginalnej metody, przy użyciu niektóre `return`, a niektóre przy użyciu `yield return`.

Można zmodyfikować ostatniego metodę używaną do nieco `yield return` wszędzie:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```
 
Czasami prawidłowa odpowiedź jest podzielić metodę iteratora na dwa sposoby. Taki, który używa `return`i drugie, która używa `yield return`. Rozważmy sytuację, w których warto zwrócić pustą kolekcję lub pierwszych 5 liczb nieparzysta, oparte na logiczną argumentu. Można zapisać który jako tych dwóch metod:

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index++ < 10)
        if (index % 2 == 1)
            yield return index;
}
```
 
Przyjrzyj się powyżej metod. Pierwszy korzysta ze standardu `return` instrukcji, aby zwrócić pustą kolekcję lub iteratora tworzone przez metodę drugiego. W drugiej metodzie `yield return` instrukcji można utworzyć żądanego sekwencji.

## <a name="deeper-dive-into-foreach"></a>Bardziej zgłębić temat do `foreach`

`foreach` Instrukcji rozwija na standardowe idiom, która używa `IEnumerable<T>` i `IEnumerator<T>` interfejsów w celu iteracji przez wszystkie elementy kolekcji. Zmniejsza on również błędów, które deweloperzy tworzą przez nie zostało prawidłowo zarządzania zasobami. 

Kompilator tłumaczy `foreach` pokazano w przykładzie pierwszy na podobny do tej konstrukcji pętli:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Konstrukcja powyżej reprezentuje kod wygenerowany przez kompilator języka C# lub nowszym w wersji 5 lub nowszym. Przed w wersji 5 `item` zmienna ma inny zakres:

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Ta zmiana została wprowadzona, ponieważ wcześniej zachowanie może prowadzić do delikatny i trudne do diagnozowanie błędów dotyczących wyrażenia lambda. Zobacz sekcję dotyczącą [wyrażenia lambda](lambda-expressions.md) Aby uzyskać więcej informacji. 

Dokładny kod wygenerowany przez kompilator jest nieco bardziej skomplikowane i obsługuje sytuacje, gdy obiekt jest zwracany przez `GetEnumerator()` implementuje `IDisposable` interfejsu. Pełnym rozszerzeniu generuje kod więcej następująco:

```csharp
{
    var enumerator = collection.GetEnumerator();
    try 
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally 
    {
        // dispose of enumerator.
    }
}
```

Sposób, w której moduł wyliczający jest usuwane jest zależna od właściwości typu `enumerator`. W przypadku ogólnych `finally` klauzuli rozwijany do:

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

Jednak jeśli typ `enumerator` jest zapieczętowanego typu i nie jest niejawna konwersja z typu `enumerator` do `IDisposable`, `finally` klauzuli rozwijany do bloku pusta:
```csharp
finally 
{
} 
```

Jeśli istnieje niejawna konwersja z typu `enumerator` do `IDisposable`, i `enumerator` jest typem wartości niedopuszczającym `finally` klauzuli rozwijany do:

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

Thankfully nie trzeba pamiętać te szczegóły. `foreach` Instrukcji obsługuje te wszystkie szczegóły dla Ciebie. Kompilator wygeneruje prawidłowego kodu dla każdego z tych konstrukcji. 


