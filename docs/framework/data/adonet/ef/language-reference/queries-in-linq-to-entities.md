---
title: Zapytania w składniku LINQ to Entities
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 268906f8b79c8baf1ac6e29012b0ae7194b17084
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539414"
---
# <a name="queries-in-linq-to-entities"></a>Zapytania w składniku LINQ to Entities
Zapytanie jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są zwykle wyrażane w specjalistycznym języku zapytań, takich jak SQL dla relacyjnych baz danych i XQuery dla XML. W związku z tym deweloperzy musieli nauczyć się nowego języka zapytań dla każdego typu źródła danych lub formatu danych, które są zapytania. Language-Integrated Query (LINQ) oferuje prostszy i spójny model do pracy z danymi w różnych rodzajach formatów i źródeł danych. W zapytaniu LINQ zawsze pracujesz z programowania obiektów.  
  
 Operacji zapytania LINQ składa się z trzech akcji: uzyskać lub źródeł danych, Utwórz zapytanie i wykonać zapytanie.  
  
 Źródła danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> ogólny interfejs lub <xref:System.Linq.IQueryable%601> interfejs ogólny może być odpytywana za pomocą LINQ. Wystąpienia ogólnego <xref:System.Data.Objects.ObjectQuery%601> klasy, która implementuje ogólnego <xref:System.Linq.IQueryable%601> interfejsu, służyć jako źródło danych dla programu LINQ do zapytań jednostki. <xref:System.Data.Objects.ObjectQuery%601> Klasa ogólna reprezentuje zapytanie, które zwraca kolekcję zero lub więcej obiektów określonego typu. Można także pozwolić kompilatorowi wydedukować typ. jednostki za pomocą słowa kluczowego języka C# `var` (wymiar w języku Visual Basic).  
  
 W zapytaniu określasz dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytania można również określić, jak te informacje powinny można sortowane, grupowane i kształtowane przed zwróceniem. W programie LINQ zapytania są przechowywane w zmiennej. Jeśli zapytanie zwraca sekwencję liczb, sama zmienna zapytania musi być typem odpytywalnym. Ta zmienna zapytania nie podejmuje żadnych działań i nie zwraca żadnych danych; tylko przechowuje informacje o kwerendzie. Po utworzeniu zapytania należy wykonać to zapytanie, aby pobrać wszystkie dane.  
  
## <a name="query-syntax"></a>Składnia zapytań  
 LINQ do zapytań jednostki może składać się w dwóch różnych składni: składnia wyrażenia oraz składni zapytania oparte na metodzie zapytania. Składnia wyrażenia kwerendy jest nowego w języku C# 3.0 i Visual Basic 9.0 i składa się z zestawu klauzule napisane w składni deklaratywnej podobnego do języka Transact-SQL lub wyrażenie XQuery. Jednak .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) nie można odczytać składni wyrażeń zapytania, sam. W związku z tym, w czasie kompilacji wyrażeń zapytania są tłumaczone na coś, co środowisko CLR zrozumienie: wywołania metody. Metody te są znane jako *standardowych operatorów zapytań*. Jako deweloper istnieje możliwość wywołania je bezpośrednio przy użyciu składni metody zamiast przy użyciu składni zapytań. Aby uzyskać więcej informacji, zobacz [składnia zapytania a składnia metody w technologii LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Składnia wyrażenia zapytania  
 Wyrażenia kwerendy są deklaratywne składnię. Ta składnia umożliwia deweloperom Pisanie zapytań w języku wysokiego poziomu, który jest sformatowany podobna do instrukcji języka Transact-SQL. Za pomocą składni wyrażeń zapytania, możesz wykonać nawet złożone filtrowanie, porządkowanie i operacji grupowania na źródeł danych za pomocą minimalnej ilości kodu. Aby uzyskać więcej informacji [podstawowe operacje zapytań (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Aby uzyskać przykłady, które pokazują, jak używać składni wyrażeń zapytania zobacz następujące tematy:  
  
- [Przykłady składni wyrażeń zapytania: Projekcja](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
- [Przykłady składni wyrażeń zapytania: Filtrowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
- [Przykłady składni wyrażeń zapytania: Określanie kolejności](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
- [Przykłady składni wyrażeń zapytania: Operatory agregacji](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
- [Przykłady składni wyrażeń zapytania: Partycjonowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
- [Przykłady składni wyrażeń zapytania: Operatory sprzężenia](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
- [Przykłady składni wyrażeń zapytania: Operatory elementu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
- [Przykłady składni wyrażeń zapytania: Grupowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
- [Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Składni zapytania oparte na metodzie  
 Innym sposobem tworzenia LINQ do zapytań jednostki jest przy użyciu zapytań oparte na metodzie. Składnia zapytania oparte na metodzie to sekwencja wywołań metody bezpośredniej do metod operatorów LINQ, przekazując wyrażenia lambda jako parametry. Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Przykłady pokazujące, jak używać składni oparte na metodzie zobacz następujące tematy:  
  
- [Przykłady składni zapytania oparte na metodzie: Projekcja](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Filtrowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Określanie kolejności](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Operatory agregacji](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Partycjonowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Konwersja](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Operatory sprzężenia](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Operatory elementu](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Grupowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
- [Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Wprowadzenie do korzystania z LINQ w C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Wprowadzenie do LINQ w Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Opcje scalania w ramach jednostki i zapytania skompilowane](https://go.microsoft.com/fwlink/?LinkId=199591)
