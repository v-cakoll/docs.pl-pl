---
title: Language-Integrated Query (LINQ) (C#)
description: Dowiedz się więcej o zapytaniach zintegrowanych z językiem (LINQ) i zapoznaj się z przykładem kompletnej operacji zapytania.
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: 6c8844c387177ce858b63a52b1f5c7246b570beb
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103423"
---
# <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

Language-Integrated Query (LINQ) to nazwa zestawu technologii w oparciu o integrację możliwości zapytań bezpośrednio w języku C#. Tradycyjnie zapytania dotyczące danych są wyrażane jako proste ciągi bez sprawdzania typu w czasie kompilacji lub obsłudze IntelliSense. Ponadto należy poznać inny język zapytań dla każdego typu źródła danych: bazy danych SQL, dokumenty XML, różne usługi sieci Web itd. W LINQ, zapytanie jest konstrukcja języka pierwszej klasy, podobnie jak klasy, metody, zdarzenia. Zapytania są pisane względem jednoznacznie wpisanych kolekcji obiektów przy użyciu słów kluczowych języka i znanych operatorów. Rodzina LINQ technologii zapewnia spójne środowisko zapytań dla obiektów (LINQ to Objects), relacyjnych baz danych (LINQ to SQL) i XML (LINQ to XML).

W przypadku deweloperów, którzy zapisują zapytania, najbardziej widoczna część "ze zintegrowanym językiem" w LINQ jest wyrażeniem zapytania. Wyrażenia zapytań są zapisywane w postaci deklaracyjnej *składni zapytań*. Za pomocą składni zapytania, można wykonywać operacje filtrowania, porządkowania i grupowania w źródłach danych z minimalnym kodem. Te same podstawowe wzorce wyrażeń zapytania służą do wykonywania zapytań i przekształcania danych w bazach danych SQL, ADO.NET, dokumentów XML i strumieni i kolekcji programu .NET.

Można napisać zapytania LINQ w języku C# dla SQL Server baz danych, dokumentów XML, zestawów danych ADO.NET oraz dowolnej kolekcji obiektów, które obsługują <xref:System.Collections.IEnumerable> lub interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601> . Wsparcie LINQ jest również udostępniane przez inne firmy dla wielu usług sieci Web i innych implementacji baz danych.

W poniższym przykładzie pokazano kompletną operację zapytania. Operacja Complete obejmuje tworzenie źródła danych, Definiowanie wyrażenia zapytania i wykonywanie zapytania w `foreach` instrukcji.

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

Poniższa ilustracja z programu Visual Studio pokazuje częściowo ukończone zapytanie LINQ względem bazy danych SQL Server w języku C# i Visual Basic za pomocą sprawdzania pełnego typu i obsługi technologii IntelliSense:

![Diagram przedstawiający zapytanie LINQ z technologią IntelliSense.](./media/introduction-to-linq/linq-query-intellisense.png)

## <a name="query-expression-overview"></a>Omówienie wyrażenia zapytania

- Wyrażenia zapytań mogą służyć do wykonywania zapytań i przekształcania danych z dowolnego źródła danych z obsługą LINQ. Na przykład pojedyncze zapytanie może pobierać dane z bazy danych SQL i generować strumień XML jako dane wyjściowe.
- Wyrażenia zapytań są łatwe w wzorcu, ponieważ korzystają z wielu znanych konstrukcji języka C#.
- Zmienne w wyrażeniu zapytania są wszystkie silnie wpisywane, chociaż w wielu przypadkach nie trzeba podawać typu jawnie, ponieważ kompilator może wywnioskować go. Aby uzyskać więcej informacji, zobacz temat [relacje typu w operacjach zapytań LINQ](type-relationships-in-linq-query-operations.md).
- Zapytanie nie jest wykonywane, dopóki nie zostanie wykonana iteracja zmiennej zapytania, na przykład w `foreach` instrukcji. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ](introduction-to-linq-queries.md).
- W czasie kompilacji wyrażenia zapytania są konwertowane na wywołania metody standardowego operatora zapytań zgodnie z regułami określonymi w specyfikacji języka C#. Wszystkie zapytania, które mogą być wyrażone za pomocą składni zapytania, można również wyrazić przy użyciu składni metody. Jednak w większości przypadków Składnia zapytania jest bardziej czytelna i zwięzła. Aby uzyskać więcej informacji, zobacz temat [Specyfikacja języka C#](~/_csharplang/spec/expressions.md#query-expressions) i [standardowe operatory zapytań — Omówienie](standard-query-operators-overview.md).
- Jako zasada podczas pisania zapytań LINQ zaleca się używanie składni zapytań wszędzie tam, gdzie to możliwe, oraz składni metod, gdy jest to konieczne. Między dwoma różnymi formularzami nie ma semantyki ani różnicy wydajności. Wyrażenia zapytań są często bardziej czytelne niż równoważne wyrażenia wpisywane w składni metody.
- Niektóre operacje zapytań, takie jak <xref:System.Linq.Enumerable.Count%2A> lub <xref:System.Linq.Enumerable.Max%2A> , nie mają równoważnej klauzuli wyrażenia zapytania i dlatego muszą być wyrażone jako wywołanie metody. Składnię metody można łączyć z składnią zapytania na różne sposoby. Aby uzyskać więcej informacji, zobacz [składnia zapytań i składnia metod w LINQ](query-syntax-and-method-syntax-in-linq.md).
- Wyrażenia zapytań można kompilować do drzew wyrażeń lub delegatów, w zależności od typu, do którego zastosowano zapytanie. <xref:System.Collections.Generic.IEnumerable%601>zapytania są kompilowane do delegatów. <xref:System.Linq.IQueryable><xref:System.Linq.IQueryable%601>zapytania są kompilowane w drzewach wyrażeń. Aby uzyskać więcej informacji, zobacz [drzewa wyrażeń](../../../expression-trees.md).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat LINQ, Zacznij od zapoznania się z niektórymi podstawowymi pojęciami dotyczącymi [wyrażeń zapytania](../../../linq/query-expression-basics.md), a następnie zapoznaj się z dokumentacją technologii LINQ, w której Cię interesują.

- Dokumenty XML: [LINQ to XML](linq-to-xml-overview.md)  
- ADO.NET Entity Framework: [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)
- Kolekcje, pliki, ciągi i tak dalej platformy .NET: [LINQ to Objects](linq-to-objects.md)

Aby uzyskać bardziej szczegółowe informacje na temat LINQ, zobacz [LINQ w C#](../../../linq/linq-in-csharp.md).

Aby rozpocząć pracę z LINQ w języku C#, zapoznaj się z samouczkiem [dotyczącym pracy z LINQ](../../../tutorials/working-with-linq.md).
