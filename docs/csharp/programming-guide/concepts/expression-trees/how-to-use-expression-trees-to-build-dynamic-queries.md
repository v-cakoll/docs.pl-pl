---
title: 'Instrukcje: Używanie drzew wyrażeń do kompilowania zapytań dynamicznychC#()'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 400668e51fda4a728b42679c37a07399d1f73326
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595077"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Instrukcje: Używanie drzew wyrażeń do kompilowania zapytań dynamicznychC#()
W LINQ, drzewa wyrażeń służą do reprezentowania zapytań strukturalnych, które są docelowymi źródłami <xref:System.Linq.IQueryable%601>danych, które implementują. Na przykład dostawca LINQ implementuje <xref:System.Linq.IQueryable%601> interfejs do wykonywania zapytań dotyczących magazynów danych relacyjnych. C# Kompilator kompiluje zapytania, które są przeznaczone dla tych źródeł danych w kodzie, który kompiluje drzewo wyrażeń w czasie wykonywania. Dostawca zapytań może następnie przechodzenie przez strukturę danych drzewa wyrażenia i przetłumaczyć je do języka zapytań odpowiedniego dla źródła danych.  
  
 Drzewa wyrażeń są również używane w LINQ do reprezentowania wyrażeń lambda, które są przypisane do zmiennych typu <xref:System.Linq.Expressions.Expression%601>.  
  
 W tym temacie opisano, jak używać drzew wyrażeń do tworzenia dynamicznych zapytań LINQ. Zapytania dynamiczne są przydatne, gdy określone zapytanie nie jest znane w czasie kompilacji. Na przykład aplikacja może udostępnić interfejs użytkownika, który umożliwia użytkownikowi końcowemu określenie co najmniej jednego predykatu w celu odfiltrowania danych. Aby można było używać LINQ do wykonywania zapytań, ten rodzaj aplikacji musi używać drzew wyrażeń do tworzenia zapytania LINQ w czasie wykonywania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać drzew wyrażeń do konstruowania zapytania względem `IQueryable` źródła danych, a następnie wykonywania go. Kod kompiluje drzewo wyrażenia, aby reprezentować następujące zapytanie:  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 Metody fabryki w <xref:System.Linq.Expressions> przestrzeni nazw są używane do tworzenia drzew wyrażeń, które reprezentują wyrażenia, które składają się na zapytanie ogólne. Wyrażenia, które reprezentują wywołania metod standardowego operatora zapytań, odnoszą się do <xref:System.Linq.Queryable> implementacji tych metod. Końcowe drzewo wyrażeń jest przenoszone do <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementacji dostawcy `IQueryable` źródła danych w celu utworzenia zapytania wykonywalnego typu `IQueryable`. Wyniki są uzyskiwane przez Wyliczenie tej zmiennej zapytania.  
  
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
  
 Ten kod używa ustalonej liczby wyrażeń w predykacie, który jest przesyłany do `Queryable.Where` metody. Można jednak napisać aplikację, która łączy zmienną liczbę wyrażeń predykatu, które są zależne od danych wprowadzonych przez użytkownika. Możesz również zmienić standardowe operatory zapytań, które są wywoływane w zapytaniu, w zależności od danych wejściowych użytkownika.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Uwzględnij przestrzeń nazw System. LINQ. Expressions.  
  
## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (C#)](./index.md)
- [Instrukcje: Wykonywanie drzew wyrażeń (C#)](./how-to-execute-expression-trees.md)
- [Instrukcje: Dynamiczne określanie filtrów predykatu w czasie wykonywania](../../linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
