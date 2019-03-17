---
title: System.Delegate i `delegate` — słowo kluczowe
description: Więcej informacji na temat klas .NET Framework, które obsługują delegatów oraz sposób mapowania tych — słowo kluczowe "delegowanie".
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 88179af0ac072464d8e9903f685ff578ca591bf0
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126178"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate i `delegate` — słowo kluczowe

[Poprzednie](delegates-overview.md)

W tym artykule omówiono klasy w .NET framework, które obsługuje delegatów oraz jak te mapowania `delegate` — słowo kluczowe.

## <a name="defining-delegate-types"></a>Definiowanie typów delegowanych

Zacznijmy od słowa kluczowego "delegowanie", ponieważ jest to głównie będzie on potrzebny podczas pracy nad delegatów. Kod, który kompilator generuje, gdy używasz `delegate` — słowo kluczowe będzie zmapowana do wywołania metody, które wywołują członkowie <xref:System.Delegate> i <xref:System.MulticastDelegate> klasy. 

Należy zdefiniować typ obiektu delegowanego przy użyciu składni, która jest podobna do definiowania podpis metody. Wystarczy dodać `delegate` — słowo kluczowe w definicji.

Możemy w dalszym użycie metody List.Sort() jako przykładu. Pierwszym krokiem jest tworzenie typu dla delegata porównania:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Kompilator generuje klasę pochodną `System.Delegate` które odpowiadają podpisowi używane (w tym przypadku metoda zwraca liczbę całkowitą, która ma dwa argumenty). Typ delegata jest `Comparison`. `Comparison` Typ delegata jest typem ogólnym. Zobacz szczegółowe informacje na temat typów ogólnych [tutaj](generics.md).

Należy zauważyć, że składnia może pojawić się tak, jakby on jest zadeklarowanie zmiennej, ale jest faktycznie deklarowanie *typu*. Można zdefiniować typy delegatów wewnątrz klasy, bezpośrednio w przestrzeni nazw albo nawet w globalnej przestrzeni nazw.

> [!NOTE]
> Deklarowanie typów delegatów (lub inne typy) bezpośrednio w globalnej przestrzeni nazw nie jest zalecane. 

Kompilator generuje również dodawanie i usuwanie programów obsługi dla tego nowego typu, aby klienci tej klasy można dodawać i usuwać metody z wystąpieniem listy wywołań. Kompilator będzie wymuszać, czy podpis metody dodawany lub usuwany pasuje do podpisu przy deklarowaniu metody. 

## <a name="declaring-instances-of-delegates"></a>Deklarowanie wystąpień obiektów delegowanych

Po zdefiniowaniu obiektu delegowanego, można utworzyć wystąpienia tego typu.
Wszystkie zmienne w, takich jak C#, nie można zadeklarować wystąpień delegata bezpośrednio w przestrzeni nazw lub w globalnej przestrzeni nazw.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Typ zmiennej jest `Comparison<T>`, wcześniej zdefiniowaną typ delegata. Nazwa zmiennej jest `comparator`.
 
 Ten fragment kodu powyżej zadeklarować zmienną członkowską wewnątrz klasy. Można również zadeklarować zmienne delegata, które są zmiennymi lokalnymi lub argumenty do metody.

## <a name="invoking-delegates"></a>Wywoływanie delegatów

Można wywołać metody, które znajdują się na liście wywołanie delegata, przez wywołanie metody delegata. Wewnątrz `Sort()` metody kod wywoła metodę porównywania, aby określić kolejność, aby umieścić obiekty:

```csharp
int result = comparator(left, right);
```

W wierszu powyżej kod *wywołuje* metody dołączony do obiektu delegowanego.
Traktuj zmiennej jako nazwę metody i wywoływać ją za pomocą składni wywołania metody normalne.

Ten wiersz kodu sprawia, że niebezpieczne założeń: Nie ma żadnej gwarancji, że element docelowy został dodany do delegata. Jeśli dołączono żadnych elementów docelowych, spowodowałoby wiersz powyżej `NullReferenceException` zostanie wygenerowany. Idiomy używane, aby rozwiązać ten problem, są bardziej skomplikowane niż proste sprawdzanie wartości null i są objęte później w tym [serii](delegates-patterns.md).

## <a name="assigning-adding-and-removing-invocation-targets"></a>Przypisywanie, dodawanie i usuwanie celów wywołania

To, jak jest zdefiniowany typ obiektu delegowanego i jak zadeklarować i wywołana wystąpień delegata.

Deweloperzy, które mają być używane `List.Sort()` metody należy zdefiniować metodę, którego podpis pasuje do definicji typu delegowanego i przypisz je do delegata używany przez metodę sortowania. To przypisanie dodaje metodę do listy wywołań obiektu delegowanego.

