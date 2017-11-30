---
title: "Porady: określanie, czy dwa obiekty są jednakowe (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02083a93e63fe799f529776f777ca877d2d138b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Porady: określanie, czy dwa obiekty są jednakowe (Visual Basic)
W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], dwóch odwołań do zmiennych są traktowane jako identyczne, jeśli ich wskaźniki są takie same, to znaczy, jeśli obie zmienne wskazać to samo wystąpienie klasy w pamięci. Na przykład w aplikacji formularzy systemu Windows, można porównanie, aby określić, czy bieżące wystąpienie (`Me`) jest taka sama jak konkretnego wystąpienia, takich jak `Form2`.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]udostępnia dwa operatory porównanie wskaźników. [Operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) zwraca `True` Jeśli obiekty są identyczne i [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) zwraca `True` Jeśli nie są one.  
  
## <a name="determining-if-two-objects-are-identical"></a>Określanie, czy dwa obiekty są jednakowe  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Aby sprawdzić, czy dwa obiekty są identyczne  
  
1.  Konfigurowanie `Boolean` wyrażenia do testowania dwóch obiektów.  
  
2.  W wyrażeniu testowania należy używać `Is` operatora z tymi dwoma obiektami jako argumentów.  
  
     `Is`Zwraca `True` Jeśli punkt obiekty do tego samego wystąpienia klasy.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Określanie, czy dwa obiekty nie są identyczne  
 Czasami chcesz wykonać akcję, jeśli dwa obiekty nie są identyczne, i można go połączyć nieodpowiednich `Not` i `Is`, na przykład `If Not obj1 Is obj2`. W takim przypadku można użyć `IsNot` operatora.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Aby określić, czy dwa obiekty nie są identyczne  
  
1.  Konfigurowanie `Boolean` wyrażenia do testowania dwóch obiektów.  
  
2.  W wyrażeniu testowania należy używać `IsNot` operatora z tymi dwoma obiektami jako argumentów.  
  
     `IsNot`Zwraca `True` Jeśli obiekty nie mogą wskazywać tego samego wystąpienia klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład testów pary `Object` zmienne, aby zobaczyć, jeśli one wskazywać tego samego wystąpienia klasy.  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 W poprzednim przykładzie przedstawiono następujące dane wyjściowe.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Zobacz też  
 [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Is — Operator](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot — Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Porady: Określanie, czy dwa obiekty są powiązane](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
