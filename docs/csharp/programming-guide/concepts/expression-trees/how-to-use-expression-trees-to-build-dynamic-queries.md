---
title: Jak używać drzew wyrażeń do tworzenia zapytań dynamicznych (C#)
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 6114ec13dd43a7df146b87dda00fba06d6eb870c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635902"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="40753-102">Jak używać drzew wyrażeń do tworzenia zapytań dynamicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="40753-102">How to use expression trees to build dynamic queries (C#)</span></span>
<span data-ttu-id="40753-103">W LINQ drzewa wyrażeń są używane do reprezentowania uporządkowanych kwerend, które są przeznaczone dla źródeł danych, które implementują <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="40753-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="40753-104">Na przykład dostawca LINQ implementuje <xref:System.Linq.IQueryable%601> interfejs do wykonywania zapytań relacyjnych magazynów danych.</span><span class="sxs-lookup"><span data-stu-id="40753-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="40753-105">Kompilator C# kompiluje kwerendy, które są przeznaczone dla takich źródeł danych do kodu, który tworzy drzewo wyrażeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40753-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="40753-106">Dostawca kwerendy może następnie przechodzić przez strukturę danych drzewa wyrażeń i tłumaczyć ją na język zapytania odpowiedni dla źródła danych.</span><span class="sxs-lookup"><span data-stu-id="40753-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="40753-107">Drzewa wyrażeń są również używane w LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="40753-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="40753-108">W tym temacie opisano sposób używania drzew wyrażeń do tworzenia dynamicznych zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="40753-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="40753-109">Zapytania dynamiczne są przydatne, gdy specyfika kwerendy nie są znane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="40753-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="40753-110">Na przykład aplikacja może dostarczyć interfejs użytkownika, który umożliwia użytkownikowi końcowemu określenie jednego lub więcej predykatów do filtrowania danych.</span><span class="sxs-lookup"><span data-stu-id="40753-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="40753-111">Aby użyć LINQ do wykonywania zapytań, tego rodzaju aplikacja musi używać drzewa wyrażeń do tworzenia kwerendy LINQ w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40753-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40753-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="40753-112">Example</span></span>  
 <span data-ttu-id="40753-113">W poniższym przykładzie pokazano, jak użyć drzewa `IQueryable` wyrażeń do konstruowania kwerendy względem źródła danych, a następnie wykonać ją.</span><span class="sxs-lookup"><span data-stu-id="40753-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="40753-114">Kod tworzy drzewo wyrażeń do reprezentowania następującej kwerendy:</span><span class="sxs-lookup"><span data-stu-id="40753-114">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="40753-115">Metody fabryczne w <xref:System.Linq.Expressions> obszarze nazw są używane do tworzenia drzew wyrażeń reprezentujących wyrażenia, które tworzą ogólną kwerendę.</span><span class="sxs-lookup"><span data-stu-id="40753-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="40753-116">Wyrażenia reprezentujące wywołania standardowych metod operatora kwerendy <xref:System.Linq.Queryable> odnoszą się do implementacji tych metod.</span><span class="sxs-lookup"><span data-stu-id="40753-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="40753-117">Drzewo wyrażeń końcowych jest przekazywane do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy źródła danych w `IQueryable` celu utworzenia kwerendy wykonywalnej typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="40753-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="40753-118">Wyniki są uzyskiwane przez wyliczenie tej zmiennej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="40753-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="40753-119">Ten kod używa stałej liczby wyrażeń w predykacie, który jest przekazywany `Queryable.Where` do metody.</span><span class="sxs-lookup"><span data-stu-id="40753-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="40753-120">Można jednak napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu, która zależy od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="40753-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="40753-121">Można również zmieniać standardowe operatory zapytań, które są wywoływane w kwerendzie, w zależności od danych wejściowych od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="40753-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40753-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="40753-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="40753-123">Dołącz obszar nazw System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="40753-123">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40753-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40753-124">See also</span></span>

- [<span data-ttu-id="40753-125">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="40753-125">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="40753-126">Jak wykonać drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="40753-126">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="40753-127">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="40753-127">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
