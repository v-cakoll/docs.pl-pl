---
title: Dziedziczenie (F#)
description: 'Dowiedz się, jak określić dziedziczenia relacji F # za pomocą słowa kluczowego "inherit".'
ms.date: 05/16/2016
ms.openlocfilehash: e4d79244fb9bada5db0c5c4c7179d4bfe6e21f3d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864472"
---
# <a name="inheritance"></a>Dziedziczenie

Dziedziczenie jest używane do modelowania relacji "jest a" lub subtyping w programowanie zorientowane obiektowo.

## <a name="specifying-inheritance-relationships"></a>Określanie relacji dziedziczenia

Należy określić za pomocą relacji dziedziczenia `inherit` — słowo kluczowe w deklaracji klasy. Podstawowe formie syntaktycznych przedstawiono w poniższym przykładzie.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Klasa może mieć co najwyżej jedną bezpośrednią klasą bazową. Jeśli nie określisz klasę bazową przy użyciu `inherit` — słowo kluczowe, klasa dziedziczy niejawnie z `System.Object`.

## <a name="inherited-members"></a>Dziedziczone elementy członkowskie

Jeśli klasa dziedziczy z innej klasy, metod i składowych klasy bazowej są dostępne dla użytkowników w klasie pochodnej, tak, jakby były one bezpośredni członkowie klasy pochodnej.

Dowolny let — powiązania i parametry konstruktora są prywatne dla klasy i w związku z tym, nie są dostępne z klas pochodnych.

Słowo kluczowe `base` jest dostępna w klasach pochodnych i odnosi się do wystąpienia klasy bazowej. Jest on używany, np. własny identyfikator.

## <a name="virtual-methods-and-overrides"></a>Metody wirtualne i zastąpień

Metody wirtualne (i właściwości) działają trochę inaczej w języku F # w porównaniu do innych języków platformy .NET. Aby zadeklarować nowa wirtualna składowa, należy użyć `abstract` — słowo kluczowe. W tym niezależnie od tego, czy zapewniasz Domyślna implementacja tej metody. Ten sposób kompletną definicję metody wirtualnej w klasie bazowej ze wzorcem to:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

I w klasie pochodnej, zastąpienie tej metody wirtualnej korzysta z tego wzorca:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Jeżeli pominięto domyślną implementację w klasie bazowej, klasa bazowa staje się klasy abstrakcyjnej.

Poniższy przykład kodu ilustruje deklarację nowej metody wirtualnej `function1` w klasie podstawowej oraz sposób jej zastąpienie w klasie pochodnej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Konstruktory i dziedziczenie

Należy wywołać konstruktora klasy podstawowej w klasie pochodnej. Argumenty dla konstruktora klasy bazowej są wyświetlane na liście argumentów w `inherit` klauzuli. Należy określić wartości, które są używane w argumentach dostarczonego do konstruktora klasy pochodnej.

Poniższy kod pokazuje klasa bazowa i Klasa pochodna, gdzie klasy pochodnej wywołuje konstruktora klasy bazowej w klauzuli dziedziczenia:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

W przypadku wiele konstruktorów służy poniższy kod. Pierwszy wiersz konstruktorami klasy pochodnej jest `inherit` klauzuli i pola są wyświetlane jako jawne pola, które są zadeklarowane za pomocą `val` — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [pola jawne: `val` — słowo kluczowe](members/explicit-fields-the-val-keyword.md).

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

W przypadkach, w których wymagane jest pomocnicze modyfikacja typu należy wziąć pod uwagę przy użyciu wyrażenie obiektu jako alternatywę dla dziedziczenia. Poniższy przykład ilustruje użycie wyrażenie obiektu jako alternatywę do tworzenia nowego typu pochodnego:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Aby uzyskać więcej informacji na temat wyrażeń obiektów, zobacz [wyrażenia obiektów](object-expressions.md).

Podczas tworzenia obiektów hierarchii, należy rozważyć użycie złożenia dyskryminowanego zamiast dziedziczenia. Związki dyskryminowane mogą również model zróżnicowane zachowanie różnych obiektów, które współużytkują wspólny typ ogólny. Pojedynczy złożenia dyskryminowanego można często wyeliminować potrzebę szereg klas pochodnych, które są niewielkich zmian. Aby uzyskać informacji na temat związki dyskryminowane, zobacz [sumy rozłączne](discriminated-unions.md).

## <a name="see-also"></a>Zobacz także

- [Wyrażenia obiektów](object-expressions.md)
- [Dokumentacja języka F#](index.md)
