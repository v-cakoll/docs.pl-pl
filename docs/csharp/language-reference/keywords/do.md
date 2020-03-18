---
title: do - C# Odwołanie
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 38224ce70c19ff67ad80b99d3da52155849f1341
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713599"
---
# <a name="do-c-reference"></a>do (odwołanie w C#)

Instrukcja `do` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne oblicza . Ponieważ wyrażenie to jest oceniane po każdym `do-while` wykonaniu pętli, pętla wykonuje jeden lub więcej razy. Różni się to od [while](while.md) pętli, która wykonuje zero lub więcej razy.

W dowolnym momencie `do` w bloku instrukcji można wyrwać się z pętli za pomocą [instrukcji break.](break.md)

Można przejść bezpośrednio do oceny `while` wyrażenia przy użyciu [continue](continue.md) instrukcji. Jeśli wyrażenie oblicza `true`, wykonanie jest kontynuowane w pierwszej instrukcji w pętli. W przeciwnym razie wykonanie jest kontynuowane w pierwszej instrukcji po pętli.

Możesz również wyjść `do-while` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `do` użycie instrukcji. Wybierz **uruchom,** aby uruchomić przykładowy kod. Następnie można zmodyfikować kod i uruchomić go ponownie.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję instrukcji do](~/_csharplang/spec/statements.md#the-do-statement) [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [podczas gdy oświadczenie](while.md)
