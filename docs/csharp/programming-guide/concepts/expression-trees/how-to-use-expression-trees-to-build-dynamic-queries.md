---
title: 'Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 3ae21422576abccde51d7708007132a87bedbad6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="65a17-102">Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="65a17-102">How to: Use Expression Trees to Build Dynamic Queries (C#)</span></span>
<span data-ttu-id="65a17-103">W składniku LINQ, drzew wyrażeń są używane do reprezentowania strukturyzowanych zapytań, które odnoszą się do źródła danych, który implementuje <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="65a17-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="65a17-104">Na przykład implementuje dostawcy LINQ <xref:System.Linq.IQueryable%601> interfejs na potrzeby zapytań o magazynach danych relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="65a17-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="65a17-105">Kompilator języka C# kompiluje zapytań, które odnoszą się do tych źródeł danych do kodu, która tworzy drzewo wyrażeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="65a17-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="65a17-106">Wyślij zapytanie do dostawcy można przechodzić między nimi danych struktury drzewa wyrażenia i przekształca ją na język kwerendy odpowiednie dla źródła danych.</span><span class="sxs-lookup"><span data-stu-id="65a17-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="65a17-107">Drzewa wyrażeń są również używane w składniku LINQ do reprezentowania wyrażenia lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="65a17-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="65a17-108">W tym temacie opisano, jak używać drzew wyrażeń do tworzenia zapytań LINQ dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="65a17-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="65a17-109">Zapytania dynamiczne są przydatne, gdy szczegółowe informacje na temat zapytania nie są znane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="65a17-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="65a17-110">Na przykład aplikacja może zawierać interfejsu użytkownika, który umożliwia użytkownikowi końcowemu określić co najmniej jeden predykaty do filtrowania danych.</span><span class="sxs-lookup"><span data-stu-id="65a17-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="65a17-111">Aby można było używać LINQ do wykonywania zapytań, tego rodzaju aplikacji musi używanie drzew wyrażeń do tworzenia zapytań LINQ w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="65a17-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65a17-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="65a17-112">Example</span></span>  
 <span data-ttu-id="65a17-113">Poniższy przykład przedstawia sposób użycia drzew wyrażeń do utworzenia zapytania dotyczącego `IQueryable` źródła danych, a następnie wykonaj go.</span><span class="sxs-lookup"><span data-stu-id="65a17-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="65a17-114">Kod tworzy drzewo wyrażenia do reprezentowania następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="65a17-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 <span data-ttu-id="65a17-115">Metodami factory w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzewa wyrażeń, reprezentujące wyrażeń, które tworzą ogólną zapytania.</span><span class="sxs-lookup"><span data-stu-id="65a17-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="65a17-116">Wyrażeń, które reprezentują wywołania metod operator standardowej kwerendy odwoływać się do <xref:System.Linq.Queryable> implementacje tych metod.</span><span class="sxs-lookup"><span data-stu-id="65a17-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="65a17-117">Drzewo wyrażeń końcowego są przekazywane do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródło danych do utworzenia pliku wykonywalnego zapytania typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="65a17-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="65a17-118">Wyniki są uzyskiwane przez wyliczania tej zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="65a17-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="65a17-119">Ten kod zawiera stała liczba wyrażeń w predykacie, który jest przekazywany do `Queryable.Where` metody.</span><span class="sxs-lookup"><span data-stu-id="65a17-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="65a17-120">Jednak można napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu zależny od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="65a17-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="65a17-121">Standardowe operatory zapytań wywoływanych w zapytaniu, w zależności od danych wejściowych od użytkownika może być różny.</span><span class="sxs-lookup"><span data-stu-id="65a17-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="65a17-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="65a17-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="65a17-123">Utwórz nową **aplikacji konsoli** projektu.</span><span class="sxs-lookup"><span data-stu-id="65a17-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="65a17-124">Dodaj odwołania do System.Core.dll, jeśli nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="65a17-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="65a17-125">Obejmują System.Linq.Expressions przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="65a17-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="65a17-126">Skopiuj kod z przykładu i wklej ją do `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="65a17-126">Copy the code from the example and paste it into the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a17-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65a17-127">See Also</span></span>  
 [<span data-ttu-id="65a17-128">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="65a17-128">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="65a17-129">Porady: wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="65a17-129">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="65a17-130">Porady: dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="65a17-130">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
