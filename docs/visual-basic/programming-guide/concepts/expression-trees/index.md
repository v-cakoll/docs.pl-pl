---
title: Drzewa wyrażeń
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: b2266cbae0a9a8a07c2a3569efa33d162ffedd1d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266420"
---
# <a name="expression-trees-visual-basic"></a>Drzewa wyrażeń (Visual Basic)
Drzewa wyrażeń reprezentują kod w strukturze danych podobnej do drzewa, gdzie każdy węzeł jest `x < y`wyrażeniem, na przykład wywołaniem metody lub operacją binarną, taką jak .  
  
 Można skompilować i uruchomić kod reprezentowany przez drzewa wyrażeń. Umożliwia to dynamiczną modyfikację kodu wykonywalnego, wykonywanie zapytań LINQ w różnych bazach danych i tworzenie zapytań dynamicznych. Aby uzyskać więcej informacji na temat drzew wyrażeń w LINQ, zobacz [Jak: Używanie drzew wyrażeń do tworzenia zapytań dynamicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Drzewa wyrażeń są również używane w dynamicznym czasie wykonywania języka (DLR), aby zapewnić współdziałanie między językami dynamicznymi a programem .NET Framework i umożliwić modułom zbierającym kompilatora emitowanie drzew wyrażeń zamiast języka pośredniego firmy Microsoft (MSIL). Aby uzyskać więcej informacji na temat biblioteki DLR, zobacz [Omówienie dynamicznego środowiska wykonawczego języka](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Kompilator języka C# lub Visual Basic może utworzyć dla Ciebie drzewo wyrażeń na podstawie anonimowego wyrażenia <xref:System.Linq.Expressions> lambda lub można ręcznie utworzyć drzewa wyrażeń przy użyciu obszaru nazw.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Tworzenie drzew wyrażeń z wyrażeń Lambda  
 Gdy wyrażenie lambda jest przypisane do <xref:System.Linq.Expressions.Expression%601>zmiennej typu, kompilator emituje kod do tworzenia drzewa wyrażeń, który reprezentuje wyrażenie lambda.  
  
 Kompilator języka Visual Basic może generować drzewa wyrażeń tylko z wyrażenie lambdas (lub lambdas jednowierszowe). Nie można przeanalizować instrukcji lambdas (lub lambdas wieloliniowych). Aby uzyskać więcej informacji na temat wyrażeń lambda w języku Visual Basic, zobacz [Wyrażenia Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Poniższe przykłady kodu pokazują, jak kompilator języka Visual Basic utworzył `Function(num) num < 5`drzewo wyrażeń, które reprezentuje wyrażenie lambda.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Tworzenie drzew wyrażeń przy użyciu interfejsu API  
 Aby utworzyć drzewa wyrażeń przy <xref:System.Linq.Expressions.Expression> użyciu interfejsu API, należy użyć klasy. Ta klasa zawiera statyczne metody fabryczne, które tworzą węzły drzewa wyrażeń określonych typów, na przykład , <xref:System.Linq.Expressions.ParameterExpression>który reprezentuje zmienną lub parametr lub <xref:System.Linq.Expressions.MethodCallExpression>, który reprezentuje wywołanie metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a inne typy specyficzne dla wyrażenia <xref:System.Linq.Expressions> są również zdefiniowane w obszarze nazw. Te typy pochodzą od <xref:System.Linq.Expressions.Expression>typu abstrakcyjnego .  
  
 Poniższy przykład kodu pokazuje, jak utworzyć drzewo wyrażeń, który reprezentuje wyrażenie `Function(num) num < 5` lambda przy użyciu interfejsu API.  
  
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
  
 W .NET Framework 4 lub nowszym interfejs API drzew wyrażeń obsługuje również przypisania `try-catch` i sterowanie wyrażeniami przepływu, takimi jak pętle, bloki warunkowe i bloki. Za pomocą interfejsu API, można utworzyć drzewa wyrażeń, które są bardziej złożone niż te, które mogą być tworzone z wyrażeń lambda przez kompilator języka Visual Basic. W poniższym przykładzie pokazano, jak utworzyć drzewo wyrażeń, które oblicza argument liczbowy liczby.  
  
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

Aby uzyskać więcej informacji, zobacz [Generowanie metod dynamicznych za pomocą drzew wyrażeń w programie Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), który ma również zastosowanie do nowszych wersji programu Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analizowanie drzew wyrażeń  
 Poniższy przykład kodu pokazuje, jak drzewo wyrażeń, który reprezentuje wyrażenie `Function(num) num < 5` lambda mogą być rozłożone na jego części.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Niezmienność drzew wyrażeń  
 Drzewa wyrażeń powinny być niezmienne. Oznacza to, że jeśli chcesz zmodyfikować drzewo wyrażeń, należy utworzyć nowe drzewo wyrażeń, kopiując istniejący i zastępując węzły w nim. Można użyć odwiedzającego drzewa wyrażeń, aby przejść przez istniejące drzewo wyrażeń. Aby uzyskać więcej informacji, zobacz [Jak: Modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilowanie drzew wyrażeń  
 Typ <xref:System.Linq.Expressions.Expression%601> zawiera <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażeń do delegata wykonywalnego.  
  
 Poniższy przykład kodu pokazuje, jak skompilować drzewo wyrażeń i uruchomić wynikowy kod.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Jak: Wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Expressions>
- [Jak: Wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Jak: Modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [Wyrażenia Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Omówienie dynamicznego środowiska wykonawczego języka](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Pojęcia programistyczne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
