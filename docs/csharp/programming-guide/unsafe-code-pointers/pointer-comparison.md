---
title: "Porównanie wskaźników (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0b45b9152272244b9a0c9d0fa3787973f8f8182a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-comparison-c-programming-guide"></a>Porównanie wskaźników (Przewodnik programowania w języku C#)
Można użyć następujących operatorów do porównania wskaźniki dowolnego typu:  
  
 **==   !=   \<   >   \<=   >=**  
  
 Operatory porównania porównać adresy dwóch argumentów operacji, ponieważ, jeśli są one liczb całkowitych bez znaku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 `True`  
  
 `False`  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)  
 [Manipulowanie wskaźnikami](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [Typy wskaźnika](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Fixed — instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
