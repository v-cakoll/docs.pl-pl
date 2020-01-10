---
title: goto — instrukcja C# -Reference
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715273"
---
# <a name="goto-c-reference"></a>goto (odwołanie w C#)

Instrukcja `goto` przekazuje kontrolę programu bezpośrednio do instrukcji oznaczonej etykietą.

Typowym zastosowaniem `goto` jest przeniesienie kontroli do konkretnej etykiety przypadku przełącznika lub etykiety domyślnej w instrukcji `switch`.

Instrukcja `goto` jest również przydatna do uzyskiwania z głęboko zagnieżdżonych pętli.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `goto` w instrukcji [Switch](switch.md) .

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `goto` do dzielenia z zagnieżdżonych pętli.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [goto, instrukcja (C++)](/cpp/cpp/goto-statement-cpp)
