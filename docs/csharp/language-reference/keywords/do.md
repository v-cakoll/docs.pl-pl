---
title: do (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d24078d3fb985f643fb66aa456900d03d2ff3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="do-c-reference"></a>do (odwołanie w C#)
`do` Instrukcji, która wykonuje instrukcję lub blok instrukcji wielokrotnie aż wynikiem obliczenia określonego wyrażenia jest `false`. Treści pętli musi być ujęta w nawiasy klamrowe, `{}`, chyba że składa się z jednej instrukcji. W takim przypadku nawiasy klamrowe są opcjonalne.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `do-while` instrukcje pętli wykonania tak długo, jak zmienna `x` jest mniejsza niż 5.  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 W odróżnieniu od [podczas](../../../csharp/language-reference/keywords/while.md) instrukcji `do-while` pętla jest wykonywana raz przed Obliczanie wyrażenia warunkowego.  
  
 W dowolnym punktu `do-while` bloku, mogą być dzielone poza przy użyciu pętli [podziału](../../../csharp/language-reference/keywords/break.md) instrukcji. Można przejść bezpośrednio do `while` instrukcja obliczania wyrażeń przy użyciu [kontynuować](../../../csharp/language-reference/keywords/continue.md) instrukcji. Jeśli `while` wyrażenie ma wartość true, wykonywanie będzie kontynuowane przy pierwszej instrukcji w pętli. Jeśli wyrażenie ma wartość false, wykonywanie będzie kontynuowane przy pierwszej instrukcji po `do-while` pętli.  
  
 A `do-while` pętli również można został zakończony przez [goto](../../../csharp/language-reference/keywords/goto.md), [zwracać](../../../csharp/language-reference/keywords/return.md), lub [throw](../../../csharp/language-reference/keywords/throw.md) instrukcje.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [czy-while — instrukcja (C++)](/cpp/cpp/do-while-statement-cpp)  
 [Iteracja — instrukcje](../../../csharp/language-reference/keywords/iteration-statements.md)
