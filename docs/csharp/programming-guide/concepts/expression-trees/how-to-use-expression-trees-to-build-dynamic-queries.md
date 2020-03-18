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
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Jak używać drzew wyrażeń do tworzenia zapytań dynamicznych (C#)
W LINQ drzewa wyrażeń są używane do reprezentowania uporządkowanych kwerend, które są przeznaczone dla źródeł danych, które implementują <xref:System.Linq.IQueryable%601>. Na przykład dostawca LINQ implementuje <xref:System.Linq.IQueryable%601> interfejs do wykonywania zapytań relacyjnych magazynów danych. Kompilator C# kompiluje kwerendy, które są przeznaczone dla takich źródeł danych do kodu, który tworzy drzewo wyrażeń w czasie wykonywania. Dostawca kwerendy może następnie przechodzić przez strukturę danych drzewa wyrażeń i tłumaczyć ją na język zapytania odpowiedni dla źródła danych.  
  
 Drzewa wyrażeń są również używane w LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.  
  
 W tym temacie opisano sposób używania drzew wyrażeń do tworzenia dynamicznych zapytań LINQ. Zapytania dynamiczne są przydatne, gdy specyfika kwerendy nie są znane w czasie kompilacji. Na przykład aplikacja może dostarczyć interfejs użytkownika, który umożliwia użytkownikowi końcowemu określenie jednego lub więcej predykatów do filtrowania danych. Aby użyć LINQ do wykonywania zapytań, tego rodzaju aplikacja musi używać drzewa wyrażeń do tworzenia kwerendy LINQ w czasie wykonywania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak użyć drzewa `IQueryable` wyrażeń do konstruowania kwerendy względem źródła danych, a następnie wykonać ją. Kod tworzy drzewo wyrażeń do reprezentowania następującej kwerendy:  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 Metody fabryczne w <xref:System.Linq.Expressions> obszarze nazw są używane do tworzenia drzew wyrażeń reprezentujących wyrażenia, które tworzą ogólną kwerendę. Wyrażenia reprezentujące wywołania standardowych metod operatora kwerendy <xref:System.Linq.Queryable> odnoszą się do implementacji tych metod. Drzewo wyrażeń końcowych jest przekazywane do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy źródła danych w `IQueryable` celu utworzenia kwerendy wykonywalnej typu `IQueryable`. Wyniki są uzyskiwane przez wyliczenie tej zmiennej kwerendy.  
  
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
  
 Ten kod używa stałej liczby wyrażeń w predykacie, który jest przekazywany `Queryable.Where` do metody. Można jednak napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu, która zależy od danych wejściowych użytkownika. Można również zmieniać standardowe operatory zapytań, które są wywoływane w kwerendzie, w zależności od danych wejściowych od użytkownika.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Dołącz obszar nazw System.Linq.Expressions.  
  
## <a name="see-also"></a>Zobacz też

- [Drzewa wyrażeń (C#)](./index.md)
- [Jak wykonać drzewa wyrażeń (C#)](./how-to-execute-expression-trees.md)
- [Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
