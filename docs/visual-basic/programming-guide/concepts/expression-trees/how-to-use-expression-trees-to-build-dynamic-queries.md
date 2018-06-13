---
title: 'Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: a2101598a083f8d0738cb531ebbaea0f7a87a577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643417"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="14931-102">Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14931-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="14931-103">W składniku LINQ, drzew wyrażeń są używane do reprezentowania strukturyzowanych zapytań, które odnoszą się do źródła danych, który implementuje <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="14931-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="14931-104">Na przykład implementuje dostawcy LINQ <xref:System.Linq.IQueryable%601> interfejs na potrzeby zapytań o magazynach danych relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="14931-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="14931-105">Kompilator Visual Basic kompiluje zapytań, które odnoszą się do tych źródeł danych do kodu, która tworzy drzewo wyrażeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="14931-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="14931-106">Wyślij zapytanie do dostawcy można przechodzić między nimi danych struktury drzewa wyrażenia i przekształca ją na język kwerendy odpowiednie dla źródła danych.</span><span class="sxs-lookup"><span data-stu-id="14931-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="14931-107">Drzewa wyrażeń są również używane w składniku LINQ do reprezentowania wyrażenia lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="14931-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="14931-108">W tym temacie opisano, jak używać drzew wyrażeń do tworzenia zapytań LINQ dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="14931-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="14931-109">Zapytania dynamiczne są przydatne, gdy szczegółowe informacje na temat zapytania nie są znane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="14931-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="14931-110">Na przykład aplikacja może zawierać interfejsu użytkownika, który umożliwia użytkownikowi końcowemu określić co najmniej jeden predykaty do filtrowania danych.</span><span class="sxs-lookup"><span data-stu-id="14931-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="14931-111">Aby można było używać LINQ do wykonywania zapytań, tego rodzaju aplikacji musi używanie drzew wyrażeń do tworzenia zapytań LINQ w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="14931-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14931-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="14931-112">Example</span></span>  
 <span data-ttu-id="14931-113">Poniższy przykład przedstawia sposób użycia drzew wyrażeń do utworzenia zapytania dotyczącego `IQueryable` źródła danych, a następnie wykonaj go.</span><span class="sxs-lookup"><span data-stu-id="14931-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="14931-114">Kod tworzy drzewo wyrażenia do reprezentowania następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="14931-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="14931-115">Metodami factory w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzewa wyrażeń, reprezentujące wyrażeń, które tworzą ogólną zapytania.</span><span class="sxs-lookup"><span data-stu-id="14931-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="14931-116">Wyrażeń, które reprezentują wywołania metod operator standardowej kwerendy odwoływać się do <xref:System.Linq.Queryable> implementacje tych metod.</span><span class="sxs-lookup"><span data-stu-id="14931-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="14931-117">Drzewo wyrażeń końcowego są przekazywane do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródło danych do utworzenia pliku wykonywalnego zapytania typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="14931-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="14931-118">Wyniki są uzyskiwane przez wyliczania tej zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="14931-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="14931-119">Ten kod zawiera stała liczba wyrażeń w predykacie, który jest przekazywany do `Queryable.Where` metody.</span><span class="sxs-lookup"><span data-stu-id="14931-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="14931-120">Jednak można napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu zależny od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14931-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="14931-121">Standardowe operatory zapytań wywoływanych w zapytaniu, w zależności od danych wejściowych od użytkownika może być różny.</span><span class="sxs-lookup"><span data-stu-id="14931-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14931-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="14931-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="14931-123">Utwórz nową **aplikacji konsoli** projektu.</span><span class="sxs-lookup"><span data-stu-id="14931-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="14931-124">Dodaj odwołania do System.Core.dll, jeśli nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="14931-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="14931-125">Obejmują System.Linq.Expressions przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="14931-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="14931-126">Skopiuj kod z przykładu i wklej ją do `Main` `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="14931-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14931-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14931-127">See Also</span></span>  
 [<span data-ttu-id="14931-128">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14931-128">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="14931-129">Porady: wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14931-129">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
