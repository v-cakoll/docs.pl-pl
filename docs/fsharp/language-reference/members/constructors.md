---
title: Konstruktory
description: 'Dowiedz się, jak definiować i używać konstruktorów w języku F # do tworzenia i inicjowania obiektów klasy i struktury.'
ms.date: 05/16/2016
ms.openlocfilehash: be8fc3f1d82a9a7c778a6d094139f14150a28813
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303442"
---
# <a name="constructors"></a>Konstruktory

W tym artykule opisano sposób definiowania i używania konstruktorów do tworzenia i inicjowania obiektów klasy i struktury.

## <a name="construction-of-class-objects"></a>Konstrukcja obiektów klasy

Obiekty typów klas mają konstruktory. Istnieją dwa rodzaje konstruktorów. Jeden jest konstruktorem podstawowym, którego parametry są wyświetlane w nawiasach tuż po nazwie typu. Należy określić inne, opcjonalne konstruktory, używając `new` słowa kluczowego. Wszelkie takie dodatkowe konstruktory muszą wywołać Konstruktor podstawowy.

Konstruktor podstawowy zawiera `let` i `do` powiązania, które pojawiają się na początku definicji klasy. `let`Powiązanie deklaruje prywatne pola i metody klasy; `do` powiązanie wykonuje kod. Aby uzyskać więcej informacji na temat `let` powiązań w konstruktorach klas, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md). Aby uzyskać więcej informacji na temat `do` powiązań w konstruktorach, zobacz [ `do` powiązania w klasach](do-bindings-in-classes.md).

Niezależnie od tego, czy Konstruktor, który ma być wywoływany, jest konstruktorem podstawowym, czy dodatkowym konstruktorem, można tworzyć obiekty przy użyciu `new` wyrażenia z lub bez `new` słowa kluczowego Optional. Obiekty są inicjowane razem z argumentami konstruktora, przez wystawienie argumentów w kolejności i oddzielone przecinkami i ujęte w nawiasy, lub za pomocą nazwanych argumentów i wartości w nawiasach. Możesz również ustawić właściwości obiektu podczas konstruowania obiektu, używając nazw właściwości i przypisując wartości tak samo jak w przypadku używania nazwanych argumentów konstruktora.

Poniższy kod ilustruje klasę, która ma Konstruktor i różne sposoby tworzenia obiektów:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Wynik jest następujący:

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Konstrukcja struktur

Struktury są zgodne ze wszystkimi regułami klas. W związku z tym, można mieć konstruktora podstawowego i można dostarczyć dodatkowych konstruktorów przy użyciu `new` . Istnieje jednak jedna ważna różnica między strukturami i klasami: struktury mogą mieć Konstruktor bez parametrów (czyli jeden bez argumentów), nawet jeśli żaden Konstruktor podstawowy nie jest zdefiniowany. Konstruktor bez parametrów inicjuje wszystkie pola do wartości domyślnej dla tego typu, zazwyczaj zero lub jego odpowiednikiem. Wszystkie konstruktory zdefiniowane dla struktur muszą mieć co najmniej jeden argument, aby nie powodowały konfliktów z konstruktorem bez parametrów.

Ponadto struktury często zawierają pola, które są tworzone za pomocą `val` słowa kluczowego; klasy mogą także mieć te pola. Struktury i klasy, które mają pola zdefiniowane za pomocą `val` słowa kluczowego, można również zainicjować w dodatkowych konstruktorach przy użyciu wyrażeń rekordów, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Aby uzyskać więcej informacji, zobacz [pola jawne: `val` słowo kluczowe](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Wykonywanie efektów ubocznych w konstruktorach

Konstruktor podstawowy w klasie może wykonać kod w `do` powiązaniu. Jednak co zrobić, jeśli trzeba wykonać kod w dodatkowym konstruktorze bez `do` powiązania? W tym celu należy użyć `then` słowa kluczowego.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Efekty uboczne konstruktora podstawowego nadal są wykonywane. W związku z tym dane wyjściowe są następujące:

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

Przyczyną tego problemu `then` jest to `do` , że słowo kluczowe jest wymagane, a nie inne, ma `do` swoje standardowe znaczenie dla nieograniczonego `unit` wyrażenia zwracającego wartość, gdy występuje w treści dodatkowego konstruktora. Ma on tylko specjalne znaczenie w kontekście konstruktorów podstawowych.

## <a name="self-identifiers-in-constructors"></a>Identyfikatory własne w konstruktorach

W innych elementach członkowskich należy podać nazwę bieżącego obiektu w definicji każdego elementu członkowskiego. Można również umieścić własny identyfikator w pierwszym wierszu definicji klasy za pomocą `as` słowa kluczowego bezpośrednio po parametrach konstruktora. Poniższy przykład ilustruje tę składnię.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

W dodatkowych konstruktorach można również zdefiniować samodzielny identyfikator, umieszczając `as` klauzulę bezpośrednio po parametrach konstruktora. Poniższy przykład ilustruje następującą składnię:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Problemy mogą wystąpić podczas próby użycia obiektu, zanim zostanie on w pełni zdefiniowany. W związku z tym użycie identyfikatora samodzielnego może spowodować, że kompilator emituje ostrzeżenie i wstawi dodatkowe sprawdzenia, aby upewnić się, że elementy członkowskie obiektu nie są dostępne przed zainicjowaniem obiektu. Samego identyfikatora można używać tylko w `do` powiązaniach konstruktora podstawowego lub po `then` słowie kluczowym w dodatkowych konstruktorach.

Nazwa identyfikatora własnego nie musi być `this` . Może być dowolnym prawidłowym identyfikatorem.

## <a name="assigning-values-to-properties-at-initialization"></a>Przypisywanie wartości do właściwości podczas inicjalizacji

Można przypisać wartości do właściwości obiektu klasy w kodzie inicjalizacji, dołączając listę przypisań formularza `property = value` do listy argumentów konstruktora. Jest to pokazane w poniższym przykładzie kodu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Poniższa wersja poprzedniego kodu ilustruje kombinację zwykłych argumentów, argumentów opcjonalnych i ustawień właściwości w jednym wywołaniu konstruktora:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Konstruktory w dziedziczonej klasie

Podczas dziedziczenia z klasy podstawowej, która ma konstruktora, należy określić jej argumenty w klauzuli Inherits. Aby uzyskać więcej informacji, zobacz [konstruktory i dziedziczenie](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Konstruktory statyczne lub konstruktory typów

Oprócz określania kodu do tworzenia obiektów, statyczne `let` i `do` powiązania mogą być tworzone w typach klas, które wykonują przed pierwszym użyciem typu do wykonania inicjalizacji na poziomie typu. Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md) i [ `do` powiązaniach w klasach](do-bindings-in-classes.md).

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
