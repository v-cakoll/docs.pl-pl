---
title: Continue — instrukcja C# -Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 74d166dbcf03b868baf464864e4c246f789df9cc
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605873"
---
# <a name="continue-c-reference"></a>continue (odwołanie w C#)

[](./while.md) [](./do.md) [](./foreach-in.md) [](./for.md)Instrukcja przekazuje formant do następnej iteracji otaczającej instrukcji while, do, for lub foreach, w której występuje. `continue`

## <a name="example"></a>Przykład

W tym przykładzie licznik jest zainicjowany do zliczenia z 1 do 10. Używając `continue` instrukcji w połączeniu z wyrażeniem `(i < 9)`, instrukcje między `continue` i końcem `for` treści są pomijane.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [break, instrukcja](/cpp/cpp/break-statement-cpp)
