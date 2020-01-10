---
title: Zastąp modyfikator C# -Reference
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713251"
---
# <a name="override-c-reference"></a>override (odwołanie w C#)

Modyfikator `override` jest wymagany do rozszerania lub modyfikowania abstrakcyjnej lub wirtualnej implementacji dziedziczonej metody, właściwości, indeksatora lub zdarzenia.

## <a name="example"></a>Przykład

W tym przykładzie Klasa `Square` musi udostępniać zastąpioną implementację `GetArea`, ponieważ `GetArea` jest dziedziczona z klasy abstrakcyjnej `Shape`:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Metoda `override` zapewnia nową implementację elementu członkowskiego, który jest Dziedziczony z klasy bazowej. Metoda zastępowana przez deklarację `override` jest znana jako zastąpiona metoda podstawowa. Zastąpiona metoda bazowa musi mieć taką samą sygnaturę jak Metoda `override`. Aby uzyskać informacje na temat dziedziczenia, zobacz [dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md).

Nie można zastąpić metody niewirtualnej lub statycznej. Zastąpiona metoda bazowa musi mieć wartość `virtual`, `abstract`lub `override`.

Deklaracja `override` nie może zmienić dostępności metody `virtual`. Zarówno Metoda `override`, jak i Metoda `virtual` muszą mieć ten sam [modyfikator poziomu dostępu](access-modifiers.md).

Nie można użyć modyfikatora `new`, `static`lub `virtual`, aby zmodyfikować metodę `override`.

Zastępowanie deklaracji właściwości musi określać dokładnie ten sam modyfikator dostępu, typ i nazwę, co Właściwość dziedziczona, a zastąpiona właściwość musi mieć wartość `virtual`, `abstract`lub `override`.

Aby uzyskać więcej informacji na temat sposobu używania słowa kluczowego `override`, zobacz [przechowywanie wersji z przesłonięciami i nowymi słowami kluczowymi](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [wiedzą, kiedy używać przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Przykład

W tym przykładzie zdefiniowano klasę bazową o nazwie `Employee`i klasę pochodną o nazwie `SalesEmployee`. Klasa `SalesEmployee` zawiera dodatkowe pole, `salesbonus`i zastępuje metodę `CalculatePay` w celu uwzględnienia tej metody.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [New (modyfikator)](new-modifier.md)
- [Polimorfizm](../../programming-guide/classes-and-structs/polymorphism.md)
