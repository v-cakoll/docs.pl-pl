---
title: Function, wyrażenie
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: a9b621ff03f833fcf0f07f876fd864ee963bef75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371184"
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
|`parameterlist`|Opcjonalny. Lista nazw zmiennych lokalnych, które reprezentują parametry tej procedury. Nawiasy muszą być obecne nawet wtedy, gdy lista jest pusta. Zobacz [listę parametrów](../statements/parameter-list.md).|  
|`expression`|Wymagany. Pojedyncze wyrażenie. Typ wyrażenia jest zwracanym typem funkcji.|  
|`statements`|Wymagany. Lista instrukcji zwracających wartość przy użyciu `Return` instrukcji. (Patrz [instrukcja return](../statements/return-statement.md)). Typ zwracanej wartości jest zwracanym typem funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie lambda* jest funkcją bez nazwy, która oblicza i zwraca wartość. Możesz użyć wyrażenia lambda wszędzie tam, gdzie można użyć typu delegata, z wyjątkiem argumentu `RemoveHandler` . Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z delegatami, zobacz [instrukcja Delegate](../statements/delegate-statement.md) i [Swobodna konwersja delegata](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda jest podobna do funkcji standardowej. Różnice są następujące:  
  
- Wyrażenie lambda nie ma nazwy.  
  
- Wyrażenia lambda nie mogą mieć modyfikatorów, takich jak `Overloads` lub `Overrides` .  
  
- Wyrażenia lambda nie używają `As` klauzuli do wyznaczania zwracanego typu funkcji. Zamiast tego, typ jest wywnioskowany na podstawie wartości, do której szacuje się treść wyrażenia lambda pojedynczego wiersza, lub wartości zwracanej wielowierszowego wyrażenia lambda. Na przykład jeśli treść wyrażenia lambda pojedynczego wiersza ma wartość `Where cust.City = "London"` , jego typem zwracanym jest `Boolean` .  
  
- Treść wyrażenia lambda pojedynczego wiersza musi być wyrażeniem, a nie instrukcją. Treść może składać się z wywołania procedury funkcji, ale nie wywołania procedury Sub.  
  
- Wszystkie parametry muszą mieć określone typy danych lub muszą zostać wywnioskowane.  
  
- Parametry opcjonalne i ParamArray są niedozwolone.  
  
- Parametry ogólne są niedozwolone.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano dwa sposoby tworzenia prostych wyrażeń lambda. Pierwszy używa `Dim` do podania nazwy dla funkcji. Aby wywołać funkcję, należy wysłać w wartości parametru.  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>Przykład  
 Alternatywnie można zadeklarować i uruchomić funkcję w tym samym czasie.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się przykład wyrażenia lambda, które zwiększa jego argument i zwraca wartość. Przykład pokazuje składnię jednowierszową i wieloliniową wyrażenia lambda dla funkcji. Aby uzyskać więcej przykładów, zobacz [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>Przykład  
 Wyrażenia lambda podstawą wiele operatorów zapytań w zapytaniach zintegrowanych z językiem (LINQ) i mogą być używane jawnie w zapytaniach opartych na metodzie. W poniższym przykładzie przedstawiono typowe zapytanie LINQ, po którym następuje tłumaczenie zapytania do formatu metody.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Aby uzyskać więcej informacji na temat metod zapytań, zobacz [zapytania](../queries/index.md). Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Omówienie](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Function, instrukcja](../statements/function-statement.md)
- [Wyrażenia lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Operatory i wyrażenia](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
- [Porównania wartości](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Wyrażenia logiczne](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If, operator](if-operator.md)
- [Swobodna konwersja delegatów](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
