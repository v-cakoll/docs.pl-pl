---
title: Zapytania w składniku LINQ to Entities
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 3144796dfb1a970152d8ae56424aa37592d5da09
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848785"
---
# <a name="queries-in-linq-to-entities"></a>Zapytania w składniku LINQ to Entities
Kwerenda jest wyrażeniem pobieranym dane ze źródła danych. Zapytania są zwykle wyrażone w specjalistycznym języku zapytań, takich jak SQL dla relacyjnych baz danych i XQuery dla XML. W związku z tym deweloperzy musieli nauczyć się nowego języka zapytań dla każdego typu źródła danych lub formatu danych, które kwerendy. Zintegrowane z językiem zapytanie (LINQ) oferuje prostszy i spójny model do pracy z danymi w różnych źródłach danych i formatach. W kwerendzie LINQ zawsze pracujesz z obiektami programowania.  
  
 Operacja kwerendy LINQ składa się z trzech akcji: uzyskać źródło danych lub źródła, utworzyć kwerendę i wykonać kwerendę.  
  
 Źródła danych, które <xref:System.Collections.Generic.IEnumerable%601> implementują <xref:System.Linq.IQueryable%601> interfejs ogólny lub interfejs ogólny można zbadać za pośrednictwem LINQ. Wystąpienia klasy ogólnej, <xref:System.Data.Objects.ObjectQuery%601> która implementuje <xref:System.Linq.IQueryable%601> interfejs ogólny, służą jako źródło danych dla LINQ do zapytań jednostek. Klasa <xref:System.Data.Objects.ObjectQuery%601> rodzajowa reprezentuje kwerendę, która zwraca kolekcję obiektów zero lub więcej wpisanych. Można również pozwolić kompilator wywnioskować typ `var` jednostki przy użyciu c# słowa kluczowego (Dim w języku Visual Basic).  
  
 W kwerendzie należy określić dokładnie informacje, które mają być pobierane ze źródła danych. Kwerenda może również określić sposób sortowania, grupowania i kształtowania tych informacji przed ich zwracaniem. W LINQ kwerenda jest przechowywana w zmiennej. Jeśli kwerenda zwraca sekwencję wartości, sama zmienna kwerendy musi być typem, który można zbadać. Ta zmienna kwerendy nie wykonuje żadnych akcji i nie zwraca żadnych danych; przechowuje tylko informacje o kwerendzie. Po utworzeniu kwerendy należy wykonać tę kwerendę, aby pobrać wszystkie dane.  
  
## <a name="query-syntax"></a>Składnia kwerendy  
 LINQ do Jednostek kwerendy mogą składać się w dwóch różnych składni: składnia wyrażenia kwerendy i składnia kwerendy opartej na metodzie. Składnia wyrażenia kwerendy jest nowa w językach C# 3.0 i Visual Basic 9.0 i składa się z zestawu klauzul zapisanych w składni deklaratywnej podobnej do Transact-SQL lub XQuery. Jednak środowisko uruchomieniowe języka wspólnego programu .NET Framework (CLR) nie może odczytać samej składni wyrażenia kwerendy. W związku z tym w czasie kompilacji wyrażenia kwerendy są tłumaczone na coś, co CLR rozumie: wywołania metody. Metody te są znane jako *standardowe operatory zapytań*. Jako deweloper masz możliwość wywoływania ich bezpośrednio przy użyciu składni metody, zamiast używać składni kwerendy. Aby uzyskać więcej informacji, zobacz [Składnia kwerendy i składnia metody w LINQ](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Składnia wyrażenia kwerendy  
 Wyrażenia kwerendy są składnią kwerendy deklaratywnej. Ta składnia umożliwia deweloperowi pisanie zapytań w języku wysokiego poziomu, który jest sformatowany podobnie do Transact-SQL. Za pomocą składni wyrażenia kwerendy, można wykonać nawet złożone operacje filtrowania, zamawiania i grupowania na źródłach danych przy minimalnym kodzie. Aby uzyskać więcej informacji, [podstawowe operacje kwerend (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Przykłady, które pokazują, jak używać składni wyrażenia kwerendy, zobacz następujące tematy:  
  
- [Przykłady składni wyrażeń zapytania, projekcja](query-expression-syntax-examples-projection.md)  
  
- [Przykłady składni wyrażeń zapytania, filtrowanie](query-expression-syntax-examples-filtering.md)  
  
- [Przykłady składni wyrażeń zapytania, porządkowanie](query-expression-syntax-examples-ordering.md)  
  
- [Przykłady składni wyrażeń zapytania, operatory agregacji](query-expression-syntax-examples-aggregate-operators.md)  
  
- [Przykłady składni wyrażeń zapytania, partycjonowanie](query-expression-syntax-examples-partitioning.md)  
  
- [Przykłady składni wyrażeń zapytania, operatory sprzężenia](query-expression-syntax-examples-join-operators.md)  
  
- [Przykłady składni wyrażeń zapytania, operatory elementu](query-expression-syntax-examples-element-operators.md)  
  
- [Przykłady składni wyrażeń zapytania, grupowanie](query-expression-syntax-examples-grouping.md)  
  
- [Przykłady składni wyrażeń zapytania, nawigowanie po relacjach](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Składnia kwerend opartych na metodzie  
 Innym sposobem skomponowania LINQ do zapytań jednostek jest przy użyciu zapytań opartych na metodach. Składnia kwerendy oparta na metodzie jest sekwencją bezpośrednich wywołań metody do metod operatora LINQ, przekazując wyrażenia lambda jako parametry. Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Przykłady, które pokazują, jak używać składni opartej na metodach, zobacz następujące tematy:  
  
- [Przykłady składni zapytania oparte na metodzie, projekcja](method-based-query-syntax-examples-projection.md)  
  
- [Przykłady składni zapytania oparte na metodzie, filtrowanie](method-based-query-syntax-examples-filtering.md)  
  
- [Przykłady składni zapytania oparte na metodzie, porządkowanie](method-based-query-syntax-examples-ordering.md)  
  
- [Przykłady składni zapytania oparte na metodzie, operatory agregacji](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [Przykłady składni zapytania oparte na metodzie, partycjonowanie](method-based-query-syntax-examples-partitioning.md)  
  
- [Przykłady składni zapytania oparte na metodzie, konwersja](method-based-query-syntax-examples-conversion.md)  
  
- [Przykłady składni zapytania oparte na metodzie, operatory sprzężenia](method-based-query-syntax-examples-join-operators.md)  
  
- [Przykłady składni zapytania oparte na metodzie, operatory elementu](method-based-query-syntax-examples-element-operators.md)  
  
- [Przykłady składni zapytania oparte na metodzie, grupowanie](method-based-query-syntax-examples-grouping.md)  
  
- [Przykłady składni zapytania oparte na metodzie, nawigowanie po relacjach](method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Zobacz też

- [LINQ to Entities](linq-to-entities.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Wprowadzenie do programu LINQ w Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Opcje scalania EF i skompilowane kwerendy](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
