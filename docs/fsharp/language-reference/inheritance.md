---
title: Dziedziczenie
description: Dowiedz się, F# jak określić relacje dziedziczenia przy użyciu słowa kluczowego "inherit".
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627669"
---
# <a name="inheritance"></a>Dziedziczenie

Dziedziczenie służy do modelowania relacji "is-a" lub podpisywania w programowaniu zorientowanym obiektowo.

## <a name="specifying-inheritance-relationships"></a>Określanie relacji dziedziczenia

Relacje dziedziczenia można określić za pomocą `inherit` słowa kluczowego w deklaracji klasy. W poniższym przykładzie przedstawiono podstawową formę składni.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Klasa może mieć co najwyżej jedną bezpośrednią klasę bazową. Jeśli nie określisz klasy bazowej przy użyciu `inherit` słowa kluczowego, Klasa niejawnie dziedziczy z. `System.Object`

## <a name="inherited-members"></a>Dziedziczone elementy członkowskie

Jeśli klasa dziedziczy z innej klasy, metody i składowe klasy bazowej są dostępne dla użytkowników klasy pochodnej, tak jakby były bezpośrednimi elementami członkowskimi klasy pochodnej.

Wszystkie powiązania let i konstruktory są prywatne z klasą, w związku z czym nie można uzyskać do nich dostępu z klas pochodnych.

Słowo kluczowe `base` jest dostępne w klasach pochodnych i odwołuje się do wystąpienia klasy bazowej. Jest on używany jako identyfikator samoobsługi.

## <a name="virtual-methods-and-overrides"></a>Metody wirtualne i zastąpienia

Metody wirtualne (i właściwości) działają nieco inaczej w F# porównaniu z innymi językami .NET. Aby zadeklarować nową wirtualną składową, należy użyć `abstract` słowa kluczowego. Należy to zrobić niezależnie od tego, czy podajesz domyślną implementację dla tej metody. W rezultacie pełna definicja metody wirtualnej w klasie podstawowej jest zgodna z tym wzorcem:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

I w klasie pochodnej przesłonięcie tej metody wirtualnej następuje po tym wzorcu:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Jeśli pominięto implementację domyślną w klasie bazowej, Klasa bazowa zostanie klasą abstrakcyjną.

Poniższy przykład kodu ilustruje deklarację nowej metody `function1` wirtualnej w klasie bazowej i jak zastąpić ją w klasie pochodnej.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Konstruktory i dziedziczenie

Konstruktor klasy bazowej musi być wywołany w klasie pochodnej. Argumenty konstruktora klasy bazowej pojawiają się na liście argumentów w `inherit` klauzuli. Wartości, które są używane, muszą być określone na podstawie argumentów dostarczonych do konstruktora klasy pochodnej.

Poniższy kod przedstawia klasę bazową i klasę pochodną, gdzie Klasa pochodna wywołuje konstruktora klasy bazowej w klauzuli inherit:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

W przypadku wielu konstruktorów można użyć poniższego kodu. Pierwszym wierszem konstruktorów klas pochodnych jest `inherit` klauzula, a pola są wyświetlane jako jawne pola, które są zadeklarowane `val` za pomocą słowa kluczowego. Aby uzyskać więcej informacji, [Zobacz pola jawne: `val` Słowo kluczowe](./members/explicit-fields-the-val-keyword.md).

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

## <a name="alternatives-to-inheritance"></a>Alternatywy do dziedziczenia

W przypadkach, gdy wymagana jest drobna modyfikacja typu, rozważ użycie wyrażenia obiektu jako alternatywy dla dziedziczenia. Poniższy przykład ilustruje użycie wyrażenia obiektu jako alternatywę do tworzenia nowego typu pochodnego:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Aby uzyskać więcej informacji na temat wyrażeń obiektów, zobacz [wyrażenia obiektów](object-expressions.md).

Podczas tworzenia hierarchii obiektów należy rozważyć użycie Unii rozłącznych zamiast dziedziczenia. Związki rozłączne mogą również modelować różne zachowania różnych obiektów, które współużytkują wspólny typ ogólny. Pojedyncza Unia rozłączna może często wyeliminować konieczność stosowania szeregu klas pochodnych, które są niewielkimi zmianami. Aby uzyskać informacje na temat związków rozłącznych, zobacz [związki](discriminated-unions.md)rozłączne.

## <a name="see-also"></a>Zobacz także

- [Wyrażenia obiektów](object-expressions.md)
- [Dokumentacja języka F#](index.md)
