---
title: Dziedziczenie
description: Dowiedz się, jak określić relacje dziedziczenia F# przy użyciu słowa kluczowego "dziedziczyć".
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400289"
---
# <a name="inheritance"></a>Dziedziczenie

Dziedziczenie służy do modelowania relacji "is-a" lub podtypowania w programowaniu obiektowym.

## <a name="specifying-inheritance-relationships"></a>Określanie relacji dziedziczenia

Relacje dziedziczenia można `inherit` określić przy użyciu słowa kluczowego w deklaracji klasy. Podstawowy formularz syntaktyczny jest pokazany w poniższym przykładzie.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Klasa może mieć co najwyżej jedną bezpośrednią klasę podstawową. Jeśli klasa podstawowa nie zostanie `inherit` określona przy użyciu słowa kluczowego, klasa niejawnie dziedziczy po pliku `System.Object`.

## <a name="inherited-members"></a>Dziedziczone elementy członkowskie

Jeśli klasa dziedziczy z innej klasy, metody i elementy członkowskie klasy podstawowej są dostępne dla użytkowników klasy pochodnej, tak jakby byli bezpośrednimi członkami klasy pochodnej.

Wszelkie let powiązania i parametry konstruktora są prywatne do klasy i w związku z tym nie można uzyskać dostępu z klas pochodnych.

Słowo `base` kluczowe jest dostępne w klasach pochodnych i odwołuje się do wystąpienia klasy podstawowej. Jest on używany jako własny identyfikator.

## <a name="virtual-methods-and-overrides"></a>Metody wirtualne i zastępowanie

Metody wirtualne (i właściwości) działają nieco inaczej w języku F# w porównaniu z innymi językami .NET. Aby zadeklarować nowego wirtualnego `abstract` członka, użyj słowa kluczowego. Można to zrobić niezależnie od tego, czy należy podać implementację domyślną dla tej metody. W związku z tym pełna definicja metody wirtualnej w klasie podstawowej następuje następujący po zwzorzec:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

W klasie pochodnej zastąpienie tej metody wirtualnej następuje po tym wzorcu:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Jeśli pominiesz domyślną implementację w klasie podstawowej, klasa podstawowa staje się klasą abstrakcyjną.

Poniższy przykład kodu ilustruje deklarację `function1` nowej metody wirtualnej w klasie podstawowej i jak zastąpić ją w klasie pochodnej.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Konstruktorzy i dziedziczenie

Konstruktor klasy podstawowej musi być wywoływana w klasie pochodnej. Argumenty dla konstruktora klasy podstawowej `inherit` są wyświetlane na liście argumentów w klauzuli. Wartości, które są używane musi być określona na podstawie argumentów dostarczonych do konstruktora klasy pochodnej.

Poniższy kod przedstawia klasę podstawową i klasę pochodną, gdzie klasa pochodna wywołuje konstruktora klasy podstawowej w klauzuli dziedziczenia:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

W przypadku wielu konstruktorów można użyć następującego kodu. Pierwszy wiersz konstruktorów klasy pochodnej `inherit` jest klauzula, a pola są wyświetlane `val` jako jawne pola, które są zadeklarowane za pomocą słowa kluczowego. Aby uzyskać więcej informacji, zobacz [Pola jawne: `val` Słowo kluczowe](./members/explicit-fields-the-val-keyword.md).

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>Alternatywy dla dziedziczenia

W przypadkach, gdy wymagana jest niewielka modyfikacja typu, należy rozważyć użycie wyrażenia obiektu jako alternatywy dla dziedziczenia. W poniższym przykładzie przedstawiono użycie wyrażenia obiektu jako alternatywy dla tworzenia nowego typu pochodnego:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Aby uzyskać więcej informacji o wyrażeniach obiektów, zobacz [Wyrażenia obiektów](object-expressions.md).

Podczas tworzenia hierarchii obiektów należy rozważyć użycie unii dyskryminowanej zamiast dziedziczenia. Dyskryminowane związki mogą również modelować zróżnicowane zachowanie różnych obiektów, które mają wspólny typ ogólny. Pojedyncza unia dyskryminowana może często wyeliminować potrzebę wielu klas pochodnych, które są mniejszymi zmianami siebie nawzajem. Aby uzyskać informacje na temat związków dyskryminowanych, zobacz [Związki dyskryminowane](discriminated-unions.md).

## <a name="see-also"></a>Zobacz też

- [Wyrażenia obiektów](object-expressions.md)
- [Odwołanie do języka F#](index.md)
