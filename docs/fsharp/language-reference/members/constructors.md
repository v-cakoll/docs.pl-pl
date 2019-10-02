---
title: Konstruktorów
description: Dowiedz się, jak definiować i używać F# konstruktorów w programie w celu tworzenia i inicjowania obiektów klasy i struktury.
ms.date: 05/16/2016
ms.openlocfilehash: 6769ec7fc6768090d8ae68e21946a58829b6eea0
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736845"
---
# <a name="constructors"></a>Konstruktorów

W tym artykule opisano sposób definiowania i używania konstruktorów do tworzenia i inicjowania obiektów klasy i struktury.

## <a name="construction-of-class-objects"></a>Konstrukcja obiektów klasy

Obiekty typów klas mają konstruktory. Istnieją dwa rodzaje konstruktorów. Jeden jest konstruktorem podstawowym, którego parametry są wyświetlane w nawiasach tuż po nazwie typu. Należy określić inne, opcjonalne konstruktory za pomocą słowa kluczowego `new`. Wszelkie takie dodatkowe konstruktory muszą wywołać Konstruktor podstawowy.

Konstruktor podstawowy zawiera powiązania `let` i `do`, które pojawiają się na początku definicji klasy. Powiązanie `let` deklaruje prywatne pola i metody klasy; powiązanie `do` wykonuje kod. Aby uzyskać więcej informacji na temat powiązań `let` w konstruktorach klas, zobacz [`let` powiązania w klasach](let-bindings-in-classes.md). Aby uzyskać więcej informacji na temat powiązań `do` w konstruktorach, zobacz [`do` powiązania w klasach](do-bindings-in-classes.md).

Niezależnie od tego, czy Konstruktor, który ma być wywoływany, jest konstruktorem podstawowym, czy dodatkowym konstruktorem, można tworzyć obiekty przy użyciu wyrażenia `new` z lub bez słowa kluczowego Optional `new`. Obiekty są inicjowane razem z argumentami konstruktora, przez wystawienie argumentów w kolejności i oddzielone przecinkami i ujęte w nawiasy, lub za pomocą nazwanych argumentów i wartości w nawiasach. Możesz również ustawić właściwości obiektu podczas konstruowania obiektu, używając nazw właściwości i przypisując wartości tak samo jak w przypadku używania nazwanych argumentów konstruktora.

Poniższy kod ilustruje klasę, która ma Konstruktor i różne sposoby tworzenia obiektów:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Dane wyjściowe są następujące:

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Konstrukcja struktur

Struktury są zgodne ze wszystkimi regułami klas. W związku z tym, można mieć konstruktora podstawowego i można dostarczyć dodatkowych konstruktorów przy użyciu `new`. Istnieje jednak jedna ważna różnica między strukturami i klasami: struktury mogą mieć Konstruktor bez parametrów (czyli jeden bez argumentów), nawet jeśli żaden Konstruktor podstawowy nie jest zdefiniowany. Konstruktor bez parametrów inicjuje wszystkie pola do wartości domyślnej dla tego typu, zazwyczaj zero lub jego odpowiednikiem. Wszystkie konstruktory zdefiniowane dla struktur muszą mieć co najmniej jeden argument, aby nie powodowały konfliktów z konstruktorem bez parametrów.

Ponadto struktury często zawierają pola, które są tworzone za pomocą słowa kluczowego `val`; klasy mogą również mieć te pola. Struktury i klasy, które mają pola zdefiniowane za pomocą słowa kluczowego `val`, można również zainicjować w dodatkowych konstruktorach przy użyciu wyrażeń rekordów, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Aby uzyskać więcej informacji, zobacz [pola jawne: słowo kluczowe `val`](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Wykonywanie efektów ubocznych w konstruktorach

Konstruktor podstawowy w klasie może wykonać kod w powiązaniu `do`. Jednak co zrobić, jeśli trzeba wykonać kod w dodatkowym konstruktorze bez powiązania `do`? W tym celu należy użyć słowa kluczowego `then`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Efekty uboczne konstruktora podstawowego nadal są wykonywane. W związku z tym dane wyjściowe są następujące:

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Identyfikatory własne w konstruktorach

W innych elementach członkowskich należy podać nazwę bieżącego obiektu w definicji każdego elementu członkowskiego. Możesz również umieścić własny identyfikator w pierwszym wierszu definicji klasy, używając słowa kluczowego `as` bezpośrednio po parametrach konstruktora. Poniższy przykład ilustruje tę składnię.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

W dodatkowych konstruktorach można również zdefiniować samodzielny identyfikator, umieszczając klauzulę `as` bezpośrednio po parametrach konstruktora. Poniższy przykład ilustruje następującą składnię:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Problemy mogą wystąpić podczas próby użycia obiektu, zanim zostanie on w pełni zdefiniowany. W związku z tym użycie identyfikatora samodzielnego może spowodować, że kompilator emituje ostrzeżenie i wstawi dodatkowe sprawdzenia, aby upewnić się, że elementy członkowskie obiektu nie są dostępne przed zainicjowaniem obiektu. Samego identyfikatora można używać tylko w powiązaniach `do` konstruktora podstawowego lub po słowie kluczowym `then` w dodatkowych konstruktorach.

Nazwa identyfikatora własnego nie musi być `this`. Może być dowolnym prawidłowym identyfikatorem.

## <a name="assigning-values-to-properties-at-initialization"></a>Przypisywanie wartości do właściwości podczas inicjalizacji

Można przypisać wartości do właściwości obiektu klasy w kodzie inicjującym, dołączając listę przypisań formularza `property = value` do listy argumentów konstruktora. Jest to pokazane w poniższym przykładzie kodu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Poniższa wersja poprzedniego kodu ilustruje kombinację zwykłych argumentów, argumentów opcjonalnych i ustawień właściwości w jednym wywołaniu konstruktora:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Konstruktory w dziedziczonej klasie

Podczas dziedziczenia z klasy podstawowej, która ma konstruktora, należy określić jej argumenty w klauzuli Inherits. Aby uzyskać więcej informacji, zobacz [konstruktory i dziedziczenie](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Konstruktory statyczne lub konstruktory typów

Oprócz określania kodu do tworzenia obiektów, statyczne powiązania `let` i `do` mogą być tworzone w typach klas, które wykonują przed pierwszym użyciem typu do wykonania inicjalizacji na poziomie typu. Aby uzyskać więcej informacji, zobacz [powiązania `let` w klasach](let-bindings-in-classes.md) i [powiązaniach `do` w klasach](do-bindings-in-classes.md).

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
