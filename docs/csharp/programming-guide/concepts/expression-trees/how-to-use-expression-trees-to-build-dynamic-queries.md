---
title: 'Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: e3afbea647bb429d25f41f37fde268565bc5bf8a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591415"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="77ecb-102">Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="77ecb-102">How to: Use Expression Trees to Build Dynamic Queries (C#)</span></span>
<span data-ttu-id="77ecb-103">W programie LINQ, drzew wyrażeń są używane do reprezentowania strukturyzowanych zapytań, których platformą docelową źródeł danych, który implementuje <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="77ecb-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="77ecb-104">Na przykład implementuje dostawcę LINQ <xref:System.Linq.IQueryable%601> interfejs do wykonywania zapytań magazynów danych relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="77ecb-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="77ecb-105">Kompilator języka C# kompiluje zapytań przeznaczonych dla tych źródeł danych do kodu, który kompiluje do drzewa wyrażenie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="77ecb-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="77ecb-106">Dostawca kwerend można przechodzić przez strukturę danych drzewa wyrażeń i tłumaczenie język zapytań, odpowiednie dla źródła danych.</span><span class="sxs-lookup"><span data-stu-id="77ecb-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="77ecb-107">Drzewa wyrażeń są również używane w składniku LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="77ecb-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="77ecb-108">W tym temacie opisano, jak używać drzew wyrażeń do tworzenia dynamicznych zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="77ecb-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="77ecb-109">Zapytania dynamiczne są przydatne, gdy szczegółowe informacje na temat zapytania nie są znane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="77ecb-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="77ecb-110">Na przykład aplikacja może dostarczyć interfejs użytkownika, który umożliwia użytkownikowi określić jeden lub więcej predykatów do filtrowania danych.</span><span class="sxs-lookup"><span data-stu-id="77ecb-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="77ecb-111">Aby można było używać programu LINQ do wykonywania zapytań, tego rodzaju aplikacji należy użyć drzew wyrażeń, aby utworzyć zapytanie LINQ w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="77ecb-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77ecb-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="77ecb-112">Example</span></span>  
 <span data-ttu-id="77ecb-113">Poniższy przykład pokazuje jak używanie drzew wyrażeń do utworzenia zapytania dotyczącego `IQueryable` źródła danych, a następnie uruchomić go.</span><span class="sxs-lookup"><span data-stu-id="77ecb-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="77ecb-114">Kod zostanie skompilowany drzewa wyrażenie do reprezentowania następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="77ecb-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 <span data-ttu-id="77ecb-115">Metodach fabryki w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzew wyrażeń, które reprezentują wyrażenia, które tworzą ogólną zapytania.</span><span class="sxs-lookup"><span data-stu-id="77ecb-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="77ecb-116">Wyrażenia, które reprezentują wywołania metody standardowego operatora zapytań odwoływać się do <xref:System.Linq.Queryable> implementacji tych metod.</span><span class="sxs-lookup"><span data-stu-id="77ecb-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="77ecb-117">Drzewa wyrażeń końcowego jest przekazywany do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródła danych do utworzenia pliku wykonywalnego zapytania typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="77ecb-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="77ecb-118">Wyniki są uzyskać, wyliczając tej zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="77ecb-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="77ecb-119">Ten kod używa stałej liczby wyrażeń w predykacie, który jest przekazywany do `Queryable.Where` metody.</span><span class="sxs-lookup"><span data-stu-id="77ecb-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="77ecb-120">Jednakże można napisać aplikację, która łączy zmienną liczbę predykatu wyrażenia zależne od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="77ecb-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="77ecb-121">Mogą też występować różne standardowe operatory zapytań, które są wywoływane w zapytaniu, w zależności od danych wejściowych od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="77ecb-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77ecb-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="77ecb-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="77ecb-123">Utwórz nową **aplikację Konsolową** projektu.</span><span class="sxs-lookup"><span data-stu-id="77ecb-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="77ecb-124">Dodaj odwołanie do biblioteki System.Core.dll, jeśli nie jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="77ecb-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="77ecb-125">Obejmują System.Linq.Expressions przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="77ecb-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="77ecb-126">Skopiuj kod z przykładu i wklej go w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="77ecb-126">Copy the code from the example and paste it into the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ecb-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77ecb-127">See Also</span></span>

- [<span data-ttu-id="77ecb-128">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="77ecb-128">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [<span data-ttu-id="77ecb-129">Porady: wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="77ecb-129">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
- [<span data-ttu-id="77ecb-130">Porady: dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="77ecb-130">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
