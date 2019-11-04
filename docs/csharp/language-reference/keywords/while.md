---
title: While — C# odwołanie
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: ab0a8ba0b724757b4f239daf1d3319b989c4531a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421914"
---
# <a name="while-c-reference"></a>while (odwołanie w C#)

Instrukcja `while` wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne daje w wyniku `true`. Ponieważ to wyrażenie jest oceniane przed każdym wykonaniem pętli, pętla `while` wykonuje zero lub więcej razy. Różni się to od [pętli do](do.md) , która wykonuje jeden lub więcej razy.

W dowolnym momencie w bloku instrukcji `while` można przerwać pętlę przy użyciu instrukcji [Break](break.md) .

Możesz przejść bezpośrednio do oceny wyrażenia `while` przy użyciu instrukcji [Continue](continue.md) . Jeśli wyrażenie zwróci wartość `true`, wykonywanie jest kontynuowane na pierwszej instrukcji w pętli. W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji po pętli.

Możesz również wyjść z pętli `while` przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .

## <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie instrukcji `while`. Wybierz pozycję **Uruchom** , aby uruchomić przykładowy kod. Następnie można zmodyfikować kod i uruchomić go ponownie.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [while](~/_csharplang/spec/statements.md#the-while-statement) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [do — instrukcja](do.md)
