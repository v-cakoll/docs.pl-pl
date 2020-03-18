---
title: System.Delegate i `delegate` słowo kluczowe
description: Dowiedz się więcej o klasach w .NET, które obsługują delegatów i jak te mapy do "delegata" słowa kluczowego.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 87fdf19c4ea810c5ac4409fe16c3cba9d5fc6574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146284"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate i `delegate` słowo kluczowe

[Wstecz](delegates-overview.md)

W tym artykule omówiono klasy w .NET, które `delegate` obsługują delegatów i jak te mapy do słowa kluczowego.

## <a name="define-delegate-types"></a>Definiowanie typów pełnomocników

Zacznijmy od słowa kluczowego "delegować", ponieważ jest to przede wszystkim to, co będzie używane podczas pracy z delegatami. Kod, który kompilator generuje `delegate` podczas korzystania ze słowa kluczowego zostanie <xref:System.Delegate> <xref:System.MulticastDelegate> mapowany do wywołania metody, które wywołają członków i klas.

Typ delegata można zdefiniować przy użyciu składni, która jest podobna do definiowania podpisu metody. Wystarczy dodać `delegate` słowo kluczowe do definicji.

Użyjmy metody List.Sort() jako naszego przykładu. Pierwszym krokiem jest utworzenie typu dla delegata porównania:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Kompilator generuje klasę, wywodzącą się z `System.Delegate` tej zgodności z użytą sygnaturą (w tym przypadku metodę, która zwraca wartość całkowitą i ma dwa argumenty). Typem tego pełnomocnika `Comparison`jest . Typ `Comparison` delegata jest typem ogólnym. Szczegółowe informacje na temat leków generycznych można znaleźć [tutaj](programming-guide/generics/index.md).

Należy zauważyć, że składnia może wyglądać tak, jakby deklaruje zmienną, ale w rzeczywistości deklaruje *typ*. Można zdefiniować typy delegatów wewnątrz klas, bezpośrednio wewnątrz obszarów nazw, a nawet w globalnej przestrzeni nazw.

> [!NOTE]
> Deklarowanie typów delegatów (lub innych typów) bezpośrednio w globalnej przestrzeni nazw nie jest zalecane.

Kompilator generuje również dodawanie i usuwanie programów obsługi dla tego nowego typu, dzięki czemu klienci tej klasy można dodawać i usuwać metody z listy wywołania wystąpienia. Kompilator wymusi, że podpis dodawanej lub usuwanej metody jest zgodny z podpisem używanym podczas deklarowania metody.

## <a name="declare-instances-of-delegates"></a>Deklarowanie wystąpień delegatów

Po zdefiniowaniu pełnomocnika można utworzyć wystąpienie tego typu.
Podobnie jak wszystkie zmienne w języku C#, nie można zadeklarować wystąpień delegata bezpośrednio w obszarze nazw lub w globalnej przestrzeni nazw.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Typ zmiennej to `Comparison<T>`typ delegata zdefiniowany wcześniej. Nazwa zmiennej to `comparator`.

 Ten fragment kodu powyżej zadeklarowane zmiennej składowej wewnątrz klasy. Można również zadeklarować zmienne delegata, które są zmiennymi lokalnymi lub argumentami do metod.

## <a name="invoke-delegates"></a>Wywoływanie delegatów

Można wywołać metody, które znajdują się na liście wywołania delegata, wywołując tego delegata. Wewnątrz `Sort()` metody kod wywoła metodę porównania, aby określić, która kolejność umieszczać obiekty:

```csharp
int result = comparator(left, right);
```

W wierszu powyżej kod *wywołuje* metodę dołączony do delegata.
Zmienną należy traktować jako nazwę metody i wywołać ją przy użyciu składni wywołania metody normalnej.

Ten wiersz kodu sprawia, że niebezpieczne założenie: Nie ma żadnej gwarancji, że obiekt docelowy został dodany do delegata. Jeśli nie zostały dołączone żadne cele, `NullReferenceException` powyższa linia spowoduje wyrzucenie. Idiomy używane do rozwiązania tego problemu są bardziej skomplikowane niż proste sprawdzanie wartości null i są omówione w [dalszej](delegates-patterns.md)części tej serii .

## <a name="assign-add-and-remove-invocation-targets"></a>Przypisywanie, dodawanie i usuwanie celów wywołania

W ten sposób typ delegata jest zdefiniowany i jak są deklarowane i wywoływane wystąpienia delegata.

Deweloperzy, którzy `List.Sort()` chcą użyć metody należy zdefiniować metodę, której podpis pasuje do definicji typu delegata i przypisać go do delegata używanego przez metodę sortowania. To przypisanie dodaje metodę do listy wywołania tego obiektu delegata.

