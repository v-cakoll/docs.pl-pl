---
title: modyfikator zastępowania — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713251"
---
# <a name="override-c-reference"></a>override (odwołanie w C#)

Modyfikator `override` jest wymagane do rozszerzenia lub zmodyfikowania abstrakcyjnej lub wirtualnej implementacji dziedziczonej metody, właściwości, indeksatora lub zdarzenia.

## <a name="example"></a>Przykład

W tym przykładzie `Square` klasa musi zapewnić zastąpioną implementację, `GetArea` ponieważ `GetArea` jest dziedziczona z klasy abstrakcyjnej: `Shape`

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Metoda `override` zapewnia nową implementację elementu członkowskiego, który jest dziedziczony z klasy podstawowej. Metoda, która jest zastępowana przez `override` deklarację jest znany jako zastąpiona metoda podstawowa. Zastąpiona metoda podstawowa musi mieć `override` taki sam podpis jak metoda. Aby uzyskać informacje o dziedziczeniu, zobacz [Dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md).

Nie można zastąpić metody niewirtualnej lub statycznej. Zastąpiona metoda podstawowa `abstract`musi `override`być `virtual`, lub .

Deklaracja `override` nie może zmienić `virtual` dostępności metody. Zarówno `override` metoda, `virtual` jak i metoda muszą mieć ten sam [modyfikator poziomu dostępu](access-modifiers.md).

Nie można `new`użyć `static`, `virtual` lub modyfikatorów do modyfikowania `override` metody.

Zaległe oświadczenie właściwości musi określać dokładnie ten sam modyfikator dostępu, typ i `virtual` `abstract`nazwę `override`jako dziedziczoną właściwość, a zastąpiona właściwość musi być , lub .

Aby uzyskać więcej informacji `override` na temat używania słowa kluczowego, zobacz [Przechowywanie wersji za pomocą słów kluczowych Zastępowania i Nowe](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) oraz Wiedza o [tym, kiedy używać funkcji Zastępowania i Nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Przykład

W tym przykładzie definiuje `Employee`klasę podstawową o `SalesEmployee`nazwie i klasę pochodną o nazwie . Klasa `SalesEmployee` zawiera dodatkowe pole `salesbonus`i zastępuje metodę, `CalculatePay` aby wziąć ją pod uwagę.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [Abstrakcja](abstract.md)
- [virtual](virtual.md)
- [nowy (modyfikator)](new-modifier.md)
- [Polimorfizm](../../programming-guide/classes-and-structs/polymorphism.md)
