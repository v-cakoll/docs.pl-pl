---
title: System.Delegate i `delegate` — słowo kluczowe
description: Więcej informacji na temat klas w programie .NET Framework, które obsługują delegatów oraz sposobu mapowania tych — słowo kluczowe "delegowanie".
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 2265d081b884a19cda6fc9d80a0f621a30c87e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate i `delegate` — słowo kluczowe

[Poprzednie](delegates-overview.md)

W tym artykule opisano klas w programie .NET framework, które obsługują delegatów, oraz sposobu te mapowania `delegate` — słowo kluczowe.

## <a name="defining-delegate-types"></a>Definiowanie typów delegata

Zacznijmy pomocą słowa kluczowego "delegowanie", ponieważ jest to przede wszystkim co będzie używać podczas pracy z obiektów delegowanych. Kod generowany przez kompilator, korzystając z `delegate` — słowo kluczowe przypisze do wywołania metody, które wywołują członkami <xref:System.Delegate> i <xref:System.MulticastDelegate> klasy. 

Należy zdefiniować typem obiektu delegowanego przy użyciu składni, która jest podobna do definiowania podpis metody. Możesz dodać `delegate` — słowo kluczowe w definicji.

Przejdź w naszym przykładzie przy użyciu metody List.Sort(). Pierwszym krokiem jest tworzenie typu dla delegata porównania:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Kompilator generuje klasę pochodzącą od `System.Delegate` odpowiadającego podpis używany (w tym przypadku metoda zwraca liczbę całkowitą, która ma dwa argumenty). Ten delegat jest `Comparison`. `Comparison` Typ delegata jest typem ogólnym. Szczegółowe informacje na ogólne można znaleźć [tutaj](generics.md).

Należy zauważyć, że składnia może pojawić się tak, jakby jest deklarowanie zmiennej, ale faktycznie jest deklarowanie *typu*. Można określić typy delegatów wewnątrz klasy, bezpośrednio w przestrzeni nazw, a nawet w globalnej przestrzeni nazw.

> [!NOTE]
> Deklarowanie typów delegata (lub innego typu) bezpośrednio w globalnej przestrzeni nazw nie jest zalecane. 

Kompilator generuje również dodawanie i usuwanie programów obsługi dla tego nowego typu, aby klienci tej klasy można dodać i usunąć z wystąpienia listy wywołania metody. Kompilator będzie wymuszać zgodność podpisu przy deklarowaniu metody podpis metody jest dodany lub usunięty. 

## <a name="declaring-instances-of-delegates"></a>Deklarowanie wystąpień obiektów delegowanych

Po zdefiniowaniu delegata, można utworzyć wystąpienia tego typu.
Podobnie jak wszystkie zmienne w języku C# nie można zadeklarować obiektu delegowanego wystąpień bezpośrednio w przestrzeni nazw lub w globalnej przestrzeni nazw.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Typ zmiennej jest `Comparison<T>`, typ delegata zdefiniowanego wcześniej. Nazwa zmiennej jest `comparator`.
 
 Ten fragment kodu powyżej zadeklarować zmiennej członkowskiej wewnątrz klasy. Można również zadeklarować zmienne delegata, które są zmienne lokalne lub argumenty do metod.

## <a name="invoking-delegates"></a>Wywoływanie delegatów

Wywołuje metody, które się na liście wywołania delegata przez wywołanie tego delegata. Wewnątrz `Sort()` metody kod wywoła metodę porównywania, aby określić kolejność, aby umieścić obiekty:

```csharp
int result = comparator(left, right);
```

W wierszu powyżej kod *wywołuje* metody dołączony do obiektu delegowanego.
Traktuj zmiennej jako nazwę metody, a następnie wywołaj za pomocą składni wywołań metody normalnego.

Ten wiersz kodu założeń niebezpieczny: nie ma żadnej gwarancji, że element docelowy został dodany do delegata. Jeśli nie zostały dołączone nie elementy docelowe, spowodowałoby wiersz powyżej `NullReferenceException` zostanie wygenerowany. Idioms używane w celu rozwiązania tego problemu są bardziej skomplikowane niż proste sprawdzanie wartości null i są uwzględnione w dalszej części tego [serii](delegates-patterns.md).

## <a name="assigning-adding-and-removing-invocation-targets"></a>Przypisywanie, dodawanie i usuwanie celów wywołania

To, jak jest zdefiniowany typ delegata i jak zadeklarowany i wywołać delegata wystąpień.

Deweloperzy, które mają być wykorzystywane `List.Sort()` metody trzeba zdefiniować metody, których Podpis pasuje do definicji typu delegowanego i przypisz je do delegata, używany przez metodę sortowania. To przypisanie dodaje metodę do listy wywołania tego obiektu delegowanego.

Załóżmy, że chcesz sortować listę ciągów ich długość. Porównanie funkcji mogą być następujące:

```csharp
private static int CompareLength(string left, string right)
{
    return left.Length.CompareTo(right.Length);
}
```

