---
title: 'Porady: definiowanie operatora'
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
ms.openlocfilehash: b99af8ff4d5428f1749bfc1a4c51a136f12405ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344874"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Porady: definiowanie operatora (Visual Basic)
Jeśli zdefiniowano klasę lub strukturę, można zdefiniować zachowanie standardowego operatora (takiego jak `*`, `<>`lub `And`), gdy jeden lub oba operandy są typu klasy lub struktury.  
  
 Zdefiniuj operatora standardowego jako procedurę operatora w klasie lub strukturze. Wszystkie procedury operatora muszą być `Public` `Shared`.  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano operator `+` dla struktury o nazwie `height`. Struktura używa wysokości mierzona w metrach i calach. 1 *cal* wynosi 2,54 centymetrów, *a jedna z* nich jest 12 cali. Aby zapewnić znormalizowaną wartość (w calach < 12,0), Konstruktor wykonuje *modulo* 12. Operator `+` używa konstruktora do generowania znormalizowanych wartości.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Możesz przetestować strukturę `height` przy użyciu następującego kodu.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>Zobacz także

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Instrukcje: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Instrukcje: używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)
- [Operator, instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod, operator](../../../../visual-basic/language-reference/operators/mod-operator.md)
