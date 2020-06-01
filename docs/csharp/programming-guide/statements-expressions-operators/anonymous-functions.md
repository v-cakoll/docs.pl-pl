---
title: Funkcje anonimowe — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: c99aaf4f35d2d294a9f07de54129bb3b4fbfbfde
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241906"
---
# <a name="anonymous-functions-c-programming-guide"></a>Funkcje anonimowe (Przewodnik programowania w języku C#)

Funkcja anonimowa jest instrukcją "inline" lub wyrażeniem, które może być używane wszędzie tam, gdzie oczekiwany jest typ delegata. Można go użyć do zainicjowania nazwanego delegata lub przekazać go zamiast nazwanego typu delegata jako parametru metody.

Możesz użyć [wyrażenia lambda](lambda-expressions.md) lub [metody anonimowej](../../language-reference/operators/delegate-operator.md) , aby utworzyć funkcję anonimową. Zalecamy używanie wyrażeń lambda, ponieważ zapewniają one bardziej zwięzły i jednoznaczny sposób pisania kodu śródwierszowego. W przeciwieństwie do metod anonimowych niektóre typy wyrażeń lambda można przekonwertować na typy drzewa wyrażenia.

## <a name="the-evolution-of-delegates-in-c"></a>Ewolucja delegatów w języku C\#

 W języku C# 1,0 utworzono wystąpienie delegata, jawnie inicjując go za pomocą metody, która została zdefiniowana w innym miejscu w kodzie. W języku C# 2,0 wprowadzono koncepcję metod anonimowych jako sposób pisania nienazwanych bloków instrukcji wbudowanych, które mogą być wykonywane w wywołaniu delegata. W języku C# 3,0 wprowadzono wyrażenia lambda, które są podobne w koncepcji metod anonimowych, ale bardziej wyraźne i zwięzłe. Te dwie funkcje są określane zbiorczo jako *funkcje anonimowe*. Ogólnie rzecz biorąc, aplikacje przeznaczone dla .NET Framework 3,5 lub nowszych powinny używać wyrażeń lambda.  
  
 Poniższy przykład ilustruje ewolucję tworzenia delegatów z C# 1,0 do C# 3,0:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [specyfikacji języka C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje, wyrażenia i operatory](./index.md)
- [Wyrażenia lambda](./lambda-expressions.md)
- [Delegaci](../delegates/index.md)
- [Drzewa wyrażeń (C#)](../concepts/expression-trees/index.md)
