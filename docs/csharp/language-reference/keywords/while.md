---
title: while - C# Reference
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 481d3f7b87dbe874de010825c3c7f052e4bc33c0
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738753"
---
# <a name="while-c-reference"></a>while (odwołanie w C#)

Instrukcja `while` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne ocenia . Ponieważ to wyrażenie jest oceniane przed każdym `while` wykonaniem pętli, pętla wykonuje zero lub więcej razy. To różni się od [pętli do,](do.md) która wykonuje jeden lub więcej razy.

W dowolnym momencie w bloku `while` instrukcji można wyrwać z pętli przy użyciu instrukcji [break.](break.md)

Można przejść bezpośrednio do oceny `while` wyrażenia przy użyciu [continue](continue.md) instrukcji. Jeśli wyrażenie ocenia `true`, wykonanie jest kontynuowane w pierwszej instrukcji w pętli. W przeciwnym razie wykonanie jest kontynuowane w pierwszej instrukcji po pętli.

Można również wyjść `while` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.

## <a name="example"></a>Przykład

W poniższym przykładzie `while` przedstawiono użycie instrukcji. Wybierz **uruchom,** aby uruchomić przykładowy kod. Następnie można zmodyfikować kod i uruchomić go ponownie.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [instrukcja do](do.md)
