---
title: Jak używać drzew wyrażeń do kompilowania zapytań dynamicznych (C#)
description: Dowiedz się, jak tworzyć dynamiczne zapytania LINQ przy użyciu drzew wyrażeń. Te zapytania są przydatne, gdy szczegółowe dane zapytania są nieznane w czasie kompilacji.
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: edcef4068c19ba8e789683cf6ba4d5ef2477e0d8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105586"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="8653a-104">Jak używać drzew wyrażeń do kompilowania zapytań dynamicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="8653a-104">How to use expression trees to build dynamic queries (C#)</span></span>
<span data-ttu-id="8653a-105">W LINQ, drzewa wyrażeń służą do reprezentowania zapytań strukturalnych, które są docelowymi źródłami danych, które implementują <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="8653a-105">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="8653a-106">Na przykład dostawca LINQ implementuje <xref:System.Linq.IQueryable%601> interfejs do wykonywania zapytań dotyczących magazynów danych relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="8653a-106">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="8653a-107">Kompilator języka C# kompiluje zapytania, które są przeznaczone dla tych źródeł danych w kodzie, który kompiluje drzewo wyrażeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8653a-107">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="8653a-108">Dostawca zapytań może następnie przechodzenie przez strukturę danych drzewa wyrażenia i przetłumaczyć je do języka zapytań odpowiedniego dla źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8653a-108">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="8653a-109">Drzewa wyrażeń są również używane w LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601> .</span><span class="sxs-lookup"><span data-stu-id="8653a-109">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="8653a-110">W tym temacie opisano, jak używać drzew wyrażeń do tworzenia dynamicznych zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="8653a-110">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="8653a-111">Zapytania dynamiczne są przydatne, gdy określone zapytanie nie jest znane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8653a-111">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="8653a-112">Na przykład aplikacja może udostępnić interfejs użytkownika, który umożliwia użytkownikowi końcowemu określenie co najmniej jednego predykatu w celu odfiltrowania danych.</span><span class="sxs-lookup"><span data-stu-id="8653a-112">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="8653a-113">Aby można było używać LINQ do wykonywania zapytań, ten rodzaj aplikacji musi używać drzew wyrażeń do tworzenia zapytania LINQ w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8653a-113">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8653a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="8653a-114">Example</span></span>  
 <span data-ttu-id="8653a-115">Poniższy przykład pokazuje, jak używać drzew wyrażeń do konstruowania zapytania względem `IQueryable` źródła danych, a następnie wykonywania go.</span><span class="sxs-lookup"><span data-stu-id="8653a-115">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="8653a-116">Kod kompiluje drzewo wyrażenia, aby reprezentować następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="8653a-116">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="8653a-117">Metody fabryki w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzew wyrażeń, które reprezentują wyrażenia, które składają się na zapytanie ogólne.</span><span class="sxs-lookup"><span data-stu-id="8653a-117">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="8653a-118">Wyrażenia, które reprezentują wywołania metod standardowego operatora zapytań, odnoszą się do <xref:System.Linq.Queryable> implementacji tych metod.</span><span class="sxs-lookup"><span data-stu-id="8653a-118">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="8653a-119">Końcowe drzewo wyrażeń jest przenoszone do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródła danych w celu utworzenia zapytania wykonywalnego typu `IQueryable` .</span><span class="sxs-lookup"><span data-stu-id="8653a-119">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="8653a-120">Wyniki są uzyskiwane przez Wyliczenie tej zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="8653a-120">The results are obtained by enumerating that query variable.</span></span>  
  
```csharp  
// Add a using directive for System.Linq.Expressions.  
  
string[] companies = { "Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",  
                   "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",  
                   "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",  
                   "Blue Yonder Airlines", "Trey Research", "The Phone Company",  
                   "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee" };  
  
// The IQueryable data to query.  
IQueryable<String> queryableData = companies.AsQueryable<string>();  
  
// Compose the expression tree that represents the parameter to the predicate.  
ParameterExpression pe = Expression.Parameter(typeof(string), "company");  
  
// ***** Where(company => (company.ToLower() == "coho winery" || company.Length > 16)) *****  
// Create an expression tree that represents the expression 'company.ToLower() == "coho winery"'.  
Expression left = Expression.Call(pe, typeof(string).GetMethod("ToLower", System.Type.EmptyTypes));  
Expression right = Expression.Constant("coho winery");  
Expression e1 = Expression.Equal(left, right);  
  
// Create an expression tree that represents the expression 'company.Length > 16'.  
left = Expression.Property(pe, typeof(string).GetProperty("Length"));  
right = Expression.Constant(16, typeof(int));  
Expression e2 = Expression.GreaterThan(left, right);  
  
// Combine the expression trees to create an expression tree that represents the  
// expression '(company.ToLower() == "coho winery" || company.Length > 16)'.  
Expression predicateBody = Expression.OrElse(e1, e2);  
  
// Create an expression tree that represents the expression  
// 'queryableData.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))'  
MethodCallExpression whereCallExpression = Expression.Call(  
    typeof(Queryable),  
    "Where",  
    new Type[] { queryableData.ElementType },  
    queryableData.Expression,  
    Expression.Lambda<Func<string, bool>>(predicateBody, new ParameterExpression[] { pe }));  
// ***** End Where *****  
  
// ***** OrderBy(company => company) *****  
// Create an expression tree that represents the expression  
// 'whereCallExpression.OrderBy(company => company)'  
MethodCallExpression orderByCallExpression = Expression.Call(  
    typeof(Queryable),  
    "OrderBy",  
    new Type[] { queryableData.ElementType, queryableData.ElementType },  
    whereCallExpression,  
    Expression.Lambda<Func<string, string>>(pe, new ParameterExpression[] { pe }));  
// ***** End OrderBy *****  
  
// Create an executable query from the expression tree.  
IQueryable<string> results = queryableData.Provider.CreateQuery<string>(orderByCallExpression);  
  
// Enumerate the results.  
foreach (string company in results)  
    Console.WriteLine(company);  
  
/*  This code produces the following output:  
  
    Blue Yonder Airlines  
    City Power & Light  
    Coho Winery  
    Consolidated Messenger  
    Graphic Design Institute  
    Humongous Insurance  
    Lucerne Publishing  
    Northwind Traders  
    The Phone Company  
    Wide World Importers  
*/  
```  
  
 <span data-ttu-id="8653a-121">Ten kod używa ustalonej liczby wyrażeń w predykacie, który jest przesyłany do `Queryable.Where` metody.</span><span class="sxs-lookup"><span data-stu-id="8653a-121">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="8653a-122">Można jednak napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu, które są zależne od danych wprowadzonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8653a-122">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="8653a-123">Możesz również zmienić standardowe operatory zapytań, które są wywoływane w zapytaniu, w zależności od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8653a-123">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8653a-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8653a-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="8653a-125">Uwzględnij przestrzeń nazw System. LINQ. Expressions.</span><span class="sxs-lookup"><span data-stu-id="8653a-125">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8653a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8653a-126">See also</span></span>

- [<span data-ttu-id="8653a-127">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="8653a-127">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="8653a-128">Wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="8653a-128">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="8653a-129">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="8653a-129">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
