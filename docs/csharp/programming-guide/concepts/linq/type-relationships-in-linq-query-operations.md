---
title: Relacje typu w operacjach kwerend LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 3b8ae80ff17ea2cf12c3d78c092dd3233ac0751d
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63774007"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Relacje typu w operacjach kwerend LINQ (C#)
Aby efektywnie pisać zapytania, należy zrozumieć jak powiązane są ze sobą typy zmiennych w kompletnej operacji zapytania. Jeśli zrozumiesz te relacje będzie łatwiej pojmować [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] i przykłady kodu w dokumentacji. Ponadto zrozumiesz, co dzieje się, gdy zmienne są wpisywane niejawnie przy użyciu `var`.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operacje zapytań są silnie typizowane w źródle danych, samo zapytanie i wykonywania zapytań. Typ zmiennych w zapytaniu musi być zgodny z typem elementów w źródle danych i z typem zmiennej iteracji w `foreach` instrukcji. To pogrubione wpisywanie gwarantuje, że błędy wpisywania są wyłapywane w czasie kompilacji, gdy mogą być poprawione zanim użytkownik je napotka.  
  
 W celu przedstawienia relacji tych typów, większość przykładów, które należy wykonać Użyj jawnego wpisywania wszystkich zmiennych. W ostatnim przykładzie pokazano, jak same zasady mają zastosowanie, nawet gdy możesz użyć niejawnego wpisywania, za pomocą [var](../../../../csharp/language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Kwerendy, które nie przetwarzają dane źródłowe  
 Poniższa ilustracja przedstawia [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operację, która nie wykonuje transformacji danych zapytania. Źródło zawiera sekwencję ciągów i wynik zapytania jest również sekwencją ciągów.  
  
 ![Diagram przedstawiający Relacja typów danych w zapytaniu programu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Argument typu źródła danych określa typ zmiennej zakresu.  
  
2. Typ wybranego obiektu określa typ zmiennej zapytania. W tym miejscu `name` jest ciągiem. Zmienna zapytania jest `IEnumerable<string>`.  
  
3. Zmienna zapytania jest powtarzana w `foreach` instrukcji. Ponieważ zmienna zapytania jest sekwencja ciągów, zmienną iteracji jest ciąg.  
  
## <a name="queries-that-transform-the-source-data"></a>Zapytania, które przetwarzają dane źródłowe  
 Poniższa ilustracja przedstawia [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operację, która wykonuje prostą transformację danych zapytania. Zapytanie pobiera sekwencję `Customer` obiektów jako dane wejściowe i wybiera jedynie `Name` właściwości w wyniku. Ponieważ `Name` jest ciągiem, tworzy zapytanie sekwencji ciągów jako dane wyjściowe.  
  
 ![Diagram przedstawiający kwerendę, która przekształca typu danych.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Argument typu źródła danych określa typ zmiennej zakresu.  
  
2. `select` Instrukcja zwraca `Name` właściwości zamiast pełnego `Customer` obiektu. Ponieważ `Name` jest ciągiem, argument typu `custNameQuery` jest `string`, a nie `Customer`.  
  
3. Ponieważ `custNameQuery` jest sekwencją ciągów, `foreach` Zmienna iteracji pętli musi być również `string`.  
  
 Na poniższej ilustracji przedstawiono nieco bardziej skomplikowaną transformację. `select` Instrukcja zwraca typ anonimowy, który przechwytuje tylko dwa elementy członkowskie oryginalnego `Customer` obiektu.  
  
 ![Diagram przedstawiający bardziej złożonego zapytania, który przekształca typu danych.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Argument typu źródła danych jest zawsze typem zmiennej zakresu w zapytaniu.  
  
2. Ponieważ `select` instrukcja generuje typ anonimowy, zmienna zapytania musi być wpisana niejawnie przy użyciu `var`.  
  
3. Ponieważ typ zmiennej zapytania jest niejawny, Zmienna iteracji w `foreach` pętli musi być niejawne.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Umożliwienie kompilatorowi wywnioskowania informacji o typie  
 Chociaż należy zrozumieć relacje typów w operacji zapytania, masz opcję, aby pozwolić kompilatorowi wykonanie całąj pracy za Ciebie. Słowo kluczowe [var](../../../../csharp/language-reference/keywords/var.md) mogą być używane dla dowolnej zmiennej lokalnej w operacji zapytania. Na poniższej ilustracji jest podobny do przykładu numer 2, który została omówiony wcześniej. Jednak kompilator dostarcza silnego typu dla każdej zmiennej w operacji zapytania.  
  
 ![Diagram pokazujący przepływ typu przy użyciu niejawnego wpisywania.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
