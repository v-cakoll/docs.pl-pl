---
title: 'Instrukcje: Definiowanie operatora konwersji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 76d0769456e30766b830023c1f27381ceca59cbb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521533"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Instrukcje: Definiowanie operatora konwersji (Visual Basic)
Jeśli zdefiniowano klasy lub struktury, można zdefiniować typ operatora konwersji między typem klasy lub struktury i inny typ danych (takich jak `Integer`, `Double`, lub `String`).  
  
 Zdefiniuj konwersji typu jako [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md) procedury w obrębie klasy lub struktury. Wszystkie procedury konwersji muszą być `Public Shared`, a każdy z nich należy określić [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) lub [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Definiowanie operatora dla klasy lub struktury jest również nazywany *przeciążenie* operatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano operatory konwersji między strukturę o nazwie `digit` i `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 Możesz przetestować struktury `digit` następującym kodem.  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: Definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: Wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Instrukcje: Używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)
- [Operator, instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
