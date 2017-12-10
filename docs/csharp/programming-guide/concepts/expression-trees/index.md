---
title: "Drzewa wyrażeń (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f141c414ef56c591baa882d9495e591e6b08bc8
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="expression-trees-c"></a>Drzewa wyrażeń (C#)
Drzewa wyrażeń reprezentuje kod w strukturze drzewa danych każdy węzeł w przypadku wyrażenia, na przykład, wywołanie metody lub operację binarną takich jak `x < y`.  
  
 Możesz skompilować i uruchomić kod reprezentowany przez drzewa wyrażeń. Umożliwia dynamiczne modyfikacji kodu wykonywalnego, wysyła zapytanie do wykonywania zapytań LINQ w różnych baz danych i tworzenie zapytań dynamicznych. Aby uzyskać więcej informacji na temat drzew wyrażeń w składniku LINQ, zobacz [porady: użycie drzew wyrażeń do tworzenia zapytań dynamicznych (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Drzewa wyrażeń są również używane w środowisku uruchomieniowym języka dynamicznego (DLR), aby zapewnić współdziałanie między językami dynamiczne i .NET Framework i umożliwić autorów kompilatora, aby emitować drzew wyrażeń zamiast język pośredni firmy Microsoft (MSIL). Aby uzyskać więcej informacji na temat DLR, zobacz [Przegląd środowiska uruchomieniowego języka dynamicznego](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Masz Utwórz drzewo wyrażeń oparte na wyrażeniu lambda anonimowe lub drzew wyrażeń można tworzyć ręcznie za pomocą kompilatora C# lub Visual Basic <xref:System.Linq.Expressions> przestrzeni nazw.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Tworzenie drzewa wyrażeń z wyrażenia Lambda  
 Jeśli wyrażenie lambda jest przypisany do zmiennej typu <xref:System.Linq.Expressions.Expression%601>, kompilator emituje kod, aby utworzyć drzewo wyrażenia, który reprezentuje wyrażenie lambda.  
  
 Kompilator języka C# można wygenerować drzewa wyrażeń tylko z wyrażenia lambda (lub jednowierszowe wyrażenia lambda). Nie można go przeanalizować instrukcji lambda (lub wielowierszowego wyrażenia lambda). Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C#, zobacz [wyrażenia Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 W poniższych przykładach kodu przedstawiają sposób kompilatora C# Utwórz drzewo wyrażeń, który reprezentuje wyrażenie lambda ma `num => num < 5`.  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Tworzenie przy użyciu interfejsu API drzew wyrażeń  
 Aby utworzyć drzewa wyrażeń przy użyciu interfejsu API, użyj <xref:System.Linq.Expressions.Expression> klasy. Ta klasa zawiera metody statyczne fabryki, tworzone wyrażenia węzły drzewa określonych typów, na przykład <xref:System.Linq.Expressions.ParameterExpression>, reprezentuje zmienna lub parametr, lub <xref:System.Linq.Expressions.MethodCallExpression>, który reprezentuje wywołanie metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, i inne typy specyficzne dla wyrażenia również są definiowane w <xref:System.Linq.Expressions> przestrzeni nazw. Te typy pochodzić od typu abstrakcyjnego <xref:System.Linq.Expressions.Expression>.  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia drzewo wyrażenia, który reprezentuje wyrażenie lambda `num => num < 5` przy użyciu interfejsu API.  
  
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
  
 W programie .NET Framework 4 lub nowszym API drzewa wyrażenia obsługuje również przydziałów i wyrażeń przepływu sterowania takich jak pętle, bloków warunkowych i `try-catch` bloków. Korzystając z interfejsu API, można utworzyć drzewa wyrażeń, które są bardziej złożone niż te, które mogą być tworzone z wyrażenia lambda za pomocą kompilatora C#. W poniższym przykładzie pokazano, jak utworzyć drzewo wyrażenia, który oblicza silnię liczby.  
  
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

Aby uzyskać więcej informacji, zobacz [metody dynamiczne generowanie z drzewa wyrażeń w Visual Studio 2010](http://go.microsoft.com/fwlink/p/?LinkId=169513), która ma zastosowanie również do nowszej wersji programu Visual Studio.
  
## <a name="parsing-expression-trees"></a>Podczas analizowania drzewa wyrażeń  
 W poniższym przykładzie kodu pokazano, jak wyrażenia drzewa, który reprezentuje wyrażenie lambda `num => num < 5` może być rozłożone na jego części.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Immutability drzew wyrażeń  
 Drzewa wyrażeń powinno być niezmienialne. Oznacza to zmodyfikować drzewo wyrażenia, kopiując istniejący i zastępowanie węzłów w nim należy tworzyć nowe drzewo wyrażenia. Obiekt odwiedzający wyrażenie drzewa umożliwia przenoszenie istniejących drzewa wyrażenia. Aby uzyskać więcej informacji, zobacz [porady: modyfikowanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilowanie drzew wyrażeń  
 <xref:System.Linq.Expressions.Expression%601> Typ zapewnia <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażenia do pliku wykonywalnego delegata.  
  
 W poniższym przykładzie pokazano, jak skompilować drzewo wyrażeń i uruchomić wynikowy kod.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [porady: wykonywanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.Expressions>  
 [Porady: wykonywanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Porady: modyfikowanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [Wyrażenia lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Omówienie środowiska uruchomieniowego języka dynamicznego](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
 [Koncepcje programowania (C#)](../../../../csharp/programming-guide/concepts/index.md)
