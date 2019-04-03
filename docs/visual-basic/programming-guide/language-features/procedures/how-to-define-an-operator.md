---
title: 'Instrukcje: Definiowanie operatora (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 3a09657ee7a79b7f590adba0e4fb0c04a8e89043
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843646"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Instrukcje: Definiowanie operatora (Visual Basic)
Jeśli zdefiniowano klasy lub struktury, można zdefiniować zachowanie standardowego operatora (takie jak `*`, `<>`, lub `And`) gdy co najmniej jeden z operandów jest typu klasy lub struktury.  
  
 Zdefiniuj operator standardowego jako procedury operatora w obrębie klasy lub struktury. Wszystkie procedury operatora musi być `Public` `Shared`.  
  
 Definiowanie operatora dla klasy lub struktury jest również nazywany *przeciążenie* operatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `+` operator dla struktury o nazwie `height`. Struktura używa mierzoną w stopach i cali wysokości. Jeden *CAL* jest 2,54 cm, a drugi *i stopka* jest cala 12. Aby zapewnić znormalizowane wartości (w calach < 12.0), Konstruktor wykonuje *modulo* 12 arytmetyczne. `+` Operator używa konstruktora do generowania wartości znormalizowana.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Możesz przetestować struktury `height` następującym kodem.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  
  
  
## <a name="see-also"></a>Zobacz także

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: Definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Instrukcje: Wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Instrukcje: Używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)
- [Operator, instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod, operator](../../../../visual-basic/language-reference/operators/mod-operator.md)
