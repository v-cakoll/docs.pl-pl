---
title: "Tablice wielowymiarowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab3a93c21ddb9541a6149967605b851ea5a50a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Tablice wielowymiarowe (Przewodnik programowania w języku C#)
Tablice mogą mieć więcej niż jednym wymiarze. Na przykład następujące oświadczenie tworzy jest tablicą dwuwymiarową cztery wierszy z dwóch kolumn.  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 Następujące oświadczenie tworzy tablicę trzy wymiary, 4, 2 i 3.  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Inicjowanie tablicy  
 Można zainicjować tablicy po deklaracji, jak to pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 Można również zainicjować tablicy bez określania rangę.  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 Jeśli wybierzesz opcję zadeklarować zmienną tablicową bez inicjowania, należy użyć `new` operatora, aby przypisać tablicę zmiennej. Korzystanie z `new` przedstawiono w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 Poniższy przykład przypisuje wartość do elementu określonej tablicy.  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 Podobnie poniższy przykład pobiera wartość elementu określonego tablicy i przypisuje go do zmiennej `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 Poniższy przykład kodu inicjuje elementów tablicy wartości domyślne (z wyjątkiem Tablice nieregularne).  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
