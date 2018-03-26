---
title: Translacja Operator zapytania standardowe
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: fc99fea9b722f6c3395f6bade625a09c6e97eb08
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="standard-query-operator-translation"></a>Translacja Operator zapytania standardowe
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonuje translację standardowych operatorów zapytań do poleceń SQL. Procesor zapytań bazy danych określa semantyki wykonywania tłumaczenia SQL.  
  
 Standardowe operatory zapytań są zdefiniowane w odniesieniu do *sekwencji*. Sekwencja jest *uporządkowane* i opiera się na tożsamości odwołania dla każdego elementu w sekwencji. Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 SQL dotyczy przede wszystkim *nieuporządkowane zestawy wartości*. Kolejność jest zwykle jawnie stwierdzono, operacja, która jest stosowana do końcowego wyniku zapytania, a nie na pośrednich wyników przetwarzania końcowego. Tożsamość jest definiowany przez wartości. Z tego powodu zapytania SQL są zrozumiałe radzenia sobie z multisets (*torebki*) zamiast *ustawia*.  
  
 Następuje opisano różnice między standardowych operatorów zapytań i ich tłumaczenia SQL dla dostawcy programu SQL Server dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="operator-support"></a>Obsługa — operator  
  
### <a name="concat"></a>concat  
 <xref:System.Linq.Enumerable.Concat%2A> Metody jest zdefiniowany dla uporządkowanych multisets, których kolejność odbiornika oraz kolejność argumentu są takie same. <xref:System.Linq.Enumerable.Concat%2A> działa jako `UNION ALL` za pośrednictwem multisets następuje wspólnej kolejności.  
  
 Ostatnim krokiem jest kolejnością SQL przed wyniki są tworzone. <xref:System.Linq.Enumerable.Concat%2A> Nie zachowuj Kolejność argumentów. W celu zapewnienia odpowiedniej kolejności, musisz jawnie kolejność wyników <xref:System.Linq.Enumerable.Concat%2A>.  
  
### <a name="intersect-except-union"></a>INTERSECT, z wyjątkiem przypadków Unii  
 <xref:System.Linq.Enumerable.Intersect%2A> i <xref:System.Linq.Enumerable.Except%2A> metody są jasno określone tylko dla zestawów. Semantyka dla multisets jest niezdefiniowana.  
  
 <xref:System.Linq.Enumerable.Union%2A> Metody określone dla multisets nieuporządkowaną złączeniem multisets (efektywnie wynik klauzuli UNION ALL w języku SQL).  
  
