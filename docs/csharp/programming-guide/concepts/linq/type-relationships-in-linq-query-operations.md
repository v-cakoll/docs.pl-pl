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
ms.openlocfilehash: 41853e6858fae9e8d449aeed95a6a84f343d5874
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635616"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Relacje typu w operacjach kwerend LINQ (C#)
Aby efektywnie pisać zapytania, należy zrozumieć, jak typy zmiennych w kompletnej operacji zapytania wszystkie odnoszą się do siebie. Jeśli rozumiesz te relacje, łatwiej będzie comprehend przykłady LINQ i przykłady kodu w dokumentacji. Ponadto dowiesz się, co się dzieje w tle, gdy zmienne są wpisywane niejawnie przy użyciu `var`.  
  
 Operacje zapytań LINQ są jednoznacznie wpisywane w źródle danych, w samej kwerendzie i w wykonaniu zapytania. Typ zmiennych w zapytaniu musi być zgodny z typem elementów w źródle danych i typem zmiennej iteracji w instrukcji `foreach`. Takie silne wpisywanie gwarantuje, że błędy typu są przechwytywane w czasie kompilacji, gdy można je poprawić przed ich wystąpieniem przez użytkowników.  
  
 Aby przedstawić te relacje typu, większość przykładów, które są zgodne z użyciem jawnego wpisywania dla wszystkich zmiennych. W ostatnim przykładzie pokazano, jak te same zasady mają zastosowanie nawet w przypadku użycia niejawnego wpisywania przy użyciu funkcji [var](../../../language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Zapytania, które nie przekształcają danych źródłowych  
 Na poniższej ilustracji przedstawiono LINQ to Objects operacji zapytania, która nie wykonuje transformacji danych. Źródło zawiera sekwencję ciągów, a dane wyjściowe zapytania są również sekwencją ciągów.  
  
 ![Diagram przedstawiający relację typów danych w zapytaniu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Argument typu źródła danych określa typ zmiennej zakresu.  
  
2. Typ wybranego obiektu określa typ zmiennej zapytania. W tym miejscu `name` jest ciągiem. W związku z tym zmienna zapytania jest `IEnumerable<string>`.  
  
3. Zmienna zapytania jest powtarzana w instrukcji `foreach`. Ponieważ zmienna zapytania jest sekwencją ciągów, Zmienna iteracji jest również ciągiem.  
  
## <a name="queries-that-transform-the-source-data"></a>Zapytania, które przekształcają dane źródłowe  
 Na poniższej ilustracji przedstawiono [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operacji zapytania, która wykonuje prostą transformację danych. Zapytanie pobiera sekwencję `Customer` obiektów jako dane wejściowe i wybiera tylko Właściwość `Name` w wyniku. Ponieważ `Name` jest ciągiem, zapytanie tworzy sekwencję ciągów jako dane wyjściowe.  
  
 ![Diagram przedstawiający zapytanie, które przekształca typ danych.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Argument typu źródła danych określa typ zmiennej zakresu.  
  
2. Instrukcja `select` zwraca właściwość `Name` zamiast kompletnego obiektu `Customer`. Ponieważ `Name` jest ciągiem, argument typu `custNameQuery` jest `string`, a nie `Customer`.  
  
3. Ponieważ `custNameQuery` jest sekwencją ciągów, Zmienna iteracji pętli `foreach` musi być `string`.  
  
 Na poniższej ilustracji przedstawiono nieco bardziej skomplikowaną transformację. Instrukcja `select` zwraca typ anonimowy, który przechwytuje tylko dwa elementy z oryginalnego obiektu `Customer`.  
  
 ![Diagram przedstawiający bardziej złożone zapytania, które przekształcają typ danych.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Argument typu źródła danych jest zawsze typem zmiennej zakresu w zapytaniu.  
  
2. Ponieważ instrukcja `select` generuje typ anonimowy, zmienna zapytania musi być wpisana niejawnie przy użyciu `var`.  
  
3. Ponieważ typ zmiennej zapytania jest niejawny, Zmienna iteracji w pętli `foreach` musi być również niejawna.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Zezwalanie na informacje o typie wnioskowania kompilatora  
 Chociaż należy zrozumieć relacje typu w operacji zapytania, masz możliwość zezwalania kompilatorowi na wykonywanie wszystkich zadań. [Var](../../../language-reference/keywords/var.md) słowa kluczowego może być używana dla każdej zmiennej lokalnej w operacji zapytania. Poniższa ilustracja jest podobna do przykładu numer 2, który został omówiony wcześniej. Jednak kompilator dostarcza mocny typ dla każdej zmiennej w operacji zapytania.  
  
 ![Diagram przedstawiający przepływ typu z niejawnym wpisywaniem.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).  
