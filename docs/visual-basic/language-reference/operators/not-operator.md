---
title: "Not — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ac160aef7b7dc8acb8bf0211b403599692f2373c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="not-operator-visual-basic"></a>Not — Operator (Visual Basic)
Wykonuje logiczną negację na `Boolean` wyrażenie lub bitowego zaprzeczenia wyrażenia liczbowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
 `expression`  
 Wymagany. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
## <a name="remarks"></a>Uwagi  
 Dla `Boolean` wyrażenia w poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression` jest|Wartość `result` jest|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Dla wyrażeń liczbowych `Not` operator odwraca wartości bitowe dowolne wyrażenie liczbowe i ustawia bit w odpowiedniej `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression` jest|Bit w `result` jest|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne arytmetyczne operatorów, wszystkie operacje bitowe powinny być ujęte w nawiasy, aby zapewnić dokładne wykonywania.  
  
## <a name="data-types"></a>Typy danych  
 Logiczna Negacja, jest typ danych w wyniku `Boolean`. Dla bitową negację, typu danych jest taka sama, jak te `expression`. Jednak jeśli wyrażenie jest `Decimal`, wynikiem jest `Long`.  
  
## <a name="overloading"></a>Przeciążenie  
 `Not` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowania podczas jej argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Not` operator logiczny negacji podczas `Boolean` wyrażenia. Wynik jest `Boolean` wartość, która reprezentuje odwrotnej wartość wyrażenia.  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 Powyższy przykład produkuje wyniki `False` i `True`odpowiednio.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Not` operatora, aby wykonać logiczny negacji poszczególnych bitów wyrażenia liczbowego. Bit we wzorcu wynik jest ustawiony na odpowiadający mu bit we wzorcu operand, łącznie z bitem odwrotnej.  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 Powyższy przykład produkuje wyników –11, –9 i –7, odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
