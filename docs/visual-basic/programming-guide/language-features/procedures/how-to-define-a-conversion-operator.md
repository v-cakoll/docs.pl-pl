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
ms.openlocfilehash: 53b0211c6304625edd7ac24fa52ff0c051d8f0a0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388092"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Porady: definiowanie operatora konwersji (Visual Basic)
Jeśli zdefiniowano klasę lub strukturę, można zdefiniować Operator konwersji typu między typem klasy lub struktury a innym typem danych (np `Integer` `Double` ., lub `String` ).  
  
 Zdefiniuj konwersję typu jako procedurę [funkcji CType](../../../language-reference/functions/ctype-function.md) w klasie lub strukturze. Wszystkie procedury konwersji muszą mieć `Public Shared` wartość, a każdy z nich musi określać [rozszerzanie](../../../language-reference/modifiers/widening.md) lub [zwężanie](../../../language-reference/modifiers/narrowing.md).  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje operatory konwersji między strukturą o nazwie `digit` i a `Byte` .  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Możesz przetestować strukturę `digit` przy użyciu następującego kodu.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Zobacz też

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)
- [Instrukcje: używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)
- [Operator — Instrukcja](../../../language-reference/statements/operator-statement.md)
- [Structure — Instrukcja](../../../language-reference/statements/structure-statement.md)
- [Instrukcje: Deklarowanie struktury](../data-types/how-to-declare-a-structure.md)
- [Konwersje jawne i niejawne](../data-types/implicit-and-explicit-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../data-types/widening-and-narrowing-conversions.md)
