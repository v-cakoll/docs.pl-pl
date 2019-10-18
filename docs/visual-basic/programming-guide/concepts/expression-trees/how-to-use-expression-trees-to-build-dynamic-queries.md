---
title: 'Instrukcje: używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 5cb4d99982deb48a47a25b52bc7f5e4c8634219c
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524220"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Instrukcje: używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)

W LINQ, drzewa wyrażeń służą do reprezentowania zapytań strukturalnych, które są docelowymi źródłami danych, które implementują <xref:System.Linq.IQueryable%601>. Na przykład dostawca LINQ implementuje interfejs <xref:System.Linq.IQueryable%601> do wykonywania zapytań dotyczących relacyjnych magazynów danych. Kompilator Visual Basic kompiluje zapytania, które są przeznaczone dla tych źródeł danych w kodzie, który kompiluje drzewo wyrażeń w czasie wykonywania. Dostawca zapytań może następnie przechodzenie przez strukturę danych drzewa wyrażenia i przetłumaczyć je do języka zapytań odpowiedniego dla źródła danych.

Drzewa wyrażeń są również używane w LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.

W tym temacie opisano, jak używać drzew wyrażeń do tworzenia dynamicznych zapytań LINQ. Zapytania dynamiczne są przydatne, gdy określone zapytanie nie jest znane w czasie kompilacji. Na przykład aplikacja może udostępnić interfejs użytkownika, który umożliwia użytkownikowi końcowemu określenie co najmniej jednego predykatu w celu odfiltrowania danych. Aby można było używać LINQ do wykonywania zapytań, ten rodzaj aplikacji musi używać drzew wyrażeń do tworzenia zapytania LINQ w czasie wykonywania.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać drzew wyrażeń do konstruowania zapytania względem źródła danych `IQueryable`, a następnie wykonywania go. Kod kompiluje drzewo wyrażenia, aby reprezentować następujące zapytanie:

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

Metody fabryki w przestrzeni nazw <xref:System.Linq.Expressions> są używane do tworzenia drzew wyrażeń, które reprezentują wyrażenia, które składają się na zapytanie ogólne. Wyrażenia, które reprezentują wywołania metod standardowego operatora zapytań, odnoszą się do <xref:System.Linq.Queryable> implementacji tych metod. Końcowe drzewo wyrażeń jest przesyłane do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródła danych w celu utworzenia zapytania wykonywalnego typu `IQueryable`. Wyniki są uzyskiwane przez Wyliczenie tej zmiennej zapytania.

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

Ten kod używa ustalonej liczby wyrażeń w predykacie, który jest przesyłany do metody `Queryable.Where`. Można jednak napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu, które są zależne od danych wprowadzonych przez użytkownika. Możesz również zmienić standardowe operatory zapytań, które są wywoływane w zapytaniu, w zależności od danych wejściowych użytkownika.

## <a name="compiling-the-code"></a>Kompilowanie kodu

- Utwórz nowy projekt **aplikacji konsolowej** .

- Uwzględnij przestrzeń nazw System. LINQ. Expressions.

- Skopiuj kod z przykładu i wklej go do procedury `Sub` `Main`.

## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Instrukcje: wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