Załóżmy, że chcesz posortować listę ciągów według ich długości. Funkcja porównywania może być następująca:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Metoda jest zadeklarowana jako metoda prywatna. To dobrze. Ta metoda może nie być częścią interfejsu publicznego. Nadal może służyć jako metoda porównania po dołączeniu do delegata. Kod wywołujący będzie miał tę metodę dołączony do listy docelowej obiektu delegata i można uzyskać do niego dostęp za pośrednictwem tego pełnomocnika.

Tę relację tworzymy, przekazując tę metodę do `List.Sort()` metody:

```csharp
phrases.Sort(CompareLength);
```

Należy zauważyć, że nazwa metody jest używana, bez nawiasów. Za pomocą metody jako argument informuje kompilator do konwersji odwołania do metody do odwołania, które mogą być używane jako obiekt docelowy wywołania delegata i dołączyć tę metodę jako miejsce docelowe wywołania.

Można również jawne, deklarując zmienną `Comparison<string>` typu i wykonując przypisanie:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

W zastosowaniach, w których metoda używana jako obiekt docelowy delegata jest małą metodą, często używa się składni [wyrażenia lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) do wykonywania przypisania:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Za pomocą wyrażeń lambda dla obiektów docelowych delegata jest omówiona bardziej w [dalszej sekcji](delegates-patterns.md).

Przykład Sort() zazwyczaj dołącza jedną metodę docelową do delegata. Jednak delegować obiekty obsługują listy wywołań, które mają wiele metod docelowych dołączonych do obiektu delegata.

## <a name="delegate-and-multicastdelegate-classes"></a>Delegowanie i MulticastDelegate klasy

Obsługa języka opisana powyżej zapewnia funkcje i wsparcie, które zazwyczaj będą potrzebne do pracy z pełnomocnikami. Te funkcje są zbudowane na dwóch klasach <xref:System.Delegate> <xref:System.MulticastDelegate>w ramach .NET Core: i .

Klasa `System.Delegate` i jej pojedynczej `System.MulticastDelegate`bezpośredniej podklasy, zapewniają wsparcie framework do tworzenia delegatów, rejestrowanie metod jako delegat obiektów docelowych i wywoływania wszystkich metod, które są zarejestrowane jako miejsce docelowe delegata.

Co ciekawe, `System.Delegate` `System.MulticastDelegate` i klasy nie są same typy delegatów. Stanowią one podstawę dla wszystkich określonych typów delegatów. Ten sam proces projektowania języka upoważnił, że `Delegate` nie `MulticastDelegate`można zadeklarować klasy, która pochodzi od lub . Reguły języka Języka C# go zabronić.

Zamiast tego kompilator C# tworzy wystąpienia `MulticastDelegate` klasy pochodzące z podczas używania języka C# — słowo kluczowe do deklarowania typów delegatów.

Ten projekt ma swoje korzenie w pierwszej wersji C# i .NET. Jednym z celów dla zespołu projektowego było zapewnienie, że język wymuszał bezpieczeństwo typów podczas korzystania z delegatów. Oznaczało to zapewnienie, że delegaci zostali powołani z odpowiednim typem i liczbą argumentów. I, że każdy typ zwracany został poprawnie wskazany w czasie kompilacji. Delegaci byli częścią wersji .NET 1.0, która była przed generykami.

Najlepszym sposobem, aby wymusić bezpieczeństwo tego typu było dla kompilatora, aby utworzyć konkretne klasy delegata, który reprezentował podpis metody używane.

Nawet jeśli nie można utworzyć klas pochodnych bezpośrednio, będzie używać metod zdefiniowanych w tych klasach. Przejdźmy przez najbardziej typowe metody, które będą używane podczas pracy z delegatów.

Pierwszym, najważniejszym faktem do zapamiętania jest to, że `MulticastDelegate`każdy delegat, z którym pracujesz, pochodzi od . Delegat multiemisji oznacza, że podczas wywoływania za pośrednictwem pełnomocnika można wywołać więcej niż jeden obiekt docelowy metody. Oryginalny projekt rozważadokonywanie rozróżnienia między delegatów, gdzie można dołączyć i wywołać tylko jedną metodę docelową, a delegatów, gdzie wiele metod docelowych można dołączyć i wywołać. Rozróżnienie to okazało się mniej użyteczne w praktyce niż początkowo sądzono. Dwie różne klasy zostały już utworzone i zostały w ramach od jego pierwszego publicznego wydania.

Metody, które będą używane najbardziej z `Invoke()` `BeginInvoke()`  /  `EndInvoke()`delegatów są i . `Invoke()`wywoła wszystkie metody, które zostały dołączone do wystąpienia określonego delegata. Jak widać powyżej, zazwyczaj wywołać delegatów przy użyciu składni wywołania metody na zmiennej delegata. Jak zobaczysz [w dalszej części tej serii,](delegates-patterns.md)istnieją wzorce, które działają bezpośrednio z tymi metodami.

Teraz, gdy widzieliście składnię języka i klas, które obsługują delegatów, zbadajmy, jak silnie typowane delegatów są używane, tworzone i wywoływane.

[Dalej](delegates-strongly-typed.md)