Załóżmy, że chcesz sortować listę ciągów według ich długości. Porównanie funkcji mogą być następujące:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Metoda jest zadeklarowany jako metoda prywatna. Jest dobrym rozwiązaniem. Może nie chcieć tę metodę, aby być częścią interfejsu publicznego. Nadal można ją jako metodę porównywania, gdy dołączony do delegata. Kod wywołujący ma mieć ta metoda dołączone do listy docelowej obiektu delegowanego i można uzyskać do niego dostęp za pośrednictwem delegata.

Tworzenie tej relacji, przekazując tej metody do `List.Sort()` metody:

```csharp
phrases.Sort(CompareLength);
```

Należy zauważyć, że nazwa metody jest używana, bez nawiasów. Przy użyciu metody jako argument informuje kompilator, aby konwertować odwołanie do metody odwołania, który może służyć jako cel wywołania delegata, a następnie Dołącz tę metodę jako obiekt docelowy wywołania.

Możesz również mogło być jawne przez zadeklarowanie zmiennej typu "porównanie<string>" i wykonując przypisania:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

W którym metoda używany jako cel delegata to metoda małe, jest często używa się używa [wyrażenia lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) składni w celu przypisania:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Użycie wyrażeń lambda, obiektów docelowych delegata jest bardziej omówione w [później sekcji](delegates-patterns.md).

W przykładzie Sort() zazwyczaj dołącza metoda pojedynczy element docelowy do delegata. Jednak obiekty delegata obsługują listy wywołania, które mają wiele metod docelowych dołączony do obiektu delegowanego.

## <a name="delegate-and-multicastdelegate-classes"></a>Klasy delegata i MulticastDelegate

Obsługa języków opisanych powyżej udostępnia funkcje i pomocy technicznej, które zwykle będą potrzebne do pracy z delegatów. Te funkcje są oparte na dwóch klas w ramach platformy .NET Core: <xref:System.Delegate> i <xref:System.MulticastDelegate>.

`System.Delegate` Klasy, a jego pojedynczego bezpośrednich podrzędnych, `System.MulticastDelegate`, zapewniają obsługę framework do tworzenia delegatów, rejestrowanie metod jako elementy docelowe delegowanego i wywołanie wszystkie metody, które są zarejestrowane jako cel delegata. 

Co ciekawe `System.Delegate` i `System.MulticastDelegate` klasy nie są same typy delegatów. Zapewniają one podstawę dla wszystkich typów określonego delegata. Czy ten sam projekt języka procesu obowiązkowe na to, że nie można zadeklarować klasy, który pochodzi z `Delegate` lub `MulticastDelegate`. C# Reguł języka zabronić jego używania.
 
Zamiast tego C# kompilator tworzy wystąpienia klasy pochodzącej od `MulticastDelegate` zastosowania C# języka — słowo kluczowe do deklarowania typów obiektów delegowanych.

Ten projekt zawiera korzenie jego pierwszego wydania C# i .NET. Jeden cel dla zespołu projektu było upewnij się, że język przy użyciu delegatów, wymuszane bezpieczeństwo typów. Oznaczało to zapewnienie, że delegaty została wywołana przy użyciu właściwego typu i liczby argumentów. Czas kompilacji i że zwracany typ any został poprawnie wskazane w. Delegaty były częścią wersji .NET 1.0, który był wcześniej typów ogólnych.

Najlepszym sposobem, aby wymusić bezpieczeństwa tego typu był przez kompilator, aby utworzyć delegata konkretnych klas, które są reprezentowane podpis metody używane.

Mimo że nie można bezpośrednio utworzyć klasy pochodne, użyjesz metody zdefiniowane w ramach tych zajęć. Przejdźmy przez najbardziej typowe metody, które będą używane podczas pracy z delegatów.

Fakt pierwszym, najważniejszym do zapamiętania jest, że każdy delegat pracujesz z jest tworzony na podstawie `MulticastDelegate`. Delegat multiemisji oznacza, że więcej niż jeden cel metoda może być wywoływany podczas wywoływania przez delegata. Oryginalny projekt jest traktowany jako, różnice między delegatów, gdzie można dołączonych i wywołana metoda tylko jednego obiektu docelowego i delegatów, gdzie można dołączyć i wywołana wielu metod docelowych. Różnica w tym okazało się być mniej przydatne w praktyce niż pierwotnie traktować. Dwoma różnymi klasami zostały już utworzone i zostały w ramach początkowego wydania publicznych.

Metody, które będą używane najczęściej z delegatów są `Invoke()` i `BeginInvoke()`  /  `EndInvoke()`. `Invoke()` wywoła wszystkie metody, które zostały dołączone do wystąpienia konkretnej pełnomocnika. Jak przedstawiono powyżej, zazwyczaj należy wywołać delegatów za pomocą składni wywołania metody na zmiennej delegata. Jak zobaczysz [dalej w tej serii](delegates-patterns.md), istnieją wzorców, które pracują bezpośrednio z tych metod.

Teraz, gdy wiesz, składni języka i klas, które obsługują delegatów, Przeanalizujmy jak silnie typizowanych obiektów delegowanych są używane, utworzona i wywoływane.

[Next](delegates-strongly-typed.md)
