---
title: '\=Operator'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ba74f7a433687b306e8b4273f3a2a6d60583396
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator"></a>\\= — Operator
Dzieli wartość zmiennej lub właściwość przez wartość wyrażenia i przypisuje całkowitą wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Zmienna numeryczna lub właściwość.  
  
 `expression`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `\=` operator może być zmienną skalarną proste, właściwością lub element tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `\=` Operator dzieli wartość zmiennej lub właściwość po lewej stronie przez wartość jego prawej stronie i przypisuje wynik całkowitą zmienna lub właściwość po lewej stronie  
  
 Aby uzyskać więcej informacji na dzielenie liczby całkowitej, zobacz [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `\` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `\` operator wpływa na działanie `\=` operatora. Jeśli używa Twój kod `\=` na klasę lub strukturę, która overloads `\`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `\=` operatora, aby podzielić jedną `Integer` zmiennej sekundę i Przypisz liczbę całkowitą wyniku do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [/ = — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