Metoda jest zadeklarowany jako metoda prywatna. Się. Nie można tej metody jako część publicznego interfejsu. Może nadal służyć jako metodę porównywania po podłączeniu do delegata. Kod wywołujący będą mieli tej metody dołączony do listy docelowej obiektu delegowanego i można do niego dostęp za pośrednictwem tego delegata.

Przez przekazanie tej metody do tworzenia relacji `List.Sort()` metody:

```csharp
phrases.Sort(CompareLength);
```

Zwróć uwagę, że używana jest nazwa metody bez nawiasów. Przy użyciu metody jako argument informuje kompilator, aby przekonwertować odwołania do metody odwołanie, które mogą być używane jako element docelowy wywołania delegata i Dołącz tej metody jako obiekt docelowy wywołania.

Możesz również mogło być jawne przez deklarowanie zmiennej typu "porównanie<string>" i wykonując przypisania:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

W zastosowaniach, gdzie metodę używany jako cel delegata to mały metoda jest często stosowanym rozwiązaniem użyj [wyrażenia Lambda](lambda-expressions.md) składni w celu przypisania:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Dla celów delegata za pomocą wyrażenia Lambda jest objęte bardziej [później sekcji](delegates-patterns.md).

W przykładzie Sort() zazwyczaj dołącza metody pojedynczym elementem docelowym delegata. Jednak obiektów delegata obsługuje listy wywołania, które mają wiele metod docelowych dołączony do obiektu delegowanego.

## <a name="delegate-and-multicastdelegate-classes"></a>Delegat i MulticastDelegate klas

Obsługa języków opisane powyżej udostępnia funkcje i pomocy technicznej, które zwykle będą potrzebne do pracy z obiektów delegowanych. Te funkcje są wbudowane w dwóch klas w ramach platformy .NET Core: <xref:System.Delegate> i <xref:System.MulticastDelegate>.

`System.Delegate` Klasy i jego bezpośrednich jednej klasy podrzędne, `System.MulticastDelegate`, zapewniają obsługę framework do tworzenia delegatów, rejestrowanie metod jako miejsca docelowe delegata i wywoływanie wszystkie metody, które są zarejestrowane jako cel delegata. 

Interesujące jest, że `System.Delegate` i `System.MulticastDelegate` klasy nie są samych typów delegatów. Udostępniają one podstawę dla wszystkich typów określonego delegata. Czy samej konstrukcji języka procesu obowiązkowe, że nie można zadeklarować klasy, która pochodzi z `Delegate` lub `MulticastDelegate`. Reguły języka C# zabronić jego używania.
 
Zamiast tego kompilatora C# tworzy wystąpienia klasy pochodzącej od `MulticastDelegate` przy deklarować typów delegowanych za pomocą słowa kluczowego języka C#.

Ten projekt nie ma jej katalogów głównych w pierwszej wersji programu C# i .NET. Celem jednego zespołu projektu był aby upewnić się, że język używanie delegatów, wymuszone zabezpieczenie typów. Która przeznaczone zapewnienie, że delegatów zostały wywołana z prawidłowym typem i liczby argumentów. Czas kompilacji i że dowolnego typu zwracanego poprawnie wskazano w. Obiekty delegowane były częścią wersji .NET 1.0, która została przed ogólne.

Najlepszym sposobem na wymuszenie bezpieczeństwa tego typu był przeznaczony dla kompilatora, aby utworzyć konkretnego obiektu delegowanego klasy, które reprezentowane podpis metody jest używany.

Mimo że nie można utworzyć klasy pochodne bezpośrednio, używasz metody zdefiniowane na tych klas. Przejdź przez najbardziej typowe metody, które będą używane podczas pracy z obiektów delegowanych.

Po pierwsze, najważniejsze do zapamiętania to czy jest pochodną co delegata pracować z `MulticastDelegate`. Delegat multiemisji oznacza, że więcej niż jeden cel metoda może być wywoływana podczas wywoływania za pośrednictwem pełnomocnika. Oryginalny projekt uznawane za różnice między delegatów, gdzie można podłączony i wywołać metody tylko jeden obiekt docelowy i delegatów, gdzie można dołączyć i wywołać wielu metod docelowych. Różnica w tym okazały się mniej użyteczny w praktyce niż pierwotnie traktować. Dwoma różnymi klasami zostały już utworzone, a zostały w ramach początkowego wydania publicznych.

Metody, które będą używane najczęściej z delegatów są `Invoke()` i `BeginInvoke()`  /  `EndInvoke()`. `Invoke()` wywoła wszystkie metody, które zostały dołączone do wystąpienia określonego delegata. Jak przedstawiono powyżej, zazwyczaj należy wywołać delegatów za pomocą składni wywołań metody zmiennej obiektu delegowanego. Jak można zauważyć [dalej w tej serii](delegates-patterns.md), istnieją wzorców, które współpracują bezpośrednio z tych metod.

Skoro już znasz składni języka i klas, które obsługują delegatów Przeanalizujmy jak jednoznacznie delegatów są używane, tworzone i wywoływane.

[Next](delegates-strongly-typed.md)
