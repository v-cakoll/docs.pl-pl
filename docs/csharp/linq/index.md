---
title: Zapytanie o języku zintegrowanym (LINQ) w języku C#
description: Wprowadza Language Integrated Query (LINQ) w języku C#.
ms.date: 11/30/2016
ms.assetid: 007cc736-f5cf-4919-b99b-0c00ab2814ce
ms.openlocfilehash: 18dafaf590697a3c9d669f346c956fd4df3378f0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197391"
---
# <a name="language-integrated-query-linq"></a>Zapytanie o języku zintegrowanym (LINQ)

Language-Integrated Query (LINQ) to nazwa zestawu technologii, w oparciu o integrację możliwości zapytania bezpośrednio w języku C#. Tradycyjne zapytania dotyczące danych są wyrażane jako zwykłe ciągi bez typu sprawdzania w kompilacji czasu lub obsługę funkcji IntelliSense. Ponadto, trzeba się język różnych zapytań dla każdego typu źródła danych: SQL bazy danych, dokumentów XML, różnych usług sieci Web i tak dalej. Za pomocą LINQ kwerenda jest staje się konstrukcją języka, podobnie jak klasy, metody i zdarzenia.

Deweloper, który zapisuje zapytania, aby uzyskać najbardziej widoczne części "language-integrated" LINQ jest wyrażenia zapytania. Wyrażenia zapytań są zapisywane w deklaratywne *składni zapytania*. Za pomocą składni zapytań, można wykonać filtrowanie, porządkowanie i operacje do źródeł danych z co najmniej kodu. Używasz tych samych wzorców wyrażeń zapytania podstawowego do wykonywania zapytań i przekształcania danych w bazy danych SQL, ADO .NET w zestawach danych, strumienie i dokumentów XML i kolekcjami .NET.

Poniższy przykład przedstawia pełną operację zapytania. Zakończyć operację obejmuje tworzenie źródła danych, definiując wyrażenie zapytania i wykonywania zapytania w `foreach` instrukcji.

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a>Omówienie zapytań w wyrażeniu

- Wyrażenia zapytań może służyć do wykonywania zapytań i przekształcania danych z dowolnego źródła danych z obsługą zapytań LINQ. Na przykład jednego zapytania można pobierać dane z bazy danych SQL i generuje strumień XML jako dane wyjściowe.

- Wyrażenia zapytań są łatwe do gałęzi głównej, ponieważ używają one wiele dobrze znanych konstrukcji języka C#.

- Zmienne w wyrażeniu zapytania są wszystkie silnie typizowane, chociaż w wielu przypadkach nie trzeba jawnie udostępniają typ, ponieważ kompilator może wywnioskować go. Aby uzyskać więcej informacji, zobacz [relacje typów w składniku LINQ zapytania operacje](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

- Zapytanie nie jest wykonywana do czasu iteracji nad zmienną kwerendy, na przykład w `foreach` instrukcji. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

- W czasie kompilacji wyrażeń zapytania są konwertowane na wywołania metody standardowej kwerendy operatora zgodnie z regułami określonymi w specyfikacji języka C#. Każde zapytanie, które mogą być wyrażone za pomocą składni zapytania można również wyrazić za pomocą składni metody. Jednak w większości przypadków Składnia kwerendy jest bardziej czytelne i zwięzłe. Aby uzyskać więcej informacji, zobacz [specyfikacji języka C#](~/_csharplang/spec/expressions.md#query-expressions) i [omówienie operatorów standardowej kwerendy](../programming-guide/concepts/linq/standard-query-operators-overview.md).

- Zgodnie z zasadą podczas pisania zapytań LINQ, firma Microsoft zaleca użycie składni zapytań, jeśli to możliwe, a składnia metody, jeśli zajdzie taka potrzeba. Brak nie semantycznego lub wydajność różnica między dwoma formami różne. Wyrażenia zapytań są często bardziej czytelne niż równoważne wyrażenia napisane przy użyciu składni metody.

- Zapytanie niektóre operacje, takie jak <xref:System.Linq.Enumerable.Count%2A> lub <xref:System.Linq.Enumerable.Max%2A>, mieć żadnej klauzuli wyrażenia kwerendy równoważne i dlatego musi być wyrażona jako wywołania metody. Składnia metody można łączyć za pomocą składni zapytań na różne sposoby. Aby uzyskać więcej informacji, zobacz [składnia zapytania i metody w technologii LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

- Wyrażenia zapytań może być kompilowane, drzew wyrażeń lub delegatów, w zależności od typu, który dotyczy zapytanie. <xref:System.Collections.Generic.IEnumerable%601> zapytania są kompilowane do delegatów. <xref:System.Linq.IQueryable> i <xref:System.Linq.IQueryable%601> kwerendy są kompilowane w drzewach wyrażeń. Aby uzyskać więcej informacji, zobacz [drzew wyrażeń](../expression-trees.md).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat LINQ, należy rozpocząć od staje się poznać niektóre podstawowe pojęcia związane z [podstawowe informacje o wyrażeniach zapytań](query-expression-basics.md), a następnie zapoznaj się z dokumentacją dla technologii LINQ, w którym interesuje Cię:

- Dokumenty XML: [LINQ to XML](../programming-guide/concepts/linq/linq-to-xml.md)

- ADO.NET Entity Framework: [składnik LINQ to entities](../../framework/data/adonet/ef/language-reference/linq-to-entities.md)

- Kolekcje .NET, pliki, ciągi i tak dalej: [LINQ do obiektów](../programming-guide/concepts/linq/linq-to-objects.md)

Aby uzyskać lepszy opis LINQ ogólnie rzecz biorąc, zobacz [LINQ w C#](linq-in-csharp.md).

Aby rozpocząć pracę z LINQ w C#, zapoznaj się z samouczkiem [Praca z technologią LINQ](../tutorials/working-with-linq.md).