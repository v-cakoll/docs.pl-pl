---
title: Relacje typu w operacjach zapytań LINQ (C#)
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
ms.openlocfilehash: 154501d666b467c94f5d1dd721f1e2303189c908
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484827"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Relacje typu w operacjach zapytań LINQ (C#)
Aby efektywnie pisać zapytania, należy zrozumieć jak powiązane są ze sobą typy zmiennych w kompletnej operacji zapytania. Jeśli zrozumiesz te relacje będzie łatwiej pojmować [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] i przykłady kodu w dokumentacji. Ponadto zrozumiesz, co dzieje się, gdy zmienne są wpisywane niejawnie przy użyciu `var`.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operacje zapytań są silnie typizowane w źródle danych, samo zapytanie i wykonywania zapytań. Typ zmiennych w zapytaniu musi być zgodny z typem elementów w źródle danych i z typem zmiennej iteracji w `foreach` instrukcji. To pogrubione wpisywanie gwarantuje, że błędy wpisywania są wyłapywane w czasie kompilacji, gdy mogą być poprawione zanim użytkownik je napotka.  
  
 W celu przedstawienia relacji tych typów, większość przykładów, które należy wykonać Użyj jawnego wpisywania wszystkich zmiennych. W ostatnim przykładzie pokazano, jak same zasady mają zastosowanie, nawet gdy możesz użyć niejawnego wpisywania, za pomocą [var](../../../../csharp/language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Kwerendy, które nie przetwarzają dane źródłowe  
 Poniższa ilustracja przedstawia [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operację, która nie wykonuje transformacji danych zapytania. Źródło zawiera sekwencję ciągów i wynik zapytania jest również sekwencją ciągów.  
  
 ![Typy relacji danych, w zapytaniu programu LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")  
  
1.  Argument typu źródła danych określa typ zmiennej zakresu.  
  
2.  Typ wybranego obiektu określa typ zmiennej zapytania. W tym miejscu `name` jest ciągiem. Zmienna zapytania jest `IEnumerable<string>`.  
  
3.  Zmienna zapytania jest powtarzana w `foreach` instrukcji. Ponieważ zmienna zapytania jest sekwencja ciągów, zmienną iteracji jest ciąg.  
  
## <a name="queries-that-transform-the-source-data"></a>Zapytania, które przetwarzają dane źródłowe  
 Poniższa ilustracja przedstawia [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operację, która wykonuje prostą transformację danych zapytania. Zapytanie pobiera sekwencję `Customer` obiektów jako dane wejściowe i wybiera jedynie `Name` właściwości w wyniku. Ponieważ `Name` jest ciągiem, tworzy zapytanie sekwencji ciągów jako dane wyjściowe.  
  
 ![Zapytanie, które przekształca typu danych](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")  
  
1.  Argument typu źródła danych określa typ zmiennej zakresu.  
  
2.  `select` Instrukcja zwraca `Name` właściwości zamiast pełnego `Customer` obiektu. Ponieważ `Name` jest ciągiem, argument typu `custNameQuery` jest `string`, a nie `Customer`.  
  
3.  Ponieważ `custNameQuery` jest sekwencją ciągów, `foreach` Zmienna iteracji pętli musi być również `string`.  
  
 Na poniższej ilustracji przedstawiono nieco bardziej skomplikowaną transformację. `select` Instrukcja zwraca typ anonimowy, który przechwytuje tylko dwa elementy członkowskie oryginalnego `Customer` obiektu.  
  
 ![Zapytanie, które przekształca typu danych](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")  
  
1.  Argument typu źródła danych jest zawsze typem zmiennej zakresu w zapytaniu.  
  
2.  Ponieważ `select` instrukcja generuje typ anonimowy, zmienna zapytania musi być wpisana niejawnie przy użyciu `var`.  
  
3.  Ponieważ typ zmiennej zapytania jest niejawny, Zmienna iteracji w `foreach` pętli musi być niejawne.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Umożliwienie kompilatorowi wywnioskowania informacji o typie  
 Chociaż należy zrozumieć relacje typów w operacji zapytania, masz opcję, aby pozwolić kompilatorowi wykonanie całąj pracy za Ciebie. Słowo kluczowe [var](../../../../csharp/language-reference/keywords/var.md) mogą być używane dla dowolnej zmiennej lokalnej w operacji zapytania. Na poniższej ilustracji jest podobny do przykładu numer 2, który została omówiony wcześniej. Jednak kompilator dostarcza silnego typu dla każdej zmiennej w operacji zapytania.  
  
 ![Typ przepływu niejawnego wpisywania](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")  
  
 Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
