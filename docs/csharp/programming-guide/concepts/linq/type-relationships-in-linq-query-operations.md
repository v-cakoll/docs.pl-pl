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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635616"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Relacje typu w operacjach kwerend LINQ (C#)
Aby skutecznie zapisywać zapytania, należy zrozumieć, jak typy zmiennych w operacji kwerendy pełnej odnoszą się do siebie nawzajem. Jeśli rozumiesz te relacje będzie łatwiej zrozumieć przykłady LINQ i przykłady kodu w dokumentacji. Ponadto można zrozumieć, co dzieje się za kulisami, gdy `var`zmienne są niejawnie wpisane przy użyciu .  
  
 Operacje zapytań LINQ są silnie wpisane w źródle danych, w samej kwerendzie i w wykonywaniu kwerendy. Typ zmiennych w kwerendzie musi być zgodny z typem elementów w źródle danych i typem `foreach` zmiennej iteracji w instrukcji. To silne wpisywanie gwarantuje, że błędy typu są przechwycone w czasie kompilacji, gdy można je poprawić, zanim użytkownicy napotkają je.  
  
 W celu zademonstrowania tych relacji typu, większość przykładów, które należy wykonać użyć jawnego wpisywania dla wszystkich zmiennych. Ostatni przykład pokazuje, jak te same zasady mają zastosowanie nawet w przypadku używania niejawnego pisania przy użyciu [var](../../../language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Kwerendy, które nie przekształcają danych źródłowych  
 Na poniższej ilustracji przedstawiono linq do obiektów zapytanie operacji, która wykonuje żadnych przekształceń na danych. Źródło zawiera sekwencję ciągów i dane wyjściowe kwerendy jest również sekwencja ciągów.  
  
 ![Diagram, który pokazuje relację typów danych w kwerendzie LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Argument typu źródła danych określa typ zmiennej zakresu.  
  
2. Typ wybranego obiektu określa typ zmiennej kwerendy. Oto `name` ciąg. W związku z tym `IEnumerable<string>`zmienna kwerendy jest .  
  
3. Zmienna kwerendy jest iterowana w `foreach` instrukcji. Ponieważ zmienna kwerendy jest sekwencją ciągów, zmienna iteracji jest również ciągiem.  
  
## <a name="queries-that-transform-the-source-data"></a>Kwerendy przekształcające dane źródłowe  
 Na poniższej [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ilustracji przedstawiono operację kwerendy, która wykonuje prostą transformację danych. Kwerenda przyjmuje sekwencję `Customer` obiektów jako dane wejściowe `Name` i wybiera tylko właściwość w wyniku. Ponieważ `Name` jest ciągiem, kwerenda tworzy sekwencję ciągów jako dane wyjściowe.  
  
 ![Diagram przedstawiający kwerendę, która przekształca typ danych.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Argument typu źródła danych określa typ zmiennej zakresu.  
  
2. Instrukcja `select` zwraca `Name` właściwość zamiast `Customer` kompletnego obiektu. Ponieważ `Name` jest ciągiem, argument `custNameQuery` `string`typu `Customer`jest , nie .  
  
3. Ponieważ `custNameQuery` jest sekwencją ciągów, zmienna iteracji `foreach` pętli `string`musi być również .  
  
 Na poniższej ilustracji przedstawiono nieco bardziej złożoną transformację. Instrukcja `select` zwraca typ anonimowy, który przechwytuje `Customer` tylko dwa elementy członkowskie oryginalnego obiektu.  
  
 ![Diagram przedstawiający bardziej złożoną kwerendę, która przekształca typ danych.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Argument typu źródła danych jest zawsze typem zmiennej zakresu w kwerendzie.  
  
2. Ponieważ `select` instrukcja tworzy typ anonimowy, zmienna kwerendy musi `var`być niejawnie wpisana przy użyciu .  
  
3. Ponieważ typ zmiennej kwerendy jest niejawna, `foreach` zmienna iteracji w pętli musi być również niejawna.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Zezwalanie kompilatorowi na wywnioskować informacje o typie  
 Chociaż należy zrozumieć relacje typu w operacji kwerendy, masz możliwość, aby umożliwić kompilator wykonać całą pracę dla Ciebie. Słowo kluczowe [var](../../../language-reference/keywords/var.md) może służyć dla dowolnej zmiennej lokalnej w operacji kwerendy. Poniższa ilustracja jest podobna do przykładu numer 2, który został omówiony wcześniej. Jednak kompilator dostarcza silny typ dla każdej zmiennej w operacji kwerendy.  
  
 ![Diagram, który pokazuje przepływ typu z niejawnym wpisywaniem.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Aby uzyskać `var`więcej informacji na temat , zobacz [Niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).  
