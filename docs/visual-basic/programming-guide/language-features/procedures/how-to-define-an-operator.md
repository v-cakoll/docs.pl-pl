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
ms.openlocfilehash: 49b9c8d1a6db56a56b50c16b4a6bb5b928df6c7d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388040"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Porady: definiowanie operatora (Visual Basic)
Jeśli zdefiniowano klasę lub strukturę, można zdefiniować zachowanie operatora standardowego (na przykład `*` , `<>` lub `And` ), gdy jeden lub oba operandy są typu klasy lub struktury.  
  
 Zdefiniuj operatora standardowego jako procedurę operatora w klasie lub strukturze. Wszystkie procedury operatora muszą być `Public` `Shared` .  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `+` operatora dla struktury o nazwie `height` . Struktura używa wysokości mierzona w metrach i calach. 1 *cal* wynosi 2,54 centymetrów, *a jedna z* nich jest 12 cali. Aby zapewnić znormalizowaną wartość (w calach < 12,0), Konstruktor wykonuje *modulo* 12. `+`Operator używa konstruktora do generowania znormalizowanych wartości.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Możesz przetestować strukturę `height` przy użyciu następującego kodu.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>Zobacz też

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Instrukcje: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Instrukcje: używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)
- [Operator — Instrukcja](../../../language-reference/statements/operator-statement.md)
- [Structure — Instrukcja](../../../language-reference/statements/structure-statement.md)
- [Instrukcje: Deklarowanie struktury](../data-types/how-to-declare-a-structure.md)
- [Mod — Operator](../../../language-reference/operators/mod-operator.md)
