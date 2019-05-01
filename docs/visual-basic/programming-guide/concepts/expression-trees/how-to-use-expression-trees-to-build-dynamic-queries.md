---
title: 'Instrukcje: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 2f91d95f888ab98902cc300afb61c41b62e64050
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966221"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="1c495-102">Instrukcje: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c495-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="1c495-103">W programie LINQ, drzew wyrażeń są używane do reprezentowania strukturyzowanych zapytań, których platformą docelową źródeł danych, który implementuje <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="1c495-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="1c495-104">Na przykład implementuje dostawcę LINQ <xref:System.Linq.IQueryable%601> interfejs do wykonywania zapytań magazynów danych relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="1c495-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="1c495-105">Kompilator Visual Basic kompiluje zapytań przeznaczonych dla tych źródeł danych do kodu, który kompiluje do drzewa wyrażenie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1c495-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="1c495-106">Dostawca kwerend można przechodzić przez strukturę danych drzewa wyrażeń i tłumaczenie język zapytań, odpowiednie dla źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1c495-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="1c495-107">Drzewa wyrażeń są również używane w składniku LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="1c495-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="1c495-108">W tym temacie opisano, jak używać drzew wyrażeń do tworzenia dynamicznych zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="1c495-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="1c495-109">Zapytania dynamiczne są przydatne, gdy szczegółowe informacje na temat zapytania nie są znane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1c495-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="1c495-110">Na przykład aplikacja może dostarczyć interfejs użytkownika, który umożliwia użytkownikowi określić jeden lub więcej predykatów do filtrowania danych.</span><span class="sxs-lookup"><span data-stu-id="1c495-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="1c495-111">Aby można było używać programu LINQ do wykonywania zapytań, tego rodzaju aplikacji należy użyć drzew wyrażeń, aby utworzyć zapytanie LINQ w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1c495-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c495-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c495-112">Example</span></span>  
 <span data-ttu-id="1c495-113">Poniższy przykład pokazuje jak używanie drzew wyrażeń do utworzenia zapytania dotyczącego `IQueryable` źródła danych, a następnie uruchomić go.</span><span class="sxs-lookup"><span data-stu-id="1c495-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="1c495-114">Kod zostanie skompilowany drzewa wyrażenie do reprezentowania następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="1c495-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="1c495-115">Metodach fabryki w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzew wyrażeń, które reprezentują wyrażenia, które tworzą ogólną zapytania.</span><span class="sxs-lookup"><span data-stu-id="1c495-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="1c495-116">Wyrażenia, które reprezentują wywołania metody standardowego operatora zapytań odwoływać się do <xref:System.Linq.Queryable> implementacji tych metod.</span><span class="sxs-lookup"><span data-stu-id="1c495-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="1c495-117">Drzewa wyrażeń końcowego jest przekazywany do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródła danych do utworzenia pliku wykonywalnego zapytania typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="1c495-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="1c495-118">Wyniki są uzyskać, wyliczając tej zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="1c495-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="1c495-119">Ten kod używa stałej liczby wyrażeń w predykacie, który jest przekazywany do `Queryable.Where` metody.</span><span class="sxs-lookup"><span data-stu-id="1c495-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="1c495-120">Jednakże można napisać aplikację, która łączy zmienną liczbę predykatu wyrażenia zależne od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1c495-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="1c495-121">Mogą też występować różne standardowe operatory zapytań, które są wywoływane w zapytaniu, w zależności od danych wejściowych od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1c495-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c495-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1c495-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="1c495-123">Utwórz nową **aplikację Konsolową** projektu.</span><span class="sxs-lookup"><span data-stu-id="1c495-123">Create a new **Console Application** project.</span></span>  
  
- <span data-ttu-id="1c495-124">Dodaj odwołanie do biblioteki System.Core.dll, jeśli nie jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="1c495-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
- <span data-ttu-id="1c495-125">Obejmują System.Linq.Expressions przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c495-125">Include the System.Linq.Expressions namespace.</span></span>  
  
- <span data-ttu-id="1c495-126">Skopiuj kod z przykładu i wklej go w `Main` `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="1c495-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c495-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c495-127">See also</span></span>

- [<span data-ttu-id="1c495-128">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c495-128">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="1c495-129">Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c495-129">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
