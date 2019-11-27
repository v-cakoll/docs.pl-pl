---
title: 'Porady: definiowanie operatora konwersji'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 0ff95390206947e5a28f7a5b85547b496746a9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344902"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Porady: definiowanie operatora konwersji (Visual Basic)
Jeśli zdefiniowano klasę lub strukturę, można zdefiniować Operator konwersji typu między typem klasy lub struktury a innym typem danych (takim jak `Integer`, `Double`lub `String`).  
  
 Zdefiniuj konwersję typu jako procedurę [funkcji CType](../../../../visual-basic/language-reference/functions/ctype-function.md) w klasie lub strukturze. Wszystkie procedury konwersji muszą być `Public Shared`, a każdy z nich musi określać [rozszerzanie](../../../../visual-basic/language-reference/modifiers/widening.md) lub [zwężanie](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje operatory konwersji między strukturą o nazwie `digit` i `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Możesz przetestować strukturę `digit` przy użyciu następującego kodu.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Instrukcje: używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)
- [Operator, instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
