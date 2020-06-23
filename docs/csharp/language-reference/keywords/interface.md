---
title: Interfejs — Dokumentacja języka C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 869f1398ae0af3c7379655aa018a9f4aacb934d7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243974"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface":::(Odwołanie w C#)

Interfejs definiuje kontrakt. Wszystkie [`class`](class.md) lub [`struct`](../builtin-types/struct.md) , które implementują ten kontrakt, muszą zapewnić implementację elementów członkowskich zdefiniowanych w interfejsie. Począwszy od języka C# 8,0, interfejs może definiować domyślną implementację elementów członkowskich. Może również definiować [`static`](static.md) członków w celu zapewnienia pojedynczej implementacji dla typowych funkcji.

W poniższym przykładzie Klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod` , która nie ma parametrów i zwraca `void` .

Aby uzyskać więcej informacji i przykładów, zobacz [interfejsy](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Interfejs może być elementem członkowskim przestrzeni nazw lub klasy. Deklaracja interfejsu może zawierać deklaracje (podpisy bez implementacji) następujących elementów członkowskich:

- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Właściwości](../../programming-guide/classes-and-structs/using-properties.md)
- [Indexers (Indeksatory)](../../programming-guide/indexers/using-indexers.md)
- [Zdarzenia](event.md)

Te poprzedzające deklaracje składowych zwykle nie zawierają treści. Począwszy od języka C# 8,0, element członkowski interfejsu może deklarować treść. Ta nazwa jest nazywana *implementacją domyślną*. Elementy członkowskie z organami umożliwiają interfejsowi określenie "domyślnej" implementacji klas i struktur, które nie zapewniają zastępowania implementacji. Ponadto począwszy od języka C# 8,0, interfejs może obejmować:

- [Stałe](const.md)
- [Operatory](../operators/operator-overloading.md)
- [Konstruktor statyczny](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [Typy zagnieżdżone](../../programming-guide/classes-and-structs/nested-types.md)
- [Pola statyczne, metody, właściwości, indeksatory i zdarzenia](static.md)
- Deklaracje elementów członkowskich przy użyciu jawnej składni implementacji interfejsu.
- Modyfikatory jawnego dostępu (domyślny dostęp to [`public`](access-modifiers.md) ).

Interfejsy nie mogą zawierać stanu wystąpienia. Gdy pola statyczne są teraz dozwolone, pola wystąpień nie są dozwolone w interfejsach. [Funkcja autowłaściwości wystąpienia](../../programming-guide/classes-and-structs/auto-implemented-properties.md) nie jest obsługiwana w interfejsach, ponieważ niejawnie deklaruje pole ukryte. Ta reguła ma delikatny efekt dla deklaracji właściwości. W deklaracji interfejsu Poniższy kod nie deklaruje właściwości, która jest implementowana przez funkcję w `class` lub `struct` . Zamiast tego deklaruje właściwość, która nie ma domyślnej implementacji, ale musi być zaimplementowana w dowolnym typie, który implementuje interfejs:

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

Poniższy przykład ilustruje implementację interfejsu. W tym przykładzie interfejs zawiera deklarację właściwości, a Klasa zawiera implementację. Każde wystąpienie klasy implementującej `IPoint` zawiera właściwości całkowite `x` i `y` .

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [interfejsy](~/_csharplang/spec/interfaces.md) [specyfikacji języka C#](~/_csharplang/spec/introduction.md) i Specyfikacja funkcji dla [domyślnych członków interfejsu — C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie w C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy odwołań](reference-types.md)
- [Interfejsy](../../programming-guide/interfaces/index.md)
- [Używanie właściwości](../../programming-guide/classes-and-structs/using-properties.md)
- [Używanie indeksatorów](../../programming-guide/indexers/using-indexers.md)
