---
title: while - C# Odwołanie
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: eb9aa2ea8d6b1c96e0be7d377f7c047194b598de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712796"
---
# <a name="while-c-reference"></a>while (odwołanie w C#)

Instrukcja `while` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne oblicza . Ponieważ to wyrażenie jest oceniane przed każdym `while` wykonaniem pętli, pętla wykonuje zero lub więcej razy. Różni się to od pętli [do,](do.md) która wykonuje jeden lub więcej razy.

W dowolnym momencie `while` w bloku instrukcji można wyrwać się z pętli za pomocą [instrukcji break.](break.md)

Można przejść bezpośrednio do oceny `while` wyrażenia przy użyciu [continue](continue.md) instrukcji. Jeśli wyrażenie oblicza `true`, wykonanie jest kontynuowane w pierwszej instrukcji w pętli. W przeciwnym razie wykonanie jest kontynuowane w pierwszej instrukcji po pętli.

Możesz również wyjść `while` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `while` użycie instrukcji. Wybierz **uruchom,** aby uruchomić przykładowy kod. Następnie można zmodyfikować kod i uruchomić go ponownie.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [While instrukcji](~/_csharplang/spec/statements.md#the-while-statement) sekcji [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [do instrukcji](do.md)
