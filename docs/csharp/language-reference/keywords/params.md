---
title: params (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 692c2f61ae99f1c1c8e04a5a1bcad08814d286fe
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753953"
---
# <a name="params-c-reference"></a>params (odwołanie w C#)
Za pomocą `params` — słowo kluczowe, można określić [parametru metody](../../../csharp/language-reference/keywords/method-parameters.md) która przyjmuje zmienną liczbę argumentów.  
  
 Możesz wysłać rozdzielana przecinkami lista argumentów o typie określonym w deklaracji parametrów lub tablice argumentów określonego typu. Możesz również wysłać bez argumentów. Jeśli wyślesz żadnych argumentów, długość `params` listy wynosi zero.  
  
 Żadne dodatkowe parametry są dozwolone po `params` — słowo kluczowe w deklaracji metody i tylko jeden `params` słowo kluczowe jest dozwolone w deklaracji metody.  
 
 Deklarowany typ `params` parametr musi być tablicy jednowymiarowej, co ilustruje poniższy przykład. W przeciwnym razie błąd kompilatora [CS0225](../../../csharp/misc/cs0225.md) występuje.
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano różne sposoby, w których argumenty mogą być wysyłane do `params` parametru.  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
