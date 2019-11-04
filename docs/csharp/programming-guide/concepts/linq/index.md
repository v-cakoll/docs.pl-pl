---
title: Zapytanie zintegrowane z językiem (LINQ)C#()
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: 07a9d68c042d524ee9faba8122b406a81e816378
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418238"
---
# <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

Language-Integrated Query (LINQ) to nazwa zestawu technologii w oparciu o integrację możliwości zapytań bezpośrednio w C# języku. Tradycyjnie zapytania dotyczące danych są wyrażane jako proste ciągi bez sprawdzania typu w czasie kompilacji lub obsłudze IntelliSense. Ponadto należy poznać inny język zapytań dla każdego typu źródła danych: bazy danych SQL, dokumenty XML, różne usługi sieci Web itd. W LINQ, zapytanie jest konstrukcja języka pierwszej klasy, podobnie jak klasy, metody, zdarzenia. Zapytania są pisane względem jednoznacznie wpisanych kolekcji obiektów przy użyciu słów kluczowych języka i znanych operatorów. Rodzina LINQ technologii zapewnia spójne środowisko zapytań dla obiektów (LINQ to Objects), relacyjnych baz danych (LINQ to SQL) i XML (LINQ to XML).

W przypadku deweloperów, którzy zapisują zapytania, najbardziej widoczna część "ze zintegrowanym językiem" w LINQ jest wyrażeniem zapytania. Wyrażenia zapytań są zapisywane w postaci deklaracyjnej *składni zapytań*. Za pomocą składni zapytania, można wykonywać operacje filtrowania, porządkowania i grupowania w źródłach danych z minimalnym kodem. Za pomocą tych samych podstawowych wzorców wyrażeń zapytania można wykonywać zapytania i przekształcać dane w bazach danych SQL, zestawach danych ADO .NET, dokumentach XML i strumieniach i kolekcjach platformy .NET.

Można napisać zapytania LINQ w programie C# dla SQL Server baz danych, dokumentów XML, zestawów danych ADO.NET i dowolnej kolekcji obiektów, które obsługują <xref:System.Collections.IEnumerable> lub ogólny interfejs <xref:System.Collections.Generic.IEnumerable%601>. Wsparcie LINQ jest również udostępniane przez inne firmy dla wielu usług sieci Web i innych implementacji baz danych.

W poniższym przykładzie pokazano kompletną operację zapytania. Operacja Complete obejmuje tworzenie źródła danych, Definiowanie wyrażenia zapytania i wykonywanie zapytania w instrukcji `foreach`.

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

Poniższa ilustracja z programu Visual Studio pokazuje częściowo ukończone zapytanie LINQ względem bazy danych SQL Server w obu C# i Visual Basic z funkcją sprawdzania pełnego typu i obsługą IntelliSense:

![Diagram przedstawiający zapytanie LINQ z technologią IntelliSense.](./media/introduction-to-linq/linq-query-intellisense.png)

## <a name="query-expression-overview"></a>Omówienie wyrażenia zapytania

- Wyrażenia zapytań mogą służyć do wykonywania zapytań i przekształcania danych z dowolnego źródła danych z obsługą LINQ. Na przykład pojedyncze zapytanie może pobierać dane z bazy danych SQL i generować strumień XML jako dane wyjściowe.
- Wyrażenia zapytań są łatwe w wzorcu, ponieważ korzystają z C# wielu znanych konstrukcji językowych.
- Zmienne w wyrażeniu zapytania są wszystkie silnie wpisywane, chociaż w wielu przypadkach nie trzeba podawać typu jawnie, ponieważ kompilator może wywnioskować go. Aby uzyskać więcej informacji, zobacz temat [relacje typu w operacjach zapytań LINQ](type-relationships-in-linq-query-operations.md).
- Zapytanie nie jest wykonywane, dopóki nie zostanie wykonana iteracja zmiennej zapytania, na przykład w instrukcji `foreach`. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ](introduction-to-linq-queries.md).
- W czasie kompilacji wyrażenia zapytania są konwertowane na wywołania metody standardowego operatora zapytań zgodnie z regułami określonymi w C# specyfikacji. Wszystkie zapytania, które mogą być wyrażone za pomocą składni zapytania, można również wyrazić przy użyciu składni metody. Jednak w większości przypadków Składnia zapytania jest bardziej czytelna i zwięzła. Aby uzyskać więcej informacji, zobacz temat [ C# Specyfikacja języka](~/_csharplang/spec/expressions.md#query-expressions) i [standardowe operatory zapytań — Omówienie](standard-query-operators-overview.md).
- Jako zasada podczas pisania zapytań LINQ zaleca się używanie składni zapytań wszędzie tam, gdzie to możliwe, oraz składni metod, gdy jest to konieczne. Między dwoma różnymi formularzami nie ma semantyki ani różnicy wydajności. Wyrażenia zapytań są często bardziej czytelne niż równoważne wyrażenia wpisywane w składni metody.
- Niektóre operacje zapytań, takie jak <xref:System.Linq.Enumerable.Count%2A> lub <xref:System.Linq.Enumerable.Max%2A>, nie mają równoważnej klauzuli wyrażenia zapytania i dlatego muszą być wyrażone jako wywołanie metody. Składnię metody można łączyć z składnią zapytania na różne sposoby. Aby uzyskać więcej informacji, zobacz [składnia zapytań i składnia metod w LINQ](query-syntax-and-method-syntax-in-linq.md).
- Wyrażenia zapytań można kompilować do drzew wyrażeń lub delegatów, w zależności od typu, do którego zastosowano zapytanie. zapytania <xref:System.Collections.Generic.IEnumerable%601> są kompilowane do delegatów. zapytania <xref:System.Linq.IQueryable> i <xref:System.Linq.IQueryable%601> są kompilowane do drzew wyrażeń. Aby uzyskać więcej informacji, zobacz [drzewa wyrażeń](../../../expression-trees.md).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat LINQ, Zacznij od zapoznania się z niektórymi podstawowymi pojęciami dotyczącymi [wyrażeń zapytania](../../../linq/query-expression-basics.md), a następnie zapoznaj się z dokumentacją technologii LINQ, w której Cię interesują.

- Dokumenty XML: [LINQ to XML](linq-to-xml-overview.md)  
- ADO.NET Entity Framework: [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)
- Kolekcje, pliki, ciągi i tak dalej platformy .NET: [LINQ to Objects](linq-to-objects.md)

Aby uzyskać bardziej szczegółowe informacje na temat LINQ, zobacz [LINQ in C# ](../../../linq/linq-in-csharp.md).

Aby rozpocząć pracę z LINQ w C#programie, zapoznaj się z samouczkiem [dotyczącym pracy z LINQ](../../../tutorials/working-with-linq.md).
