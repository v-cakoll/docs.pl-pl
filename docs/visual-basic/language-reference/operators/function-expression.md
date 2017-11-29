---
title: "Function — Wyrażenie (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1d9d1223b340b2172c12bd8c2f364e314e764b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="function-expression-visual-basic"></a>Function — Wyrażenie (Visual Basic)
Deklaruje parametry i kod, który definiuje wyrażenie lambda funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`parameterlist`|Opcjonalny. Lista nazwy zmiennych lokalnych, które reprezentują parametry tej procedury. Nawiasy musi być obecny, nawet wtedy, gdy lista jest pusta. Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Wymagany. Jedno wyrażenie. Typ wyrażenia jest zwracany typ funkcji.|  
|`statements`|Wymagany. Lista instrukcji, która zwraca wartość przy użyciu `Return` instrukcji. (Zobacz [instrukcja Return](../../../visual-basic/language-reference/statements/return-statement.md).) Typ wartości zwracanej jest zwracany typ funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 A *wyrażenia lambda* jest funkcją bez nazwy, która jest obliczana i zwraca wartość. Można użyć wyrażenia lambda dowolnym można użyć typu delegata, z wyjątkiem jako argument `RemoveHandler`. Aby uzyskać więcej informacji dotyczących obiektów delegowanych i korzystanie z wyrażenia lambda z delegatów, zobacz [instrukcji delegata](../../../visual-basic/language-reference/statements/delegate-statement.md) i [swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda podobny ze standardową funkcję. Różnice są następujące:  
  
-   Wyrażenia lambda nie ma nazwy.  
  
-   Wyrażenia lambda nie może mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.  
  
-   Wyrażenia lambda nie należy używać `As` klauzuli, aby określić typ zwracany funkcji. Zamiast tego typu jest wywnioskowany na podstawie wartości, która daje w wyniku treści wyrażenia lambda jeden wiersz lub wartość zwracana w wielowierszowym wyrażeniu lambda. Na przykład, jeśli treść wyrażenia lambda jeden wiersz jest `Where cust.City = "London"`, jego typem zwracanym jest `Boolean`.  
  
-   Treść wyrażenia lambda jeden wiersz musi być wyrażeniem, nie instrukcję. Treść może zawierać wywołania procedurę function, ale nie wywołaniu procedury sub.  
  
-   Albo wszystkie parametry muszą określono można wywnioskować typów danych lub wszystkich.  
  
-   Parametry opcjonalne i Paramarray są niedozwolone.  
  
-   Parametry ogólne są niedozwolone.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano dwa sposoby tworzenia wyrażenia lambda proste. Używa pierwszego `Dim` o podanie nazwy funkcji. W wywołaniu funkcji, wysyłania wartości parametru.  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>Przykład  
 Alternatywnie można zadeklarować i uruchomić funkcję w tym samym czasie.  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład zwiększa jej argument, który zwraca wartość wyrażenia lambda. W przykładzie zarówno jeden wiersz i wielowierszowe składnia wyrażenia lambda dla funkcji. Aby uzyskać więcej przykładów, zobacz [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>Przykład  
 Wyrażenia lambda opierają się wiele operatorów zapytań w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]i może służyć jawnie w zapytaniach oparte na metodzie. W poniższym przykładzie przedstawiono typowe [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, następuje translacja zapytania do formatu — metoda.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Aby uzyskać więcej informacji o metodach zapytania, zobacz [zapytania](../../../visual-basic/language-reference/queries/queries.md). Aby uzyskać więcej informacji dotyczących standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
## <a name="see-also"></a>Zobacz też  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Porównania wartości](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Wyrażenia logiczne](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Jeśli — Operator](../../../visual-basic/language-reference/operators/if-operator.md)  
 [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
