---
title: "^= — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9d87d2f090a8c18aaab742e73878c7b80f55c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>^= — Operator (Visual Basic)
Podnosi wartość zmiennej lub właściwości do potęgi wyrażenia i przypisuje wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Zmienna numeryczna lub właściwość.  
  
 `expression`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `^=` operator może być zmienną skalarną proste, właściwością lub element tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `^=` Operator najpierw podnosi wartość zmiennej lub właściwości (po lewej stronie operatora) do potęgi równej wartości wyrażenia (po prawej stronie operatora). Następnie operator przypisuje wynik tej operacji do zmiennej lub właściwości.  
  
 Visual Basic zawsze przeprowadza potęgowania w [— typ danych Double](../../../visual-basic/language-reference/data-types/double-data-type.md). Argumenty operacji dowolnego innego typu są konwertowane na `Double`, a wynik jest zawsze `Double`.  
  
 Wartość `expression` może być ułamkową ujemne lub oba.  
  
## <a name="overloading"></a>Przeciążenie  
 [^ — Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `^` operator wpływa na działanie `^=` operatora. Jeśli używa Twój kod `^=` na klasę lub strukturę, która overloads `^`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `^=` operatora, aby podnieść wartość jednego `Integer` zmiennej do potęgi równej drugiej zmiennej i przypisz wynik do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [^ — Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
