---
title: 'Porady: używanie drzew wyrażeń do kompilowania zapytań dynamicznych'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: bf15880c1988ac5639dd80ba56d330372dc3803b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344716"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="cd984-102">Instrukcje: używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd984-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>

<span data-ttu-id="cd984-103">W LINQ, drzewa wyrażeń służą do reprezentowania zapytań strukturalnych, które są docelowymi źródłami danych, które implementują <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="cd984-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="cd984-104">Na przykład dostawca LINQ implementuje interfejs <xref:System.Linq.IQueryable%601> do wykonywania zapytań dotyczących relacyjnych magazynów danych.</span><span class="sxs-lookup"><span data-stu-id="cd984-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="cd984-105">Kompilator Visual Basic kompiluje zapytania, które są przeznaczone dla tych źródeł danych w kodzie, który kompiluje drzewo wyrażeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cd984-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="cd984-106">Dostawca zapytań może następnie przechodzenie przez strukturę danych drzewa wyrażenia i przetłumaczyć je do języka zapytań odpowiedniego dla źródła danych.</span><span class="sxs-lookup"><span data-stu-id="cd984-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>

<span data-ttu-id="cd984-107">Drzewa wyrażeń są również używane w LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="cd984-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>

<span data-ttu-id="cd984-108">W tym temacie opisano, jak używać drzew wyrażeń do tworzenia dynamicznych zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd984-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="cd984-109">Zapytania dynamiczne są przydatne, gdy określone zapytanie nie jest znane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cd984-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="cd984-110">Na przykład aplikacja może udostępnić interfejs użytkownika, który umożliwia użytkownikowi końcowemu określenie co najmniej jednego predykatu w celu odfiltrowania danych.</span><span class="sxs-lookup"><span data-stu-id="cd984-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="cd984-111">Aby można było używać LINQ do wykonywania zapytań, ten rodzaj aplikacji musi używać drzew wyrażeń do tworzenia zapytania LINQ w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cd984-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>

## <a name="example"></a><span data-ttu-id="cd984-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd984-112">Example</span></span>

<span data-ttu-id="cd984-113">Poniższy przykład pokazuje, jak używać drzew wyrażeń do konstruowania zapytania względem źródła danych `IQueryable`, a następnie wykonywania go.</span><span class="sxs-lookup"><span data-stu-id="cd984-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="cd984-114">Kod kompiluje drzewo wyrażenia, aby reprezentować następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="cd984-114">The code builds an expression tree to represent the following query:</span></span>

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

<span data-ttu-id="cd984-115">Metody fabryki w przestrzeni nazw <xref:System.Linq.Expressions> są używane do tworzenia drzew wyrażeń, które reprezentują wyrażenia, które składają się na zapytanie ogólne.</span><span class="sxs-lookup"><span data-stu-id="cd984-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="cd984-116">Wyrażenia, które reprezentują wywołania metod standardowego operatora zapytań, odnoszą się do <xref:System.Linq.Queryable> implementacji tych metod.</span><span class="sxs-lookup"><span data-stu-id="cd984-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="cd984-117">Końcowe drzewo wyrażeń jest przesyłane do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródła danych w celu utworzenia zapytania wykonywalnego typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="cd984-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="cd984-118">Wyniki są uzyskiwane przez Wyliczenie tej zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="cd984-118">The results are obtained by enumerating that query variable.</span></span>

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

<span data-ttu-id="cd984-119">Ten kod używa ustalonej liczby wyrażeń w predykacie, który jest przesyłany do metody `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="cd984-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="cd984-120">Można jednak napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu, które są zależne od danych wprowadzonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cd984-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="cd984-121">Możesz również zmienić standardowe operatory zapytań, które są wywoływane w zapytaniu, w zależności od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cd984-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="cd984-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cd984-122">Compiling the Code</span></span>

- <span data-ttu-id="cd984-123">Utwórz nowy projekt **aplikacji konsolowej** .</span><span class="sxs-lookup"><span data-stu-id="cd984-123">Create a new **Console Application** project.</span></span>

- <span data-ttu-id="cd984-124">Uwzględnij przestrzeń nazw System. LINQ. Expressions.</span><span class="sxs-lookup"><span data-stu-id="cd984-124">Include the System.Linq.Expressions namespace.</span></span>

- <span data-ttu-id="cd984-125">Skopiuj kod z przykładu i wklej go do procedury `Sub` `Main`.</span><span class="sxs-lookup"><span data-stu-id="cd984-125">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd984-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd984-126">See also</span></span>

- [<span data-ttu-id="cd984-127">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd984-127">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="cd984-128">Instrukcje: wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd984-128">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
