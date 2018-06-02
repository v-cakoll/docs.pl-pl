---
title: Drzewa wyrażeń (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: babee41f7df48f270d0c56cb2af91e463407d5c1
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696952"
---
# <a name="expression-trees-visual-basic"></a>Drzewa wyrażeń (Visual Basic)
Drzewa wyrażeń reprezentuje kod w strukturze drzewa danych każdy węzeł w przypadku wyrażenia, na przykład, wywołanie metody lub operację binarną takich jak `x < y`.  
  
 Możesz skompilować i uruchomić kod reprezentowany przez drzewa wyrażeń. Umożliwia dynamiczne modyfikacji kodu wykonywalnego, wysyła zapytanie do wykonywania zapytań LINQ w różnych baz danych i tworzenie zapytań dynamicznych. Aby uzyskać więcej informacji na temat drzew wyrażeń w składniku LINQ, zobacz [porady: użycie drzew wyrażeń do tworzenia zapytań dynamicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Drzewa wyrażeń są również używane w środowisku uruchomieniowym języka dynamicznego (DLR), aby zapewnić współdziałanie między językami dynamiczne i .NET Framework i umożliwić autorów kompilatora, aby emitować drzew wyrażeń zamiast język pośredni firmy Microsoft (MSIL). Aby uzyskać więcej informacji na temat DLR, zobacz [Przegląd środowiska uruchomieniowego języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Masz Utwórz drzewo wyrażeń oparte na wyrażeniu lambda anonimowe lub drzew wyrażeń można tworzyć ręcznie za pomocą kompilatora C# lub Visual Basic <xref:System.Linq.Expressions> przestrzeni nazw.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Tworzenie drzewa wyrażeń z wyrażenia Lambda  
 Jeśli wyrażenie lambda jest przypisany do zmiennej typu <xref:System.Linq.Expressions.Expression%601>, kompilator emituje kod, aby utworzyć drzewo wyrażenia, który reprezentuje wyrażenie lambda.  
  
 Kompilator Visual Basic można wygenerować drzewa wyrażeń tylko z wyrażenia lambda (lub jednowierszowe wyrażenia lambda). Nie można go przeanalizować instrukcji lambda (lub wielowierszowego wyrażenia lambda). Aby uzyskać więcej informacji na temat wyrażeń lambda w języku Visual Basic, zobacz [wyrażenia Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 W poniższych przykładach kodu przedstawiają sposób kompilator Visual Basic, utwórz drzewo wyrażeń, który reprezentuje wyrażenie lambda ma `Function(num) num < 5`.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Tworzenie przy użyciu interfejsu API drzew wyrażeń  
 Aby utworzyć drzewa wyrażeń przy użyciu interfejsu API, użyj <xref:System.Linq.Expressions.Expression> klasy. Ta klasa zawiera metody statyczne fabryki, tworzone wyrażenia węzły drzewa określonych typów, na przykład <xref:System.Linq.Expressions.ParameterExpression>, reprezentuje zmienna lub parametr, lub <xref:System.Linq.Expressions.MethodCallExpression>, który reprezentuje wywołanie metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, i inne typy specyficzne dla wyrażenia również są definiowane w <xref:System.Linq.Expressions> przestrzeni nazw. Te typy pochodzić od typu abstrakcyjnego <xref:System.Linq.Expressions.Expression>.  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia drzewo wyrażenia, który reprezentuje wyrażenie lambda `Function(num) num < 5` przy użyciu interfejsu API.  
  
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
  
 W programie .NET Framework 4 lub nowszym API drzewa wyrażenia obsługuje również przydziałów i wyrażeń przepływu sterowania takich jak pętle, bloków warunkowych i `try-catch` bloków. Korzystając z interfejsu API, można utworzyć drzewa wyrażeń, które są bardziej złożone niż te, które mogą być tworzone z wyrażenia lambda przez kompilator Visual Basic. W poniższym przykładzie pokazano, jak utworzyć drzewo wyrażenia, który oblicza silnię liczby.  
  
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

Aby uzyskać więcej informacji, zobacz [metody dynamiczne generowanie z drzewa wyrażeń w Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010), która ma zastosowanie również do nowszej wersji programu Visual Studio.
  
## <a name="parsing-expression-trees"></a>Podczas analizowania drzewa wyrażeń  
 W poniższym przykładzie kodu pokazano, jak wyrażenia drzewa, który reprezentuje wyrażenie lambda `Function(num) num < 5` może być rozłożone na jego części.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Immutability drzew wyrażeń  
 Drzewa wyrażeń powinno być niezmienialne. Oznacza to zmodyfikować drzewo wyrażenia, kopiując istniejący i zastępowanie węzłów w nim należy tworzyć nowe drzewo wyrażenia. Obiekt odwiedzający wyrażenie drzewa umożliwia przenoszenie istniejących drzewa wyrażenia. Aby uzyskać więcej informacji, zobacz [porady: modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilowanie drzew wyrażeń  
 <xref:System.Linq.Expressions.Expression%601> Typ zapewnia <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażenia do pliku wykonywalnego delegata.  
  
 W poniższym przykładzie pokazano, jak skompilować drzewo wyrażeń i uruchomić wynikowy kod.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [porady: wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.Expressions>  
 [Porady: wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Porady: modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [Wyrażenia lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Przegląd środowiska uruchomieniowego języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
 [Koncepcje programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
