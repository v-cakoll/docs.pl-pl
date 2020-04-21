---
title: do - Odwołanie do języka C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 1d4323366e567dab4b27b07803d0c06e731611ce
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738907"
---
# <a name="do-c-reference"></a>do (odwołanie w C#)

Instrukcja `do` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne ocenia . Ponieważ to wyrażenie jest oceniane po każdym `do-while` wykonaniu pętli, pętla wykonuje jeden lub więcej razy. To różni się od [while](while.md) pętli, która wykonuje zero lub więcej razy.

W dowolnym momencie w bloku `do` instrukcji można wyrwać z pętli przy użyciu instrukcji [break.](break.md)

Można przejść bezpośrednio do oceny `while` wyrażenia przy użyciu [continue](continue.md) instrukcji. Jeśli wyrażenie ocenia `true`, wykonanie jest kontynuowane w pierwszej instrukcji w pętli. W przeciwnym razie wykonanie jest kontynuowane w pierwszej instrukcji po pętli.

Można również wyjść `do-while` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.

## <a name="example"></a>Przykład

W poniższym przykładzie `do` przedstawiono użycie instrukcji. Wybierz **uruchom,** aby uruchomić przykładowy kod. Następnie można zmodyfikować kod i uruchomić go ponownie.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [podczas gdy oświadczenie](while.md)
