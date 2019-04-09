---
title: Iteratory
description: Dowiedz się, jak używać wbudowanych C# Iteratory oraz jak tworzyć swoje własne metody iteratora niestandardowych.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: f1be4e9a8b67f0e71615c730af4316253224b888
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155223"
---
# <a name="iterators"></a>Iteratory

Prawie każdy program, który napiszesz będzie miał pewne konieczność iteracji po kolekcji. Napiszesz kod, który sprawdza, czy każdy element w kolekcji. 

Utworzysz też metody iteratora, które są metodami, które tworzy iterator dla elementów tej klasy. Mogą one być używane dla:

+ Wykonując akcję dla każdego elementu w kolekcji.
+ Wyliczanie kolekcji niestandardowej.
+ Rozszerzanie [LINQ](linq/index.md) lub inne biblioteki.
+ Tworzenie potoku danych, gdzie dane przepływają efektywnie za pośrednictwem metody iteratora.

C# Język oferuje funkcje dla obu tych scenariuszy. Ten artykuł zawiera omówienie tych funkcji.

W tym samouczku składa się z wielu kroków. Po każdym kroku możesz uruchomić aplikację i wyświetlić postęp. Możesz również [wyświetlanie lub Pobieranie ukończone przykładowe](https://github.com/dotnet/samples/blob/master/csharp/iterators) w tym temacie. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Iterowanie za pomocą instrukcji foreach

Wyliczanie kolekcji jest prosty: `foreach` — Słowo kluczowe wylicza kolekcji, wykonywania osadzona instrukcja jeden raz dla każdego elementu w kolekcji:
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

To wszystko jest do niego. Iterowanie cała zawartość kolekcji, `foreach` instrukcja to wszystko, czego potrzebujesz. `foreach` Instrukcja nie jest magic, mimo że. Opiera się na dwóch interfejsach ogólnych zdefiniowane w bibliotece programu .NET core w celu wygenerowania kodu niezbędne do iteracji kolekcji: `IEnumerable<T>` i `IEnumerator<T>`. Ten mechanizm jest opisano szczegółowo poniżej.

Oba te interfejsy mają również odpowiedniki nieogólnego: `IEnumerable` i `IEnumerator`. [Ogólny](programming-guide/generics/index.md) wersje są preferowane dla nowoczesnego kodu.

## <a name="enumeration-sources-with-iterator-methods"></a>Wyliczenie źródeł za pomocą metody iteratora

Kolejną atrakcyjną funkcją C# języka umożliwia tworzenie metody tworzące źródła dla wyliczenia. Są one określane jako *metody iteracyjne*. Metoda iteratora jest definiuje sposób generowania obiekty w kolejności, w przypadku żądania. Możesz użyć `yield return` kontekstowymi słowami kluczowymi, aby zdefiniować metodę iteratora. 

Można zapisać tę metodę, aby utworzyć sekwencję liczb całkowitych z zakresu od 0 do 9:

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

Powyższy kod przedstawia różne `yield return` instrukcji, aby wyróżnić faktów, których można używać wielu dyskretnych `yield return` instrukcji w metodzie iteratora.
Można (i często tak robią) korzystanie z innych konstrukcji językowych w celu uproszczenia kodu metody iteratora. Poniżej definicję metody generuje dokładnie tej samej sekwencji liczb:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

Nie trzeba zdecydować z jednej z nich. Masz tyle `yield return` instrukcji, co jest niezbędne do potrzeb Twojej formy:

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

To podstawowa składnia. Rozważmy przykład rzeczywistych, w którym należy napisać metodę iteratora. Wyobraź sobie, możesz teraz projektu IoT i czujników urządzenia generować bardzo duże strumienia danych. Aby można było uzyskać pewne pojęcie dla danych, można napisać metodę, która pobiera próbki każdy element danych n-ty. Ta metoda iteratora małych wykonuje lewy:

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

Istnieje jeden ważne ograniczenia metody iteracyjne: nie może posiadać równocześnie `return` instrukcji i `yield return` instrukcji w tej samej metody. Następujące nie zostanie skompilowany:

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

To ograniczenie jest zwykle problemem. Masz do wyboru przy użyciu `yield return` w całej metody lub rozdzielając oryginalnej metody na wiele sposobów, za pomocą niektórych `return`, a niektóre przy użyciu `yield return`.

Możesz zmodyfikować ostatnie metoda nieco `yield return` wszędzie:

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
 
Czasami prawidłowej odpowiedzi jest podzielić metodę iteratora na dwa sposoby. Jedną, która używa `return`oraz drugiego, który używa `yield return`. Rozważmy sytuację, w których warto zwrócić pustą kolekcję lub 5 pierwszych liczby nieparzyste, w oparciu o argument logiczny. Można napisać, jako tych dwóch metod:

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
 
Spójrz na powyższych metod. Pierwszy używa standardowych `return` instrukcji, aby zwrócić pustą kolekcję lub iteratora, tworzone przez metodę drugiego. W drugiej metodzie `yield return` instrukcję, aby utworzyć żądany sekwencji.

## <a name="deeper-dive-into-foreach"></a>Bardziej zgłębić temat do `foreach`

`foreach` Instrukcji rozwija się na standardowych idiom, który używa `IEnumerable<T>` i `IEnumerator<T>` interfejsy do iteracji dla wszystkich elementów w kolekcji. Minimalizuje błędy, które deweloperzy mogą stosować przez nie został poprawnie zarządzanie zasobami. 

Kompilator tłumaczy `foreach` pętli wyświetlane w pierwszym przykładzie w sposób podobny do tej konstrukcji:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Konstrukcja powyżej reprezentuje kod wygenerowany przez C# kompilatora, począwszy od wersji 5 lub nowszym. Przed wersją 5 `item` zmienna ma inny zakres:

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

Ta zmiana została wprowadzona, ponieważ wcześniej zachowanie może prowadzić do subtelnym, trudno Diagnozuj błędy dotyczące wyrażeń lambda. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md).

Dokładne kod wygenerowany przez kompilator jest nieco bardziej skomplikowane i obsługuje sytuacje, gdy obiekt jest zwracany przez `GetEnumerator()` implementuje `IDisposable` interfejsu. Pełnym rozszerzeniu generuje kod więcej następująco:

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

Sposób, w którym moduł wyliczający jest usunięty zależy cechy typu `enumerator`. W przypadku ogólnych `finally` klauzula jest rozszerzany, aby:

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

Jednak jeśli typ `enumerator` jest typie zapieczętowanym i istnieje niejawna konwersja z typu `enumerator` do `IDisposable`, `finally` klauzuli rozwija do pustego bloku:
```csharp
finally 
{
} 
```

Jeśli istnieje niejawna konwersja z typu `enumerator` do `IDisposable`, i `enumerator` jest typem wartości niedopuszczającym wartości `finally` klauzula jest rozszerzany, aby:

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

Szczęście nie trzeba pamiętać te szczegóły. `foreach` Instrukcja obsługuje te szczegóły skutecznego dla Ciebie. Kompilator wygeneruje poprawny kod dla każdej z tych konstrukcji. 
