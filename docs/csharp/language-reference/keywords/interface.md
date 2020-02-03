---
title: C# informacje o interfejsie
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: b315d1f04c9e74700afba8ee7871b23ab4b2fd28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744689"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface"::: (C# odwołanie)

Interfejs definiuje kontrakt. Wszelkie [`class`](class.md) lub [`struct`](struct.md) implementujące ten kontrakt muszą zawierać implementację elementów członkowskich zdefiniowanych w interfejsie. Począwszy od C# 8,0, interfejs może definiować domyślną implementację elementów członkowskich. Może również definiować [`static`](static.md) składowe w celu zapewnienia pojedynczej implementacji dla typowych funkcji.

W poniższym przykładzie Klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod`, która nie ma parametrów i zwraca `void`.

Aby uzyskać więcej informacji i przykładów, zobacz [interfejsy](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Interfejs może być elementem członkowskim przestrzeni nazw lub klasy. Deklaracja interfejsu może zawierać deklaracje (podpisy bez implementacji) następujących elementów członkowskich:

- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Właściwości](../../programming-guide/classes-and-structs/using-properties.md)
- [Indeksatory](../../programming-guide/indexers/using-indexers.md)
- [Zdarzenia](event.md)

Te poprzedzające deklaracje składowych zwykle nie zawierają treści. Począwszy od C# 8,0, element członkowski interfejsu może deklarować treść. Ta nazwa jest nazywana *implementacją domyślną*. Elementy członkowskie z organami umożliwiają interfejsowi określenie "domyślnej" implementacji klas i struktur, które nie zapewniają zastępowania implementacji. Ponadto począwszy od C# 8,0, interfejs może obejmować:

- [Stałe](const.md)
- [Operatory](../operators/operator-overloading.md)
- [Konstruktor statyczny](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [Typy zagnieżdżone](../../programming-guide/classes-and-structs/nested-types.md)
- [Pola statyczne, metody, właściwości, indeksatory i zdarzenia](static.md)
- Deklaracje elementów członkowskich przy użyciu jawnej składni implementacji interfejsu.
- Modyfikatory jawnego dostępu (domyślny dostęp jest [`public`](access-modifiers.md)).

Interfejsy nie mogą zawierać stanu wystąpienia. Gdy pola statyczne są teraz dozwolone, pola wystąpień nie są dozwolone w interfejsach. [Funkcja autowłaściwości wystąpienia](../../programming-guide/classes-and-structs/auto-implemented-properties.md) nie jest obsługiwana w interfejsach, ponieważ niejawnie deklaruje pole ukryte. Ta reguła ma delikatny efekt dla deklaracji właściwości. W deklaracji interfejsu Poniższy kod nie deklaruje właściwości, która jest implementowana w `class` lub `struct`. Zamiast tego deklaruje właściwość, która nie ma domyślnej implementacji, ale musi być zaimplementowana w dowolnym typie, który implementuje interfejs:

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

Interfejs może dziedziczyć z jednego lub kilku interfejsów podstawowych. Gdy interfejs [zastępuje metodę](override.md) zaimplementowaną w interfejsie podstawowym, musi używać [jawnej składni implementacji interfejsu](../../programming-guide/interfaces/explicit-interface-implementation.md) .

Gdy lista typów podstawowych zawiera klasę bazową i interfejsy, Klasa bazowa musi znajdować się na liście.

Klasa implementująca interfejs może jawnie implementować elementy członkowskie tego interfejsu. Nie można uzyskać dostępu do jawnie zaimplementowanego elementu członkowskiego za pomocą wystąpienia klasy, ale tylko za pomocą wystąpienia interfejsu. Ponadto do domyślnych członków interfejsu można uzyskać dostęp tylko za pomocą wystąpienia interfejsu.

Aby uzyskać więcej informacji na temat jawnej implementacji interfejsu, zobacz [jawną implementację interfejsu](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje implementację interfejsu. W tym przykładzie interfejs zawiera deklarację właściwości, a Klasa zawiera implementację. Każde wystąpienie klasy implementującej `IPoint` ma właściwości całkowite `x` i `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [interfejsy](~/_csharplang/spec/interfaces.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md) i Specyfikacja funkcji dla [domyślnych członków interfejsu C# — 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy odwołań](reference-types.md)
- [Interfejsy](../../programming-guide/interfaces/index.md)
- [Używanie właściwości](../../programming-guide/classes-and-structs/using-properties.md)
- [Używanie indeksatorów](../../programming-guide/indexers/using-indexers.md)
- [class](class.md)
- [struct](struct.md)
- [Interfejsy](../../programming-guide/interfaces/index.md)
