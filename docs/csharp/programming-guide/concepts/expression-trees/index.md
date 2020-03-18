---
title: Drzewa wyrażeń (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: f425ab38bf7bb54814fe777b7cb02180d022a8af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169639"
---
# <a name="expression-trees-c"></a>Drzewa wyrażeń (C#)
Drzewa wyrażeń reprezentują kod w strukturze danych przypominającej drzewo, gdzie każdy węzeł jest `x < y`wyrażeniem, na przykład wywołaniem metody lub operacją binarną, taką jak .  
  
 Można skompilować i uruchomić kod reprezentowany przez drzewa wyrażeń. Umożliwia to dynamiczne modyfikowanie kodu wykonywalnego, wykonywanie zapytań LINQ w różnych bazach danych i tworzenie zapytań dynamicznych. Aby uzyskać więcej informacji na temat drzew wyrażeń w LINQ, zobacz [Jak używać drzew wyrażeń do tworzenia zapytań dynamicznych (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).
  
 Drzewa wyrażeń są również używane w czasie wykonywania języka dynamicznego (DLR) w celu zapewnienia współdziałania między językami dynamicznymi i programem .NET Framework oraz w celu umożliwienia modułom zapisów kompilatora emitowania drzew wyrażeń zamiast języka pośredniego firmy Microsoft (MSIL). Aby uzyskać więcej informacji na temat dlr, zobacz [Omówienie wykonywania języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Kompilator Języka C# lub Visual Basic może utworzyć drzewo wyrażeń na podstawie anonimowego wyrażenia <xref:System.Linq.Expressions> lambda lub ręcznie utworzyć drzewa wyrażeń przy użyciu obszaru nazw.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Tworzenie drzew wyrażeń z wyrażeń Lambda  
 Gdy wyrażenie lambda jest przypisane do <xref:System.Linq.Expressions.Expression%601>zmiennej typu, kompilator emituje kod do tworzenia drzewa wyrażeń, który reprezentuje wyrażenie lambda.  
  
 Kompilator C# może generować drzewa wyrażeń tylko z wyrażenia lambdas (lub lambdas jednowierszowego). Nie można przeanalizować lambdas instrukcji (lub lambdas wielowierszowe). Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C#, zobacz [Wyrażenia Lambda](../../statements-expressions-operators/lambda-expressions.md).  
  
 Poniższe przykłady kodu pokazują, jak mieć kompilator C# utworzyć drzewo `num => num < 5`wyrażeń, które reprezentuje wyrażenie lambda .  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Tworzenie drzew wyrażeń przy użyciu interfejsu API  
 Aby utworzyć drzewa wyrażeń przy <xref:System.Linq.Expressions.Expression> użyciu interfejsu API, należy użyć klasy. Ta klasa zawiera statyczne metody fabryczne, które tworzą węzły <xref:System.Linq.Expressions.ParameterExpression>drzewa wyrażeń określonych <xref:System.Linq.Expressions.MethodCallExpression>typów, na przykład , który reprezentuje zmienną lub parametr lub , który reprezentuje wywołanie metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a inne typy specyficzne dla wyrażenia są <xref:System.Linq.Expressions> również zdefiniowane w obszarze nazw. Te typy pochodzą od <xref:System.Linq.Expressions.Expression>typu abstrakcyjnego .  
  
 W poniższym przykładzie kodu przedstawiono sposób tworzenia drzewa wyrażeń, które reprezentuje wyrażenie `num => num < 5` lambda przy użyciu interfejsu API.  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Manually build the expression tree for
// the lambda expression num => num < 5.  
ParameterExpression numParam = Expression.Parameter(typeof(int), "num");  
ConstantExpression five = Expression.Constant(5, typeof(int));  
BinaryExpression numLessThanFive = Expression.LessThan(numParam, five);  
Expression<Func<int, bool>> lambda1 =  
    Expression.Lambda<Func<int, bool>>(  
        numLessThanFive,  
        new ParameterExpression[] { numParam });  
```  
  
 W .NET Framework 4 lub nowszych drzewa wyrażenie interfejsu API obsługuje również przypisania `try-catch` i wyrażenia przepływu sterowania, takich jak pętle, bloki warunkowe i bloki. Za pomocą interfejsu API, można utworzyć drzewa wyrażeń, które są bardziej złożone niż te, które mogą być tworzone z wyrażeń lambda przez kompilator C#. W poniższym przykładzie pokazano, jak utworzyć drzewo wyrażeń, które oblicza argumentacji liczby.  
  
```csharp  
// Creating a parameter expression.  
ParameterExpression value = Expression.Parameter(typeof(int), "value");  
  
// Creating an expression to hold a local variable.
ParameterExpression result = Expression.Parameter(typeof(int), "result");  
  
// Creating a label to jump to from a loop.  
LabelTarget label = Expression.Label(typeof(int));  
  
// Creating a method body.  
BlockExpression block = Expression.Block(  
    // Adding a local variable.  
    new[] { result },  
    // Assigning a constant to a local variable: result = 1  
    Expression.Assign(result, Expression.Constant(1)),  
    // Adding a loop.  
        Expression.Loop(  
    // Adding a conditional block into the loop.  
           Expression.IfThenElse(  
    // Condition: value > 1  
               Expression.GreaterThan(value, Expression.Constant(1)),  
    // If true: result *= value --  
               Expression.MultiplyAssign(result,  
                   Expression.PostDecrementAssign(value)),  
    // If false, exit the loop and go to the label.  
               Expression.Break(label, result)  
           ),  
    // Label to jump to.  
       label  
    )  
);  
  
// Compile and execute an expression tree.  
int factorial = Expression.Lambda<Func<int, int>>(block, value).Compile()(5);  
  
Console.WriteLine(factorial);  
// Prints 120.  
```

Aby uzyskać więcej informacji, zobacz [Generowanie metod dynamicznych z drzewami wyrażeń w programie Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), który dotyczy również nowszych wersji programu Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analizowanie drzew wyrażeń  
 Poniższy przykład kodu pokazuje, jak drzewo wyrażeń, `num => num < 5` które reprezentuje wyrażenie lambda może być rozłożone na jego części.  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Create an expression tree.  
Expression<Func<int, bool>> exprTree = num => num < 5;  
  
// Decompose the expression tree.  
ParameterExpression param = (ParameterExpression)exprTree.Parameters[0];  
BinaryExpression operation = (BinaryExpression)exprTree.Body;  
ParameterExpression left = (ParameterExpression)operation.Left;  
ConstantExpression right = (ConstantExpression)operation.Right;  
  
Console.WriteLine("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value);  
  
// This code produces the following output:  
  
// Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a>Niezmienność drzew wyrażeń  
 Drzewa wyrażeń powinny być niezmienne. Oznacza to, że jeśli chcesz zmodyfikować drzewo wyrażeń, należy skonstruować nowe drzewo wyrażeń, kopiując istniejące i zastępując węzły w nim. Za pomocą odwiedzającego drzewo wyrażeń można przechodzić przez istniejące drzewo wyrażeń. Aby uzyskać więcej informacji, zobacz [Jak modyfikować drzewa wyrażeń (C#)](./how-to-modify-expression-trees.md).
  
## <a name="compiling-expression-trees"></a>Kompilowanie drzew wyrażeń  
 Typ <xref:System.Linq.Expressions.Expression%601> udostępnia <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażeń do delegata wykonywalnego.  
  
 W poniższym przykładzie kodu przedstawiono sposób kompilowania drzewa wyrażeń i uruchamiania kodu wynikowego.  
  
```csharp  
// Creating an expression tree.  
Expression<Func<int, bool>> expr = num => num < 5;  
  
// Compiling the expression tree into a delegate.  
Func<int, bool> result = expr.Compile();  
  
// Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4));  
  
// Prints True.  
  
// You can also use simplified syntax  
// to compile and run an expression tree.  
// The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4));  
  
// Also prints True.  
```  
  
 Aby uzyskać więcej informacji, zobacz [Jak wykonać drzewa wyrażeń (C#)](./how-to-execute-expression-trees.md).
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Expressions>
- [Jak wykonać drzewa wyrażeń (C#)](./how-to-execute-expression-trees.md)
- [Jak zmodyfikować drzewa wyrażeń (C#)](./how-to-modify-expression-trees.md)
- [Wyrażenia Lambda](../../statements-expressions-operators/lambda-expressions.md)
- [Omówienie czasu wykonywania języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepcje programowania (C#)](../index.md)
