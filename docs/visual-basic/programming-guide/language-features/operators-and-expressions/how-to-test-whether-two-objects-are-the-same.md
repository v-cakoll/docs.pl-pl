---
title: 'Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 005c91e6f4ec556a7e1bf255b47c8276a5d3d185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)
Jeśli masz dwie zmienne odwołujące się do obiektów, możesz użyć albo `Is` lub `IsNot` operatora i/lub do określenia, czy odnoszą się do tego samego wystąpienia.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Aby sprawdzić, czy dwa obiekty są takie same  
  
-   Użyj [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) lub [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) z dwie zmienne jako argumentów.  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 Warto podjąć pewne akcję w zależności od tego, czy dwa obiekty odwoływać się do tego samego wystąpienia. Powyższy przykład porównuje kontroli `c` przed aktywną kontrolkę w formularzu `f`. Jeśli wystąpi nie aktywny formant, lub jeśli istnieje jeden, ale nie jest to samo wystąpienie formantu jako `c`, a następnie `If` instrukcja nie powiedzie się i procedury zwraca bez dalszego przetwarzania.  
  
 Określa, czy używasz `Is` lub `IsNot` polega na wygodę osobistych użytkownika. Co może być bardziej czytelny niż w podane wyrażenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
