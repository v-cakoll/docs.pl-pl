---
title: Zapytanie zintegrowane z językiem (LINQ) (C#)
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: a2e53d6c7f4d24fd57b1f91c1428b8341386b6f9
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463895"
---
# <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

Zapytanie zintegrowane z językiem (LINQ) to nazwa zestawu technologii opartych na integracji możliwości zapytań bezpośrednio z językiem C#. Tradycyjnie zapytania dotyczące danych są wyrażane jako proste ciągi bez sprawdzania typu w czasie kompilacji lub obsługi IntelliSense. Ponadto należy nauczyć się innego języka zapytań dla każdego typu źródła danych: bazy danych SQL, dokumenty XML, różne usługi sieci Web i tak dalej. Z LINQ kwerendy jest najwyższej klasy konstrukcji języka, podobnie jak klasy, metody, zdarzenia. Piszesz zapytania względem silnie typizowane kolekcje obiektów przy użyciu słów kluczowych języka i znanych operatorów. Rodzina technologii LINQ zapewnia spójne środowisko zapytań dla obiektów (LINQ do obiektów), relacyjnych baz danych (LINQ do SQL) i XML (LINQ do XML).

Dla dewelopera, który pisze zapytania, najbardziej widoczne "język zintegrowane" część LINQ jest wyrażenie kwerendy. Wyrażenia kwerendy są zapisywane w *składni kwerendy*deklaratywnej . Za pomocą składni kwerendy, można wykonać filtrowanie, zamawianie i grupowanie operacji na źródłach danych z minimum kodu. Te same wzorce wyrażeń zapytań podstawowych są używane do wykonywania zapytań i przekształcania danych w bazach danych SQL, ADO.NET zestawów danych, dokumentach i strumieniach XML oraz kolekcjach .NET.

Można pisać zapytania LINQ w języku C# dla baz danych programu SQL Server, dokumentów XML, <xref:System.Collections.IEnumerable> ADO.NET zestawy <xref:System.Collections.Generic.IEnumerable%601> danych i dowolnej kolekcji obiektów, które obsługuje lub ogólnego interfejsu. Obsługa LINQ jest również świadczona przez strony trzecie dla wielu usług sieci Web i innych implementacji bazy danych.

W poniższym przykładzie przedstawiono pełną operację kwerendy. Pełna operacja obejmuje tworzenie źródła danych, definiowanie wyrażenia kwerendy i `foreach` wykonywanie kwerendy w instrukcji.

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

Na poniższej ilustracji z programu Visual Studio przedstawiono częściowo ukończone zapytanie LINQ względem bazy danych programu SQL Server w języku C# i Visual Basic z pełnym sprawdzaniem typu i obsługą intellisense:

![Diagram, który pokazuje kwerendę LINQ z Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)

## <a name="query-expression-overview"></a>Omówienie wyrażenia kwerendy

- Wyrażenia kwerendy mogą służyć do wykonywania zapytań i przekształcania danych z dowolnego źródła danych z włączoną funkcją LINQ. Na przykład pojedyncza kwerenda może pobierać dane z bazy danych SQL i tworzyć strumień XML jako dane wyjściowe.
- Wyrażenia kwerendy są łatwe do opanowania, ponieważ używają wielu znanych konstrukcji języka Języka C#.
- Zmienne w wyrażeniu kwerendy są silnie wpisane, chociaż w wielu przypadkach nie trzeba jawnie podać typ, ponieważ kompilator można wywnioskować. Aby uzyskać więcej informacji, zobacz [Typ relacji w operacjach kwerend LINQ](type-relationships-in-linq-query-operations.md).
- Kwerenda nie jest wykonywana, dopóki nie będzie iterować `foreach` nad zmienną kwerendy, na przykład w instrukcji. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do zapytań LINQ](introduction-to-linq-queries.md).
- W czasie kompilacji wyrażenia kwerendy są konwertowane na wywołania metody standardowego operatora kwerend zgodnie z regułami określonymi w specyfikacji języka C#. Każda kwerenda, która może być wyrażona przy użyciu składni kwerendy, może być również wyrażona przy użyciu składni metody. Jednak w większości przypadków składnia kwerendy jest bardziej czytelna i zwięzła. For more information, see [C# language specification](~/_csharplang/spec/expressions.md#query-expressions) and [Standard query operators overview](standard-query-operators-overview.md).
- Z reguły podczas pisania zapytań LINQ zaleca się użycie składni kwerendy, gdy tylko jest to możliwe, a składnia metody w razie potrzeby. Nie ma różnicy semantyczne lub wydajności między dwoma różnymi formami. Wyrażenia kwerendy są często bardziej czytelne niż wyrażenia równoważne napisane w składni metody.
- Niektóre operacje kwerendy, takie jak <xref:System.Linq.Enumerable.Count%2A> lub <xref:System.Linq.Enumerable.Max%2A>, nie mają równoważnej klauzuli wyrażenia zapytania i dlatego muszą być wyrażone jako wywołanie metody. Składni metody można łączyć ze składnią kwerendy na różne sposoby. Aby uzyskać więcej informacji, zobacz [Składnia kwerendy i składnia metody w LINQ](query-syntax-and-method-syntax-in-linq.md).
- Wyrażenia kwerendy mogą być kompilowane do drzew wyrażeń lub delegatów, w zależności od typu, do jakiej kwerenda jest stosowana. <xref:System.Collections.Generic.IEnumerable%601>zapytania są kompilowane do delegatów. <xref:System.Linq.IQueryable>i <xref:System.Linq.IQueryable%601> zapytania są kompilowane do drzew wyrażeń. Aby uzyskać więcej informacji, zobacz [Drzewa wyrażeń](../../../expression-trees.md).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej szczegółów na temat LINQ, zacznij od zapoznania się z kilkoma podstawowymi pojęciami w [podstawach wyrażenia kwerendy,](../../../linq/query-expression-basics.md)a następnie przeczytaj dokumentację technologii LINQ, w której jesteś zainteresowany:

- Dokumenty XML: [LINQ do XML](linq-to-xml-overview.md)  
- ADO.NET entity Framework: [LINQ do jednostek](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)
- .NET kolekcje, pliki, ciągi i tak dalej: [LINQ do obiektów](linq-to-objects.md)

Aby uzyskać głębsze zrozumienie LINQ w ogóle, zobacz [LINQ w języku C#](../../../linq/linq-in-csharp.md).

Aby rozpocząć pracę z LINQ w języku C#, zobacz samouczek [Praca z LINQ](../../../tutorials/working-with-linq.md).
