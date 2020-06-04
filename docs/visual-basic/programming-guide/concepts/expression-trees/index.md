---
title: Drzewa wyrażeń
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: 5d30b2e2e66aa322e6d43b5fbf4a4baf3435b2a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410969"
---
# <a name="expression-trees-visual-basic"></a>Drzewa wyrażeń (Visual Basic)
Drzewa wyrażeń reprezentują kod w strukturze danych przypominającej drzewo, gdzie każdy węzeł jest wyrażeniem, na przykład wywołaniem metody lub operacją binarną, taką jak `x < y` .  
  
 Można skompilować i uruchomić kod reprezentowany przez drzewa wyrażeń. Umożliwia to dynamiczną modyfikację kodu wykonywalnego, wykonywanie zapytań LINQ w różnych bazach danych i tworzenie zapytań dynamicznych. Aby uzyskać więcej informacji na temat drzew wyrażeń w LINQ, zobacz [jak: używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Drzewa wyrażeń są również używane w środowisku uruchomieniowym języka dynamicznego (DLR) w celu zapewnienia współdziałania między językami dynamicznymi i .NET Framework i umożliwiają autorom kompilatora emitowanie drzew wyrażeń zamiast języka pośredniego firmy Microsoft (MSIL). Aby uzyskać więcej informacji na temat DLR, zobacz [Omówienie środowiska uruchomieniowego języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Można utworzyć drzewo wyrażeń w języku C# lub kompilator Visual Basic na podstawie anonimowego wyrażenia lambda lub można utworzyć drzewa wyrażeń ręcznie przy użyciu <xref:System.Linq.Expressions> przestrzeni nazw.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Tworzenie drzew wyrażeń na podstawie wyrażeń lambda  
 Gdy wyrażenie lambda jest przypisane do zmiennej typu <xref:System.Linq.Expressions.Expression%601> , kompilator emituje kod w celu skompilowania drzewa wyrażenia, które reprezentuje wyrażenie lambda.  
  
 Kompilator Visual Basic może generować drzewa wyrażeń tylko z wyrażeń lambda (lub jednowierszowych wyrażeń lambda). Nie można analizować instrukcji lambda (lub wielowierszowych wyrażeń lambda). Aby uzyskać więcej informacji na temat wyrażeń lambda w Visual Basic, zobacz [lambda Expressions](../../language-features/procedures/lambda-expressions.md).  
  
 Poniższy przykład kodu przedstawia sposób, w jaki kompilator Visual Basic tworzy drzewo wyrażenia, które reprezentuje wyrażenie lambda `Function(num) num < 5` .  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Tworzenie drzew wyrażeń przy użyciu interfejsu API  
 Aby utworzyć drzewa wyrażeń przy użyciu interfejsu API, użyj <xref:System.Linq.Expressions.Expression> klasy. Ta klasa zawiera statyczne metody fabryki, które tworzą węzły drzewa wyrażenia określonych typów, na przykład, <xref:System.Linq.Expressions.ParameterExpression> która reprezentuje zmienną lub parametr lub <xref:System.Linq.Expressions.MethodCallExpression> , który reprezentuje wywołanie metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> i inne typy specyficzne dla wyrażenia są również zdefiniowane w <xref:System.Linq.Expressions> przestrzeni nazw. Te typy pochodzą z typu abstrakcyjnego <xref:System.Linq.Expressions.Expression> .  
  
 Poniższy przykład kodu ilustruje sposób tworzenia drzewa wyrażenia, które reprezentuje wyrażenie lambda przy `Function(num) num < 5` użyciu interfejsu API.  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 W .NET Framework 4 lub nowszych interfejs API drzew wyrażeń obsługuje również przypisania i wyrażenia przepływu sterowania, takie jak pętle, Bloki warunkowe i `try-catch` bloki. Za pomocą interfejsu API można utworzyć drzewa wyrażeń, które są bardziej złożone niż te, które mogą być tworzone na podstawie wyrażeń lambda przez kompilator Visual Basic. Poniższy przykład ilustruje sposób tworzenia drzewa wyrażenia, które oblicza silnię liczby.  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

Aby uzyskać więcej informacji, zobacz [generowanie metod dynamicznych z drzewami wyrażeń w programie Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), które mają zastosowanie również do nowszych wersji programu Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analizowanie drzew wyrażeń  
 Poniższy przykład kodu demonstruje, jak drzewo wyrażeń reprezentujące wyrażenie lambda `Function(num) num < 5` może być rozłożone na jego części.  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a>Niezmienności drzew wyrażeń  
 Drzewa wyrażeń powinny być niezmienne. Oznacza to, że jeśli chcesz zmodyfikować drzewo wyrażenia, należy utworzyć nowe drzewo wyrażeń przez skopiowanie istniejącego i zastępowanie węzłów w tym elemencie. Możesz użyć odwiedzania drzewa wyrażenia, aby przejść do istniejącego drzewa wyrażenia. Aby uzyskać więcej informacji, zobacz [How to: Modify Expression Trees (Visual Basic)](how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilowanie drzew wyrażeń  
 <xref:System.Linq.Expressions.Expression%601>Typ udostępnia <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażenia w delegatze pliku wykonywalnego.  
  
 Poniższy przykład kodu demonstruje sposób kompilowania drzewa wyrażenia i uruchamiania wyniku.  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 Aby uzyskać więcej informacji, zobacz [jak: wykonywanie drzew wyrażeń (Visual Basic)](how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Expressions>
- [Instrukcje: wykonywanie drzew wyrażeń (Visual Basic)](how-to-execute-expression-trees.md)
- [Instrukcje: modyfikowanie drzew wyrażeń (Visual Basic)](how-to-modify-expression-trees.md)
- [Wyrażenia lambda](../../language-features/procedures/lambda-expressions.md)
- [Omówienie środowiska uruchomieniowego języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepcje programowania (Visual Basic)](../index.md)
