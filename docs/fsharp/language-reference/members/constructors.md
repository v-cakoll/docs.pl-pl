---
title: Konstruktorzy (F#)
description: "Dowiedz się, jak zdefiniować i użyć konstruktorów w języku F # do tworzenia i inicjowania klasy i struktury obiektów."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e0da2250-29de-4145-a1be-e5faff080759
ms.openlocfilehash: 60ed93f1c1dc15e99465d969c9e4fd3e61c28ffa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="constructors"></a>Konstruktorów

W tym temacie opisano sposób definiowania i konstruktory umożliwia tworzenie i Inicjowanie obiektów klasy i struktury.


## <a name="construction-of-class-objects"></a>Konstrukcja obiektów klasy
Obiekty typu klasy mieć konstruktorów. Istnieją dwa rodzaje konstruktorów. Jedna jest podstawowego konstruktora, którego parametry są wyświetlane w nawiasach zaraz po nazwie typu. Określ inne, opcjonalne dodatkowe konstruktorów przy użyciu `new` — słowo kluczowe. Wszelkie dodatkowe konstruktorów należy wywołać konstruktora podstawowego.

Zawiera podstawowego konstruktora `let` i `do` powiązania, które pojawiają się na początku definicji klasy. A `let` powiązanie deklaruje pól prywatnych i metod klasy; `do` powiązania wykonuje kod. Aby uzyskać więcej informacji na temat `let` powiązania konstruktorów klas, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md). Aby uzyskać więcej informacji na temat `do` powiązania w konstruktorach, zobacz [ `do` powiązania w klasach](do-bindings-in-classes.md).

Niezależnie od tego, czy chcesz wywołać konstruktora podstawowego konstruktora lub konstruktora dodatkowe, można tworzyć obiektów przy użyciu `new` wyrażenia, lub bez opcjonalny `new` — słowo kluczowe. Inicjowanie obiektów wraz z argumentów konstruktora przez listę argumentów w kolejności i oddzielone przecinkami i ujęte w nawiasy lub przy użyciu argumentów nazwanych i wartości w nawiasach. Można również ustawiać właściwości obiektu podczas konstruowania obiektu przy użyciu nazw właściwości i przypisywanie wartości, tak samo, jak używasz nazwane argumenty konstruktora.

Poniższy kod przedstawia klasę, która ma Konstruktor i różne sposoby tworzenia obiektów.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Dane wyjściowe są następujące:

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Konstrukcja struktury
Struktury wykonaj wszystkie reguły klas. W związku z tym może mieć podstawowego konstruktora i możesz podać dodatkowe konstruktorów przy użyciu `new`. Istnieje jednak jedną istotną różnicą między struktury i klasy: struktury może mieć konstruktora domyślnego (tzn bez argumentów), nawet jeśli żaden konstruktor podstawowy jest zdefiniowany. Konstruktor domyślny inicjuje wszystkie pola na wartość domyślną dla tego typu, zazwyczaj zero lub jego odpowiednik. Wszystkie konstruktory zdefiniowane dla struktury musi mieć co najmniej jednego argumentu, tak aby nie powodują konfliktów z konstruktora domyślnego.

Ponadto struktury często mają pola, które są tworzone za pomocą `val` — słowo kluczowe; klas ma także te pola. Struktury i klasy, które są zdefiniowane przy użyciu pola `val` — słowo kluczowe również można zainicjować w konstruktorach dodatkowe przy użyciu wyrażenia rekordów, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Aby uzyskać więcej informacji, zobacz [pola jawne: `val` — słowo kluczowe](explicit-fields-the-val-keyword.md).


## <a name="executing-side-effects-in-constructors"></a>Wykonywanie efekty uboczne w konstruktorach
Podstawowy Konstruktor w klasie może uruchomić kod w `do` powiązania. Niemniej jednak, co zrobić, jeśli należy wykonać kod w dodatkowych konstruktora bez `do` powiązanie? Aby to zrobić, należy użyć `then` — słowo kluczowe.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Efekty uboczne podstawowego konstruktora nadal wykonywać. W związku z tym dane wyjściowe ma następującą składnię.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Samoidentyfikatory w konstruktorach
W innych elementach członkowskich należy podać nazwę dla bieżącego obiektu w definicji dla każdego elementu członkowskiego. Można również wprowadzić własnego identyfikatora w pierwszym wierszu definicji klasy, za pomocą `as` — słowo kluczowe bezpośrednio po parametrami konstruktora. Poniższy przykład przedstawia tej składni.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

W konstruktorach dodatkowe istnieje także możliwość zdefiniowania własnego identyfikatora ustawiając `as` klauzuli bezpośrednio po parametrami konstruktora. Poniższy przykład przedstawia tej składni.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Podczas próby użycia obiektu przed jest całkowicie zdefiniowane, mogą wystąpić problemy. W związku z tym używa własnego identyfikatora może spowodować kompilator, aby emitować ostrzeżenie i Wstaw dodatkowe kontrole w celu zapewnienia, że elementów członkowskich obiektu nie są dostępne, przed zainicjowaniem obiektu. Należy używać tylko własnego identyfikatora w `do` powiązania podstawowego konstruktora lub po `then` — słowo kluczowe w dodatkowych konstruktorów.

Nazwę własnego identyfikatora nie ma być `this`. Może to być dowolny poprawny identyfikator.


## <a name="assigning-values-to-properties-at-initialization"></a>Przypisywanie wartości do właściwości podczas inicjowania
Można przypisać wartości do właściwości obiektu klasy w kodzie inicjowania przez dołączenie listę przypisań formularza `property = value` do listy argumentów dla konstruktora. Przedstawiono to w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Następująca wersja poprzedni kod ilustruje kombinacja argumentów zwykłej, argumenty opcjonalne i ustawienia właściwości w wywołaniu jeden konstruktor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a>Konstruktory w dziedziczonej klasie
Podczas dziedziczenia z klasy podstawowej, która ma Konstruktor, należy określić argumenty w klauzuli dziedziczenia. Aby uzyskać więcej informacji, zobacz [konstruktory i dziedziczenie](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Konstruktory statyczne lub konstruktorów typu
Oprócz określenia kodu do tworzenia obiektów statycznych `let` i `do` powiązania można tworzyć w typach klas, które są wykonywane przed typem najpierw służy do wykonywania inicjowania na poziomie typu. Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md) i [ `do` powiązania w klasach](do-bindings-in-classes.md).

## <a name="see-also"></a>Zobacz też
[Elementy członkowskie](index.md)
