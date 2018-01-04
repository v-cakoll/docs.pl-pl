---
title: "Zapytania w składniku LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6fe20fd26b78bde19ed73e2415b1b5c283a0d1f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="queries-in-linq-to-entities"></a>Zapytania w składniku LINQ to Entities
Zapytanie jest wyrażenie, które pobiera dane ze źródła danych. Zapytania są zwykle zapisywane w język kwerendy specjalnych, takich jak SQL relacyjnych baz danych i XQuery dla formatu XML. W związku z tym deweloperzy było nauczyć się nowy język kwerendy dla każdego typu źródła danych lub format danych są zapytania. Zapytanie języku zintegrowanym (LINQ) oferuje prostszy, spójny model do pracy z danymi w różnych rodzajów źródeł danych i formaty. Zapytania LINQ zawsze do pracy z programowania obiektów.  
  
 Operacji zapytania LINQ składa się z trzech akcji: uzyskać źródła danych lub źródła, Utwórz zapytanie i wykonać zapytanie.  
  
 Źródła danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> ogólny interfejs lub <xref:System.Linq.IQueryable%601> ogólny interfejs można tworzyć zapytania za pomocą LINQ. Wystąpienia ogólnych <xref:System.Data.Objects.ObjectQuery%601> klasy, która implementuje ogólnego <xref:System.Linq.IQueryable%601> interfejsu, służyć jako źródło danych dla [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. <xref:System.Data.Objects.ObjectQuery%601> Klasa ogólna reprezentuje kwerendę, która zwraca kolekcję zero lub więcej obiektów określonego typu. Można także pozwolić kompilatora wnioskować o typie jednostki przy użyciu słowa kluczowego języka C# `var` (Dim w języku Visual Basic).  
  
 W zapytaniu możesz określić dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytania można również określić, jak te informacje sortowania, grupowane i w kształcie przed zwróceniem jest. W składniku LINQ zapytanie jest przechowywana w zmiennej. Jeśli zapytanie zwraca sekwencję wartości, samej zmiennej zapytania musi być typem zapytań. Ta zmienna zapytania Brak działania i zwraca żadnych danych; tylko przechowuje informacje o kwerendzie. Po utworzeniu zapytania należy wykonać zapytania można pobrać żadnych danych.  
  
## <a name="query-syntax"></a>Składnia zapytania  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]zapytania mogą być składane w dwóch składnie: wyrażenie składnia zapytania i metody zapytań. Składnia wyrażeń jest nowego w języku C# 3.0 i 9.0 Visual Basic i składa się z zestawu klauzule napisany w składni deklaratywnej podobny do języka Transact-SQL lub XQuery. Jednak [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] środowisko uruchomieniowe języka wspólnego (CLR) nie może odczytać sam składnia wyrażenia zapytania. W związku z tym podczas kompilacji wyrażenia zapytania są translacji obsługiwanym przez środowisko CLR: wywołania metody. Te metody są określane jako *standardowych operatorów zapytań*. Deweloper istnieje możliwość wywołania je bezpośrednio, używając składni metody zamiast za pomocą składni zapytań. Aby uzyskać więcej informacji, zobacz [składnia zapytania a składnia metody w technologii LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Składnia wyrażenia zapytania  
 Wyrażenia zapytania są deklaratywne składnię. Ta składnia umożliwia deweloperom Pisanie zapytań w języku wysokiego poziomu, który jest sformatowany podobny do języka Transact-SQL. Przy użyciu składni wyrażeń zapytania, można wykonywać nawet złożone filtrowanie, kolejność i operacji grupowania na źródeł danych z minimalnym kodu. Aby uzyskać więcej informacji [podstawowe operacje zapytań (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Aby uzyskać przykłady pokazujące, które pokazują, jak używać składni wyrażenia zapytania zobacz następujące tematy:  
  
-   [Przykłady składni wyrażeń zapytania, projekcja](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [Przykłady składni wyrażeń zapytania, filtrowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [Przykłady składni wyrażeń zapytania, porządkowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [Przykłady składni wyrażeń zapytania, operatory agregacji](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [Przykłady składni wyrażeń zapytania, partycjonowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [Przykłady składni wyrażeń zapytania, operatory sprzężenia](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [Przykłady składni wyrażeń zapytania, operatory elementu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [Przykłady składni wyrażeń zapytania, grupowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [Przykłady składni wyrażeń zapytania, nawigowanie po relacjach](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Składnia zapytań — metoda  
 Innym sposobem tworzenia [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania jest za pomocą zapytań na podstawie metody. Składnia zapytania oparte na metodzie jest sekwencją metoda bezpośrednia wywołania metod operator LINQ, przekazując wyrażenia lambda jako parametry. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Aby uzyskać przykłady pokazujące, które pokazują, jak używać składni oparte na metodzie zobacz następujące tematy:  
  
-   [Przykłady składni zapytania oparte na metodzie, projekcja](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [Przykłady składni zapytania oparte na metodzie, filtrowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [Przykłady składni zapytania oparte na metodzie, porządkowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [Przykłady składni zapytania oparte na metodzie, operatory agregacji](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [Przykłady składni zapytania oparte na metodzie, partycjonowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [Przykłady składni zapytania oparte na metodzie, konwersja](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [Przykłady składni zapytania oparte na metodzie, operatory sprzężenia](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [Przykłady składni zapytania oparte na metodzie, operatory elementu](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [Przykłady składni zapytania oparte na metodzie, grupowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [Przykłady składni zapytania oparte na metodzie, nawigowanie po relacjach](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [Wprowadzenie do korzystania z LINQ w C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Wprowadzenie do korzystania z LINQ w Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Opcje scalania Entity Framework i skompilowane zapytania](http://go.microsoft.com/fwlink/?LinkId=199591)
