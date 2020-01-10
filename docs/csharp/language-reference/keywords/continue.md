---
title: Continue — instrukcja C# -Reference
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713660"
---
# <a name="continue-c-reference"></a>continue (odwołanie w C#)

Instrukcja `continue` przekazuje formant do następnej iteracji otaczającej instrukcji [while](./while.md), do, [for](./for.md)lub [foreach](./foreach-in.md) [, w](./do.md)której występuje.

## <a name="example"></a>Przykład

W tym przykładzie licznik jest zainicjowany do zliczenia z 1 do 10. Używając instrukcji `continue` w połączeniu z `(i < 9)`wyrażenia, instrukcje między `continue` i końcem treści `for` są pomijane.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [break, instrukcja](/cpp/cpp/break-statement-cpp)
