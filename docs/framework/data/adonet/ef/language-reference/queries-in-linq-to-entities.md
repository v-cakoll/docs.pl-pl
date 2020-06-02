---
title: Zapytania w składniku LINQ to Entities
description: Dowiedz się, w jaki sposób LINQ oferuje prosty, spójny model służący do pracy z danymi w różnych rodzajach źródeł danych i formatach przy użyciu obiektów programistycznych.
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 048fd56fc687dd715292fb3bb09405130de09779
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286821"
---
# <a name="queries-in-linq-to-entities"></a>Zapytania w składniku LINQ to Entities
Zapytanie jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są zwykle wyrażane w wyspecjalizowanym języku zapytań, takim jak SQL dla relacyjnych baz danych i XQuery for XML. W związku z tym deweloperzy musieli poznać nowy język zapytań dla każdego typu źródła danych lub formatu danych, który wykonuje zapytanie. Program Query Integrated Language (LINQ) oferuje prostszy, spójny model służący do pracy z danymi w różnych rodzajach źródeł danych i formatach. W zapytaniu LINQ zawsze pracujesz z obiektami programowania.  
  
 Operacja zapytania LINQ składa się z trzech akcji: uzyskanie źródła danych lub źródeł, utworzenie zapytania i wykonanie zapytania.  
  
 Do źródeł danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> interfejs ogólny lub <xref:System.Linq.IQueryable%601> interfejs generyczny, można wykonywać zapytania za pomocą LINQ. Wystąpienia klasy generycznej <xref:System.Data.Objects.ObjectQuery%601> implementującej <xref:System.Linq.IQueryable%601> interfejs ogólny, służące jako źródło danych dla zapytań LINQ to Entities. <xref:System.Data.Objects.ObjectQuery%601>Klasa generyczna reprezentuje zapytanie, które zwraca kolekcję składającą się z zero lub więcej obiektów z określonym typem. Można również zezwolić kompilatorowi na wnioskowanie typu jednostki za pomocą słowa kluczowego C# `var` (Dim w Visual Basic).  
  
 W zapytaniu należy określić dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytanie może również określać, jak te informacje powinny być sortowane, grupowane i ukształtowane przed zwróceniem. W LINQ, zapytanie jest przechowywane w zmiennej. Jeśli zapytanie zwraca sekwencję wartości, zmienna zapytania musi być typem queryable. Ta zmienna zapytania nie przyjmuje żadnej akcji i nie zwraca żadnych danych. przechowuje on tylko informacje o zapytaniu. Po utworzeniu zapytania należy wykonać to zapytanie w celu pobrania danych.  
  
## <a name="query-syntax"></a>Składnia zapytania  
 Zapytania LINQ to Entities mogą składać się z dwóch różnych składni: składni wyrażeń zapytania i składni zapytania opartego na metodzie. Składnia wyrażenia zapytania jest nowością w języku C# 3,0 i Visual Basic 9,0 i składa się z zestawu klauzul pisanych w składni deklaracyjnej podobnej do Transact-SQL lub XQuery. Jednak .NET Framework środowiska uruchomieniowego języka wspólnego (CLR) nie może odczytać samej składni wyrażenia zapytania. W związku z tym w czasie kompilacji wyrażenia zapytania są tłumaczone na element, który jest rozpoznawany przez środowisko CLR: wywołania metody. Te metody są znane jako *standardowe operatory zapytań*. Deweloperem jest możliwość wywoływania ich bezpośrednio przy użyciu składni metody zamiast przy użyciu składni zapytania. Aby uzyskać więcej informacji, zobacz [składnia zapytań i składnia metod w LINQ](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Składnia wyrażenia zapytania  
 Wyrażenia zapytań są deklaratywną składnią zapytań. Ta składnia umożliwia deweloperowi Pisanie zapytań w języku wysokiego poziomu, który jest sformatowany podobnie do języka Transact-SQL. Używając składni wyrażeń zapytania, można wykonywać nawet złożone operacje filtrowania, porządkowania i grupowania dla źródeł danych o minimalnym kodzie. Aby uzyskać więcej informacji, [podstawowe operacje zapytań (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Przykłady, które pokazują, jak używać składni wyrażenia zapytania, można znaleźć w następujących tematach:  
  
- [Przykłady składni wyrażeń zapytania, projekcja](query-expression-syntax-examples-projection.md)  
  
- [Przykłady składni wyrażeń zapytania, filtrowanie](query-expression-syntax-examples-filtering.md)  
  
- [Przykłady składni wyrażeń zapytania, porządkowanie](query-expression-syntax-examples-ordering.md)  
  
- [Przykłady składni wyrażeń zapytania, operatory agregacji](query-expression-syntax-examples-aggregate-operators.md)  
  
- [Przykłady składni wyrażeń zapytania, partycjonowanie](query-expression-syntax-examples-partitioning.md)  
  
- [Przykłady składni wyrażeń zapytania, operatory sprzężenia](query-expression-syntax-examples-join-operators.md)  
  
- [Przykłady składni wyrażeń zapytania, operatory elementu](query-expression-syntax-examples-element-operators.md)  
  
- [Przykłady składni wyrażeń zapytania, grupowanie](query-expression-syntax-examples-grouping.md)  
  
- [Przykłady składni wyrażeń zapytania, nawigowanie po relacjach](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Składnia zapytania oparta na metodzie  
 Innym sposobem tworzenia zapytań LINQ to Entities jest użycie zapytań opartych na metodzie. Składnia zapytania oparta na metodzie jest sekwencją wywołań metod bezpośrednich do metod operatora LINQ, przekazując wyrażenia lambda jako parametry. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Przykłady, które pokazują, jak używać składni opartej na metodzie, można znaleźć w następujących tematach:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Entities](linq-to-entities.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Wprowadzenie do programu LINQ w Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Opcje scalania EF i skompilowane zapytania](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
