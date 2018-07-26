---
title: new — Ograniczenie (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199466"
---
# <a name="new-constraint-c-reference"></a>new — Ograniczenie (odwołanie w C#)
`new` Ograniczenie Określa, że dowolny argument typu w deklaracji klasy ogólnej musi mieć publicznego konstruktora bez parametrów. Aby użyć nowego ograniczenia, typ nie może być abstrakcyjna.  
  
## <a name="example"></a>Przykład  
 Zastosuj `new` ograniczenie parametru typu, gdy ogólne klasy tworzy nowe wystąpienia typu, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a>Przykład  
 Kiedy używasz `new()` ograniczenie z innymi ograniczeniami, musi być określona ostatnio:  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)
