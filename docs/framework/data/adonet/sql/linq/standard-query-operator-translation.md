---
title: Translacja standardowego operatora zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: af22b6a895fef8037eb5c069ffb7cb23d1333531
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833681"
---
# <a name="standard-query-operator-translation"></a>Translacja standardowego operatora zapytania

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy standardowe operatory zapytań na polecenia SQL. Procesor zapytań bazy danych określa semantykę wykonywania translacji SQL.

Standardowe operatory zapytań są zdefiniowane dla *sekwencji*. Sekwencja jest *uporządkowana* i opiera się na tożsamości odwołania dla każdego elementu sekwencji. Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań —C#omówienie ()](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) lub [standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

Program SQL zajmuje się głównie *nieuporządkowanymi zestawami wartości*. Kolejność jest zwykle jawnie określona, operacja po przetworzeniu, która jest stosowana do końcowego wyniku zapytania, a nie do wyników pośrednich. Tożsamość jest definiowana przez wartości. Z tego powodu zapytania SQL są zrozumiałe do postępowania z wielozestawami *(* zbiorami), a nie *zestawami*.

W poniższych akapitach opisano różnice między standardowymi operatorami zapytań i ich tłumaczenia SQL dla dostawcy SQL Server dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].

## <a name="operator-support"></a>Obsługa operatorów

### <a name="concat"></a>Concat

Metoda <xref:System.Linq.Enumerable.Concat%2A> jest definiowana dla uporządkowanych zestawów wielozbiorów, w których kolejność odbiornika i kolejność argumentu są takie same. <xref:System.Linq.Enumerable.Concat%2A> działa jako `UNION ALL` w przypadku zestawów wielozbiorów, po których następuje typowa kolejność.

Ostatnim krokiem jest porządkowanie w języku SQL, zanim zostaną wygenerowane wyniki. <xref:System.Linq.Enumerable.Concat%2A> nie zachowuje kolejności argumentów. Aby zapewnić odpowiednią kolejność, należy jawnie zastanowić się nad wynikami <xref:System.Linq.Enumerable.Concat%2A>.

### <a name="intersect-except-union"></a>Intersect, EXCEPT, Union

Metody <xref:System.Linq.Enumerable.Intersect%2A> i <xref:System.Linq.Enumerable.Except%2A> są dobrze zdefiniowane tylko w zestawach. Semantyka dla wielozestawów jest niezdefiniowana.

Metoda <xref:System.Linq.Enumerable.Union%2A> jest definiowana dla wielozbiorów jako nieuporządkowane łączenie wielozestawów (w efekcie w wyniku klauzuli UNION ALL w języku SQL).

### <a name="take-skip"></a>Zrób, Pomiń

Metody <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> są dobrze zdefiniowane tylko w odniesieniu do *uporządkowanych zestawów*. Semantyka nieuporządkowanych zestawów lub zestawów wielozbiorówowych nie jest zdefiniowana.

> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są używane w zapytaniach do SQL Server 2000. Aby uzyskać więcej informacji, zobacz wpis "Pomiń i przejmowanie wyjątków w SQL Server 2000" w [temacie Rozwiązywanie problemów](troubleshooting.md).

Ze względu na ograniczenia dotyczące porządkowania w programie SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbuje przenieść kolejność argumentów tych metod do wyniku metody. Rozważmy na przykład następujące [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania:

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

Wygenerowane SQL dla tego kodu przenosi kolejność do końca w następujący sposób:

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

Jest oczywiste, że wszystkie określone porządkowanie musi być spójne, gdy <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> są połączone łańcuchowo. W przeciwnym razie wyniki są niezdefiniowane.

Zarówno <xref:System.Linq.Enumerable.Take%2A>, jak i <xref:System.Linq.Enumerable.Skip%2A> są dobrze zdefiniowane dla nieujemnych, stałych argumentów całkowitych opartych na standardowej specyfikacji operatora zapytań.

### <a name="operators-with-no-translation"></a>Operatory bez tłumaczenia

Następujące metody nie są tłumaczone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Najbardziej typową przyczyną jest różnica między nieuporządkowanymi zestawami i sekwencjami.

|Operatory|Ich uzasadnienie|
|---------------|---------------|
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|Zapytania SQL działają na wielozestawach, a nie na sekwencjach. `ORDER BY` musi być ostatnią klauzulą zastosowana do wyników. Z tego powodu nie istnieje tłumaczenie ogólnego przeznaczenia dla tych dwóch metod.|
|<xref:System.Linq.Enumerable.Reverse%2A>|Tłumaczenie tej metody jest możliwe dla uporządkowanego zestawu, ale nie jest obecnie przetłumaczone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Tłumaczenie tych metod jest możliwe dla uporządkowanego zestawu, ale nie jest obecnie przetłumaczone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Zapytania SQL działają na wielozestawach, a nie w sekwencjach z indeksem.|
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (Przeciążenie z argumentem domyślnym)|Ogólnie rzecz biorąc nie można określić wartości domyślnej dla dowolnej krotki. W niektórych przypadkach wartości null dla krotek są możliwe przez sprzężenia zewnętrzne.|

## <a name="expression-translation"></a>Tłumaczenie wyrażeń

### <a name="null-semantics"></a>Semantyka o wartości null

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie nakłada semantyki porównania o wartości null na SQL. Operatory porównania są syntaktycznie przetłumaczone na ich odpowiedniki języka SQL. Z tego powodu semantyka odzwierciedla semantykę SQL, która jest zdefiniowana przez ustawienia serwera lub połączenia. Na przykład dwie wartości null są uznawane za nierówne w domyślnych ustawieniach SQL Server, ale można zmienić ustawienia, aby zmienić semantykę. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie uwzględnia ustawień serwera podczas tłumaczenia zapytań.

Porównanie z literałem null jest tłumaczone na odpowiednią wersję SQL (`is null` lub `is not null`).

Wartość `null` w sortowaniu jest definiowana przez SQL Server. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie zmienia sortowania.

### <a name="aggregates"></a>Agregaty

Metoda agregująca standardowego operatora zapytania <xref:System.Linq.Enumerable.Sum%2A> szacuje się na zero dla pustej sekwencji lub dla sekwencji zawierającej tylko wartości null. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] semantyka SQL pozostaje niezmieniona, a <xref:System.Linq.Enumerable.Sum%2A> daje do `null` zamiast zero dla pustej sekwencji lub dla sekwencji zawierającej tylko wartości null.

