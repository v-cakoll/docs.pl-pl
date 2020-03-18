---
title: Funkcje anonimowe - Przewodnik po programowaniu Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: cfb0190ee263e65e8130a8925f76357a382eafa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712003"
---
# <a name="anonymous-functions-c-programming-guide"></a>Funkcje anonimowe (Przewodnik programowania C#)

Funkcja anonimowa jest instrukcją "inline" lub wyrażeniem, które może być używane wszędzie tam, gdzie oczekuje się typu delegata. Można go użyć do zainicjowania nazwanego pełnomocnika lub przekazania go zamiast nazwanego typu pełnomocnika jako parametrmetody.

Można użyć [wyrażenia lambda](lambda-expressions.md) lub [metody anonimowej,](../../language-reference/operators/delegate-operator.md) aby utworzyć funkcję anonimową. Zaleca się używanie wyrażeń lambda, ponieważ zapewniają one bardziej zwięzły i ekspresyjny sposób pisania kodu w wierszu. W przeciwieństwie do metod anonimowych niektóre typy wyrażeń lambda można przekonwertować na typy drzewa wyrażeń.

## <a name="the-evolution-of-delegates-in-c"></a>Ewolucja delegatów w C\#

 W języku C# 1.0 utworzono wystąpienie pełnomocnika, jawnie inicjując je za pomocą metody zdefiniowanej w innym miejscu w kodzie. C# 2.0 wprowadzono pojęcie metod anonimowych jako sposób pisania nienazwanych wbudowanych bloków instrukcji, które mogą być wykonywane w wywołaniu delegata. C# 3.0 wprowadzono wyrażenia lambda, które są podobne w koncepcji do metod anonimowych, ale bardziej wyraziste i zwięzłe. Te dwie funkcje są znane zbiorczo jako *funkcje anonimowe.* Ogólnie rzecz biorąc aplikacje, które są przeznaczone dla wersji 3.5 i nowszej .NET Framework należy użyć wyrażenia lambda.  
  
 W poniższym przykładzie przedstawiono ewolucję tworzenia delegata z c# 1.0 do C# 3.0:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [anonimowe wyrażenia funkcji](~/_csharplang/spec/expressions.md#anonymous-function-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje, wyrażenia i operatory](./index.md)
- [Wyrażenia Lambda](./lambda-expressions.md)
- [Delegaty](../delegates/index.md)
- [Drzewa wyrażeń (C#)](../concepts/expression-trees/index.md)
