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
ms.openlocfilehash: 274c5eaee2b4bf0e1331fb7a4a1a89a432a567c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Relacje typu w operacjach zapytań LINQ (C#)
Skutecznie pisać zapytania, należy zrozumieć, jak typy zmiennych w operacji zapytania ukończone wszystkie powiązane ze sobą relacjami. Jeśli znasz te relacje będzie łatwo pojmować [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przykłady i przykładów kodu w dokumentacji. Ponadto będzie zrozumiałe, występujące w tle podczas wpisywania niejawnie za pomocą zmiennych `var`.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Operacje kwerend są silnie typizowane w źródle danych, samą kwerendę i do wykonywania zapytania. Typ zmiennych w kwerendzie musi być zgodny z typem elementów w źródle danych i typ zmiennej iteracji w `foreach` instrukcji. Silne wpisywanie gwarantuje, że typ błędy są przechwytywane w czasie kompilacji podczas ich może zostać poprawione przed ich napotkaniu.  
  
 W celu zaprezentowania relacje tych typów, większość przykładów, które należy wykonać Użyj jawnego wpisanie wszystkich zmiennych. Ostatni przykładzie pokazano, jak te same zasady stosowane, nawet jeśli używasz wpisanie niejawna przy użyciu [var](../../../../csharp/language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Zapytania, które nie przetwarzają dane źródłowe  
 Na poniższej ilustracji pokazano [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do obiektów operacji, który wykonuje nie przekształcenia danych zapytania. Źródło zawiera sekwencję ciągów i wyników zapytania jest również sekwencję ciągów.  
  
 ![Typy relacji danych w zapytaniu składnika LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")  
  
1.  Argument typu źródła danych określa rodzaj zmiennej zakresu.  
  
2.  Typ obiektu, który wybrano określa typu zmienną zapytania. W tym miejscu `name` jest ciągiem. W związku z tym jest zmienną zapytania `IEnumerable` \<ciąg >.  
  
3.  Do zmiennej zapytania jest powtórzyć za pośrednictwem w `foreach` instrukcji. Ponieważ zmienną zapytania jest sekwencję ciągów, zmiennej iteracji również jest ciągiem.  
  
## <a name="queries-that-transform-the-source-data"></a>Zapytania, które przetwarzają dane źródłowe  
 Na poniższej ilustracji pokazano [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operacji, który wykonuje transformację proste danych zapytania. Zapytanie pobiera sekwencję `Customer` obiekty jako dane wejściowe i wybierze opcję tylko `Name` właściwości w wyniku. Ponieważ `Name` to ciąg zapytania i tworzy sekwencję ciągów jako dane wyjściowe.  
  
 ![Zapytanie, które przekształca typu danych](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")  
  
1.  Argument typu źródła danych określa rodzaj zmiennej zakresu.  
  
2.  `select` Zwraca instrukcji `Name` zamiast pełnej właściwości `Customer` obiektu. Ponieważ `Name` to ciąg argumentu typu `custNameQuery` jest `string`, a nie `Customer`.  
  
3.  Ponieważ `custNameQuery` Sekwencja ciągów, `foreach` zmiennej iteracji pętli musi być również `string`.  
  
 Na poniższej ilustracji przedstawiono nieco bardziej złożone przekształcenia. `select` Instrukcja zwraca typ anonimowy, który przechwytuje tylko dwa elementy członkowskie z oryginalną `Customer` obiektu.  
  
 ![Zapytanie, które przekształca typu danych](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")  
  
1.  Argument typu źródła danych jest zawsze typu zmienną zakresu w zapytaniu.  
  
2.  Ponieważ `select` instrukcji powoduje typu anonimowego, zmienną zapytania musi być niejawnie wpisanych przy użyciu `var`.  
  
3.  Ponieważ pośrednie, jest typu zmienną zapytania zmiennej iteracji w `foreach` pętli musi być również niejawnej.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Umożliwienie kompilatora wnioskowanie informacji o typie  
 Chociaż należy zrozumieć relacje typu w operacji zapytania, masz opcję umożliwiającą programowi kompilatora wykonać całą pracę za Ciebie. Słowo kluczowe [var](../../../../csharp/language-reference/keywords/var.md) może służyć do dowolnej zmiennej lokalnej w operacji zapytania. Poniższa ilustracja jest podobny do numer przykład 2 wcześniejszym opisem. Jednak kompilator dostarcza silnego typu dla każdej zmiennej w operacji zapytania.  
  
 ![Typ przepływu niejawnego wpisując](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")  
  
 Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
