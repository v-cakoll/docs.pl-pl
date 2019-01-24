---
title: 'Instrukcje: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: dd1e5fff21ef68683d0b721e84c4690d8e440d60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645469"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Instrukcje: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)
W programie LINQ, drzew wyrażeń są używane do reprezentowania strukturyzowanych zapytań, których platformą docelową źródeł danych, który implementuje <xref:System.Linq.IQueryable%601>. Na przykład implementuje dostawcę LINQ <xref:System.Linq.IQueryable%601> interfejs do wykonywania zapytań magazynów danych relacyjnych. Kompilator Visual Basic kompiluje zapytań przeznaczonych dla tych źródeł danych do kodu, który kompiluje do drzewa wyrażenie w czasie wykonywania. Dostawca kwerend można przechodzić przez strukturę danych drzewa wyrażeń i tłumaczenie język zapytań, odpowiednie dla źródła danych.  
  
 Drzewa wyrażeń są również używane w składniku LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.  
  
 W tym temacie opisano, jak używać drzew wyrażeń do tworzenia dynamicznych zapytań LINQ. Zapytania dynamiczne są przydatne, gdy szczegółowe informacje na temat zapytania nie są znane w czasie kompilacji. Na przykład aplikacja może dostarczyć interfejs użytkownika, który umożliwia użytkownikowi określić jeden lub więcej predykatów do filtrowania danych. Aby można było używać programu LINQ do wykonywania zapytań, tego rodzaju aplikacji należy użyć drzew wyrażeń, aby utworzyć zapytanie LINQ w czasie wykonywania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak używanie drzew wyrażeń do utworzenia zapytania dotyczącego `IQueryable` źródła danych, a następnie uruchomić go. Kod zostanie skompilowany drzewa wyrażenie do reprezentowania następujące zapytanie:  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 Metodach fabryki w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzew wyrażeń, które reprezentują wyrażenia, które tworzą ogólną zapytania. Wyrażenia, które reprezentują wywołania metody standardowego operatora zapytań odwoływać się do <xref:System.Linq.Queryable> implementacji tych metod. Drzewa wyrażeń końcowego jest przekazywany do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródła danych do utworzenia pliku wykonywalnego zapytania typu `IQueryable`. Wyniki są uzyskać, wyliczając tej zmiennej zapytania.  
  
```vb  
' Add an Imports statement for System.Linq.Expressions.  
  
Dim companies =   
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",   
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",   
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",   
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",   
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}  
  
' The IQueryable data to query.  
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()  
  
' Compose the expression tree that represents the parameter to the predicate.  
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")  
  
' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****  
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".  
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))  
Dim right As Expression = Expression.Constant("coho winery")  
Dim e1 As Expression = Expression.Equal(left, right)  
  
' Create an expression tree that represents the expression: company.Length > 16.  
left = Expression.Property(pe, GetType(String).GetProperty("Length"))  
right = Expression.Constant(16, GetType(Integer))  
Dim e2 As Expression = Expression.GreaterThan(left, right)  
  
' Combine the expressions to create an expression tree that represents the  
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).  
Dim predicateBody As Expression = Expression.OrElse(e1, e2)  
  
' Create an expression tree that represents the expression:  
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)  
Dim whereCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "Where",   
        New Type() {queryableData.ElementType},   
        queryableData.Expression,   
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))  
' ***** End Where *****  
  
' ***** OrderBy(Function(company) company) *****  
' Create an expression tree that represents the expression:  
' whereCallExpression.OrderBy(Function(company) company)  
Dim orderByCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "OrderBy",   
        New Type() {queryableData.ElementType, queryableData.ElementType},   
        whereCallExpression,   
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))  
' ***** End OrderBy *****  
  
' Create an executable query from the expression tree.  
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)  
  
' Enumerate the results.  
For Each company As String In results  
    Console.WriteLine(company)  
Next  
  
' This code produces the following output:  
'  
' Blue Yonder Airlines  
' City Power & Light  
' Coho Winery  
' Consolidated Messenger  
' Graphic Design Institute  
' Humongous Insurance  
' Lucerne Publishing  
' Northwind Traders  
' The Phone Company  
' Wide World Importers  
```  
  
 Ten kod używa stałej liczby wyrażeń w predykacie, który jest przekazywany do `Queryable.Where` metody. Jednakże można napisać aplikację, która łączy zmienną liczbę predykatu wyrażenia zależne od danych wejściowych użytkownika. Mogą też występować różne standardowe operatory zapytań, które są wywoływane w zapytaniu, w zależności od danych wejściowych od użytkownika.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Utwórz nową **aplikację Konsolową** projektu.  
  
-   Dodaj odwołanie do biblioteki System.Core.dll, jeśli nie jest wywoływany.  
  
-   Obejmują System.Linq.Expressions przestrzeni nazw.  
  
-   Skopiuj kod z przykładu i wklej go w `Main` `Sub` procedury.  
  
## <a name="see-also"></a>Zobacz także
- [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
