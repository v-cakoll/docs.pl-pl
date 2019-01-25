---
title: 'Instrukcje: Sprawdź, czy dwa obiekty są tego samego (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 4130dfbe70682e28b6bb15db633ede2790e20aa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595555"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Instrukcje: Sprawdź, czy dwa obiekty są tego samego (Visual Basic)
Jeśli masz dwie zmienne odwołujące się do obiektów, można użyć albo `Is` lub `IsNot` operatora i / lub, aby ustalić, czy odnoszą się do tego samego wystąpienia.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Aby sprawdzić, czy dwa obiekty są takie same  
  
-   Użyj [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) lub [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) z dwoma zmiennymi argumentami operacji.  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 Możesz chcieć wykonać określone działanie w zależności od tego, czy dwa obiekty odnoszą się do tego samego wystąpienia. W poprzednim przykładzie porównano kontroli `c` względem aktywny formant w formularzu `f`. Jeśli istnieje nie aktywną kontrolkę, lub jeżeli istnieje jeden, ale nie jest tego samego wystąpienia formantu, co `c`, a następnie `If` instrukcja kończy się niepowodzeniem i procedura jest zwracane bez dalszego przetwarzania.  
  
 Czy używać `Is` lub `IsNot` jest kwestią osobistych wygodę dla użytkownika. Jeden może być łatwiejsza do odczytania niż ten drugi z danego wyrażenia.  
  
## <a name="see-also"></a>Zobacz także
- [Operatory porównania w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
