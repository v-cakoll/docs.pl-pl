---
title: Mapowania typów środowiska SQL-CLR
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: d2ec70d014198299bd911b1a72ab8eb26c096ba9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592472"
---
# <a name="sql-clr-type-mapping"></a>Mapowania typów środowiska SQL-CLR
Model danych relacyjnej bazy danych w składniku LINQ to SQL, mapuje modelu obiektów, które są jest wyrażone w wybranym języku programowania. Gdy aplikacja zostanie uruchomiona, LINQ to SQL tłumaczy języku zintegrowanym zapytania w modelu obiektów programu SQL i wysyła je do bazy danych do wykonania. Po powrocie z bazy danych wyników programu LINQ to SQL tłumaczy wyniki z powrotem do obiektów, które może pracować w języku użytkownika, programowania.  
  
 W celu tłumaczenia danych między model obiektu i bazy danych, *mapowania typów* musi być zdefiniowany. LINQ do SQL używa mapowania typów w celu dopasowania każdy typ środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego z określonym typem programu SQL Server. Można zdefiniować mapowanie typu i inne informacje dotyczące mapowania, takich jak bazy danych struktury i relacji między tabelami, wewnątrz modelu obiektów za pomocą mapowania opartych na atrybutach. Alternatywnie można określić informacje dotyczące mapowania poza model obiektów przy użyciu pliku mapowanie zewnętrzne. Aby uzyskać więcej informacji, zobacz [mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) i [mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 W tym temacie omówiono następujące kwestie:  
  
- [Domyślny typ mapowania](#DefaultTypeMapping)  
  
- [Typ mapowania macierzy zachowania w czasie wykonywania](#BehaviorMatrix)  
  
- [Różnice zachowanie środowiska CLR i wykonywania instrukcji SQL.](#BehaviorDiffs)  
  
- [Mapowanie wyliczenia](#EnumMapping)  
  
- [Mapowanie liczbowe](#NumericMapping)  
  
- [Tekst i mapowania XML](#TextMapping)  
  
- [Data i godzina mapowania](#DateMapping)  
  
- [Mapowanie binarne](#BinaryMapping)  
  
- [Różne mapowania](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## <a name="default-type-mapping"></a>Domyślny typ mapowania  
 Można utworzyć modelu obiektów lub pliku mapowania zewnętrznych automatycznie Object Relational Designer (Projektant O/R) lub narzędzie wiersza polecenia SQLMetal. Domyślne mapowania typu tych narzędzi definiują, jakie typy CLR zostały wybrane do mapowania kolumn w bazie danych programu SQL Server. Aby uzyskać więcej informacji na temat używania tych narzędzi, zobacz [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md).  
  
 Można również użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metodę, aby utworzyć bazę danych programu SQL Server na podstawie mapowania informacji w pliku mapowania zewnętrznych lub model obiektów. Mapowania typ domyślny dla <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metodę zdefiniować typ serwera SQL, które kolumny są tworzone do mapowania środowiska CLR, typy w modelu obiektów. Aby uzyskać więcej informacji, zobacz [jak: Dynamiczne tworzenie bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>   
## <a name="type-mapping-run-time-behavior-matrix"></a>Typ mapowania macierzy zachowania w czasie wykonywania  
 Poniższy diagram przedstawia oczekiwanego zachowania mapowania określonego typu w czasie wykonywania, gdy dane są pobierane lub zapisywane w bazie danych. Z wyjątkiem serializacji LINQ to SQL nie obsługuje mapowania między żadnych danych CLR lub SQL Server, typy, które nie zostały określone w tej macierzy. Aby uzyskać więcej informacji na temat obsługi serializacji, zobacz [serializacji binarnej](#BinarySerialization).  
 
![Program SQL Server do tabeli mapowania typu danych SQL CLR](media/sql-clr-type-mapping.png)

> [!NOTE]
>  Niektóre mapowania typu może spowodować wyjątki utraty danych lub przepełnienie podczas tłumaczenia do lub z bazy danych.  
  
### <a name="custom-type-mapping"></a>Mapowanie niestandardowego typu  
 Za pomocą LINQ to SQL nie są ograniczone do domyślnego mapowania typu używane przez projektanta O/R SQLMetal i <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metody. Mapowanie niestandardowego typu można utworzyć, jawnie określając je w pliku DBML. Następnie można użyć tego pliku DBML, można utworzyć pliku kod i mapowanie modelu obiektu. Aby uzyskać więcej informacji, zobacz [SQL CLR niestandardowy typ mapowania](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>   
## <a name="behavior-differences-between-clr-and-sql-execution"></a>Różnice zachowanie środowiska CLR i wykonywania instrukcji SQL.  
 Ze względu na różnice w dokładności i wykonywania CLR i programu SQL Server możesz odbierać różne wyniki lub występują inne zachowanie w zależności od tego, gdzie wykonać obliczeń. Obliczenia wykonywane w składniku LINQ do zapytań SQL są faktycznie tłumaczone języka Transact-SQL i następnie wykonywane w bazie danych programu SQL Server. Obliczenia wykonywane poza LINQ do zapytań SQL są wykonywane w kontekście środowiska CLR.  
  
 Na przykład poniżej przedstawiono niektóre różnice w zachowaniu między CLR i programu SQL Server:  
  
- Program SQL Server inaczej niż dane typu równoważne zamówień niektóre typy danych w CLR. Na przykład dane programu SQL Server typu `UNIQUEIDENTIFIER` są porządkowane inaczej niż dane typu CLR <xref:System.Guid?displayProperty=nameWithType>.  
  
- Program SQL Server obsługuje niektóre operacje porównania ciągu inaczej niż środowiska CLR. W programie SQL Server zachowanie porównania ciągu zależy od ustawienia sortowania na serwerze. Aby uzyskać więcej informacji, zobacz [Praca z ustawień sortowania](https://go.microsoft.com/fwlink/?LinkId=115330) w programie Microsoft SQL Server — książki Online.  
  
- Program SQL Server może zwracać różne wartości dla niektórych funkcji zamapowanego niż środowiska CLR. Na przykład równości funkcji różnią się, ponieważ program SQL Server uwzględnia dwa ciągi równy, jeśli różnią się odstępu; Środowisko CLR uważa musiały być równe.  
  
<a name="EnumMapping"></a>   
## <a name="enum-mapping"></a>Mapowanie wyliczenia  
 LINQ do SQL obsługuje mapowanie środowiska CLR <xref:System.Enum?displayProperty=nameWithType> typu do typów programu SQL Server na dwa sposoby:  
  
- Mapowanie na typy liczbowe języka SQL (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)  
  
     Podczas mapowania CLR <xref:System.Enum?displayProperty=nameWithType> typu do typu numerycznego SQL, możesz zamapować wartość całkowitą bazowego środowiska CLR <xref:System.Enum?displayProperty=nameWithType> wartość kolumny bazy danych programu SQL Server. Na przykład jeśli <xref:System.Enum?displayProperty=nameWithType> o nazwie `DaysOfWeek` zawiera element o nazwie `Tue` ze źródłową wartością całkowitą 3, ten element członkowski jest mapowany na wartość 3 dla bazy danych.  
  
- Mapowania typów tekstu SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)  
  
     Podczas mapowania CLR <xref:System.Enum?displayProperty=nameWithType> typu do typu SQL, wartości bazy danych SQL jest mapowany do nazw środowiska CLR <xref:System.Enum?displayProperty=nameWithType> elementów członkowskich. Na przykład jeśli <xref:System.Enum?displayProperty=nameWithType> o nazwie `DaysOfWeek` zawiera element o nazwie `Tue` ze źródłową wartością całkowitą 3, ten element członkowski mapy do wartości bazy danych `Tue`.  
  
> [!NOTE]
>  Podczas mapowania typów tekstu SQL do CLR <xref:System.Enum?displayProperty=nameWithType>, zawierają tylko nazwy <xref:System.Enum> elementów członkowskich w mapowanej kolumny SQL. Inne wartości nie są obsługiwane w <xref:System.Enum>-mapowane na kolumny SQL.  
  
 Narzędzie wiersza polecenia O/R Designer i SQLMetal automatycznie nie można zamapować typu SQL do CLR <xref:System.Enum> klasy. To mapowanie należy skonfigurować jawnie, dostosowując do użytku przez projektanta O/R i SQLMetal za pomocą pliku DBML. Aby uzyskać więcej informacji na temat mapowania typu niestandardowego zobacz [niestandardowe mapowania typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
 Ponieważ kolumny SQL przeznaczonych do wyliczenia będzie tego samego typu co inne kolumny liczbowe i tekstowe; Narzędzia te nie rozpoznaje Twoje intencje i domyślne mapowanie zgodnie z opisem w następujących [liczbowych mapowania](#NumericMapping) i [tekstu i mapowania XML](#TextMapping) sekcje. Aby uzyskać więcej informacji na temat generowania kodu za pomocą pliku DBML zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda tworzy kolumny SQL typu liczbowego, aby zamapować CLR <xref:System.Enum?displayProperty=nameWithType> typu.  
  
<a name="NumericMapping"></a>   
## <a name="numeric-mapping"></a>Mapowanie liczbowe  
 LINQ do SQL umożliwia mapowanie wielu CLR i programu SQL Server typów liczbowych. W poniższej tabeli przedstawiono typy CLR, że O/R Designer i SQLMetal wybrać podczas tworzenia modelu obiektów lub pliku mapowania zewnętrznych, na podstawie Twojej bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez projektanta O/R i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BIT`|<xref:System.Boolean?displayProperty=nameWithType>|  
|`TINYINT`|<xref:System.Int16?displayProperty=nameWithType>|  
|`INT`|<xref:System.Int32?displayProperty=nameWithType>|  
|`BIGINT`|<xref:System.Int64?displayProperty=nameWithType>|  
|`SMALLMONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`MONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`DECIMAL`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`NUMERIC`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`REAL/FLOAT(24)`|<xref:System.Single?displayProperty=nameWithType>|  
|`FLOAT/FLOAT(53)`|<xref:System.Double?displayProperty=nameWithType>|  
  
 W następnej tabeli przedstawiono domyślne mapowania typu, używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typy kolumn programu SQL są tworzone do mapowania na typy CLR zdefiniowane w modelu obiektu lub pliku mapowania zewnętrznych.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|`BIT`|  
|<xref:System.Byte?displayProperty=nameWithType>|`TINYINT`|  
|<xref:System.Int16?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.Int32?displayProperty=nameWithType>|`INT`|  
|<xref:System.Int64?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.SByte?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.UInt16?displayProperty=nameWithType>|`INT`|  
|<xref:System.UInt32?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.UInt64?displayProperty=nameWithType>|`DECIMAL(20)`|  
|<xref:System.Decimal?displayProperty=nameWithType>|`DECIMAL(29,4)`|  
|<xref:System.Single?displayProperty=nameWithType>|`REAL`|  
|<xref:System.Double?displayProperty=nameWithType>|`FLOAT`|  
  
 Istnieje wiele innych mapowaniach numeryczne, możesz wybrać, ale niektóre może spowodować przepełnienie lub dane utraty wyjątki podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
### <a name="decimal-and-money-types"></a>Dziesiętnego i typy pieniędzy  
 Domyślna dokładność programu SQL Server `DECIMAL` typu (18 cyfr dziesiętnych po lewej i prawej stronie przecinka dziesiętnego) jest znacznie mniejsza niż precyzja CLR <xref:System.Decimal?displayProperty=nameWithType> typ, który jest powiązany z, domyślnie. Może to spowodować utratę dokładności podczas zapisywania danych w bazie danych. Jednak po prostu przeciwieństwem może nastąpić, jeśli program SQL Server `DECIMAL` typ jest skonfigurowany z więcej niż 29 cyfr precyzji. Gdy serwer SQL `DECIMAL` typ został skonfigurowany z większą precyzję niż CLR <xref:System.Decimal?displayProperty=nameWithType>, może dojść do utraty precyzji podczas pobierania danych z bazy danych.  
  
 SQL Server `MONEY` i `SMALLMONEY` typy, które również są skojarzone z CLR <xref:System.Decimal?displayProperty=nameWithType> wpisz domyślnie, ma dużo mniejsze dokładności, co może skutkować wyjątki utraty danych lub przepełnienie podczas zapisywania danych w bazie danych.  
  
<a name="TextMapping"></a>   
## <a name="text-and-xml-mapping"></a>Tekst i mapowania XML  
 Dostępne są także wiele oparte na tekście oraz typy XML, które można zamapować za pomocą LINQ to SQL. W poniższej tabeli przedstawiono typy CLR, że O/R Designer i SQLMetal wybrać podczas tworzenia modelu obiektów lub pliku mapowania zewnętrznych, na podstawie Twojej bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez projektanta O/R i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 W następnej tabeli przedstawiono domyślne mapowania typu, używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typy kolumn programu SQL są tworzone do mapowania na typy CLR zdefiniowane w modelu obiektu lub pliku mapowania zewnętrznych.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Implementowanie niestandardowego typu `Parse()` i `ToString()`|`NVARCHAR(MAX)`|  
  
 Istnieje wiele innych oparte na tekście i mapowania XML można wybrać, ale niektóre może spowodować przepełnienie lub dane utraty wyjątki podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
### <a name="xml-types"></a>Typy XML  
 SQL Server `XML` — typ danych jest dostępna, począwszy od programu Microsoft SQL Server 2005. SQL Server można mapować `XML` typ danych ma <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, lub <xref:System.String>. Jeśli kolumna przechowuje fragmenty XML, które nie można odczytać na <xref:System.Xml.Linq.XElement>, kolumna musi być zamapowany na <xref:System.String> w celu uniknięcia błędów czasu wykonywania. Fragmenty XML, które muszą być zamapowane na <xref:System.String> obejmują następujące elementy:  
  
- Sekwencja elementów XML  
  
- Atrybuty  
  
- Publiczne identyfikatory (PI)  
  
- Komentarze  
  
 Mimo że można mapować <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> do programu SQL Server, jak pokazano na [macierzy zachowanie czas uruchomienia mapowania typu](#BehaviorMatrix), <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda nie ma domyślnego programu SQL Server typu mapowania dla tych typów.  
  
### <a name="custom-types"></a>Niestandardowe typy  
 Jeśli klasa implementuje `Parse()` i `ToString()`, obiekt można mapować do dowolnego typu tekstu SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`, `TEXT`, `NTEXT`, `XML`). Obiekt jest przechowywany w bazie danych, wysyłając wartość zwrócona przez obiekt `ToString()` w kolumnie zamapowanego bazy danych. Obiekt jest odtworzone, wywołując `Parse()` na ciąg zwracany przez bazę danych.  
  
> [!NOTE]
>  LINQ do SQL nie obsługuje serializacji przy użyciu <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.  
  
<a name="DateMapping"></a>   
## <a name="date-and-time-mapping"></a>Data i godzina mapowania  
 Za pomocą LINQ to SQL można mapować wielu typów daty i godziny programu SQL Server. W poniższej tabeli przedstawiono typy CLR, że O/R Designer i SQLMetal wybrać podczas tworzenia modelu obiektów lub pliku mapowania zewnętrznych, na podstawie Twojej bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez projektanta O/R i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 W następnej tabeli przedstawiono domyślne mapowania typu, używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typy kolumn programu SQL są tworzone do mapowania na typy CLR zdefiniowane w modelu obiektu lub pliku mapowania zewnętrznych.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Istnieje wiele innych daty i godziny mapowania możesz wybrać, ale niektóre może spowodować przepełnienie lub dane utraty wyjątki podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
> [!NOTE]
>  Typy programu SQL Server `DATETIME2`, `DATETIMEOFFSET`, `DATE`, i `TIME` są dostępne, począwszy od programu Microsoft SQL Server 2008. LINQ do SQL obsługuje mapowanie na te nowe typy, począwszy od .NET Framework w wersji 3.5 z dodatkiem SP1.  
  
### <a name="systemdatetime"></a>System.Datetime  
 Zakres i dokładność CLR <xref:System.DateTime?displayProperty=nameWithType> typu jest większy niż zakres i dokładność, programu SQL Server `DATETIME` typ, który jest domyślnym typem mapowanie <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody. Aby zapobiec powstawaniu wyjątki związane z datami poza zakresem `DATETIME`, użyj `DATETIME2`, która jest dostępna, począwszy od programu Microsoft SQL Server 2008. `DATETIME2` może odnosić się zakres i dokładność CLR <xref:System.DateTime?displayProperty=nameWithType>.  
  
 Daty programu SQL Server nie ma żadnych koncepcji <xref:System.TimeZone>, funkcja, która graficznie jest obsługiwana w środowisku CLR. <xref:System.TimeZone> wartości są zapisywane jako bazy danych bez <xref:System.TimeZone> konwersji, niezależnie od tego, oryginalnym <xref:System.DateTimeKind> informacji. Gdy <xref:System.DateTime> wartości są pobierane z bazy danych, ich wartość jest załadowany, ponieważ jest w <xref:System.DateTime> z <xref:System.DateTimeKind> z <xref:System.DateTimeKind.Unspecified>. Aby uzyskać więcej informacji na temat obsługiwanych <xref:System.DateTime?displayProperty=nameWithType> metod, zobacz [metody System.DateTime](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.TimeSpan  
 Microsoft SQL Server 2008 i .NET Framework 3.5 SP1 pozwalają na mapowanie środowiska CLR <xref:System.TimeSpan?displayProperty=nameWithType> typu do programu SQL Server `TIME` typu. Istnieje jednak duża różnica między zakresu, środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> obsługuje i jakie programu SQL Server `TIME` wpisz obsługuje. Mapowania wartości mniejszej niż 0 lub większa od godziny 23:59:59.9999999 SQL `TIME` spowoduje wyjątki przepełnienia. Aby uzyskać więcej informacji, zobacz [metody System.TimeSpan](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md).  
  
 W programie Microsoft SQL Server 2000 i SQL Server 2005, nie można zamapować pola bazy danych do <xref:System.TimeSpan>. Jednak operacje na <xref:System.TimeSpan> są obsługiwane, ponieważ <xref:System.TimeSpan> wartości mogą być zwracane przez <xref:System.DateTime> odejmowania lub wprowadzane do wyrażenia jako zmienną literału lub powiązanej.  
  
<a name="BinaryMapping"></a>   
## <a name="binary-mapping"></a>Mapowanie binarne  
 Istnieje wiele typów programu SQL Server, które można zamapować na typ CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType>. W poniższej tabeli przedstawiono typy programu SQL Server, które powodują O/R Designer i SQLMetal w celu określenia CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType> typu podczas tworzenia modelu obiektów lub pliku mapowania zewnętrznego na podstawie Twojej bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez projektanta O/R i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)` za pomocą `FILESTREAM` atrybutu|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 W następnej tabeli przedstawiono domyślne mapowania typu, używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typy kolumn programu SQL są tworzone do mapowania na typy CLR zdefiniowane w modelu obiektu lub pliku mapowania zewnętrznych.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Istnieje wiele innych mapowaniach binarne, możesz wybrać, ale niektóre może spowodować przepełnienie lub dane utraty wyjątki podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
### <a name="sql-server-filestream"></a>Program SQL Server FILESTREAM  
 `FILESTREAM` Atrybutu dla `VARBINARY(MAX)` kolumny jest dostępna, począwszy od programu Microsoft SQL Server 2008; można mapować do niego za pomocą LINQ to SQL, począwszy od .NET Framework w wersji 3.5 z dodatkiem SP1.  
  
 Mimo że można mapować `VARBINARY(MAX)` kolumn z `FILESTREAM` atrybutu <xref:System.Data.Linq.Binary> obiektów <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda nie może automatycznie tworzyć kolumny z `FILESTREAM` atrybutu. Aby uzyskać więcej informacji na temat `FILESTREAM`, zobacz [Przegląd FILESTREAM](https://go.microsoft.com/fwlink/?LinkId=115291) w programie Microsoft SQL Server — książki Online.  
  
<a name="BinarySerialization"></a>   
### <a name="binary-serialization"></a>Serializacja binarna  
 Jeśli klasa implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu, może wykonać serializację obiektu dla dowolnego pola binarne, SQL (`BINARY`, `VARBINARY`, `IMAGE`). Obiekt jest serializacji i deserializacji zgodnie z sposób, w jaki <xref:System.Runtime.Serialization.ISerializable> interfejs jest implementowany. Aby uzyskać więcej informacji, zobacz [serializacji binarnej](https://go.microsoft.com/fwlink/?LinkId=115581).  
  
<a name="MiscMapping"></a>   
## <a name="miscellaneous-mapping"></a>Różne mapowania  
 W poniższej tabeli przedstawiono domyślne mapowania typu dla niektórych dodatkowych typów, które nie zostały wymienione. W poniższej tabeli przedstawiono typy CLR, że O/R Designer i SQLMetal wybrać podczas tworzenia modelu obiektów lub pliku mapowania zewnętrznych, na podstawie Twojej bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez projektanta O/R i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 W następnej tabeli przedstawiono domyślne mapowania typu, używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typy kolumn programu SQL są tworzone do mapowania na typy CLR zdefiniowane w modelu obiektu lub pliku mapowania zewnętrznych.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ do SQL nie obsługuje innych mapowania typów dla tych różnych typów.  Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Niezgodność typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)
