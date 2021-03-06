---
title: 'Zapytanie zintegrowane języka (LINQ) w języku C #'
description: Wprowadza language Integrated Query (LINQ) w języku C#.
ms.date: 11/30/2016
ms.assetid: 007cc736-f5cf-4919-b99b-0c00ab2814ce
ms.openlocfilehash: fe408210b30b5f6118dc66b4c8f7057fb6654881
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399442"
---
# <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

Language-Integrated Query (LINQ) to nazwa zestawu technologii opartych na integracji funkcji zapytania bezpośrednio z językiem C#. Tradycyjnie zapytania dotyczące danych są wyrażane jako proste ciągi bez sprawdzania typu w czasie kompilacji lub obsługi IntelliSense. Ponadto musisz nauczyć się innego języka zapytań dla każdego typu źródła danych: baz danych SQL, dokumentów XML, różnych usług sieci Web i tak dalej. Z LINQ kwerendy jest konstrukcją języka pierwszej klasy, podobnie jak klasy, metody, zdarzenia.

Dla dewelopera, który pisze zapytania, najbardziej widoczne "język zintegrowany" część LINQ jest wyrażenie kwerendy. Wyrażenia kwerend y są zapisywane w *składni kwerendy*deklaratywnej . Za pomocą składni kwerendy można wykonywać operacje filtrowania, porządkowania i grupowania w źródłach danych przy użyciu minimalnego kodu. Te same wzorce wyrażeń zapytań podstawowych są używane do wykonywania zapytań i przekształcania danych w bazach danych SQL, zestawach danych ADO .NET, dokumentach i strumieniach XML oraz w kolekcjach .NET.

W poniższym przykładzie przedstawiono pełną operację kwerendy. Pełna operacja obejmuje tworzenie źródła danych, definiowanie wyrażenia kwerendy `foreach` i wykonywanie kwerendy w instrukcji.

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a>Omówienie wyrażeń kwerendy

- Wyrażeń kwerend można używać do wykonywania zapytań i przekształcania danych z dowolnego źródła danych z włączoną funkcją LINQ. Na przykład pojedyncza kwerenda może pobrać dane z bazy danych SQL i utworzyć strumień XML jako dane wyjściowe.

- Wyrażenia zapytań są łatwe do opanowania, ponieważ używają wielu znanych konstrukcji języka C#.

- Zmienne w wyrażeniu zapytania są silnie typowane, chociaż w wielu przypadkach nie trzeba podawać typu jawnie, ponieważ kompilator można go wywnioskować. Aby uzyskać więcej informacji, zobacz [Relacje typu w operacjach kwerend LINQ](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

- Kwerenda nie jest wykonywana, dopóki nie iterate nad `foreach` zmienną kwerendy, na przykład w instrukcji. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do zapytań LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

- W czasie kompilacji wyrażenia kwerendy są konwertowane na wywołania metody standardowego operatora kwerend zgodnie z regułami określonymi w specyfikacji Języka C#. Każda kwerenda, która może być wyrażona przy użyciu składni kwerendy, może być również wyrażona przy użyciu składni metody. Jednak w większości przypadków składnia zapytania jest bardziej czytelna i zwięzła. For more information, see [C# language specification](~/_csharplang/spec/expressions.md#query-expressions) and [Standard query operators overview](../programming-guide/concepts/linq/standard-query-operators-overview.md).

- Z reguły podczas pisania zapytań LINQ zaleca się, aby w miarę możliwości używać składni kwerendy i składni metody, gdy jest to konieczne. Nie ma różnicy semantyczne lub wydajność między dwiema różnymi formami. Wyrażenia kwerendy są często bardziej czytelne niż równoważne wyrażenia napisane w składni metody.

- Niektóre operacje kwerendy, takie jak <xref:System.Linq.Enumerable.Count%2A> lub <xref:System.Linq.Enumerable.Max%2A>, nie mają równoważnej klauzuli wyrażenia zapytania i dlatego muszą być wyrażone jako wywołanie metody. Składnia metody można łączyć ze składnią kwerendy na różne sposoby. Aby uzyskać więcej informacji, zobacz [Składnia kwerendy i składnia metody w pliku LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

- Wyrażenia kwerendy można skompilować do drzewa wyrażeń lub delegatów, w zależności od typu, do którego kwerenda jest stosowana. <xref:System.Collections.Generic.IEnumerable%601>zapytania są kompilowane do delegatów. <xref:System.Linq.IQueryable>i <xref:System.Linq.IQueryable%601> zapytania są kompilowane do drzewa wyrażeń. Aby uzyskać więcej informacji, zobacz [Drzewa wyrażeń](../expression-trees.md).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o LINQ, zacznij od zapoznania się z kilkoma podstawowymi pojęciami w [podstawach wyrażenia zapytania,](query-expression-basics.md)a następnie przeczytaj dokumentację technologii LINQ, która Cię interesuje:

- Dokumenty XML: [LINQ do XML](../programming-guide/concepts/linq/linq-to-xml-overview.md)

- ADO.NET ramach jednostki: [LINQ do jednostek](../../framework/data/adonet/ef/language-reference/linq-to-entities.md)

- Kolekcje.NET, pliki, ciągi i tak dalej: [LINQ do obiektów](../programming-guide/concepts/linq/linq-to-objects.md)

Aby uzyskać głębsze zrozumienie LINQ w ogóle, zobacz [LINQ w języku C#](linq-in-csharp.md).

Aby rozpocząć pracę z LINQ w języku C#, zobacz samouczek [Praca z LINQ](../tutorials/working-with-linq.md).
