---
title: wartość kontekstowe słowo kluczowe - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712900"
---
# <a name="value-c-reference"></a>value (odwołanie w C#)

Kontekstowe słowo `value` kluczowe jest `set` używane w akcesor w [deklaracji właściwości](../../programming-guide/classes-and-structs/properties.md) i [indeksatora.](../../programming-guide/indexers/index.md) Jest on podobny do parametru wejściowego metody. Słowo `value` odwołuje się do wartości, którą kod klienta próbuje przypisać do właściwości lub indeksatora. W poniższym `MyDerivedClass` przykładzie ma `Name` właściwość o `value` nazwie, która używa parametru, `name`aby przypisać nowy ciąg do pola zapasowego . Z punktu widzenia kodu klienta operacja jest zapisywana jako proste przypisanie.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Aby uzyskać więcej informacji, zobacz [właściwości](../../programming-guide/classes-and-structs/properties.md) i [indeksatorzy artykułów.](../../programming-guide/indexers/index.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