### <a name="take-skip"></a>Take, Skip  
 <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> metody są jasno określone tylko przed *uporządkowane zestawy*. Semantyka nieuporządkowaną zestawów lub multisets jest nieokreślona.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są one używane w kwerendach do programu SQL Server 2000. Aby uzyskać więcej informacji, zobacz wpis "Pomiń i podjąć wyjątków w programie SQL Server 2000" w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 Ze względu na ograniczenia dotyczące kolejności w programie SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbuje przenieść kolejność argument tych metod do wyniku metody. Na przykład, należy wziąć pod uwagę następujące [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania:  
  
 [!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
 [!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]  
  
 Wygenerowany SQL dla tego kodu przenosi kolejność w celu ich w następujący sposób:  
  
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
  
 Staje się oczywiste, że wszystkie określona kolejność musi być spójna kiedy <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> są połączone. W przeciwnym razie wyniki są niezdefiniowane.  
  
 Zarówno <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> są dobrze zdefiniowany dla ujemna, stałych argumentów całkowitych na podstawie specyfikacji standardowe — Operator zapytań.  
  
### <a name="operators-with-no-translation"></a>Operatory bez translacji  
 Następujących metod nie są tłumaczone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Najczęstszą przyczyną jest różnica między nieuporządkowaną multisets i sekwencji.  
  
|Operatory|Decyzja|  
|---------------|---------------|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|Zapytania SQL działają na multisets nie znajduje się w sekwencji. `ORDER BY` musi być ostatniej zastosowana wyniki. Z tego powodu nie istnieje żadne ogólnego przeznaczenia Translacja te dwie metody.|  
|<xref:System.Linq.Enumerable.Reverse%2A>|Tłumaczenie tej metody jest możliwość uporządkowany zestaw, ale nie jest obecnie translacji przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Tłumaczenie z tych metod jest możliwe w dla zestawu uporządkowanych, ale nie jest obecnie translacji przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Zapytania SQL działają na multisets na nie można indeksować sekwencji.|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (przeciążenia z arg domyślne)|Ogólnie rzecz biorąc wartości domyślnej nie można określić dla dowolnego spójnej kolekcji. Wartości null dla krotek są możliwe w niektórych przypadkach za pomocą sprzężeń zewnętrznych.|  
  
## <a name="expression-translation"></a>Wyrażenie tłumaczenia  
  
### <a name="null-semantics"></a>Semantyka wartości null  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie nakłada semantykę porównania wartości null na SQL. Operatory porównania składniowo są przekształcane na ich odpowiedniki SQL. Z tego powodu semantykę odzwierciedlają semantyki SQL są definiowane przez ustawienia serwera lub połączenia. Na przykład dwie wartości null są traktowane jako nierówne w domyślnych ustawień programu SQL Server, ale można zmienić ustawienia, aby zmienić semantykę. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie należy wziąć pod uwagę ustawienia serwera podczas tłumaczy zapytania.  
  
 Przetłumaczono porównanie z wartością literału null do odpowiedniej wersji programu SQL (`is null` lub `is not null`).  
  
 Wartość `null` w sortowaniu jest zdefiniowany przez program SQL Server. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie powoduje zmiany sortowania.  
  
### <a name="aggregates"></a>Agregaty  
 Metoda agregacji standardowe — Operator zapytań <xref:System.Linq.Enumerable.Sum%2A> oblicza od zera dla pustej sekwencji lub sekwencję, która zawiera tylko wartości null. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], semantykę SQL pozostaną bez zmian, i <xref:System.Linq.Enumerable.Sum%2A> daje w wyniku `null` zamiast zero sekwencji, który zawiera tylko wartości null lub pustej sekwencji.  
  
 Ograniczenia SQL pośrednich wyników dotyczą wartości zagregowanych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Linq.Enumerable.Sum%2A> 32-bitowej liczby całkowitej ilości nie jest obliczana przy użyciu 64-bitowych wyników. Przepełnienie mogą wystąpić w przypadku [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczenie <xref:System.Linq.Enumerable.Sum%2A>nawet w przypadku wdrożenia standardowego — Operator zapytań nie spowoduje przepełnienie w odpowiedniej sekwencji w pamięci.  
  
 Podobnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczenie <xref:System.Linq.Enumerable.Average%2A> liczby całkowitej wartości jest obliczana jako `integer`, nie jako `double`.  
  
### <a name="entity-arguments"></a>Argumenty jednostki  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Włącza typy jednostek, które mają być używane w <xref:System.Linq.Enumerable.GroupBy%2A> i <xref:System.Linq.Enumerable.OrderBy%2A> metody. W tłumaczeniu wartości tych operatorów Użyj argumentu typu jest uważana za równoważne określenie wszystkich elementów członkowskich tego typu. Na przykład następujący kod jest równoważne:  
  
 [!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
 [!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]  
  
### <a name="equatable--comparable-arguments"></a>Equatable / można porównywać argumentów  
 Równość argumentów jest wymagane w celu wykonania następujących metod:  
  
 <xref:System.Linq.Enumerable.Contains%2A>  
  
 <xref:System.Linq.Enumerable.Skip%2A>  
  
 <xref:System.Linq.Enumerable.Union%2A>  
  
 <xref:System.Linq.Enumerable.Intersect%2A>  
  
 <xref:System.Linq.Enumerable.Except%2A>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje równości i porównania dla *płaskiej* argumentów, ale nie dla argumentów, które są lub zawierać sekwencji. Płaski argument jest typu, które mogą być mapowane na wiersz SQL. Rzutowania typów jednostek, które można ustalić statycznie nie może zawierać sekwencję jest traktowany jako płaska argument.  
  
 Poniżej przedstawiono przykłady płaskiej argumentów:  
  
 [!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
 [!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]  
  
 Poniżej przedstawiono przykłady argumentów płaski (hierarchiczna).  
  
 [!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
 [!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]  
  
### <a name="visual-basic-function-translation"></a>Tłumaczenie funkcji języka Visual Basic  
 Następujące funkcje pomocnicze, które są używane przez kompilator Visual Basic są tłumaczone na odpowiednich operatory SQL i funkcje:  
  
 `CompareString`  
  
 `DateTime.Compare`  
  
 `Decimal.Compare`  
  
 `IIf (in Microsoft.VisualBasic.Interaction)`  
  
 Metody konwersji:  
  
|||||  
|-|-|-|-|  
|ToBoolean|Tosbyte —|ToByte|ToChar|  
|ToCharArrayRankOne|ToDate|Todecimal —|Todouble —|  
|ToInteger|ToUInteger|ToLong|ToULong|  
|ToShort|ToUShort|Tosingle —|ToString|  
  
## <a name="inheritance-support"></a>Obsługa dziedziczenia  
  
### <a name="inheritance-mapping-restrictions"></a>Ograniczenia dotyczące mapowania dziedziczenia  
 Aby uzyskać więcej informacji, zobacz [porady: hierarchii dziedziczenia mapy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
### <a name="inheritance-in-queries"></a>Dziedziczenie w zapytaniach  
 C# rzutowania są obsługiwane tylko w projekcji. Rzutowania, które są używane w innym miejscu, nie są tłumaczone i są ignorowane. Jako uzupełnienie SQL funkcji nazwy, SQL naprawdę przeprowadza tylko operacje odpowiednikiem środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.Convert>. Oznacza to, że SQL można zmienić wartości typu jeden do innego. Nie ma odpowiednika z rzutowania, ponieważ nie istnieje żadne koncepcji reinterpreting tej samej usługi bits, jak inny typ CLR. Właśnie dlatego C# rzutowania działa tylko lokalnie. Nie jest on zdalny.  
  
 Operatory, `is` i `as`i `GetType` — metoda nie są ograniczone do `Select` operatora. Ich użyciem w innych operatorów zapytań również.  
  
## <a name="sql-server-2008-support"></a>Obsługa programu SQL Server 2008  
 LINQ do SQL w programie .NET Framework 3.5 z dodatkiem SP1, obsługuje mapowanie Nowa data i czas typy programu Microsoft SQL Server 2008. Istnieją jednak pewne ograniczenia w składniku LINQ to SQL operatorów zapytań, używane podczas pracy z wartościami mapowane na te nowe typy.  
  
### <a name="unsupported-query-operators"></a>Operatory kwerend nieobsługiwana  
 Następujące operatory zapytań nie są obsługiwane w wartości mapowane na nowe typy Data i godzina programu SQL Server: `DATETIME2`, `DATE`, `TIME`, i `DATETIMEOFFSET`.  
  
-   `Aggregate`  
  
-   `Average`  
  
-   `LastOrDefault`  
  
-   `OfType`  
  
-   `Sum`  
  
 Aby uzyskać więcej informacji dotyczących mapowania do tych typów Data i godzina programu SQL Server, zobacz [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="sql-server-2005-support"></a>Obsługa programu SQL Server 2005  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje następujące funkcje programu SQL Server 2005:  
  
-   Procedury składowane napisane dla SQL CLR.  
  
-   Typ zdefiniowany przez użytkownika.  
  
-   Funkcje zapytań języka XML.  
  
## <a name="sql-server-2000-support"></a>Obsługa programu SQL Server 2000  
 Następujące [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ograniczenia (w porównaniu do [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) mają wpływ na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje.  
  
### <a name="cross-apply-and-outer-apply-operators"></a>Zastosuj Cross i zewnętrznych zastosować operatory  
 Operatory te nie są dostępne w [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbuje szereg modyfikacji oprogramowania należy zastąpić odpowiednie sprzężenia.  
  
 `Cross Apply` i `Outer Apply` są generowane dla nawigacji relacji. Zbiór zapytań, dla których są możliwe takich modyfikacji oprogramowania nie jest dobrze zdefiniowany. Z tego powodu minimalny zbiór zapytań, które jest obsługiwana w przypadku [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] zestaw nie jest związana z nawigacji relacji.  
  
### <a name="text--ntext"></a>tekst / ntext  
 Typy danych `text`  /  `ntext` nie można używać w pewnych operacji zapytania względem `varchar(max)`  /  `nvarchar(max)`, które są obsługiwane przez [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].  
  
 Nie rozwiązanie jest dostępne dla tego ograniczenia. W szczególności nie można użyć `Distinct()` na dowolny wynik, który zawiera elementy członkowskie, które są mapowane na `text` lub `ntext` kolumn.  
  
### <a name="behavior-triggered-by-nested-queries"></a>Zachowanie wyzwalane przez zapytania zagnieżdżone  
 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] (za pośrednictwem SP4) integratora ma specyfikę wyzwalane przez zapytania zagnieżdżone. Zestaw zapytania SQL, który uruchamia te idiosyncrasies nie jest dobrze zdefiniowany. Z tego powodu nie można zdefiniować zestawu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania, które mogą spowodować wyjątków programu SQL Server.  
  
### <a name="skip-and-take-operators"></a>SKIP i Take operatorów  
 <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są one używane w zapytaniach przed [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. Aby uzyskać więcej informacji, zobacz wpis "Pomiń i podjąć wyjątków w programie SQL Server 2000" w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="object-materialization"></a>Obiekt Materialization  
 Materialization tworzy obiekty CLR z wierszy zwracanych przez co najmniej jednego zapytania SQL.  
  
-   Następujące wywołania są *wykonywane lokalnie* jako część materialization:  
  
    -   Konstruktorów  
  
    -   `ToString` metody w projekcji  
  
    -   Rzutowania typów w projekcji  
  
-   Metody, które należy wykonać <xref:System.Linq.Enumerable.AsEnumerable%2A> metody są *wykonywane lokalnie*. Ta metoda nie powoduje natychmiastowego wykonania.  
  
-   Można użyć `struct` jako zwracany typ wyniku zapytania lub elementem członkowskim typu wyniku. Jednostek muszą być klasy. Typy anonimowe są zmaterializowany jako wystąpień klasy, ale nazwanego struktur (z systemem innym niż jednostek) może być używana w projekcji.  
  
-   Członek zwracany typ wyniku zapytania mogą być typu <xref:System.Linq.IQueryable%601>. Jest on zmaterializowany jako kolekcja lokalna.  
  
-   Następujące metody powodują *materialization natychmiastowego* sekwencji, które metody są stosowane do:  
  
    -   <xref:System.Linq.Enumerable.ToList%2A>  
  
    -   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
    -   <xref:System.Linq.Enumerable.ToArray%2A>  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Zwracanie lub pomijanie elementów w sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 [Łączenie dwóch sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 [Zwracanie zestawu różnic między dwoma sekwencjami](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 [Zwracanie zestawu części wspólnych dwóch sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 [Zwracanie sumy zbiorów dwóch sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
