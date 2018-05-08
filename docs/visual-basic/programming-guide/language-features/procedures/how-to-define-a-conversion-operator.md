---
title: 'Porady: definiowanie operatora konwersji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 24bbe41af67f757cae661a78d482a423ff0ffd85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Porady: definiowanie operatora konwersji (Visual Basic)
Jeśli zdefiniowano klasę lub strukturę można zdefiniować typu operatora konwersji między typem klasy lub struktury i inny typ danych (takich jak `Integer`, `Double`, lub `String`).  
  
 Zdefiniuj konwersji typu jako [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) procedury w obrębie klasy lub struktury. Wszystkie procedury konwersji muszą być `Public Shared`, a każda z nich należy określić albo [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) lub [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano operatory konwersji między strukturę o nazwie `digit` i `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 Można przetestować struktury `digit` następującym kodem.  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury operatorów](./operator-procedures.md)  
 [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)  
 [Instrukcje: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)  
 [Instrukcje: używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)  
 [Operator, instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
