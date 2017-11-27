---
title: "while (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords: while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a>while (odwołanie w C#)
`while` Instrukcji wykonuje instrukcję lub blok instrukcji, dopóki wynikiem obliczenia określonego wyrażenia jest `false`.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>Przykład  
 Ponieważ test `while` wyrażenie ma miejsce przed każdym wykonywania pętli, `while` pętla jest wykonywana zero lub więcej razy. To różni się od [czy](../../../csharp/language-reference/keywords/do.md) pętli, które wykonuje jeden lub więcej razy.  
  
 A `while` pętli może zostać zakończony, kiedy [podziału](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [zwracać](../../../csharp/language-reference/keywords/return.md), lub [throw](../../../csharp/language-reference/keywords/throw.md) instrukcji przekazuje sterowanie poza pętli. Aby przekazanie sterowania do następnej iteracji bez wyjścia z pętli, należy użyć [kontynuować](../../../csharp/language-reference/keywords/continue.md) instrukcji. Zwróć uwagę różnice w danych wyjściowych w trzech poprzednich przykładach, w zależności od tego, gdzie `int n` jest zwiększany. W przykładzie poniżej żadnych danych wyjściowych jest generowany.  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [while — instrukcja (C++)](/cpp/cpp/while-statement-cpp)  
 [Iteracja — instrukcje](../../../csharp/language-reference/keywords/iteration-statements.md)
