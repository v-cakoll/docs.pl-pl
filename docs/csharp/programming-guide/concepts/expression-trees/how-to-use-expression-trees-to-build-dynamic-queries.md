---
title: "Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 78de99ed9b2a2d80c17cb013715a15f45f8fa2ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)
W składniku LINQ, drzew wyrażeń są używane do reprezentowania strukturyzowanych zapytań, które odnoszą się do źródła danych, który implementuje <xref:System.Linq.IQueryable%601>. Na przykład implementuje dostawcy LINQ <xref:System.Linq.IQueryable%601> interfejs na potrzeby zapytań o magazynach danych relacyjnych. Kompilator języka C# kompiluje zapytań, które odnoszą się do tych źródeł danych do kodu, która tworzy drzewo wyrażeń w czasie wykonywania. Wyślij zapytanie do dostawcy można przechodzić między nimi danych struktury drzewa wyrażenia i przekształca ją na język kwerendy odpowiednie dla źródła danych.  
  
 Drzewa wyrażeń są również używane w składniku LINQ do reprezentowania wyrażenia lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.  
  
 W tym temacie opisano, jak używać drzew wyrażeń do tworzenia zapytań LINQ dynamicznych. Zapytania dynamiczne są przydatne, gdy szczegółowe informacje na temat zapytania nie są znane w czasie kompilacji. Na przykład aplikacja może zawierać interfejsu użytkownika, który umożliwia użytkownikowi końcowemu określić co najmniej jeden predykaty do filtrowania danych. Aby można było używać LINQ do wykonywania zapytań, tego rodzaju aplikacji musi używanie drzew wyrażeń do tworzenia zapytań LINQ w czasie wykonywania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia drzew wyrażeń do utworzenia zapytania dotyczącego `IQueryable` źródła danych, a następnie wykonaj go. Kod tworzy drzewo wyrażenia do reprezentowania następujące zapytanie:  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 Metodami factory w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzewa wyrażeń, reprezentujące wyrażeń, które tworzą ogólną zapytania. Wyrażeń, które reprezentują wywołania metod operator standardowej kwerendy odwoływać się do <xref:System.Linq.Queryable> implementacje tych metod. Drzewo wyrażeń końcowego są przekazywane do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródło danych do utworzenia pliku wykonywalnego zapytania typu `IQueryable`. Wyniki są uzyskiwane przez wyliczania tej zmiennej zapytania.  
  
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
  
 Ten kod zawiera stała liczba wyrażeń w predykacie, który jest przekazywany do `Queryable.Where` metody. Jednak można napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu zależny od danych wejściowych użytkownika. Standardowe operatory zapytań wywoływanych w zapytaniu, w zależności od danych wejściowych od użytkownika może być różny.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Utwórz nową **aplikacji konsoli** projektu.  
  
-   Dodaj odwołania do System.Core.dll, jeśli nie jest już używany.  
  
-   Obejmują System.Linq.Expressions przestrzeni nazw.  
  
-   Skopiuj kod z przykładu i wklej ją do `Main` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Porady: wykonywanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Porady: dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
