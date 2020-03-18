---
title: instrukcja goto — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715273"
---
# <a name="goto-c-reference"></a>goto (odwołanie w C#)

Instrukcja `goto` przenosi formant programu bezpośrednio do instrukcji z etykietą.

Typowym zastosowaniem `goto` jest przeniesienie kontroli do określonej etykiety switch-case lub etykiety domyślnej w `switch` instrukcji.

Instrukcja `goto` jest również przydatne, aby wydostać się z głęboko zagnieżdżonych pętli.

## <a name="example"></a>Przykład

W poniższym przykładzie `goto` przedstawiono użycie w [instrukcji switch.](switch.md)

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Przykład

W poniższym przykładzie `goto` przedstawiono użycie do wyrwania się z pętli zagnieżdżonych.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [goto, instrukcja (C++)](/cpp/cpp/goto-statement-cpp)
