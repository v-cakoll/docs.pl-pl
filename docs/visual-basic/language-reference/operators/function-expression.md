---
title: Function — Wyrażenie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: cfdd17f6f4ee6c4ddb3fa73ab3ec9c5ce46a162f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183096"
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
|`parameterlist`|Opcjonalna. Lista nazwy zmiennych lokalnych, które reprezentują parametry tej procedury. Nawiasy musi być obecny, nawet wtedy, gdy lista jest pusta. Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Wymagane. Pojedyncze wyrażenie. Typ wyrażenia jest zwracany typ funkcji.|  
|`statements`|Wymagane. Listę instrukcji, która zwraca wartość przy użyciu `Return` instrukcji. (Zobacz [Return, instrukcja](../../../visual-basic/language-reference/statements/return-statement.md).) Typ wartości zwracanej jest zwracany typ funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 A *wyrażenia lambda* jest funkcją bez nazwy, który oblicza i zwraca wartość. Można użyć wyrażenia lambda dowolnym można użyć typu delegata, z wyjątkiem jako argument do `RemoveHandler`. Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z obiektów delegowanych, zobacz [instrukcji delegata](../../../visual-basic/language-reference/statements/delegate-statement.md) i [swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda przypomina w przypadku standardowej funkcji. Różnice są następujące:  
  
-   Wyrażenie lambda nie ma nazwy.  
  
-   Wyrażenia lambda nie może mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.  
  
-   Nie należy używać wyrażeń lambda `As` klauzuli do wyznaczenia zwracany typ funkcji. Zamiast tego typ jest wnioskowany z wartość, która daje w wyniku treść wyrażenia lambda jeden wiersz lub wartość zwracana wyrażenia lambda wielowierszowe. Na przykład, jeśli treść wyrażenia lambda jednowierszowego jest `Where cust.City = "London"`, jego typem zwracanym jest `Boolean`.  
  
-   Treść wyrażenia lambda w pojedynczej linii musi być wyrażeniem, nie instrukcję. Treść może obejmować wywołania procedurę function, ale nie po wywołaniu procedury sub.  
  
-   Musi mieć określony albo wszystkie parametry można wywnioskować typów danych lub wszystkich.  
  
-   Parametry opcjonalne i Paramarray nie są dozwolone.  
  
-   Parametry ogólne nie są dozwolone.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano dwa sposoby tworzenia wyrażeń lambda proste. Używa pierwszego `Dim` Podaj nazwę dla tej funkcji. Aby wywołać funkcję, Wyślij w wartości parametru.  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>Przykład  
 Alternatywnie można zadeklarować i uruchom funkcję w tym samym czasie.  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>Przykład  
 Oto przykład wyrażenie lambda, która zwiększa jej argument i zwraca wartość. W przykładzie pokazano oba jeden wiersz i wielowierszowe składnia wyrażenia lambda dla funkcji. Aby uzyskać więcej przykładów, zobacz [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>Przykład  
 Wyrażenia lambda podstawą wielu operatorów zapytań w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]i może służyć jawnie oparte na metodzie zapytania. W poniższym przykładzie przedstawiono typowe [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, następuje tłumaczenie zapytania do formatu metody.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Aby uzyskać więcej informacji na temat metody zapytań, zobacz [zapytania](../../../visual-basic/language-reference/queries/index.md). Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Przegląd](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Porównania wartości](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Wyrażenia logiczne](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [If, operator](../../../visual-basic/language-reference/operators/if-operator.md)  
 [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