Ograniczenia SQL dotyczące wyników pośrednich stosują się do agregacji w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. @No__t-0 z 32-bitowe liczby całkowite nie są obliczane przy użyciu 64-bitowych wyników. Przepełnienie może wystąpić w przypadku [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translacji <xref:System.Linq.Enumerable.Sum%2A>, nawet jeśli implementacja standardowego operatora zapytań nie powoduje przepełnienia odpowiedniej sekwencji w pamięci.

Analogicznie, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translacja <xref:System.Linq.Enumerable.Average%2A> wartości całkowitych jest obliczana jako `integer`, a nie jako `double`.

### <a name="entity-arguments"></a>Argumenty jednostek

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] włącza typy jednostek, które mają być używane w metodach <xref:System.Linq.Enumerable.GroupBy%2A> i <xref:System.Linq.Enumerable.OrderBy%2A>. W tłumaczeniu tych operatorów Użycie argumentu typu jest uznawane za równoważne do określenia wszystkich elementów członkowskich tego typu. Na przykład następujący kod jest równoważny:

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a>Argumenty równe/porównywalne

W implementacji następujących metod jest wymagana równość argumentów:

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje równość i porównanie dla *prostych* argumentów, ale nie dla argumentów, które są lub zawierają sekwencje. Prosty argument jest typem, który można zamapować na wiersz SQL. Rzutowanie co najmniej jednego typu jednostki, które można statycznie określić, aby nie zawierało sekwencji jest traktowane jako argument prosty.

Poniżej przedstawiono przykłady prostych argumentów:

