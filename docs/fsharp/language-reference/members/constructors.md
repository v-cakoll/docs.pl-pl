---
title: Konstruktorzy (F#)
description: 'Dowiedz się, jak zdefiniować i używać konstruktorów języka F # do tworzenia i inicjowania obiektów klasy i struktury.'
ms.date: 05/16/2016
ms.openlocfilehash: ff2463f890034cce0bbaa85d9a5c93e50427cd03
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514306"
---
# <a name="constructors"></a>Konstruktorów

W tym temacie opisano sposób definiowania i tworzenie i Inicjowanie obiektów klasy i struktury za pomocą konstruktorów.

## <a name="construction-of-class-objects"></a>Konstrukcja klasy obiektów

Obiekty typów klas mieć konstruktorów. Istnieją dwa rodzaje konstruktorów. Jeden jest podstawowy Konstruktor, której parametry są wyświetlane w nawiasach zaraz po nazwę typu. Określ inne, opcjonalne konstruktory dodatkowe za pomocą `new` — słowo kluczowe. Wszelkie dodatkowe konstruktory musi wywołać konstruktora podstawowego.

Zawiera podstawowy Konstruktor `let` i `do` powiązania, które pojawiają się na początku definicji klasy. A `let` powiązanie deklaruje, prywatnych pola i metody klasy; `do` powiązania wykonuje kod. Aby uzyskać więcej informacji na temat `let` powiązania w konstruktorów klas, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md). Aby uzyskać więcej informacji na temat `do` powiązania w konstruktorach, zobacz [ `do` powiązania w klasach](do-bindings-in-classes.md).

Niezależnie od tego, czy konstruktora, aby wywołać konstruktor podstawowym lub dodatkowym konstruktorze, możesz tworzyć obiekty używając `new` wyrażenia, z lub bez opcjonalnego `new` — słowo kluczowe. Inicjowanie obiektów wraz z argumentów konstruktora, wyświetlając listę argumentów w porządku i rozdzielone przecinkami i ujęte w nawiasy, lub za pomocą nazwanych argumentów i wartości w nawiasach. Można można również ustawić właściwości dla obiektu podczas konstruowania obiektu za pomocą nazwy właściwości i przypisywania wartości, tak jak używasz nazwane argumenty konstruktora.

Poniższy kod ilustruje klasę, która ma Konstruktor i różne sposoby tworzenia obiektów.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Dane wyjściowe są następujące:

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Konstrukcja struktury

Struktury postępuj zgodnie z regułami klasy. W związku z tym, może mieć konstruktora podstawowego i możesz podać dodatkowe konstruktory przy użyciu `new`. Istnieje jednak jedną istotną różnicą między strukturami i klasami: struktury mogą mieć domyślnego konstruktora (czyli jeden bez argumentów), nawet jeśli żaden konstruktor podstawowy jest zdefiniowany. Konstruktor domyślny inicjuje wszystkie pola na wartość domyślną dla tego typu, zwykle zero lub jej odpowiednik. Żadnych konstruktorów, zdefiniowanych przez użytkownika w strukturach muszą mieć co najmniej jeden argument, tak, aby nie wchodziły przy użyciu domyślnego konstruktora.

Ponadto struktury często mają pola, które są tworzone za pomocą `val` słowo kluczowe klasy mogą także mieć tych pól. Struktur i klas, które mają pola zdefiniowane przy użyciu `val` — słowo kluczowe może również być inicjowane w konstruktorach dodatkowe przy użyciu wyrażeń rekordów jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Aby uzyskać więcej informacji, zobacz [pola jawne: `val` — słowo kluczowe](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Wykonywanie efekty uboczne w konstruktorach

Podstawowy Konstruktor w klasie może wykonać kod w `do` powiązania. Jednak co zrobić, jeśli trzeba wykonać kod w dodatkowym konstruktorze, bez `do` powiązanie? Aby to zrobić, należy użyć `then` — słowo kluczowe.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Efekty uboczne konstruktora podstawowego nadal wykonywać. W związku z tym dane wyjściowe wyglądają następująco.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Samoidentyfikatory w konstruktorach

Inne elementy członkowskie służy do Podaj nazwę dla bieżącego obiektu w definicji każdego elementu członkowskiego. Własny identyfikator można umieścić w pierwszym wierszu definicji klasy, za pomocą `as` — słowo kluczowe natychmiast po parametry konstruktora. W poniższym przykładzie pokazano tej składni.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

W konstruktorach dodatkowych można zdefiniować własny identyfikator, umieszczając `as` klauzuli od razu po parametry konstruktora. W poniższym przykładzie pokazano tej składni.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Podczas próby użycia obiektu przed jest w pełni zdefiniowana, mogą wystąpić problemy. W związku z tym wykorzystuje własny identyfikator może spowodować aby kompilator emituje ostrzeżenia i wstawić dodatkowe kontrole w celu zapewnienia, że elementów członkowskich obiektu nie są dostępne, zanim obiekt jest zainicjowany. Należy używać tylko własny identyfikator w `do` powiązania konstruktora podstawowego lub po `then` — słowo kluczowe w konstruktorach dodatkowe.

Nazwa identyfikatora self nie ma być `this`. Może być dowolnym prawidłowym identyfikatorem.

## <a name="assigning-values-to-properties-at-initialization"></a>Przypisywanie wartości do właściwości podczas inicjowania

Można przypisać wartości do właściwości obiektu klasy w kodzie inicjowania, dodając listę przypisań formularza `property = value` do listy argumentów dla konstruktora. Jest to pokazane w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Następująca wersja poprzedniego kodu ilustruje kombinacji zwykłych argumenty, opcjonalne argumenty i ustawienia właściwości w wywołaniu jeden konstruktor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Konstruktorów w klasie dziedziczonej

Gdy dziedziczy z klasy podstawowej, która ma Konstruktor, należy określić argumenty w klauzuli dziedziczenia. Aby uzyskać więcej informacji, zobacz [konstruktorów i dziedziczenie](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Konstruktory statyczne lub konstruktory typu

Oprócz określenia kodu do tworzenia obiektów statycznych `let` i `do` powiązania można tworzyć w typach klasy, które są wykonywane przed typ najpierw jest używany do wykonywania Inicjalizacja na poziomie typu. Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md) i [ `do` powiązania w klasach](do-bindings-in-classes.md).

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
