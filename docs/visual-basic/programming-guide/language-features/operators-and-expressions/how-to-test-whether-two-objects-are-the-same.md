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
ms.openlocfilehash: b215225dbc2d8c0d2bdfe2206e5d4a4f1faa6d0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403424"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)
Jeśli istnieją dwie zmienne odwołujące się do obiektów, można użyć `Is` operatora OR lub `IsNot` obu, aby określić, czy odwołują się do tego samego wystąpienia.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Aby sprawdzić, czy dwa obiekty są takie same  
  
- Użyj [operatora is](../../../language-reference/operators/is-operator.md) lub [operatora IsNot](../../../language-reference/operators/isnot-operator.md) z dwiema zmiennymi jako operandami.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 Możesz chcieć wykonać określoną akcję w zależności od tego, czy dwa obiekty odwołują się do tego samego wystąpienia. Poprzedni przykład porównuje kontrolę `c` z aktywną kontrolką w formularzu `f` . Jeśli nie ma aktywnej kontrolki lub jeśli istnieje, ale nie jest to samo wystąpienie formantu co `c` , `If` instrukcja kończy się niepowodzeniem, a procedura zwróci wartość bez dalszej obróbki.  
  
 Bez względu na to, czy korzystasz z możliwości użytkownika, czy `Is` też `IsNot` jest to osobna wygoda. Jeden z nich może być łatwiejszy do odczytania w danym wyrażeniu.  
  
## <a name="see-also"></a>Zobacz też

- [Operatory porównania w Visual Basic](comparison-operators.md)
