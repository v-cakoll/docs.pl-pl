---
title: do- C# odwołanie
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 38224ce70c19ff67ad80b99d3da52155849f1341
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713599"
---
# <a name="do-c-reference"></a>do (odwołanie w C#)

Instrukcja `do` wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne daje w wyniku `true`. Ponieważ to wyrażenie jest oceniane po każdym wykonaniu pętli, pętla `do-while` wykonuje jeden lub więcej razy. Różni się to od pętli [while](while.md) , która wykonuje zero lub więcej razy.

W dowolnym momencie w bloku instrukcji `do` można przerwać pętlę przy użyciu instrukcji [Break](break.md) .

Możesz przejść bezpośrednio do oceny wyrażenia `while` przy użyciu instrukcji [Continue](continue.md) . Jeśli wyrażenie zwróci wartość `true`, wykonywanie jest kontynuowane na pierwszej instrukcji w pętli. W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji po pętli.

Możesz również wyjść z pętli `do-while` przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .

## <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie instrukcji `do`. Wybierz pozycję **Uruchom** , aby uruchomić przykładowy kod. Następnie można zmodyfikować kod i uruchomić go ponownie.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję do [instrukcji](~/_csharplang/spec/statements.md#the-do-statement) [ C# języka Specification](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [while, instrukcja](while.md)
