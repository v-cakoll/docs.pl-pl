---
title: Drzewa wyrażeń (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 7e63bf28f10070daa9624daa67bd5118fa67874d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926713"
---
# <a name="expression-trees-c"></a>Drzewa wyrażeń (C#)
Drzewa wyrażeń reprezentują kod w strukturze danych przypominającej drzewo, gdzie każdy węzeł jest wyrażeniem, na przykład wywołaniem metody lub operacją binarną, taką jak `x < y`.  
  
 Można skompilować i uruchomić kod reprezentowany przez drzewa wyrażeń. Umożliwia to dynamiczną modyfikację kodu wykonywalnego, wykonywanie zapytań LINQ w różnych bazach danych i tworzenie zapytań dynamicznych. Aby uzyskać więcej informacji na temat drzew wyrażeń w LINQ [, zobacz How to: Używaj drzew wyrażeń do kompilowania zapytań dynamicznychC#(](./how-to-use-expression-trees-to-build-dynamic-queries.md)).  
  
 Drzewa wyrażeń są również używane w środowisku uruchomieniowym języka dynamicznego (DLR) w celu zapewnienia współdziałania między językami dynamicznymi i .NET Framework i umożliwiają autorom kompilatora emitowanie drzew wyrażeń zamiast języka pośredniego firmy Microsoft (MSIL). Aby uzyskać więcej informacji na temat DLR, zobacz [Omówienie środowiska uruchomieniowego języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Można utworzyć drzewo wyrażenia C# lub Visual Basic w oparciu o anonimowe wyrażenie lambda lub można utworzyć drzewa wyrażeń ręcznie przy użyciu <xref:System.Linq.Expressions> przestrzeni nazw.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Tworzenie drzew wyrażeń na podstawie wyrażeń lambda  
 Gdy wyrażenie lambda jest przypisane do zmiennej typu <xref:System.Linq.Expressions.Expression%601>, kompilator emituje kod w celu skompilowania drzewa wyrażenia, które reprezentuje wyrażenie lambda.  
  
 C# Kompilator może generować drzewa wyrażeń tylko z wyrażeń lambda (lub jednowierszowych wyrażeń lambda). Nie można analizować instrukcji lambda (lub wielowierszowych wyrażeń lambda). Aby uzyskać więcej informacji na temat wyrażeń C#lambda w, zobacz [lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).  
  
 W poniższym przykładzie kodu pokazano, jak utworzyć w C# kompilatorze drzewo wyrażenia, które reprezentuje wyrażenie `num => num < 5`lambda.  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Tworzenie drzew wyrażeń przy użyciu interfejsu API  
 Aby utworzyć drzewa wyrażeń przy użyciu interfejsu API, użyj <xref:System.Linq.Expressions.Expression> klasy. Ta klasa zawiera statyczne metody fabryki, które tworzą węzły drzewa wyrażenia określonych typów, na przykład <xref:System.Linq.Expressions.ParameterExpression>, która reprezentuje zmienną lub parametr lub <xref:System.Linq.Expressions.MethodCallExpression>, który reprezentuje wywołanie metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>i inne typy specyficzne dla wyrażenia są również zdefiniowane <xref:System.Linq.Expressions> w przestrzeni nazw. Te typy pochodzą z typu <xref:System.Linq.Expressions.Expression>abstrakcyjnego.  
  
 Poniższy przykład kodu ilustruje sposób tworzenia drzewa wyrażenia, które reprezentuje wyrażenie `num => num < 5` lambda przy użyciu interfejsu API.  
  
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
  
 W .NET Framework 4 lub nowszych interfejs API drzew wyrażeń obsługuje również przypisania i wyrażenia przepływu sterowania, takie jak pętle, Bloki warunkowe `try-catch` i bloki. Za pomocą interfejsu API można utworzyć drzewa wyrażeń, które są bardziej złożone niż te, które mogą być tworzone na podstawie wyrażeń lambda przez C# kompilator. Poniższy przykład ilustruje sposób tworzenia drzewa wyrażenia, które oblicza silnię liczby.  
  
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

Aby uzyskać więcej informacji, zobacz [generowanie metod dynamicznych z drzewami wyrażeń w programie Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), które mają zastosowanie również do nowszych wersji programu Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analizowanie drzew wyrażeń  
 Poniższy przykład kodu demonstruje, jak drzewo wyrażeń reprezentujące wyrażenie `num => num < 5` lambda może być rozłożone na jego części.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Niezmienności drzew wyrażeń  
 Drzewa wyrażeń powinny być niezmienne. Oznacza to, że jeśli chcesz zmodyfikować drzewo wyrażenia, należy utworzyć nowe drzewo wyrażeń przez skopiowanie istniejącego i zastępowanie węzłów w tym elemencie. Możesz użyć odwiedzania drzewa wyrażenia, aby przejść do istniejącego drzewa wyrażenia. Aby uzyskać więcej informacji, zobacz [jak: Modyfikuj drzewa wyrażeń (C#)](./how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilowanie drzew wyrażeń  
 <xref:System.Linq.Expressions.Expression%601> Typ<xref:System.Linq.Expressions.Expression%601.Compile%2A> udostępnia metodę, która kompiluje kod reprezentowany przez drzewo wyrażenia w delegatze pliku wykonywalnego.  
  
 Poniższy przykład kodu demonstruje sposób kompilowania drzewa wyrażenia i uruchamiania wyniku.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie drzew wyrażeń (C#)](./how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.Expressions>
- [Instrukcje: Wykonywanie drzew wyrażeń (C#)](./how-to-execute-expression-trees.md)
- [Instrukcje: Modyfikuj drzewa wyrażeń (C#)](./how-to-modify-expression-trees.md)
- [Wyrażenia lambda](../../statements-expressions-operators/lambda-expressions.md)
- [Przegląd środowiska uruchomieniowego języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepcje programowaniaC#()](../index.md)
