---
title: 'Porady: testowanie, czy dwa obiekty są takie same'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343620"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)
Jeśli istnieją dwie zmienne odwołujące się do obiektów, można użyć operatora `Is` lub `IsNot` lub obu, aby określić, czy odwołują się do tego samego wystąpienia.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Aby sprawdzić, czy dwa obiekty są takie same  
  
- Użyj [operatora is](../../../../visual-basic/language-reference/operators/is-operator.md) lub [operatora IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) z dwiema zmiennymi jako operandami.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 Możesz chcieć wykonać określoną akcję w zależności od tego, czy dwa obiekty odwołują się do tego samego wystąpienia. Poprzedni przykład porównuje `c` formantu z aktywną kontrolką w `f`formularza. Jeśli nie ma aktywnej kontrolki lub jeśli istnieje, ale nie jest to samo wystąpienie kontrolki co `c`, instrukcja `If` kończy się niepowodzeniem, a procedura zwróci wartość bez dalszej obróbki.  
  
 Bez względu na to, czy korzystasz z `Is`, czy `IsNot`, to osobista wygoda użytkownika. Jeden z nich może być łatwiejszy do odczytania w danym wyrażeniu.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
