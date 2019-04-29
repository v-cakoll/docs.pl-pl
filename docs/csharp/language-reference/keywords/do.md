---
title: do — C# odwołania
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 4bdbd1c8efac0b7ba95d4c8d16dae3101fe6bcb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661792"
---
# <a name="do-c-reference"></a>do (odwołanie w C#)

`do` Instrukcji wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne, które daje w wyniku `true`. Ponieważ to wyrażenie jest oceniane po każdym wykonaniu pętli, `do-while` pętla jest wykonywana raz lub więcej razy. To różni się od [podczas](while.md) pętli, która wykonuje zero lub więcej razy.

W dowolnym punkcie w `do` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji.

Użytkownik może przechodzić bezpośrednio do obliczania `while` wyrażenie, używając [nadal](continue.md) instrukcji. Jeśli wyrażenie ma `true`, wykonywanie jest kontynuowane po pierwszej instrukcji w pętli. W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji następującej po pętli.

Możesz również wyjść `do-while` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `do` instrukcji. Wybierz **Uruchom** do uruchamiania kodu przykładu. Po tym można zmodyfikować kod i uruchom go ponownie.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [instrukcji](~/_csharplang/spec/statements.md#the-do-statement) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje iteracji](iteration-statements.md)
- [while — instrukcja](while.md)
