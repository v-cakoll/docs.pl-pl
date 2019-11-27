---
title: Function — Wyrażenie
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: d14d7c9bc701b5e06c51202c07c3b79832aba7cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331080"
---
# <a name="function-expression-visual-basic"></a>Function — Wyrażenie (Visual Basic)
Deklaruje parametry i kod, który definiuje funkcję wyrażenia lambda.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`parameterlist`|Opcjonalna. Lista nazw zmiennych lokalnych, które reprezentują parametry tej procedury. Nawiasy muszą być obecne nawet wtedy, gdy lista jest pusta. Zobacz [listę parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Wymagana. Pojedyncze wyrażenie. Typ wyrażenia jest zwracanym typem funkcji.|  
|`statements`|Wymagana. Lista instrukcji zwracających wartość przy użyciu instrukcji `Return`. (Patrz [instrukcja return](../../../visual-basic/language-reference/statements/return-statement.md)). Typ zwracanej wartości jest zwracanym typem funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie lambda* jest funkcją bez nazwy, która oblicza i zwraca wartość. Możesz użyć wyrażenia lambda wszędzie tam, gdzie można użyć typu delegata, z wyjątkiem jako argumentu `RemoveHandler`. Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z delegatami, zobacz [instrukcja Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) i [Swobodna konwersja delegata](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda jest podobna do funkcji standardowej. Różnice są następujące:  
  
- Wyrażenie lambda nie ma nazwy.  
  
- Wyrażenia lambda nie mogą mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.  
  
- Wyrażenia lambda nie używają klauzuli `As` do wyznaczania zwracanego typu funkcji. Zamiast tego, typ jest wywnioskowany na podstawie wartości, do której szacuje się treść wyrażenia lambda pojedynczego wiersza, lub wartości zwracanej wielowierszowego wyrażenia lambda. Na przykład jeśli treść wyrażenia lambda pojedynczego wiersza jest `Where cust.City = "London"`, jego typ zwracany jest `Boolean`.  
  
- Treść wyrażenia lambda pojedynczego wiersza musi być wyrażeniem, a nie instrukcją. Treść może składać się z wywołania procedury funkcji, ale nie wywołania procedury Sub.  
  
- Wszystkie parametry muszą mieć określone typy danych lub muszą zostać wywnioskowane.  
  
- Parametry opcjonalne i ParamArray są niedozwolone.  
  
- Parametry ogólne są niedozwolone.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano dwa sposoby tworzenia prostych wyrażeń lambda. Pierwszy używa `Dim`, aby podać nazwę funkcji. Aby wywołać funkcję, należy wysłać w wartości parametru.  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>Przykład  
 Alternatywnie można zadeklarować i uruchomić funkcję w tym samym czasie.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się przykład wyrażenia lambda, które zwiększa jego argument i zwraca wartość. Przykład pokazuje składnię jednowierszową i wieloliniową wyrażenia lambda dla funkcji. Aby uzyskać więcej przykładów, zobacz [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>Przykład  
 Wyrażenia lambda podstawą wiele operatorów zapytań w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]i mogą być używane jawnie w zapytaniach opartych na metodzie. W poniższym przykładzie przedstawiono typowe zapytanie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], po którym następuje tłumaczenie zapytania do formatu metody.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Aby uzyskać więcej informacji na temat metod zapytań, zobacz [zapytania](../../../visual-basic/language-reference/queries/index.md). Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Omówienie](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
- [Porównania wartości](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Wyrażenia logiczne](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If, operator](../../../visual-basic/language-reference/operators/if-operator.md)
- [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
