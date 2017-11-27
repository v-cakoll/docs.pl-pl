---
title: Dziedziczenie (F#)
description: "Dowiedz się, jak określać dziedziczenia relacji F # za pomocą słowa kluczowego \"inherit\"."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b38ab2f6-7ba7-4839-8eff-e6bd6cfd2b2f
ms.openlocfilehash: 331c8f4e39aacd9d5e55bfbaf584f037e58d36a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="inheritance"></a>Dziedziczenie

Dziedziczenie jest używana do modelowania relacji "jest a", lub subtyping w programowanie zorientowane obiektowo.


## <a name="specifying-inheritance-relationships"></a>Określanie relacji dziedziczenia
Należy określić przy użyciu relacji dziedziczenia `inherit` — słowo kluczowe w deklaracji klasy. W poniższym przykładzie przedstawiono podstawowe syntaktycznych formularza.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Klasa może mieć co najwyżej jeden bezpośredniej klasie podstawowej. Jeśli nie określisz klasy podstawowej za pomocą `inherit` — słowo kluczowe, klasy niejawnie dziedziczy `System.Object`.


## <a name="inherited-members"></a>Dziedziczone elementy członkowskie
Jeśli klasa dziedziczy z innej klasy, metod i elementów członkowskich klasy podstawowej są dostępne użytkownikom klasy pochodnej, tak jakby były bezpośrednie elementy członkowskie klasy pochodnej.

Wszelkie let — powiązania i parametrami konstruktora prywatne do klasy, a w związku z tym nie ma dostępu z klasy pochodnej.

Słowo kluczowe `base` jest dostępna w klasach pochodnych i odwołuje się do wystąpienia klasy podstawowej. Jest on używany jak własny identyfikator.


## <a name="virtual-methods-and-overrides"></a>Metody wirtualne i zastąpień
Metody wirtualne (i właściwości) działają trochę inaczej w języku F # porównaniu z innymi językami .NET. Aby zadeklarować nowy wirtualny element członkowski, należy użyć `abstract` — słowo kluczowe. W tym niezależnie od tego, czy użytkownik udostępnia domyślną implementację dla tej metody. W związku z tym pełnej definicji wirtualnej metody w klasie podstawowej następujące tego wzorca:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

I w klasie pochodnej przesłonięcie tej metody wirtualnej jest zgodna z tego wzorca:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

W przypadku pominięcia domyślna Implementacja klasy podstawowej, klasa podstawowa staje się klasy abstrakcyjnej.

Poniższy przykład kodu pokazuje deklaracji nowej metody wirtualnej `function1` w klasie podstawowej oraz sposób jej zastąpienie w klasie pochodnej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a>Konstruktory i dziedziczenie
Konstruktor dla klasy podstawowej musi zostać wywołany w klasie pochodnej. Argumenty dla konstruktora klasy podstawowej są wyświetlane na liście argumentów w `inherit` klauzuli. Należy określić wartości, które są używane w argumentach przekazany do konstruktora klasy pochodnej.

Poniższy kod przedstawia klasa podstawowa i Klasa pochodna, gdzie klasy pochodnej wywołuje konstruktor klasy podstawowej w klauzuli dziedziczenia:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

W przypadku wiele konstruktorów można użyć poniższego kodu. Jest to pierwszy wiersz konstruktory klas pochodnych `inherit` klauzuli i pola są wyświetlane jako pola jawne, które są zadeklarowane z `val` — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [pola jawne: `val` — słowo kluczowe](members/explicit-fields-the-val-keyword.md).

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
W przypadkach, gdy wymagane jest pomocnicze modyfikacja typu Rozważ użycie wyrażenia obiektu zamiast dziedziczenia. Poniższy przykład przedstawia użycie wyrażenia obiektu jako alternatywę do utworzenia nowego typu pochodnego:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Aby uzyskać więcej informacji na temat wyrażenia obiektów, zobacz [wyrażenia obiektów](object-expressions.md).

Podczas tworzenia obiektu hierarchii, należy rozważyć użycie rozróżnianą Unię zamiast dziedziczenia. Sumy rozłączne może również zachowanie modelu różne w różnych obiektów, które mają wspólny typ ogólny. Pojedynczy rozróżnianą Unię można często wyeliminować potrzebę szereg klas pochodnych, które są niewielkich zmian. Aby uzyskać informacje o rozłączne, zobacz [Suma rozłączna unie](discriminated-unions.md).


## <a name="see-also"></a>Zobacz też
[Wyrażenia obiektów](object-expressions.md)

[Dokumentacja języka F #](index.md)
