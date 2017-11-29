---
title: "Funkcje anonimowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 888743bb1c49df123b57b4d09e0251dbe1e049d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-functions-c-programming-guide"></a>Funkcje anonimowe (Przewodnik programowania w języku C#)
Funkcja anonimowa jest instrukcji "wbudowany" lub wyrażenie, które mogą służyć wszędzie tam, gdzie oczekiwany jest typ delegata. Można go zainicjować delegata o nazwie lub przekaż go zamiast typu delegata o nazwie jako parametru metody.  
  
 Istnieją dwa rodzaje funkcje anonimowe, które są omawiane w następujących tematach:  
  
-   [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
-   [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  Wyrażenia lambda, może być powiązana do drzewa wyrażeń, a także do delegatów.  
  
## <a name="the-evolution-of-delegates-in-c"></a>Rozwój delegatów w języku C#  
 W języku C# 1.0 utworzonego wystąpienia delegata przez jawne inicjowanie za pomocą metody, która została zdefiniowana w innym miejscu w kodzie. C# 2.0 wprowadzono pojęcie usługi metod anonimowych jako sposób zapisu bloków instrukcji nienazwane wbudowanego wykonanych w wywołaniu obiektu delegowanego. C# 3.0 wprowadzono wyrażenia lambda, które są podobne do metod anonimowych, ale bardziej obszerne i zwięzłe. Te dwie funkcje są nazywane *funkcje anonimowe*. Ogólnie rzecz biorąc, aplikacje których docelowe wersji 3.5 lub nowszej [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] powinien użycie wyrażeń lambda.  
  
 W poniższym przykładzie pokazano ewolucję utworzenia delegata z C# w wersji 1.0 C# 3.0:  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje, wyrażenia i operatory](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Obiekty delegowane](../../../csharp/programming-guide/delegates/index.md)  
 [Drzewa wyrażeń](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
