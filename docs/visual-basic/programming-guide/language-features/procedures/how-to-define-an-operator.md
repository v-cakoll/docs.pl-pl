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
ms.openlocfilehash: 14aa25de78eb357f8474d3828aa45e48e7a4f9c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126116"
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
- [Operator — Instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure — Instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcje: Deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod — Operator](../../../../visual-basic/language-reference/operators/mod-operator.md)
