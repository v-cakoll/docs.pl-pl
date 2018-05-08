---
title: while (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 23c5ca3bb7dc401a894a6c3918fbaec9a9306153
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [while, instrukcja (C++)](/cpp/cpp/while-statement-cpp)  
 [Instrukcje iteracji](../../../csharp/language-reference/keywords/iteration-statements.md)
