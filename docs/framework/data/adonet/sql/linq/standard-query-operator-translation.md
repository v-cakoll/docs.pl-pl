---
title: Translacja standardowego operatora zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: 48c95411d08aefc3ecb7d8a7041ac47d44e6b9ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127949"
---
# <a name="standard-query-operator-translation"></a>Translacja standardowego operatora zapytania
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy standardowych operatorów zapytań do polecenia SQL. Procesor zapytań bazy danych określa semantyka wykonania tłumaczenia SQL.  
  
 Standardowe operatory zapytań są zdefiniowane dla *sekwencje*. Sekwencja jest *uporządkowane* i opiera się na tożsamości referencyjnej dla każdego elementu w sekwencji. Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) lub [standardowe operatory zapytań — Przegląd (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 SQL dotyczy przede wszystkim *nieuporządkowane zestawy wartości*. Kolejność jest zazwyczaj wyraźnie określone, przetwarzanie końcowe operacji, która jest stosowana do końcowego wyniku zapytania, a nie do wyników pośrednich. Tożsamość jest definiowany przez wartości. Z tego powodu zapytania SQL są zrozumiałe radzenia sobie z multisets (*zbiory*) zamiast *ustawia*.  
  
 Następuje opisano różnice między standardowych operatorów zapytań i ich tłumaczenia SQL dla dostawcy programu SQL Server dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="operator-support"></a>Operator pomocy technicznej  
  
### <a name="concat"></a>concat  
 <xref:System.Linq.Enumerable.Concat%2A> Metoda jest zdefiniowana dla uporządkowane multisets, których kolejność odbiornik i kolejność argument są takie same. <xref:System.Linq.Enumerable.Concat%2A> działa jako `UNION ALL` za pośrednictwem multisets, a następnie według kolejności wspólne.  
  
 Ostatnim krokiem jest kolejność w języku SQL, zanim wyniki są tworzone. <xref:System.Linq.Enumerable.Concat%2A> nie pozwala zachować kolejność argumentów. W celu zapewnienia odpowiedniej kolejności, należy jawnie kolejność wyników <xref:System.Linq.Enumerable.Concat%2A>.  
  
### <a name="intersect-except-union"></a>INTERSECT, z wyjątkiem Unii  
 <xref:System.Linq.Enumerable.Intersect%2A> i <xref:System.Linq.Enumerable.Except%2A> metody są dobrze zdefiniowane tylko na zestawach. Semantyka dla multisets jest niezdefiniowane.  
  
 <xref:System.Linq.Enumerable.Union%2A> Metoda jest zdefiniowana dla multisets jako Nieuporządkowana łączenie multisets (skutecznie wynik klauzuli UNION ALL w języku SQL).  
  
### <a name="take-skip"></a>Take, Skip  
 <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> metody są dobrze zdefiniowane wyłącznie w odniesieniu do *uporządkowane zestawy*. Semantyka nieuporządkowane zestawy lub multisets są niezdefiniowane.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są one używane w kwerendach do programu SQL Server 2000. Aby uzyskać więcej informacji, zobacz wpis "Pomiń i Pobierz wyjątki w programie SQL Server 2000 do niego dostępu" w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 Ze względu na ograniczenia dotyczące kolejności w programie SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spróbuje przenieść Kolejność argumentów z tych metod do wyniku metody. Na przykład, należy wziąć pod uwagę następujące [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kwerendy:  
  
 [!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
 [!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]  
  
 Wygenerowany SQL dla tego kodu przenosi, to porządkowanie-to-end, w następujący sposób:  
  
```  
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
  
 Staje się oczywiste, że wszystkie określonej kolejności, muszą być zgodne po <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> są połączone. W przeciwnym wypadku wyniki są niezdefiniowane.  
  
 Zarówno <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> są dobrze zdefiniowanych dla wartość nieujemną, stała argumentów całkowitych na podstawie specyfikacji standardowej kwerendy operatora.  
  
### <a name="operators-with-no-translation"></a>Operatory bez translacji  
 Następujących metod nie są one tłumaczone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Najbardziej typową przyczyną jest różnica między multisets nieuporządkowane i sekwencji.  
  
|Operatory|Racjonalne uzasadnienie|  
|---------------|---------------|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|Zapytania SQL działają na multisets nie w sekwencji. `ORDER BY` musi zostać ostatniej zastosowana do wyników. Z tego powodu nie ma żadnych tłumaczeń ogólnego przeznaczenia dla tych dwóch metod.|  
|<xref:System.Linq.Enumerable.Reverse%2A>|Tłumaczenie tej metody jest możliwe, aby uporządkowany zestaw, ale nie jest obecnie tłumaczyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Tłumaczenie tych metod jest możliwe uporządkowany zestaw, ale nie jest obecnie tłumaczyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Zapytania SQL działają na multisets na nie można indeksować sekwencji.|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (przeciążenia za pomocą domyślnego argumentu)|Ogólnie rzecz biorąc wartość domyślna, nie można określić dla dowolnego spójnej kolekcji. Wartości null dla krotek są możliwe w niektórych przypadkach za pomocą sprzężeń zewnętrznych.|  
  
## <a name="expression-translation"></a>Translacja wyrażeń  
  
### <a name="null-semantics"></a>Semantyka wartości null  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie wymusza semantykę porównania wartości null w języku SQL. Operatory porównania składniowo są tłumaczone na ich odpowiedniki SQL. Z tego powodu semantykę odzwierciedlają semantyki SQL, które są definiowane przez ustawienia serwera lub połączenia. Na przykład dwie wartości null są uznawane za nierówne w obszarze domyślne ustawienia programu SQL Server, ale możesz zmienić ustawienia, aby zmienić semantyki. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie należy traktować ustawienia serwera, gdy przekłada zapytania.  
  
 Porównanie z literałem o wartości null jest tłumaczona na odpowiednią wersję programu SQL (`is null` lub `is not null`).  
  
 Wartość `null` w sortowaniu jest zdefiniowany przez program SQL Server. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie powoduje zmiany sortowania.  
  
### <a name="aggregates"></a>Agregaty  
 Metoda agregacji standardowej kwerendy operatora <xref:System.Linq.Enumerable.Sum%2A> osiągnie wartość zero dla pustej sekwencji lub sekwencję która zawiera tylko wartości null. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], semantyki programu SQL Server są pozostawione bez zmian, i <xref:System.Linq.Enumerable.Sum%2A> daje w wyniku `null` zamiast zero sekwencję która zawiera tylko wartości null lub pustą sekwencją.  
  
 SQL na wyniki pośrednie ograniczenia wartości zagregowanych umieszczonych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Linq.Enumerable.Sum%2A> Z 32-bitowej liczby całkowitej ilości nie jest kolumną obliczaną za pomocą 64-bitowych wyników. Przepełnienie mogą wystąpić w przypadku [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczenia <xref:System.Linq.Enumerable.Sum%2A>nawet wtedy, gdy implementacja standardowej kwerendy operatora nie powoduje przepełnienie w odpowiedniej sekwencji w pamięci.  
  
 Podobnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczenia <xref:System.Linq.Enumerable.Average%2A> liczby całkowitej wartości jest obliczana jako `integer`, nie jako `double`.  
  
### <a name="entity-arguments"></a>Argumenty jednostki  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Włącza typów jednostek, które zostaną użyte w <xref:System.Linq.Enumerable.GroupBy%2A> i <xref:System.Linq.Enumerable.OrderBy%2A> metody. W tłumaczeniu tych operatorów Użyj argumentu typu jest uważana za równoważne do określania wszystkie elementy członkowskie tego typu. Na przykład poniższy kod jest równoważne:  
  
 [!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
 [!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]  
  
### <a name="equatable--comparable-arguments"></a>Argumenty equatable / porównywalnych  
 Równość argumentów jest wymagany w celu wykonania poniższych metod:  
  
 <xref:System.Linq.Enumerable.Contains%2A>  
  
 <xref:System.Linq.Enumerable.Skip%2A>  
  
 <xref:System.Linq.Enumerable.Union%2A>  
  
 <xref:System.Linq.Enumerable.Intersect%2A>  
  
 <xref:System.Linq.Enumerable.Except%2A>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje równości i porównanie *prostego* argumentów, ale nie dla argumentów, które są lub zawierać sekwencje. Płaski argument jest typu, które mogą być mapowane do wiersza SQL. Rzutowanie typów jednostek, które mogą być statycznie uznane za nie zawierać sekwencję jest traktowany jako stała argumentu.  
  
 Poniżej przedstawiono przykłady prostego argumenty:  
  
 [!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
 [!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]  
  
 Poniżej przedstawiono przykłady argumentów płaskiej (hierarchiczne).  
  
 [!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
 [!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]  
  
### <a name="visual-basic-function-translation"></a>Tłumaczenie funkcji języka Visual Basic  
 Następujące funkcje pomocnika, które są używane przez kompilator Visual Basic są tłumaczone na odpowiednie operatory SQL i funkcje:  
  
 `CompareString`  
  
 `DateTime.Compare`  
  
 `Decimal.Compare`  
  
 `IIf (in Microsoft.VisualBasic.Interaction)`  
  
 Metody konwersji:  
  
|||||  
|-|-|-|-|  
|ToBoolean|ToSByte|Tobyte —|ToChar|  
|ToCharArrayRankOne|ToDate|ToDecimal|Todouble —|  
|ToInteger|ToUInteger|ToLong|ToULong|  
|ToShort|ToUShort|Tosingle —|ToString|  
  
## <a name="inheritance-support"></a>Obsługa dziedziczenia  
  
### <a name="inheritance-mapping-restrictions"></a>Ograniczenia dotyczące mapowania dziedziczenia  
 Aby uzyskać więcej informacji, zobacz [jak: Mapowanie hierarchii dziedziczenia](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
### <a name="inheritance-in-queries"></a>Dziedziczenie w zapytaniach  
 C# rzutowania są obsługiwane tylko w projekcji. Wzory, które są używane w innym miejscu, nie są przekształcane i są ignorowane. Oprócz SQL nazwy funkcji, SQL tak naprawdę tylko wykonuje odpowiednik środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.Convert>. Oznacza to SQL, można zmienić wartości z jednego typu na inny. Nie ma odpowiednika rzutowania, ponieważ nie istnieje koncepcji reinterpretacja tej samej usługi bits, jak te innego typu CLR. Właśnie dlatego rzutowania języka C# działa tylko lokalnie. Nie jest zdalny.  
  
 Operatory, `is` i `as`i `GetType` metody nie są ograniczone do `Select` operatora. Ich zastosowania w innych operatorów zapytania również.  
  
## <a name="sql-server-2008-support"></a>SQL Server 2008 Support  
 Począwszy od .NET Framework 3.5 SP1, LINQ to SQL obsługuje mapowanie na nową datę i czas typy wprowadzone w programie SQL Server 2008. Istnieją jednak pewne ograniczenia dotyczące LINQ to SQL operatorów zapytań, które można użyć podczas pracy w odniesieniu do wartości mapowane na te nowe typy.  
  
### <a name="unsupported-query-operators"></a>Nieobsługiwane zapytanie operatorów  
 Następujące operatory zapytań nie są obsługiwane na wartościach mapowane na nowe typy daty i godziny programu SQL Server: `DATETIME2`, `DATE`, `TIME`, i `DATETIMEOFFSET`.  
  
-   `Aggregate`  
  
-   `Average`  
  
-   `LastOrDefault`  
  
-   `OfType`  
  
-   `Sum`  
  
 Aby uzyskać więcej informacji na temat mapowania do tych typów daty i godziny programu SQL Server, zobacz [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="sql-server-2005-support"></a>SQL Server 2005 Support  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje następujących funkcji programu SQL Server 2005:  
  
-   Procedury składowane napisane dla środowiska CLR programu SQL.  
  
-   Typ zdefiniowany przez użytkownika.  
  
-   Funkcje zapytania XML.  
  
## <a name="sql-server-2000-support"></a>SQL Server 2000 Support  
 Następujące [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ograniczenia (w porównaniu do [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) wpływają na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pomocy technicznej.  
  
### <a name="cross-apply-and-outer-apply-operators"></a>Cross Apply i zewnętrznych stosowanie operatorów  
 Te operatory nie są dostępne w [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbuje szereg modyfikacji oprogramowania, aby zastąpić odpowiednie sprzężenia.  
  
 `Cross Apply` i `Outer Apply` są generowane dla tego relacji. Zestaw zapytań, dla których są możliwe takich modyfikacji oprogramowania nie jest dobrze zdefiniowane. Z tego powodu minimalny zestaw zapytań, które jest obsługiwane w przypadku [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] to zestaw, który nie wymaga nawigacji relacji.  
  
### <a name="text--ntext"></a>Text / ntext  
 Typy danych `text`  /  `ntext` nie można używać w niektórych operacji zapytań dotyczących `varchar(max)`  /  `nvarchar(max)`, które są obsługiwane przez [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].  
  
 Rozwiązanie jest dostępne dla tego ograniczenia. Ściślej mówiąc, nie można użyć `Distinct()` na dowolny wynik, który zawiera elementy członkowskie, które są mapowane na `text` lub `ntext` kolumn.  
  
### <a name="behavior-triggered-by-nested-queries"></a>Zachowanie wyzwolone przez zapytań zagnieżdżonej  
 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] (za pośrednictwem SP4) integratorów modeli zawiera specyfikę, które są uruchamiane w zapytań zagnieżdżonej. Zestaw zapytań SQL, który wyzwala te idiosyncrasies nie jest dobrze zdefiniowane. Z tego powodu nie można zdefiniować zestaw [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytań, które mogłyby spowodować wyjątków programu SQL Server.  
  
### <a name="skip-and-take-operators"></a>Pomiń i Pobierz operatorów  
 <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są one używane w zapytaniach względem [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. Aby uzyskać więcej informacji, zobacz wpis "Pomiń i Pobierz wyjątki w programie SQL Server 2000 do niego dostępu" w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="object-materialization"></a>Materializacja obiektu  
 Materializacja tworzy obiekty CLR z wierszy zwracanych przez co najmniej jeden zapytania SQL.  
  
-   Następujące wywołania są *wykonywany lokalnie,* jako część materializacja:  
  
    -   Konstruktorów  
  
    -   `ToString` metody w projekcji  
  
    -   Rzutowania typów w projekcji  
  
-   Metody, które należy wykonać <xref:System.Linq.Enumerable.AsEnumerable%2A> metoda są *wykonywany lokalnie,*. Ta metoda nie powoduje natychmiastowe wykonanie.  
  
-   Możesz użyć `struct` jako zwracany typ wyniku zapytania lub elementem członkowskim typu wyniku. Jednostki są wymagane do klasy. Typy anonimowe są zmaterializowanego jako wystąpienia klasy, ale nazwanej struktury (inne niż jednostek) mogą być używane w projekcji.  
  
-   Członek typu zwracanego wyniku zapytania mogą być typu <xref:System.Linq.IQueryable%601>. Jest on zmaterializowany jako kolekcja lokalna.  
  
-   Następujące metody powodują *natychmiastowego materializacja* sekwencji, które metody są stosowane do:  
  
    -   <xref:System.Linq.Enumerable.ToList%2A>  
  
    -   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
    -   <xref:System.Linq.Enumerable.ToArray%2A>  
  
## <a name="see-also"></a>Zobacz także

- [Tematy pomocy](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Zwracanie lub pomijanie elementów w sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)
- [Łączenie dwóch sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)
- [Zwracanie zestawu różnic między dwoma sekwencjami](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)
- [Zwracanie zestawu części wspólnych dwóch sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)
- [Zwracanie sumy zbiorów dwóch sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
