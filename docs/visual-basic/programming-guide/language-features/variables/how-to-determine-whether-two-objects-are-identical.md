---
title: 'Porady: określanie, czy dwa obiekty są jednakowe'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348597"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Porady: określanie, czy dwa obiekty są jednakowe (Visual Basic)
W Visual Basic, dwa odwołania do zmiennych są uważane za identyczne, jeśli ich wskaźniki są takie same, czyli jeśli obie zmienne wskazują na to samo wystąpienie klasy w pamięci. Na przykład w aplikacji Windows Forms można przeprowadzić porównanie, aby określić, czy bieżące wystąpienie (`Me`) jest takie samo jak określone wystąpienie, takie jak `Form2`.  
  
 Visual Basic udostępnia dwa operatory do porównywania wskaźników. [Operator is](../../../../visual-basic/language-reference/operators/is-operator.md) zwraca `True`, jeśli obiekty są identyczne, a [operator IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) zwraca `True`, jeśli nie.  
  
## <a name="determining-if-two-objects-are-identical"></a>Określanie, czy dwa obiekty są identyczne  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Aby określić, czy dwa obiekty są identyczne  
  
1. Skonfiguruj wyrażenie `Boolean`, aby przetestować dwa obiekty.  
  
2. W wyrażeniu testowym Użyj operatora `Is` z dwoma obiektami jako operandami.  
  
     `Is` zwraca `True`, jeśli obiekty wskazują to samo wystąpienie klasy.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Określanie, czy dwa obiekty nie są identyczne  
 Czasami chcesz wykonać akcję, jeśli dwa obiekty nie są identyczne i można niewygodna połączyć `Not` i `Is`, na przykład `If Not obj1 Is obj2`. W takim przypadku można użyć operatora `IsNot`.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Aby określić, czy dwa obiekty nie są identyczne  
  
1. Skonfiguruj wyrażenie `Boolean`, aby przetestować dwa obiekty.  
  
2. W wyrażeniu testowym Użyj operatora `IsNot` z dwoma obiektami jako operandami.  
  
     `IsNot` zwraca `True`, jeśli obiekty nie wskazują tego samego wystąpienia klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład sprawdza pary zmiennych `Object`, aby sprawdzić, czy wskazują one na to samo wystąpienie klasy.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 W poprzednim przykładzie przedstawiono następujące dane wyjściowe.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Zobacz także

- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Is, operator](../../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot, operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Instrukcje: określanie, czy dwa obiekty są powiązane](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
