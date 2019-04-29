---
title: Zastąp modyfikator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 6a8e79da3897e867fa3becab5fcfc70afe72e614
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660999"
---
# <a name="override-c-reference"></a>override (odwołanie w C#)

`override` Modyfikator jest wymagane, aby rozszerzyć lub zmodyfikować implementacji abstrakcyjne lub wirtualne dziedziczonej metody, właściwości, indeksatora lub zdarzenia.

## <a name="example"></a>Przykład

W tym przykładzie `Square` klasa musi dostarczać implementację zgodnym z przesłoniętą `Area` ponieważ `Area` jest dziedziczony z abstrakcyjnej `ShapesClass`:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

`override` Metoda dostarcza nową implementację elementu członkowskiego, który jest dziedziczony z klasy bazowej. Metoda, która została zastąpiona przez `override` deklaracji jest znany jako przesłonięte metody podstawowej. Zastąpione metody podstawowej musi mieć taką samą sygnaturę jak `override` metody. Aby uzyskać informacji na temat dziedziczenia, zobacz [dziedziczenia](../../programming-guide/classes-and-structs/inheritance.md).

Nie można zastąpić niewirtualną lub statycznej metody. Zastąpione metody podstawowej musi być `virtual`, `abstract`, lub `override`.

`override` Deklaracji nie można zmienić dostępności `virtual` metody. Zarówno `override` metody i `virtual` metoda musi mieć takie same [modyfikator dostępu dla poziomu](access-modifiers.md).

Nie można użyć `new`, `static`, lub `virtual` Modyfikatory do modyfikowania `override` metody.

Przesłanianie deklaracja właściwości należy określić jako właściwość dziedziczona dokładnie tych samych modyfikator dostępu, typ i nazwa i właściwości musi być `virtual`, `abstract`, lub `override`.

Aby uzyskać więcej informacji o sposobie używania `override` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [użycie przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Przykład

Ten przykład definiuje klasę bazową, o nazwie `Employee`, a klasa pochodna o nazwie `SalesEmployee`. `SalesEmployee` Klasa zawiera dodatkowe pola, `salesbonus`i zastępuje metodę `CalculatePay` niezbędny do konta.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](modifiers.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [new](new.md)
- [Polimorfizm](../../programming-guide/classes-and-structs/polymorphism.md)
