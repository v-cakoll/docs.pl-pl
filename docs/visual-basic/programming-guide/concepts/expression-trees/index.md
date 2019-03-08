---
title: Drzewa wyrażeń (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
---
# <a name="expression-trees-visual-basic"></a>Drzewa wyrażeń (Visual Basic)
Drzew wyrażeń reprezentują kodu struktury drzewa danych, gdzie każdy węzeł jest wyrażeniem, na przykład, wywołanie metody lub operacja binarna, takich jak `x < y`.  
  
 Można skompilować i uruchomić kod reprezentowany przez drzew wyrażeń. Dzięki temu dynamicznych modyfikacji kodu wykonywalnego, wykonywanie zapytań LINQ zapytania w różnych baz danych i tworzenia zapytań dynamicznych. Aby uzyskać więcej informacji na temat drzew wyrażeń LINQ zobacz [jak: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Drzewa wyrażeń są również używane w środowisko uruchomieniowe języka dynamicznego (DLR), aby zapewnić współdziałanie języków dynamicznego i .NET Framework i umożliwiają twórcom kompilatorów emitować drzew wyrażeń, zamiast języka Microsoft intermediate language (MSIL). Aby uzyskać więcej informacji na temat DLR zobacz [dynamiczny przegląd środowiska uruchomieniowego języka](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Możesz mieć, aby utworzyć drzewo wyrażenia, oparty na wyrażeniu lambda anonimowe lub tworzenia drzew wyrażeń ręcznie za pomocą kompilatora C# lub Visual Basic <xref:System.Linq.Expressions> przestrzeni nazw.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Tworzenie drzew wyrażeń z wyrażenia Lambda  
 Gdy wyrażenie lambda jest przypisany do zmiennej typu <xref:System.Linq.Expressions.Expression%601>, kompilator generuje kod, aby utworzyć drzewo wyrażenia, który reprezentuje wyrażenie lambda.  
  
 Kompilator Visual Basic można wygenerować drzew wyrażeń, tylko z wyrażenia lambda (lub pojedynczej linii wyrażenia lambda). Nie można go przeanalizować lambdy instrukcji (lub wielowierszowego wyrażenia lambda). Aby uzyskać więcej informacji na temat wyrażeń lambda w języku Visual Basic, zobacz [wyrażeń Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Poniższe przykłady kodu przedstawiają sposób pozwolić kompilatorowi języka Visual Basic, utworzyć drzewo wyrażenia, który reprezentuje wyrażenie lambda `Function(num) num < 5`.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Tworzenia drzew wyrażeń, korzystając z interfejsu API  
 Do tworzenia drzew wyrażeń, korzystając z interfejsu API, należy użyć <xref:System.Linq.Expressions.Expression> klasy. Ta klasa zawiera statycznych metod fabryki tworzonych wyrażeń węzły drzewa określonych typów, na przykład <xref:System.Linq.Expressions.ParameterExpression>, która reprezentuje zmienna lub parametr, lub <xref:System.Linq.Expressions.MethodCallExpression>, która reprezentuje wywołanie metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, i inne typy wyrażeń określonych również są definiowane w <xref:System.Linq.Expressions> przestrzeni nazw. Te typy pochodzić od typu abstrakcyjnego <xref:System.Linq.Expressions.Expression>.  
  
 Poniższy przykład kodu demonstruje sposób tworzenia drzewa wyrażeń, który reprezentuje wyrażenie lambda `Function(num) num < 5` za pomocą interfejsu API.  
  
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
  
 W programie .NET Framework 4 lub nowszym, interfejs API drzew wyrażeń obsługuje również przydziałów i wyrażeń przepływu sterowania takie jak pętle i bloków warunkowych i `try-catch` bloków. Za pomocą interfejsu API, można utworzyć drzew wyrażeń, które są bardziej skomplikowane niż te, które można tworzyć na podstawie wyrażenia lambda przez kompilator języka Visual Basic. Poniższy przykład przedstawia sposób tworzenia drzewa wyrażeń, który oblicza silnię liczby.  
  
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

Aby uzyskać więcej informacji, zobacz [metody dynamiczne generowanie za pomocą drzew w programie Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), która ma zastosowanie również do nowszej wersji programu Visual Studio.
  
## <a name="parsing-expression-trees"></a>Podczas analizowania drzew wyrażeń  
 Poniższy przykład kodu demonstruje, jak wyrażenie drzewa, która reprezentuje wyrażenia lambda `Function(num) num < 5` może być rozłożone na jego części.  
  
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
 Drzewa wyrażeń powinno być niezmienialne. Oznacza to zmodyfikować drzewo wyrażenia, przez skopiowanie istniejącego i zastępując węzły w nim należy tworzyć nowego drzewa wyrażeń. Obiekt odwiedzający drzewa wyrażenie umożliwia przenoszenie istniejących drzewa wyrażeń. Aby uzyskać więcej informacji, zobacz [jak: Modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilowanie drzew wyrażeń  
 <xref:System.Linq.Expressions.Expression%601> Typ zapewnia <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażenia do pliku wykonywalnego delegata.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Linq.Expressions>
- [Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Instrukcje: Modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [Wyrażenia lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Przegląd środowiska uruchomieniowego języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepcje programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
