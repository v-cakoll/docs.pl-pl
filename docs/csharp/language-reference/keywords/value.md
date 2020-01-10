---
title: kontekstowe słowo kluczowe C# wartości — odwołanie
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712900"
---
# <a name="value-c-reference"></a>value (odwołanie w C#)

Kontekstowe słowo kluczowe `value` jest używane w metodzie dostępu `set` w deklaracjach [Właściwości](../../programming-guide/classes-and-structs/properties.md) i [indeksatora](../../programming-guide/indexers/index.md) . Jest podobny do parametru wejściowego metody. Słowo `value` odwołuje się do wartości, którą kod klienta próbuje przypisać do właściwości lub indeksatora. W poniższym przykładzie `MyDerivedClass` ma właściwość o nazwie `Name`, która używa parametru `value` do przypisywania nowego ciągu do pola zapasowego `name`. Z punktu widzenia kodu klienta operacja jest zapisywana jako proste przypisanie.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Aby uzyskać więcej informacji, zobacz artykuły [Properties](../../programming-guide/classes-and-structs/properties.md) i [Indexeres](../../programming-guide/indexers/index.md) .

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
