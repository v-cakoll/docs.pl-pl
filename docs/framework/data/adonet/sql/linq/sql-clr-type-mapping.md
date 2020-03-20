---
title: Mapowania typów środowiska SQL-CLR
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 336732e0fe7ca8955702d325309db6a8e61b1722
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174540"
---
# <a name="sql-clr-type-mapping"></a>Mapowania typów środowiska SQL-CLR
W LINQ do SQL model danych relacyjnej bazy danych mapuje do modelu obiektu, który jest wyrażony w wybranym języku programowania. Po uruchomieniu aplikacji LINQ do SQL tłumaczy zapytania zintegrowane z językiem w modelu obiektu na język SQL i wysyła je do bazy danych do wykonania. Gdy baza danych zwraca wyniki, LINQ do języka SQL tłumaczy wyniki z powrotem do obiektów, które można pracować z w języku programowania.  
  
 Aby przetłumaczyć dane między modelem obiektu a bazą danych, należy zdefiniować *mapowanie typu.* LINQ do SQL używa mapowania typu, aby dopasować każdy typ wspólnego środowiska wykonawczego języka (CLR) do określonego typu programu SQL Server. Mapowania typów i inne informacje o mapowaniu, takie jak struktura bazy danych i relacje tabel, można zdefiniować wewnątrz modelu obiektu za pomocą mapowania opartego na atrybutach. Alternatywnie można określić informacje o mapowaniu poza modelem obiektu za pomocą zewnętrznego pliku mapowania. Aby uzyskać więcej informacji, zobacz [Mapowanie oparte na atrybutach](attribute-based-mapping.md) i [Mapowanie zewnętrzne](external-mapping.md).  
  
 W tym temacie omówiono następujące kwestie:  
  
