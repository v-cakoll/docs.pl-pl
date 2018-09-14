---
title: do (odwołanie w C#)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 89c13f5b547c13052e229ff6eb3a39ae5babce41
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591007"
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

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)  
- [do-while, instrukcja (C++)](/cpp/cpp/do-while-statement-cpp)  
- [Instrukcje iteracji](iteration-statements.md)  
- [while — instrukcja](while.md)  
