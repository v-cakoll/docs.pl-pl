---
title: 'Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: e3afbea647bb429d25f41f37fde268565bc5bf8a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44048707"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)
W programie LINQ, drzew wyrażeń są używane do reprezentowania strukturyzowanych zapytań, których platformą docelową źródeł danych, który implementuje <xref:System.Linq.IQueryable%601>. Na przykład implementuje dostawcę LINQ <xref:System.Linq.IQueryable%601> interfejs do wykonywania zapytań magazynów danych relacyjnych. Kompilator języka C# kompiluje zapytań przeznaczonych dla tych źródeł danych do kodu, który kompiluje do drzewa wyrażenie w czasie wykonywania. Dostawca kwerend można przechodzić przez strukturę danych drzewa wyrażeń i tłumaczenie język zapytań, odpowiednie dla źródła danych.  
  
 Drzewa wyrażeń są również używane w składniku LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.  
  
 W tym temacie opisano, jak używać drzew wyrażeń do tworzenia dynamicznych zapytań LINQ. Zapytania dynamiczne są przydatne, gdy szczegółowe informacje na temat zapytania nie są znane w czasie kompilacji. Na przykład aplikacja może dostarczyć interfejs użytkownika, który umożliwia użytkownikowi określić jeden lub więcej predykatów do filtrowania danych. Aby można było używać programu LINQ do wykonywania zapytań, tego rodzaju aplikacji należy użyć drzew wyrażeń, aby utworzyć zapytanie LINQ w czasie wykonywania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak używanie drzew wyrażeń do utworzenia zapytania dotyczącego `IQueryable` źródła danych, a następnie uruchomić go. Kod zostanie skompilowany drzewa wyrażenie do reprezentowania następujące zapytanie:  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 Metodach fabryki w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzew wyrażeń, które reprezentują wyrażenia, które tworzą ogólną zapytania. Wyrażenia, które reprezentują wywołania metody standardowego operatora zapytań odwoływać się do <xref:System.Linq.Queryable> implementacji tych metod. Drzewa wyrażeń końcowego jest przekazywany do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródła danych do utworzenia pliku wykonywalnego zapytania typu `IQueryable`. Wyniki są uzyskać, wyliczając tej zmiennej zapytania.  
  
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
  
 Ten kod używa stałej liczby wyrażeń w predykacie, który jest przekazywany do `Queryable.Where` metody. Jednakże można napisać aplikację, która łączy zmienną liczbę predykatu wyrażenia zależne od danych wejściowych użytkownika. Mogą też występować różne standardowe operatory zapytań, które są wywoływane w zapytaniu, w zależności od danych wejściowych od użytkownika.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Utwórz nową **aplikację Konsolową** projektu.  
  
-   Dodaj odwołanie do biblioteki System.Core.dll, jeśli nie jest wywoływany.  
  
-   Obejmują System.Linq.Expressions przestrzeni nazw.  
  
-   Skopiuj kod z przykładu i wklej go w `Main` metody.  
  
## <a name="see-also"></a>Zobacz też

- [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [Porady: wykonywanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
- [Porady: dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
