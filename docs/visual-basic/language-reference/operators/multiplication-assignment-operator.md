---
title: "*= — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0a2c638f3faaf20fadb745ef437941ee29d4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>*= — Operator (Visual Basic)
Mnoży wartość zmiennej lub właściwość przez wartość wyrażenia i przypisuje wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Zmienna numeryczna lub właściwość.  
  
 `expression`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `*=` operator może być zmienną skalarną proste, właściwością lub element tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `*=` Operator najpierw Mnoży wartość wyrażenia (po prawej stronie operatora) przez wartość zmiennej lub właściwości (po lewej stronie operatora). Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.  
  
## <a name="overloading"></a>Przeciążenie  
 [* — Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `*` operator wpływa na działanie `*=` operatora. Jeśli używa Twój kod `*=` na klasę lub strukturę, która overloads `*`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `*=` operatora, aby pomnożyć jedną `Integer` zmiennej sekundę i przypisz wynik do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [* — Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md)  
 [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