[!code-csharp[DLinqSQOTranslation#3](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

Poniżej przedstawiono przykłady niepłaskich (hierarchicznych) argumentów:

[!code-csharp[DLinqSQOTranslation#4](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a>Tłumaczenie funkcji Visual Basic

Następujące funkcje pomocnika, które są używane przez kompilator Visual Basic są tłumaczone na odpowiednie operatory i funkcje SQL:

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

Metody konwersji:

|||||
|-|-|-|-|
|ToBoolean|ToSByte —|ToByte —|ToChar —|
|ToCharArrayRankOne|ToDate|ToDecimal —|ToDouble —|
|ToInteger|ToUInteger|ToLong|ToULong|
|ToShort|ToUShort|ToSingle —|ToString|

## <a name="inheritance-support"></a>Obsługa dziedziczenia

### <a name="inheritance-mapping-restrictions"></a>Ograniczenia mapowania dziedziczenia

Aby uzyskać więcej informacji, zobacz [How to: map dziedziczenia hierarchii](how-to-map-inheritance-hierarchies.md).

### <a name="inheritance-in-queries"></a>Dziedziczenie w zapytaniach

C#rzutowania są obsługiwane tylko w projekcji. Rzutowania, które są używane w innym miejscu, nie są tłumaczone i są ignorowane. Oprócz nazw funkcji SQL, SQL naprawdę wykonuje tylko odpowiednik środowiska uruchomieniowego języka wspólnego (CLR) <xref:System.Convert>. Oznacza to, że SQL może zmienić wartość jednego typu na inny. Nie istnieje odpowiednik rzutowania CLR, ponieważ nie ma koncepcji dotyczącej reinterpretacji tych samych bitów, co w przypadku innych typów. To dlatego, że C# rzutowanie działa tylko lokalnie. Nie jest ona zdalna.

Operatory, `is` i `as`, a metoda `GetType` nie są ograniczone do operatora `Select`. Mogą one być używane w innych operatorach zapytań.

## <a name="sql-server-2008-support"></a>Obsługa SQL Server 2008

Począwszy od .NET Framework 3,5 z dodatkiem SP1, LINQ to SQL obsługuje mapowanie do nowych typów dat i godzin wprowadzonych w SQL Server 2008. Istnieją jednak ograniczenia dotyczące LINQ to SQL operatorów zapytań, których można używać podczas pracy z wartościami mapowanymi na te nowe typy.

### <a name="unsupported-query-operators"></a>Nieobsługiwane operatory zapytań

Następujące operatory zapytań nie są obsługiwane w przypadku wartości zamapowanych na nowe SQL Server typy daty i godziny: `DATETIME2`, `DATE`, `TIME` i `DATETIMEOFFSET`.

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

Aby uzyskać więcej informacji na temat mapowania na te SQL Server typy daty i godziny, zobacz [Mapowanie typu SQL-CLR](sql-clr-type-mapping.md).

## <a name="sql-server-2005-support"></a>Obsługa SQL Server 2005

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje następujących funkcji SQL Server 2005:

- Procedury składowane zapisane dla środowiska SQL CLR.

- Typ zdefiniowany przez użytkownika.

- Funkcje zapytania XML.

## <a name="sql-server-2000-support"></a>Obsługa SQL Server 2000

Następujące ograniczenia SQL Server 2000 (w porównaniu do Microsoft SQL Server 2005) wpływają na obsługę [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].

### <a name="cross-apply-and-outer-apply-operators"></a>Cross Apply i OUTER APPLY — operatory

Te operatory nie są dostępne w SQL Server 2000. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbuje serię zastąpień, aby zamienić je na odpowiednie sprzężenia.

dla nawigacji relacji są generowane `Cross Apply` i `Outer Apply`. Zestaw zapytań, dla których takie ponowne zapisywanie jest możliwe, nie jest dobrze zdefiniowany. Z tego powodu minimalny zestaw zapytań, który jest obsługiwany przez SQL Server 2000, jest zestawem, który nie obejmuje nawigacji między relacjami.

### <a name="text--ntext"></a>tekst/ntext

Typów danych `text` @ no__t-1 @ no__t-2 nie można używać w niektórych operacjach zapytania dla `varchar(max)` @ no__t-4 @ no__t-5, które są obsługiwane przez Microsoft SQL Server 2005.

Dla tego ograniczenia nie jest dostępne żadne rozwiązanie. W związku z tym nie można użyć `Distinct()` w żadnym wyniku, który zawiera elementy członkowskie, które są zmapowane do kolumn `text` lub `ntext`.

### <a name="behavior-triggered-by-nested-queries"></a>Zachowanie wyzwalane przez zapytania zagnieżdżone

Spinacz SQL Server 2000 (do SP4) ma pewne idiosyncrasies, które są wyzwalane przez zagnieżdżone zapytania. Zbiór zapytań SQL, które wyzwalają te idiosyncrasies, nie jest dobrze zdefiniowany. Z tego powodu nie można zdefiniować zestawu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytań, które mogą spowodować SQL Server wyjątków.

### <a name="skip-and-take-operators"></a>Pomiń i wykonaj operatory

<xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są używane w zapytaniach do SQL Server 2000. Aby uzyskać więcej informacji, zobacz wpis "Pomiń i przejmowanie wyjątków w SQL Server 2000" w [temacie Rozwiązywanie problemów](troubleshooting.md).

## <a name="object-materialization"></a>Materializacja obiektu

Materializację tworzy obiekty CLR z wierszy, które są zwracane przez co najmniej jedno zapytanie SQL.

- Następujące wywołania są *wykonywane lokalnie* jako część materializację:

  - Konstruktorów

  - Metody `ToString` w projekcjach

  - Wpisz rzutowania w projekcjach

- Metody, które przestrzegają metody <xref:System.Linq.Enumerable.AsEnumerable%2A> są *wykonywane lokalnie*. Ta metoda nie powoduje natychmiastowego wykonania.

- Można użyć `struct` jako zwracany typ wyniku zapytania lub jako element członkowski typu wynik. Jednostki muszą być klasami. Typy anonimowe są materiałowe jako wystąpienia klas, ale nazwanych struktur (niebędących jednostkami) można używać w projekcji.

- Element członkowski typu zwracanego wyniku zapytania może być typu <xref:System.Linq.IQueryable%601>. Jest on materiałowy jako kolekcja lokalna.

- Następujące metody powodują *natychmiastowe materializację* sekwencji, do której są stosowane metody:

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a>Zobacz także

- [Tematy pomocy](reference.md)
- [Zwracanie lub pomijanie elementów w sekwencji](return-or-skip-elements-in-a-sequence.md)
- [Łączenie dwóch sekwencji](concatenate-two-sequences.md)
- [Zwracanie zestawu różnic między dwoma sekwencjami](return-the-set-difference-between-two-sequences.md)
- [Zwracanie zestawu części wspólnych dwóch sekwencji](return-the-set-intersection-of-two-sequences.md)
- [Zwracanie sumy zbiorów dwóch sekwencji](return-the-set-union-of-two-sequences.md)
