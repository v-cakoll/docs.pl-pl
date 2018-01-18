---
title: "Mapowanie typu środowiska CLR SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cc6a3d38b8534c9727562cb3fb82f96fa60db7ec
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sql-clr-type-mapping"></a>Mapowanie typu środowiska CLR SQL
W składniku LINQ to SQL relacyjnej bazy danych w modelu danych mapuje modelu obiektów, które są jest wyrażone w języku programowania wybranych przez użytkownika. Po uruchomieniu aplikacji, LINQ do SQL tłumaczy zapytania języku zintegrowanym w modelu obiektów programu SQL i wysyła je do bazy danych do wykonania. Po powrocie z bazy danych wyników LINQ do SQL tłumaczy wyniki z powrotem do obiektów, które można pracować w języku programowania w języku użytkownika.  
  
 W celu tłumaczenia danych między model obiektów i bazę danych, *mapowanie typu* musi być zdefiniowany. LINQ do SQL używa mapowania typu w celu dopasowania każdego języka wspólnego typu środowiska uruchomieniowego (języka wspólnego CLR) z określonym typem programu SQL Server. Można zdefiniować mapowania typów i inne informacje dotyczące mapowania, takie jak bazy danych struktury i relacji między tabelami, wewnątrz modelu obiektów z mapowaniem, na podstawie atrybutów. Alternatywnie można określić informacje dotyczące mapowania poza model obiektów przy użyciu pliku mapowania zewnętrznych. Aby uzyskać więcej informacji, zobacz [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) i [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 W tym temacie omówiono następujące kwestie:  
  
-   [Domyślne mapowanie typu](#DefaultTypeMapping)  
  
-   [Typ mapowania macierzy zachowania w czasie wykonywania](#BehaviorMatrix)  
  
-   [Zachowanie różnice między CLR i wykonywania instrukcji SQL](#BehaviorDiffs)  
  
-   [Mapowanie wyliczenia](#EnumMapping)  
  
-   [Mapowanie numeryczne](#NumericMapping)  
  
-   [Tekst i mapowanie XML](#TextMapping)  
  
-   [Data i godzina mapowania](#DateMapping)  
  
-   [Mapowanie binarne](#BinaryMapping)  
  
-   [Różne mapowania](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## <a name="default-type-mapping"></a>Domyślne mapowanie typu  
 Można utworzyć modelu obiektu lub plik mapowania zewnętrznych automatycznie Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) lub narzędzie wiersza polecenia SQLMetal. Domyślne mapowania typu dla tych narzędzi zdefiniować, jakie typy CLR zostały wybrane do mapowania kolumn w bazie danych programu SQL Server. Aby uzyskać więcej informacji o korzystaniu z tych narzędzi, zobacz [tworzenia modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md).  
  
 Można również użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metodę w celu utworzenia bazy danych programu SQL Server na podstawie mapowania informacji w pliku mapowania zewnętrznych lub model obiektów. Domyślny typ mapowania <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metody Zdefiniuj typy typu kolumny są tworzone do mapowania do środowiska CLR programu SQL Server w modelu obiektów. Aby uzyskać więcej informacji, zobacz [porady: dynamiczne tworzenie bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>   
## <a name="type-mapping-run-time-behavior-matrix"></a>Typ mapowania macierzy zachowania w czasie wykonywania  
 Poniższy diagram przedstawia oczekiwane zachowanie środowiska wykonawczego mapowań określonego typu, gdy dane są pobierane z lub zapisane w bazie danych. Z wyjątkiem serializacji LINQ do SQL nie obsługuje mapowania między żadnych danych CLR lub SQL Server typy, które nie zostały określone w tej macierzy. Aby uzyskać więcej informacji na temat obsługi serializacji, zobacz [szeregowanie binarne](#BinarySerialization).  
  
> [!NOTE]
>  Niektóre mapowania typów może skutkować wyjątki utrata danych lub przepełnienie podczas tłumaczenia do lub z bazy danych.  
  
### <a name="custom-type-mapping"></a>Mapowanie typu niestandardowego  
 Za pomocą LINQ do SQL, nie jest do domyślne mapowania typu używane przez Projektanta obiektów relacyjnych SQLMetal i <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metody. Można utworzyć mapowania typu niestandardowego, jawnie określając je w pliku DBML. Następnie można użyć tego pliku DBML, aby utworzyć plik kodu i mapowania modelu obiektu. Aby uzyskać więcej informacji, zobacz [mapowanie typu środowiska CLR SQL niestandardowe](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>   
## <a name="behavior-differences-between-clr-and-sql-execution"></a>Zachowanie różnice między CLR i wykonywania instrukcji SQL  
 Z powodu różnic w precision i wykonywania CLR i SQL Server mogą otrzymywać różne wyniki lub wystąpić inaczej w zależności od tego, gdzie można wykonać obliczeń. Obliczenia wykonywane w składniku LINQ kwerendy SQL są faktycznie przetłumaczony na język Transact-SQL i następnie wykonywane w bazie danych programu SQL Server. Wykonane poza LINQ kwerendy SQL obliczenia są wykonywane w kontekście CLR.  
  
 Na przykład poniżej przedstawiono niektóre różnice w zachowaniu między CLR i SQL Server:  
  
-   SQL Server inaczej niż dane typu równoważne zamówień niektórych typów danych w środowisku CLR. Na przykład dane programu SQL Server typu `UNIQUEIDENTIFIER` porządkowania inaczej niż dane typu CLR <xref:System.Guid?displayProperty=nameWithType>.  
  
-   SQL Server obsługuje niektóre operacje na ciągach porównania inaczej niż środowiska CLR. W programie SQL Server działanie porównanie ciągu zależy od ustawień sortowania na serwerze. Aby uzyskać więcej informacji, zobacz [Praca z sortowania](http://go.microsoft.com/fwlink/?LinkId=115330) w programie Microsoft SQL Server — książki Online.  
  
-   SQL Server może zwracać różne wartości dla niektórych funkcji mapowanej niż środowiska CLR. Na przykład równości funkcji różnią się, ponieważ program SQL Server uwzględnia dwa ciągi równe, jeśli tylko różnią się one w końcu spację; Środowisko CLR uważa je, aby nie może być taki sam.  
  
<a name="EnumMapping"></a>   
## <a name="enum-mapping"></a>Mapowanie wyliczenia  
 LINQ do SQL obsługuje mapowania CLR <xref:System.Enum?displayProperty=nameWithType> typu do typów programu SQL Server na dwa sposoby:  
  
-   Mapowanie na typy liczbowe SQL (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)  
  
     Podczas mapowania CLR <xref:System.Enum?displayProperty=nameWithType> typu na typ numeryczny SQL, mapy źródłowej wartość całkowitą typu CLR <xref:System.Enum?displayProperty=nameWithType> wartość kolumny bazy danych programu SQL Server. Na przykład jeśli <xref:System.Enum?displayProperty=nameWithType> o nazwie `DaysOfWeek` zawiera element o nazwie `Tue` z wartością całkowitą podstawowej 3, ten element członkowski mapy bazy danych na wartość 3.  
  
-   Mapowanie do typów tekstu SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)  
  
     Podczas mapowania CLR <xref:System.Enum?displayProperty=nameWithType> typ do typu SQL, wartość bazy danych SQL jest mapowany do nazw środowiska CLR <xref:System.Enum?displayProperty=nameWithType> elementów członkowskich. Na przykład jeśli <xref:System.Enum?displayProperty=nameWithType> o nazwie `DaysOfWeek` zawiera element o nazwie `Tue` z wartością całkowitą podstawowej 3, ten element członkowski mapy do wartości bazy danych `Tue`.  
  
> [!NOTE]
>  Podczas mapowania typów tekstu SQL do CLR <xref:System.Enum?displayProperty=nameWithType>, zawiera tylko nazw <xref:System.Enum> elementów członkowskich w kolumnie SQL zamapowane. Inne wartości nie są obsługiwane w <xref:System.Enum>-zamapować kolumny SQL.  
  
 Narzędzie wiersza polecenia Projektanta obiektów relacyjnych i SQLMetal nie może automatycznie zmapować typu SQL CLR <xref:System.Enum> klasy. To mapowanie muszą jawnie skonfigurować dostosowując za pomocą pliku DBML do użycia przez Projektanta obiektów relacyjnych i SQLMetal. Aby uzyskać więcej informacji o mapowaniu typu niestandardowego, zobacz [niestandardowe mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
 Ponieważ kolumny SQL przeznaczonych do wyliczenia będzie taki sam typ jak innych kolumn liczbowych i tekst; tych narzędzi nie rozpoznaje opcje, a domyślne mapowanie zgodnie z opisem w następujących [liczbowych mapowania](#NumericMapping) i [tekstowego i mapowanie XML](#TextMapping) sekcje. Aby uzyskać więcej informacji na temat generowania kodu przy użyciu pliku DBML, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda tworzy kolumny SQL liczbowego typu CLR mapowania <xref:System.Enum?displayProperty=nameWithType> typu.  
  
<a name="NumericMapping"></a>   
## <a name="numeric-mapping"></a>Mapowanie numeryczne  
 LINQ do SQL umożliwia mapowanie wielu CLR i SQL Server typy liczbowe. W poniższej tabeli przedstawiono typy CLR, że Projektanta obiektów relacyjnych i SQLMetal wybrać podczas tworzenia obiektu modelu lub pliku zewnętrznego mapowania na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez Projektanta obiektów relacyjnych i SQLMetal|  
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
  
 W następnej tabeli przedstawiono domyślne mapowania typ używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typu kolumny SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektów lub zewnętrznego mapowania pliku.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
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
  
 Istnieje wiele innych mapowania liczbowego, możesz wybrać, ale niektóre może spowodować przepełnienie lub danych utraty wyjątków podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
### <a name="decimal-and-money-types"></a>Decimal i pieniądze typów  
 Dokładność domyślnego programu SQL Server `DECIMAL` typu (18 cyfr dziesiętnych po lewej i prawej strony punktu dziesiętnego) jest znacznie mniejszy niż precyzja CLR <!--zz <xref:System.Decima?displayProperty=nameWithType>l --> `Decimal` typu, który wraz z domyślnie. Może to spowodować utratę dokładności podczas zapisywania danych w bazie danych. Jednak tylko przeciwieństwem może nastąpić, jeśli program SQL Server `DECIMAL` typ jest skonfigurowany z więcej niż 29 cyfr precyzji. Gdy serwer SQL `DECIMAL` o dokładności większej niż środowiska CLR został skonfigurowany typu <xref:System.Decimal?displayProperty=nameWithType>, może wystąpić utrata dokładności, podczas pobierania danych z bazy danych.  
  
 SQL Server `MONEY` i `SMALLMONEY` typy, które są również łączyć się z aparatu CLR <xref:System.Decimal?displayProperty=nameWithType> wpisz domyślnie, mają dużo mniejsze dokładności, co może spowodować wyjątki utrata danych lub przepełnienie podczas zapisywania danych w bazie danych.  
  
<a name="TextMapping"></a>   
## <a name="text-and-xml-mapping"></a>Tekst i mapowanie XML  
 Istnieją także wiele opartego na tekście oraz typów XML, mapowane za pomocą LINQ do SQL. W poniższej tabeli przedstawiono typy CLR, że Projektanta obiektów relacyjnych i SQLMetal wybrać podczas tworzenia obiektu modelu lub pliku zewnętrznego mapowania na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez Projektanta obiektów relacyjnych i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 W następnej tabeli przedstawiono domyślne mapowania typ używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typu kolumny SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektów lub zewnętrznego mapowania pliku.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Implementacja typu niestandardowego `Parse()` i`ToString()`|`NVARCHAR(MAX)`|  
  
 Istnieje wiele innych tekstowych i mapowania XML można, ale niektóre może spowodować przepełnienie lub danych utraty wyjątków podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
### <a name="xml-types"></a>Typy XML  
 SQL Server `XML` — typ danych jest dostępne w programie Microsoft SQL Server 2005. SQL Server można mapować `XML` typ danych <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, lub <xref:System.String>. Jeśli kolumna przechowuje fragmenty XML, których nie można odczytać w <xref:System.Xml.Linq.XElement>, kolumna musi być zamapowany na <xref:System.String> w celu uniknięcia błędów czasu wykonywania. Fragmenty XML, które muszą być zamapowane na <xref:System.String> są następujące:  
  
-   Kolejność elementów XML  
  
-   Atrybuty  
  
-   Identyfikatory publiczny (PI)  
  
-   Komentarze  
  
 Mimo że można mapować <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> do programu SQL Server, jak pokazano w [macierzy zachowanie czas uruchomienia mapowania typu](#BehaviorMatrix), <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> — metoda nie ma domyślnego programu SQL Server typu mapowania dla tych typów.  
  
### <a name="custom-types"></a>Niestandardowe typy  
 Jeśli klasa implementuje `Parse()` i `ToString()`, możesz mapować obiektu do dowolnego typu tekstu SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`, `TEXT`, `NTEXT`, `XML`). Obiekt jest przechowywany w bazie danych, wysyłając wartość zwrócona przez `ToString()` do kolumny zamapowanej bazy danych. Obiekt jest odtworzone wywołując `Parse()` na ciąg zwrócony przez bazę danych.  
  
> [!NOTE]
>  LINQ do SQL nie obsługuje serializacji przy użyciu <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.  
  
<a name="DateMapping"></a>   
## <a name="date-and-time-mapping"></a>Data i godzina mapowania  
 Za pomocą LINQ do SQL możesz mapować wielu typów programu SQL Server Data i godzina. W poniższej tabeli przedstawiono typy CLR, że Projektanta obiektów relacyjnych i SQLMetal wybrać podczas tworzenia obiektu modelu lub pliku zewnętrznego mapowania na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez Projektanta obiektów relacyjnych i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 W następnej tabeli przedstawiono domyślne mapowania typ używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typu kolumny SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektów lub zewnętrznego mapowania pliku.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Istnieje wiele innych Data i godzina mapowania, możesz wybrać, ale niektóre może spowodować przepełnienie lub danych utraty wyjątków podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
> [!NOTE]
>  Typy programu SQL Server `DATETIME2`, `DATETIMEOFFSET`, `DATE`, i `TIME` są dostępne w programie Microsoft SQL Server 2008. LINQ do SQL obsługuje mapowania do tych nowych typów w programie .NET Framework w wersji 3.5 z dodatkiem SP1.  
  
### <a name="systemdatetime"></a>System.Datetime  
 Zakres i dokładność środowiska CLR <xref:System.DateTime?displayProperty=nameWithType> typu jest większa od zakresu i dokładność programu SQL Server `DATETIME` typ, który jest domyślnym typem mapowania dla <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody. Aby uniknąć wyjątki związane z dat poza zakresem `DATETIME`, użyj `DATETIME2`, która jest dostępnych w programie Microsoft SQL Server 2008. `DATETIME2`można dopasować zakresu i dokładność CLR <xref:System.DateTime?displayProperty=nameWithType>.  
  
 Dat programu SQL Server nie ma żadnych koncepcji <xref:System.TimeZone>, funkcja, która Bogato jest obsługiwana w środowisku CLR. <xref:System.TimeZone>wartości są zapisywane jako bazy danych bez <xref:System.TimeZone> konwersji, niezależnie od oryginalnej <xref:System.DateTimeKind> informacji. Gdy <xref:System.DateTime> wartości są pobierane z bazy danych, ich wartości został załadowany, ponieważ jest do <xref:System.DateTime> z <xref:System.DateTimeKind> z <xref:System.DateTimeKind.Unspecified>. Aby uzyskać więcej informacji na temat obsługiwanych <xref:System.DateTime?displayProperty=nameWithType> metod, zobacz [metody System.DateTime](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.TimeSpan  
 Microsoft SQL Server 2008 i .NET Framework 3.5 SP1 umożliwiają mapowanie CLR <xref:System.TimeSpan?displayProperty=nameWithType> typu z programem SQL Server `TIME` typu. Istnieje jednak duża różnica zakres który CLR <xref:System.TimeSpan?displayProperty=nameWithType> obsługuje i jakie programu SQL Server `TIME` wpisz obsługuje. Mapowanie wartości mniejszej niż 0 lub większą niż godziny 23:59:59.9999999 SQL `TIME` spowoduje przepełnienie wyjątków. Aby uzyskać więcej informacji, zobacz [metody System.TimeSpan](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md).  
  
 W programie Microsoft SQL Server 2000 i SQL Server 2005, nie można mapować pola bazy danych do <xref:System.TimeSpan>. Jednak operacje na <xref:System.TimeSpan> są obsługiwane, ponieważ <xref:System.TimeSpan> może zwracać wartości <xref:System.DateTime> odejmowania lub wprowadzane jako zmienną literału lub powiązane wyrażenia.  
  
<a name="BinaryMapping"></a>   
## <a name="binary-mapping"></a>Mapowanie binarne  
 Istnieje wiele typów programu SQL Server, które można zamapować na typ CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType>. W poniższej tabeli przedstawiono typy programu SQL Server, które powodują Projektanta obiektów relacyjnych i SQLMetal zdefiniować CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType> wpisz podczas tworzenia modelu obiektu lub plik mapowania zewnętrznych na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez Projektanta obiektów relacyjnych i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`z `FILESTREAM` atrybutu|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 W następnej tabeli przedstawiono domyślne mapowania typ używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typu kolumny SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektów lub zewnętrznego mapowania pliku.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Istnieje wiele innych mapowania binarnego, możesz wybrać, ale niektóre może spowodować przepełnienie lub danych utraty wyjątków podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
### <a name="sql-server-filestream"></a>Serwer SQL FILESTREAM  
 `FILESTREAM` Atrybutu dla `VARBINARY(MAX)` kolumn jest dostępnych w programie Microsoft SQL Server 2008; można mapować do niego za pomocą LINQ do SQL w programie .NET Framework w wersji 3.5 z dodatkiem SP1.  
  
 Mimo że można mapować `VARBINARY(MAX)` kolumny z `FILESTREAM` atrybutu <xref:System.Data.Linq.Binary> obiektów, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> — metoda nie może automatycznie utworzyć kolumny z `FILESTREAM` atrybutu. Aby uzyskać więcej informacji na temat `FILESTREAM`, zobacz [omówienie FILESTREAM](http://go.microsoft.com/fwlink/?LinkId=115291) w programie Microsoft SQL Server — książki Online.  
  
<a name="BinarySerialization"></a>   
### <a name="binary-serialization"></a>Serializacja binarna  
 Jeśli klasa implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu, może wykonać serializację obiektu do dowolnego pola binarne SQL (`BINARY`, `VARBINARY`, `IMAGE`). Obiekt jest serializacji i deserializacji zgodnie z jak <xref:System.Runtime.Serialization.ISerializable> interfejs jest wdrażany. Aby uzyskać więcej informacji, zobacz [szeregowanie binarne](http://go.microsoft.com/fwlink/?LinkId=115581).  
  
<a name="MiscMapping"></a>   
## <a name="miscellaneous-mapping"></a>Różne mapowania  
 W poniższej tabeli przedstawiono domyślne mapowania typu dla niektórych różnych typów, które nie zostały wymienione. W poniższej tabeli przedstawiono typy CLR, że Projektanta obiektów relacyjnych i SQLMetal wybrać podczas tworzenia obiektu modelu lub pliku zewnętrznego mapowania na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu środowiska CLR używane przez Projektanta obiektów relacyjnych i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 W następnej tabeli przedstawiono domyślne mapowania typ używany przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę, aby zdefiniować typu kolumny SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektów lub zewnętrznego mapowania pliku.  
  
|Typ CLR|Typ serwera SQL domyślne używane przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ do SQL nie obsługuje innych mapowanie typu dla tych różnych typów.  Aby uzyskać więcej informacji, zobacz [Typ mapowania Uruchom czas zachowania macierzy](#BehaviorMatrix).  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [Niezgodność typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)
