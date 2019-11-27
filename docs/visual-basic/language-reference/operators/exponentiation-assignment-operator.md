---
title: ^=, operator
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: fe5e8fc2b64b9e7c33483612071d338a0ee22768
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331295"
---
# <a name="-operator-visual-basic"></a>^= — Operator (Visual Basic)
Podnosi wartość zmiennej lub właściwości do potęgi wyrażenia i przypisuje wynik z powrotem do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagana. Dowolna zmienna lub właściwość numeryczna.  
  
 `expression`  
 Wymagana. Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie operatora `^=` może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operator `^=` najpierw podnosi wartość zmiennej lub właściwości (po lewej stronie operatora) do potęgi wartości wyrażenia (po prawej stronie operatora).... Następnie operator przypisuje wynik tej operacji z powrotem do zmiennej lub właściwości.  
  
 Visual Basic zawsze wykonuje potęgowanie w [podwójnym typie danych](../../../visual-basic/language-reference/data-types/double-data-type.md). Operandy dowolnego typu są konwertowane na `Double`, a wynik jest zawsze `Double`.  
  
 Wartość `expression` może być ułamkowa, ujemna lub obie.  
  
## <a name="overloading"></a>Przeciążenie  
 [Operator ^](../../../visual-basic/language-reference/operators/exponentiation-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie operatora `^` ma wpływ na zachowanie operatora `^=`. Jeśli kod używa `^=` na klasie lub strukturze, która przeciąża `^`, należy zapoznać się z jego ponownie zdefiniowanym zachowaniem. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `^=`, aby podnieść wartość jednej zmiennej `Integer` do potęgi drugiej zmiennej i przypisać wynik do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz także

- [^, operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
