---
title: while (odwołanie w C#)
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: e3e9493b5371fbd6f53a779ba73743efc6d6e05b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43390027"
---
# <a name="while-c-reference"></a>while (odwołanie w C#)

`while` Instrukcji wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne, które daje w wyniku `true`. Ponieważ to wyrażenie jest obliczane przed każdym wykonaniu pętli, `while` pętla jest wykonywana zero lub więcej razy. To różni się od [czy](do.md) pętli, która wykonuje jeden lub więcej razy.

W dowolnym punkcie w `while` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji.

Użytkownik może przechodzić bezpośrednio do obliczania `while` wyrażenie, używając [nadal](continue.md) instrukcji. Jeśli wyrażenie ma `true`, wykonywanie jest kontynuowane po pierwszej instrukcji w pętli. W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji następującej po pętli.

Możesz również wyjść `while` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `while` instrukcji. Wybierz **Uruchom** do uruchamiania kodu przykładu. Po tym można zmodyfikować kod i uruchom go ponownie.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)  
- [while, instrukcja (C++)](/cpp/cpp/while-statement-cpp)  
- [Instrukcje iteracji](iteration-statements.md)  
- [— Instrukcja](do.md)  
