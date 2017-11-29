---
title: "new — Ograniczenie (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8557e056a664fd470b1f185b619d81235c8fcba7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="new-constraint-c-reference"></a>new — Ograniczenie (odwołanie w C#)
`new` Ograniczenia Określa, że wszystkich argumentów typu w deklaracji klasy ogólnej musi mieć publicznego konstruktora bez parametrów. Aby użyć nowego ograniczenia, typu nie mogą być abstrakcyjne.  
  
## <a name="example"></a>Przykład  
 Zastosuj `new` ograniczenia parametru typu w klasie ogólnego tworzy nowych wystąpień tego typu, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a>Przykład  
 Jeśli używasz `new()` ograniczenia inne ograniczenia, musi zostać określona ostatnich:  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)
