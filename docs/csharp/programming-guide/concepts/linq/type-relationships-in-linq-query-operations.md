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
ms.openlocfilehash: 42519a74be1bd6934bc7a3304d154321697d128c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591021"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Relacje typu w operacjach kwerend LINQ (C#)
Aby efektywnie pisać zapytania, należy zrozumieć, jak typy zmiennych w kompletnej operacji zapytania wszystkie odnoszą się do siebie. Jeśli rozumiesz te relacje, łatwiej będzie comprehend [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przykłady i przykłady kodu w dokumentacji. Ponadto dowiesz się, co się dzieje w tle, gdy zmienne są wpisywane niejawnie `var`przy użyciu.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]operacje zapytań są jednoznacznie wpisywane w źródle danych, w samej kwerendzie i w wykonaniu zapytania. Typ zmiennych w zapytaniu musi być zgodny z typem elementów w źródle danych i typem zmiennej iteracji w `foreach` instrukcji. Takie silne wpisywanie gwarantuje, że błędy typu są przechwytywane w czasie kompilacji, gdy można je poprawić przed ich wystąpieniem przez użytkowników.  
  
 Aby przedstawić te relacje typu, większość przykładów, które są zgodne z użyciem jawnego wpisywania dla wszystkich zmiennych. W ostatnim przykładzie pokazano, jak te same zasady mają zastosowanie nawet w przypadku użycia niejawnego wpisywania przy użyciu funkcji [var](../../../language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Zapytania, które nie przekształcają danych źródłowych  
 Na poniższej ilustracji przedstawiono [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operację zapytania do obiektów, która nie wykonuje transformacji danych. Źródło zawiera sekwencję ciągów, a dane wyjściowe zapytania są również sekwencją ciągów.  
  
 ![Diagram przedstawiający relację typów danych w zapytaniu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Argument typu źródła danych określa typ zmiennej zakresu.  
  
2. Typ wybranego obiektu określa typ zmiennej zapytania. Oto `name` ciąg. W związku z tym zmienna zapytania jest `IEnumerable<string>`.  
  
3. Zmienna zapytania jest powtarzana w `foreach` instrukcji. Ponieważ zmienna zapytania jest sekwencją ciągów, Zmienna iteracji jest również ciągiem.  
  
## <a name="queries-that-transform-the-source-data"></a>Zapytania, które przekształcają dane źródłowe  
 Na poniższej ilustracji przedstawiono [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operację zapytania, która wykonuje prostą transformację danych. Zapytanie pobiera sekwencję `Customer` obiektów jako dane wejściowe i wybiera `Name` tylko właściwość w wyniku. Ponieważ `Name` jest ciągiem, zapytanie tworzy sekwencję ciągów jako dane wyjściowe.  
  
 ![Diagram przedstawiający zapytanie, które przekształca typ danych.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Argument typu źródła danych określa typ zmiennej zakresu.  
  
2. Instrukcja zwraca właściwość zamiast kompletnego `Customer`obiektu. `select` `Name` Ponieważ `Name` jest ciągiem, `custNameQuery` argument typu ma wartość `string`, a nie `Customer`.  
  
3. Ponieważ `custNameQuery` jest sekwencją ciągów `foreach` , `string`Zmienna iteracji pętli musi być również.  
  
 Na poniższej ilustracji przedstawiono nieco bardziej skomplikowaną transformację. Instrukcja zwraca typ anonimowy, który przechwytuje tylko dwa elementy członkowskie oryginalnego `Customer` obiektu. `select`  
  
 ![Diagram przedstawiający bardziej złożone zapytania, które przekształcają typ danych.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Argument typu źródła danych jest zawsze typem zmiennej zakresu w zapytaniu.  
  
2. Ponieważ instrukcja generuje typ anonimowy, zmienna zapytania musi być wpisana niejawnie przy użyciu `var`. `select`  
  
3. Ponieważ typ zmiennej zapytania jest niejawny, Zmienna iteracji w `foreach` pętli musi być również niejawna.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Zezwalanie na informacje o typie wnioskowania kompilatora  
 Chociaż należy zrozumieć relacje typu w operacji zapytania, masz możliwość zezwalania kompilatorowi na wykonywanie wszystkich zadań. [Var](../../../language-reference/keywords/var.md) słowa kluczowego może być używana dla każdej zmiennej lokalnej w operacji zapytania. Poniższa ilustracja jest podobna do przykładu numer 2, który został omówiony wcześniej. Jednak kompilator dostarcza mocny typ dla każdej zmiennej w operacji zapytania.  
  
 ![Diagram przedstawiający przepływ typu z niejawnym wpisywaniem.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Aby uzyskać więcej informacji `var`na temat, zobacz niejawnie [wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).  