- [Domyślne mapowanie typów](#DefaultTypeMapping)  
  
- [Macierz zachowania czasu wykonywania mapowania typu](#BehaviorMatrix)  
  
- [Różnice w zachowaniu między programem CLR a wykonywaniem SQL](#BehaviorDiffs)  
  
- [Mapowanie wyliczenia](#EnumMapping)  
  
- [Mapowanie numeryczne](#NumericMapping)  
  
- [Mapowanie tekstu i XML](#TextMapping)  
  
- [Mapowanie daty i godziny](#DateMapping)  
  
- [Mapowanie binarne](#BinaryMapping)  
  
- [Różne mapowanie](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>
## <a name="default-type-mapping"></a>Domyślne mapowanie typów  
 Model obiektu lub plik mapowania zewnętrznego można utworzyć automatycznie za pomocą projektanta relacyjnego obiektu (projektanta O/R) lub narzędzia wiersza polecenia SQLMetal. Domyślne mapowania typów dla tych narzędzi określają, które typy CLR są wybierane do mapowania na kolumny wewnątrz bazy danych programu SQL Server. Aby uzyskać więcej informacji na temat korzystania z tych narzędzi, zobacz [Tworzenie modelu obiektu](creating-the-object-model.md).  
  
 Można również użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A> tej metody do utworzenia bazy danych programu SQL Server na podstawie informacji o mapowaniu w modelu obiektu lub pliku mapowania zewnętrznego. Domyślne mapowania typów <xref:System.Data.Linq.DataContext.CreateDatabase%2A> dla metody określają, który typ kolumn programu SQL Server są tworzone w celu mapowania typów CLR w modelu obiektu. Aby uzyskać więcej informacji, zobacz [Jak: Dynamicznie tworzyć bazę danych](how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>
## <a name="type-mapping-run-time-behavior-matrix"></a>Macierz zachowania czasu wykonywania mapowania typu  
 Na poniższym diagramie przedstawiono oczekiwane zachowanie w czasie wykonywania mapowań określonego typu, gdy dane są pobierane z bazy danych lub zapisywane w niej. Z wyjątkiem serializacji LINQ do SQL nie obsługuje mapowania między typami danych CLR lub SQL Server, które nie są określone w tej macierzy. Aby uzyskać więcej informacji na temat obsługi serializacji, zobacz [Serializacja binarna](#BinarySerialization).  

![Tabela mapowania typów danych SQL Server do SQL CLR](./media/sql-clr-type-mapping.png)

> [!NOTE]
> Niektóre mapowania typów może spowodować przepełnienie lub wyjątki utraty danych podczas tłumaczenia do lub z bazy danych.  
  
### <a name="custom-type-mapping"></a>Niestandardowe mapowanie typów  
 Z LINQ do SQL, nie są ograniczone do domyślnych mapowań typu używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A> Projektant O/R, SQLMetal i metody. Mapowania typów niestandardowych można tworzyć, wyraźnie określając je w pliku DBML. Następnie można użyć tego pliku DBML, aby utworzyć kod modelu obiektu i plik mapowania. Aby uzyskać więcej informacji, zobacz [Sql-CLR Niestandardowe mapowania typów](sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>
## <a name="behavior-differences-between-clr-and-sql-execution"></a>Różnice w zachowaniu między programem CLR a wykonywaniem SQL  
 Ze względu na różnice w precyzji i wykonaniu między CLR i SQL Server, mogą pojawić się różne wyniki lub wystąpić różne zachowanie w zależności od tego, gdzie można wykonać obliczenia. Obliczenia wykonywane w LINQ na zapytania SQL są faktycznie tłumaczone na transact-SQL, a następnie wykonywane w bazie danych programu SQL Server. Obliczenia wykonywane poza LINQ do zapytań SQL są wykonywane w kontekście CLR.  
  
 Na przykład poniżej przedstawiono pewne różnice w zachowaniu między programem CLR i SQL Server:  
  
- SQL Server zamawia niektóre typy danych inaczej niż dane równoważnego typu w programie CLR. Na przykład dane typu `UNIQUEIDENTIFIER` programu SQL Server są uporządkowane <xref:System.Guid?displayProperty=nameWithType>inaczej niż dane typu CLR .  
  
- SQL Server obsługuje niektóre operacje porównywania ciągów inaczej niż CLR. W programie SQL Server zachowanie porównywania ciągów znaków zależy od ustawień sortowania na serwerze. Aby uzyskać więcej informacji, zobacz [Praca z sortowania](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms187582(v=sql.105)) w usłudze Microsoft SQL Server Books Online.  
  
- SQL Server może zwracać różne wartości dla niektórych mapowanych funkcji niż CLR. Na przykład funkcje równości będą się różnić, ponieważ SQL Server uważa, że dwa ciągi są równe, jeśli różnią się tylko w końcowych odstępu; mając na uwadze, że CLR uważa je za nie równe.  
  
<a name="EnumMapping"></a>
## <a name="enum-mapping"></a>Mapowanie wyliczenia  
 LINQ do SQL obsługuje <xref:System.Enum?displayProperty=nameWithType> mapowanie typu CLR do typów programu SQL Server na dwa sposoby:  
  
- Mapowanie na typy`TINYINT` `SMALLINT`liczbowe SQL ( , , `INT`, `BIGINT`)  
  
     Podczas mapowania typu <xref:System.Enum?displayProperty=nameWithType> CLR na typ liczbowy SQL, mapowanie podstawowej <xref:System.Enum?displayProperty=nameWithType> wartości całkowitej CLR do wartości kolumny bazy danych programu SQL Server. Na przykład jeśli <xref:System.Enum?displayProperty=nameWithType> `DaysOfWeek` nazwa zawiera `Tue` element członkowski o nazwie o podstawowej wartości całkowitej 3, ten element członkowski mapuje do wartości bazy danych 3.  
  
- Mapowanie na typy `NCHAR` `VARCHAR`tekstu `NVARCHAR`SQL (`CHAR`, , , )  
  
     Podczas mapowania typu <xref:System.Enum?displayProperty=nameWithType> CLR na typ tekstu SQL wartość bazy danych SQL jest <xref:System.Enum?displayProperty=nameWithType> mapowana na nazwy elementów członkowskich CLR. Na przykład jeśli <xref:System.Enum?displayProperty=nameWithType> `DaysOfWeek` nazwa zawiera `Tue` element członkowski o nazwie o podstawowej wartości całkowitej `Tue`3, ten element członkowski mapuje do wartości bazy danych .  
  
> [!NOTE]
> Podczas mapowania typów tekstu <xref:System.Enum?displayProperty=nameWithType>SQL do CLR <xref:System.Enum> , należy podać tylko nazwy elementów członkowskich w mapowane kolumny SQL. Inne wartości nie są <xref:System.Enum>obsługiwane w kolumnie -mapowane SQL.  
  
 Narzędzie wiersza polecenia O/R Designer i SQLMetal nie może automatycznie <xref:System.Enum> mapować typu SQL na klasę CLR. Należy jawnie skonfigurować to mapowanie, dostosowując plik DBML do użytku przez Projektanta O/R i SQLMetal. Aby uzyskać więcej informacji na temat mapowania typów niestandardowych, zobacz [Mapowania typów niestandardowych SQL-CLR](sql-clr-custom-type-mappings.md).  
  
 Ponieważ kolumna SQL przeznaczona do wyliczenia będzie tego samego typu co inne kolumny numeryczne i tekstowe; te narzędzia nie rozpoznają intencji i domyślnie mapowania, jak opisano w następujących [mapowania numerycznych](#NumericMapping) i [tekstu i mapowania XML](#TextMapping) sekcje. Aby uzyskać więcej informacji na temat generowania kodu za pomocą pliku DBML, zobacz [Generowanie kodu w LINQ do SQL](code-generation-in-linq-to-sql.md).  
  
 Metoda <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> tworzy kolumnę SQL typu numerycznego do <xref:System.Enum?displayProperty=nameWithType> mapowania typu CLR.  
  
<a name="NumericMapping"></a>
## <a name="numeric-mapping"></a>Mapowanie numeryczne  
 LINQ do SQL umożliwia mapowanie wielu typów numerycznych CLR i SQL Server. W poniższej tabeli przedstawiono typy CLR, które O/R Designer i SQLMetal wybrać podczas tworzenia modelu obiektu lub pliku mapowania zewnętrznego na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu CLR używane przez projektanta o/r i SQLMetal|  
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
  
 Następna tabela przedstawia domyślne mapowania typów używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę definiowania, który typ kolumn SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektu lub pliku mapowania zewnętrznego.  
  
|Typ CLR|Domyślny typ serwera SQL używany przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
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
  
 Istnieje wiele innych mapowań liczbowych, które można wybrać, ale niektóre mogą spowodować przepełnienie lub wyjątki utraty danych podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [macierz zachowania czasu wykonywania mapowania typów](#BehaviorMatrix).  
  
### <a name="decimal-and-money-types"></a>Typy dziesiętne i pieniężne  
 Domyślna precyzja `DECIMAL` typu PROGRAMU SQL Server (18 cyfr dziesiętnych po lewej i prawej stronie przecinka <xref:System.Decimal?displayProperty=nameWithType> dziesiętnego) jest znacznie mniejsza niż dokładność typu CLR, z którą jest domyślnie sparowany. Może to spowodować utratę precyzji podczas zapisywania danych w bazie danych. Jednak wręcz przeciwnie może się zdarzyć, jeśli typ programu SQL Server `DECIMAL` jest skonfigurowany z większą niż 29 cyfr precyzji. Jeśli typ `DECIMAL` programu SQL Server został skonfigurowany z <xref:System.Decimal?displayProperty=nameWithType>większą precyzją niż CLR, podczas pobierania danych z bazy danych może wystąpić utrata precyzji.  
  
 SQL Server `MONEY` `SMALLMONEY` i typy, które są również <xref:System.Decimal?displayProperty=nameWithType> sparowane z typem CLR domyślnie mają znacznie mniejszą precyzję, co może spowodować przepełnienie lub wyjątki utraty danych podczas zapisywania danych w bazie danych.  
  
<a name="TextMapping"></a>
## <a name="text-and-xml-mapping"></a>Mapowanie tekstu i XML  
 Istnieje również wiele typów tekstowych i XML, które można mapować za pomocą LINQ do SQL. W poniższej tabeli przedstawiono typy CLR, które O/R Designer i SQLMetal wybrać podczas tworzenia modelu obiektu lub pliku mapowania zewnętrznego na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu CLR używane przez projektanta o/r i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 Następna tabela przedstawia domyślne mapowania typów używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę definiowania, który typ kolumn SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektu lub pliku mapowania zewnętrznego.  
  
|Typ CLR|Domyślny typ serwera SQL używany przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Niestandardowe implementowanie `Parse()` typu i`ToString()`|`NVARCHAR(MAX)`|  
  
 Istnieje wiele innych mapowań tekstowych i XML, które można wybrać, ale niektóre mogą spowodować przepełnienie lub wyjątki utraty danych podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [macierz zachowania czasu wykonywania mapowania typów](#BehaviorMatrix).  
  
### <a name="xml-types"></a>Typy XML  
 Typ danych `XML` programu SQL Server jest dostępny od programu Microsoft SQL Server 2005. Typ danych programu `XML` SQL Server <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>można <xref:System.String>mapować na , lub . Jeśli kolumna przechowuje fragmenty XML, które nie mogą być odczytane do <xref:System.Xml.Linq.XElement>kolumny muszą być mapowane, aby <xref:System.String> uniknąć błędów w czasie wykonywania. Fragmenty XML, które muszą <xref:System.String> być mapowane w celu uwzględnienia następujących:  
  
- Sekwencja elementów XML  
  
- Atrybuty  
  
- Identyfikatory publiczne (PI)  
  
- Komentarze  
  
 Chociaż można <xref:System.Xml.Linq.XElement> mapować i <xref:System.Xml.Linq.XDocument> do programu SQL Server, jak <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> pokazano w [macierzy zachowania czasu wykonywania mapowania typów,](#BehaviorMatrix)metoda nie ma domyślnego mapowania typu programu SQL Server dla tych typów.  
  
### <a name="custom-types"></a>Typy niestandardowe  
 Jeśli klasa `Parse()` implementuje `ToString()`i , można mapować obiekt`CHAR`na `NCHAR` `VARCHAR`dowolny `NVARCHAR` `TEXT`typ `NTEXT`tekstu SQL ( , , , , , , , . `XML` Obiekt jest przechowywany w bazie danych, `ToString()` wysyłając wartość zwróconą przez do kolumny mapowanej bazy danych. Obiekt jest rekonstruowany `Parse()` przez wywołanie ciągu zwróconego przez bazę danych.  
  
> [!NOTE]
> LINQ do SQL nie obsługuje <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>serializacji przy użyciu .  
  
<a name="DateMapping"></a>
## <a name="date-and-time-mapping"></a>Mapowanie daty i godziny  
 Z LINQ do SQL, można mapować wiele typów daty i godziny programu SQL Server. W poniższej tabeli przedstawiono typy CLR, które O/R Designer i SQLMetal wybrać podczas tworzenia modelu obiektu lub pliku mapowania zewnętrznego na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu CLR używane przez projektanta o/r i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 Następna tabela przedstawia domyślne mapowania typów używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę definiowania, który typ kolumn SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektu lub pliku mapowania zewnętrznego.  
  
|Typ CLR|Domyślny typ serwera SQL używany przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Istnieje wiele innych mapowań daty i godziny, które można wybrać, ale niektóre mogą spowodować przepełnienie lub wyjątki utraty danych podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [macierz zachowania czasu wykonywania mapowania typów](#BehaviorMatrix).  
  
> [!NOTE]
> Sql Server `DATETIME2`typy `DATE`, `TIME` `DATETIMEOFFSET`, i są dostępne począwszy od programu Microsoft SQL Server 2008. LINQ do SQL obsługuje mapowanie do tych nowych typów, począwszy od .NET Framework w wersji 3.5 SP1.  
  
### <a name="systemdatetime"></a>System.datetime  
 Zakres i precyzja typu <xref:System.DateTime?displayProperty=nameWithType> CLR jest większa niż zakres `DATETIME` i precyzja typu PROGRAMU SQL <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Server, który jest domyślnym mapowaniem typu dla metody. Aby uniknąć wyjątków związanych z `DATETIME`datami `DATETIME2`spoza zakresu programu , use , który jest dostępny począwszy od programu Microsoft SQL Server 2008. `DATETIME2`może odpowiadać zakresowi i <xref:System.DateTime?displayProperty=nameWithType>precyzji clr .  
  
 Daty programu SQL <xref:System.TimeZone>Server nie mają pojęcia , funkcja, która jest bogato obsługiwane w programie CLR. <xref:System.TimeZone>wartości są zapisywane w <xref:System.TimeZone> bazie danych bez konwersji, niezależnie od oryginalnych <xref:System.DateTimeKind> informacji. Gdy <xref:System.DateTime> wartości są pobierane z bazy danych, ich <xref:System.DateTime> wartość <xref:System.DateTimeKind> <xref:System.DateTimeKind.Unspecified>jest ładowana, jak jest do a z . Aby uzyskać więcej <xref:System.DateTime?displayProperty=nameWithType> informacji na temat obsługiwanych metod, zobacz [System.DateTime Methods](system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.timespan  
 Program Microsoft SQL Server 2008 i dodatek SP1 programu .NET <xref:System.TimeSpan?displayProperty=nameWithType> Framework 3.5 umożliwiają mapowanie typu CLR na typ programu SQL Server. `TIME` Istnieje jednak duża różnica między zakresem, <xref:System.TimeSpan?displayProperty=nameWithType> który obsługuje program `TIME` CLR, a tym, co obsługuje typ programu SQL Server. Mapowanie wartości mniej niż 0 lub większe niż 23:59:59.9999999 godzin do SQL `TIME` spowoduje przepełnienie wyjątków. Aby uzyskać więcej informacji, zobacz [System.TimeSpan Methods](system-timespan-methods.md).  
  
 W programach Microsoft SQL Server 2000 i SQL Server 2005 nie można mapować pól bazy danych na <xref:System.TimeSpan>program . Jednak operacje <xref:System.TimeSpan> na są <xref:System.TimeSpan> obsługiwane, ponieważ <xref:System.DateTime> wartości mogą być zwracane z odejmowania lub wprowadzone do wyrażenia jako zmiennej literału lub powiązanej.  
  
<a name="BinaryMapping"></a>
## <a name="binary-mapping"></a>Mapowanie binarne  
 Istnieje wiele typów programu SQL Server, które <xref:System.Data.Linq.Binary?displayProperty=nameWithType>można mapować na typ CLR . W poniższej tabeli przedstawiono typy programu SQL Server, które <xref:System.Data.Linq.Binary?displayProperty=nameWithType> powodują, że projektant O/R i SQLMetal definiują typ CLR podczas tworzenia modelu obiektu lub pliku mapowania zewnętrznego na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu CLR używane przez projektanta o/r i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`z `FILESTREAM` atrybutem|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 Następna tabela przedstawia domyślne mapowania typów używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę definiowania, który typ kolumn SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektu lub pliku mapowania zewnętrznego.  
  
|Typ CLR|Domyślny typ serwera SQL używany przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Istnieje wiele innych mapowań binarnych, które można wybrać, ale niektóre mogą spowodować przepełnienie lub wyjątki utraty danych podczas tłumaczenia do lub z bazy danych. Aby uzyskać więcej informacji, zobacz [macierz zachowania czasu wykonywania mapowania typów](#BehaviorMatrix).  
  
### <a name="sql-server-filestream"></a>STRUMIEŃ PLIKÓW PROGRAMU SQL Server  
 Atrybut `FILESTREAM` dla `VARBINARY(MAX)` kolumn jest dostępny począwszy od programu Microsoft SQL Server 2008; można mapować do niego z LINQ do SQL, począwszy od .NET Framework w wersji 3.5 SP1.  
  
 Chociaż można `VARBINARY(MAX)` mapować kolumny `FILESTREAM` z <xref:System.Data.Linq.Binary> atrybutem <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> do obiektów, metoda nie jest `FILESTREAM` w stanie automatycznie tworzyć kolumny z atrybutem. Aby uzyskać `FILESTREAM`więcej informacji na temat , zobacz [FILESTREAM Overview](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb933993(v=sql.105)).  
  
<a name="BinarySerialization"></a>
### <a name="binary-serialization"></a>Serializacja binarna  
 Jeśli klasa implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs, można serializować obiekt do`BINARY`dowolnego `VARBINARY` `IMAGE`pola binarnego SQL ( , , ). Obiekt jest serializowany i deserializowany zgodnie z tym, <xref:System.Runtime.Serialization.ISerializable> jak interfejs jest implementowany. Aby uzyskać więcej informacji, zobacz [Serializacja binarna](../../../../../standard/serialization/binary-serialization.md).
  
<a name="MiscMapping"></a>
## <a name="miscellaneous-mapping"></a>Różne mapowanie  
 W poniższej tabeli przedstawiono domyślne mapowania typów dla niektórych typów różnych, które nie zostały jeszcze wymienione. W poniższej tabeli przedstawiono typy CLR, które O/R Designer i SQLMetal wybrać podczas tworzenia modelu obiektu lub pliku mapowania zewnętrznego na podstawie bazy danych.  
  
|Typ serwera SQL|Domyślne mapowanie typu CLR używane przez projektanta o/r i SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 Następna tabela przedstawia domyślne mapowania typów używane przez <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodę definiowania, który typ kolumn SQL są tworzone do mapowania typów CLR zdefiniowanych w modelu obiektu lub pliku mapowania zewnętrznego.  
  
|Typ CLR|Domyślny typ serwera SQL używany przez<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ do SQL nie obsługuje żadnych innych mapowań typu dla tych typów różnych.  Aby uzyskać więcej informacji, zobacz [macierz zachowania czasu wykonywania mapowania typów](#BehaviorMatrix).  
  
## <a name="see-also"></a>Zobacz też

- [Mapowanie oparte na atrybutach](attribute-based-mapping.md)
- [Mapowanie zewnętrzne](external-mapping.md)
- [Typy danych i funkcje](data-types-and-functions.md)
- [Niezgodność typu SQL CLR](sql-clr-type-mismatches.md)
