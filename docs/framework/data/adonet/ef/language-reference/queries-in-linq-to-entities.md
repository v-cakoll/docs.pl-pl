---
title: Zapytania w składniku LINQ to Entities
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 561fa3217a80a8437b7c4d175d5a1156096ac241
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249560"
---
# <a name="queries-in-linq-to-entities"></a>Zapytania w składniku LINQ to Entities
Zapytanie jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są zwykle wyrażane w wyspecjalizowanym języku zapytań, takim jak SQL dla relacyjnych baz danych i XQuery for XML. W związku z tym deweloperzy musieli poznać nowy język zapytań dla każdego typu źródła danych lub formatu danych, który wykonuje zapytanie. Program Query Integrated Language (LINQ) oferuje prostszy, spójny model służący do pracy z danymi w różnych rodzajach źródeł danych i formatach. W zapytaniu LINQ zawsze pracujesz z obiektami programowania.  
  
 Operacja zapytania LINQ składa się z trzech akcji: uzyskanie źródła danych lub źródeł, utworzenie zapytania i wykonanie zapytania.  
  
 Do źródeł danych, które <xref:System.Collections.Generic.IEnumerable%601> implementują interfejs ogólny <xref:System.Linq.IQueryable%601> lub interfejs generyczny, można wykonywać zapytania za pomocą LINQ. Wystąpienia klasy generycznej <xref:System.Data.Objects.ObjectQuery%601> implementującej interfejs ogólny <xref:System.Linq.IQueryable%601> , służące jako źródło danych dla zapytań LINQ to Entities. Klasa <xref:System.Data.Objects.ObjectQuery%601> generyczna reprezentuje zapytanie, które zwraca kolekcję składającą się z zero lub więcej obiektów z określonym typem. Możesz również pozwolić, aby kompilator wywnioskuje typ jednostki za pomocą C# słowa kluczowego `var` (Dim w Visual Basic).  
  
 W zapytaniu należy określić dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytanie może również określać, jak te informacje powinny być sortowane, grupowane i ukształtowane przed zwróceniem. W LINQ, zapytanie jest przechowywane w zmiennej. Jeśli zapytanie zwraca sekwencję wartości, zmienna zapytania musi być typem queryable. Ta zmienna zapytania nie przyjmuje żadnej akcji i nie zwraca żadnych danych. przechowuje on tylko informacje o zapytaniu. Po utworzeniu zapytania należy wykonać to zapytanie w celu pobrania danych.  
  
## <a name="query-syntax"></a>Składnia zapytania  
 Zapytania LINQ to Entities mogą składać się z dwóch różnych składni: składni wyrażeń zapytania i składni zapytania opartego na metodzie. Składnia wyrażenia zapytania jest nowością C# w 3,0 i Visual Basic 9,0 i składa się z zestawu klauzul pisanych w składni deklaracyjnej podobnej do Transact-SQL lub XQuery. Jednak .NET Framework środowiska uruchomieniowego języka wspólnego (CLR) nie może odczytać samej składni wyrażenia zapytania. W związku z tym w czasie kompilacji wyrażenia zapytania są tłumaczone na element, który jest rozpoznawany przez środowisko CLR: wywołania metody. Te metody są znane jako *standardowe operatory zapytań*. Deweloperem jest możliwość wywoływania ich bezpośrednio przy użyciu składni metody zamiast przy użyciu składni zapytania. Aby uzyskać więcej informacji, zobacz [składnia zapytań i składnia metod w LINQ](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Składnia wyrażenia zapytania  
 Wyrażenia zapytań są deklaratywną składnią zapytań. Ta składnia umożliwia deweloperowi Pisanie zapytań w języku wysokiego poziomu, który jest sformatowany podobnie do języka Transact-SQL. Używając składni wyrażeń zapytania, można wykonywać nawet złożone operacje filtrowania, porządkowania i grupowania dla źródeł danych o minimalnym kodzie. Aby uzyskać więcej informacji, [podstawowe operacje zapytań (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Przykłady, które pokazują, jak używać składni wyrażenia zapytania, można znaleźć w następujących tematach:  
  
- [Przykłady składni wyrażeń zapytania: Stając](query-expression-syntax-examples-projection.md)  
  
- [Przykłady składni wyrażeń zapytania: Identyfikatorów](query-expression-syntax-examples-filtering.md)  
  
- [Przykłady składni wyrażeń zapytania: Zamówienie](query-expression-syntax-examples-ordering.md)  
  
- [Przykłady składni wyrażeń zapytania: Operatory agregujące](query-expression-syntax-examples-aggregate-operators.md)  
  
- [Przykłady składni wyrażeń zapytania: Podziału](query-expression-syntax-examples-partitioning.md)  
  
- [Przykłady składni wyrażeń zapytania: Operatory sprzężenia](query-expression-syntax-examples-join-operators.md)  
  
- [Przykłady składni wyrażeń zapytania: Operatory elementu](query-expression-syntax-examples-element-operators.md)  
  
- [Przykłady składni wyrażeń zapytania: Grupie](query-expression-syntax-examples-grouping.md)  
  
- [Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Składnia zapytania oparta na metodzie  
 Innym sposobem tworzenia zapytań LINQ to Entities jest użycie zapytań opartych na metodzie. Składnia zapytania oparta na metodzie jest sekwencją wywołań metod bezpośrednich do metod operatora LINQ, przekazując wyrażenia lambda jako parametry. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Przykłady, które pokazują, jak używać składni opartej na metodzie, można znaleźć w następujących tematach:  
  
- [Przykłady składni zapytania oparte na metodzie: Stając](method-based-query-syntax-examples-projection.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Identyfikatorów](method-based-query-syntax-examples-filtering.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Zamówienie](method-based-query-syntax-examples-ordering.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Operatory agregujące](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Podziału](method-based-query-syntax-examples-partitioning.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Kursy](method-based-query-syntax-examples-conversion.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Operatory sprzężenia](method-based-query-syntax-examples-join-operators.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Operatory elementu](method-based-query-syntax-examples-element-operators.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Grupie](method-based-query-syntax-examples-grouping.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach](method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Entities](linq-to-entities.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Wprowadzenie ze składnikami LINQ w Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Entity Framework opcje scalania i skompilowane zapytania](https://go.microsoft.com/fwlink/?LinkId=199591)
