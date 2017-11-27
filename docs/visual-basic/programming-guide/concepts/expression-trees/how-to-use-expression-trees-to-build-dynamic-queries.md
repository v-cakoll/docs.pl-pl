---
title: "Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d09f89b0b49118d575690f577c77c5c3d2a76e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)
W składniku LINQ, drzew wyrażeń są używane do reprezentowania strukturyzowanych zapytań, które odnoszą się do źródła danych, który implementuje <xref:System.Linq.IQueryable%601>. Na przykład implementuje dostawcy LINQ <xref:System.Linq.IQueryable%601> interfejs na potrzeby zapytań o magazynach danych relacyjnych. Kompilator Visual Basic kompiluje zapytań, które odnoszą się do tych źródeł danych do kodu, która tworzy drzewo wyrażeń w czasie wykonywania. Wyślij zapytanie do dostawcy można przechodzić między nimi danych struktury drzewa wyrażenia i przekształca ją na język kwerendy odpowiednie dla źródła danych.  
  
 Drzewa wyrażeń są również używane w składniku LINQ do reprezentowania wyrażenia lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.  
  
 W tym temacie opisano, jak używać drzew wyrażeń do tworzenia zapytań LINQ dynamicznych. Zapytania dynamiczne są przydatne, gdy szczegółowe informacje na temat zapytania nie są znane w czasie kompilacji. Na przykład aplikacja może zawierać interfejsu użytkownika, który umożliwia użytkownikowi końcowemu określić co najmniej jeden predykaty do filtrowania danych. Aby można było używać LINQ do wykonywania zapytań, tego rodzaju aplikacji musi używanie drzew wyrażeń do tworzenia zapytań LINQ w czasie wykonywania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia drzew wyrażeń do utworzenia zapytania dotyczącego `IQueryable` źródła danych, a następnie wykonaj go. Kod tworzy drzewo wyrażenia do reprezentowania następujące zapytanie:  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 Metodami factory w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzewa wyrażeń, reprezentujące wyrażeń, które tworzą ogólną zapytania. Wyrażeń, które reprezentują wywołania metod operator standardowej kwerendy odwoływać się do <xref:System.Linq.Queryable> implementacje tych metod. Drzewo wyrażeń końcowego są przekazywane do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródło danych do utworzenia pliku wykonywalnego zapytania typu `IQueryable`. Wyniki są uzyskiwane przez wyliczania tej zmiennej zapytania.  
  
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
  
 Ten kod zawiera stała liczba wyrażeń w predykacie, który jest przekazywany do `Queryable.Where` metody. Jednak można napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu zależny od danych wejściowych użytkownika. Standardowe operatory zapytań wywoływanych w zapytaniu, w zależności od danych wejściowych od użytkownika może być różny.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Utwórz nową **aplikacji konsoli** projektu.  
  
-   Dodaj odwołania do System.Core.dll, jeśli nie jest już używany.  
  
-   Obejmują System.Linq.Expressions przestrzeni nazw.  
  
-   Skopiuj kod z przykładu i wklej ją do `Main` `Sub` procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [Porady: wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
