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
ms.openlocfilehash: dbb268175d197e7b931af45a98f3a273c593e5a3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819129"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Instrukcje: Sprawdź, czy dwa obiekty są tego samego (Visual Basic)
Jeśli masz dwie zmienne odwołujące się do obiektów, można użyć albo `Is` lub `IsNot` operatora i / lub, aby ustalić, czy odnoszą się do tego samego wystąpienia.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Aby sprawdzić, czy dwa obiekty są takie same  
  
-   Użyj [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) lub [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) z dwoma zmiennymi argumentami operacji.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 Możesz chcieć wykonać określone działanie w zależności od tego, czy dwa obiekty odnoszą się do tego samego wystąpienia. W poprzednim przykładzie porównano kontroli `c` względem aktywny formant w formularzu `f`. Jeśli istnieje nie aktywną kontrolkę, lub jeżeli istnieje jeden, ale nie jest tego samego wystąpienia formantu, co `c`, a następnie `If` instrukcja kończy się niepowodzeniem i procedura jest zwracane bez dalszego przetwarzania.  
  
 Czy używać `Is` lub `IsNot` jest kwestią osobistych wygodę dla użytkownika. Jeden może być łatwiejsza do odczytania niż ten drugi z danego wyrażenia.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory porównania w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
