---
title: 'Instrukcje: używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 7f18539dba17f9fcb8769ca56d977908c58e6579
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418675"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="e6997-102">Instrukcje: używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="e6997-102">How to: Use Expression Trees to Build Dynamic Queries (C#)</span></span>
<span data-ttu-id="e6997-103">W LINQ, drzewa wyrażeń służą do reprezentowania zapytań strukturalnych, które są docelowymi źródłami danych, które implementują <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="e6997-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="e6997-104">Na przykład dostawca LINQ implementuje interfejs <xref:System.Linq.IQueryable%601> do wykonywania zapytań dotyczących relacyjnych magazynów danych.</span><span class="sxs-lookup"><span data-stu-id="e6997-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="e6997-105">C# Kompilator kompiluje zapytania, które są przeznaczone dla tych źródeł danych w kodzie, który kompiluje drzewo wyrażeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e6997-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="e6997-106">Dostawca zapytań może następnie przechodzenie przez strukturę danych drzewa wyrażenia i przetłumaczyć je do języka zapytań odpowiedniego dla źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e6997-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="e6997-107">Drzewa wyrażeń są również używane w LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="e6997-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="e6997-108">W tym temacie opisano, jak używać drzew wyrażeń do tworzenia dynamicznych zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="e6997-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="e6997-109">Zapytania dynamiczne są przydatne, gdy określone zapytanie nie jest znane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e6997-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="e6997-110">Na przykład aplikacja może udostępnić interfejs użytkownika, który umożliwia użytkownikowi końcowemu określenie co najmniej jednego predykatu w celu odfiltrowania danych.</span><span class="sxs-lookup"><span data-stu-id="e6997-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="e6997-111">Aby można było używać LINQ do wykonywania zapytań, ten rodzaj aplikacji musi używać drzew wyrażeń do tworzenia zapytania LINQ w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e6997-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6997-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6997-112">Example</span></span>  
 <span data-ttu-id="e6997-113">Poniższy przykład pokazuje, jak używać drzew wyrażeń do konstruowania zapytania względem źródła danych `IQueryable`, a następnie wykonywania go.</span><span class="sxs-lookup"><span data-stu-id="e6997-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="e6997-114">Kod kompiluje drzewo wyrażenia, aby reprezentować następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="e6997-114">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="e6997-115">Metody fabryki w przestrzeni nazw <xref:System.Linq.Expressions> są używane do tworzenia drzew wyrażeń, które reprezentują wyrażenia, które składają się na zapytanie ogólne.</span><span class="sxs-lookup"><span data-stu-id="e6997-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="e6997-116">Wyrażenia, które reprezentują wywołania metod standardowego operatora zapytań, odnoszą się do <xref:System.Linq.Queryable> implementacji tych metod.</span><span class="sxs-lookup"><span data-stu-id="e6997-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="e6997-117">Końcowe drzewo wyrażeń jest przesyłane do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródła danych w celu utworzenia zapytania wykonywalnego typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="e6997-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="e6997-118">Wyniki są uzyskiwane przez Wyliczenie tej zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="e6997-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="e6997-119">Ten kod używa ustalonej liczby wyrażeń w predykacie, który jest przesyłany do metody `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="e6997-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="e6997-120">Można jednak napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu, które są zależne od danych wprowadzonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e6997-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="e6997-121">Możesz również zmienić standardowe operatory zapytań, które są wywoływane w zapytaniu, w zależności od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e6997-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e6997-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e6997-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="e6997-123">Uwzględnij przestrzeń nazw System. LINQ. Expressions.</span><span class="sxs-lookup"><span data-stu-id="e6997-123">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6997-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6997-124">See also</span></span>

- [<span data-ttu-id="e6997-125">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="e6997-125">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="e6997-126">Instrukcje: wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="e6997-126">How to: Execute Expression Trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="e6997-127">Instrukcje: dynamiczne określanie filtrów predykatu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="e6997-127">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
