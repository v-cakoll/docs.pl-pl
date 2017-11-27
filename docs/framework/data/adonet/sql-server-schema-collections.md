---
title: "Kolekcje schematów serwera SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c2f03065ee6f1292f72a33a72b1d43b1fed0c8f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-schema-collections"></a>Kolekcje schematów serwera SQL
Dostawcy danych programu Microsoft .NET Framework dla programu SQL Server obsługuje kolekcje schematów dodatkowe, oprócz typowych kolekcje schematów. Kolekcje schematów nieco różnią się zależnie od wersji programu SQL Server są używane. Ustalenie listy kolekcji schematu obsługiwanych wywołać **GetSchema** metody bez argumentów lub nazwą kolekcji schematów "MetaDataCollections". Spowoduje to zwrócenie <xref:System.Data.DataTable> z listą kolekcji obsługiwanych schematu, liczba ograniczeń obsługiwanych przez każdy z nich i części identyfikatora, które korzystają z.  
  
## <a name="databases"></a>Bazy danych  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|nazwa_bazy_danych|String|Nazwa bazy danych.|  
|DBID|Int16|Identyfikator bazy danych.|  
|create_date|DataGodzina|Data utworzenia bazy danych.|  
  
## <a name="foreign-keys"></a>Klucze obce  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|String|Należy katalogu ograniczenia.|  
|CONSTRAINT_SCHEMA|String|Schemat, który zawiera ograniczenie.|  
|CONSTRAINT_NAME|String|Nazwa.|  
|TABLE_CATALOG|String|Ograniczenie Nazwa tabeli jest częścią.|  
|TABLE_SCHEMA|String|Czy tabela zawiera schemat.|  
|TABLE_NAME|String|Nazwa tabeli|  
|CONSTRAINT_TYPE|String|Typ ograniczenia. Dozwolone jest tylko "FOREIGN KEY".|  
|IS_DEFERRABLE|String|Określa, czy ograniczenie jest deferrable. Nie zwraca.|  
|INITIALLY_DEFERRED|String|Określa, czy ograniczenie jest początkowo deferrable. Nie zwraca.|  
  
## <a name="indexes"></a>Indeksy  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, który należy do indeksu.|  
|constraint_schema|String|Schemat, który zawiera indeks.|  
|constraint_name|String|Nazwa indeksu.|  
|table_catalog|String|Nazwa tabeli indeksu jest skojarzony.|  
|table_schema|String|Schemat, który zawiera tabelę indeks jest skojarzony.|  
|nazwa_tabeli|String|Nazwa tabeli.|  
|index_name|String|Nazwa indeksu.|  
  
### <a name="indexes-sql-server-2008"></a>Indeksy (SQL Server 2008)  
 Począwszy od programu .NET Framework w wersji 3.5 z dodatkiem SP1 i program SQL Server 2008, następujące kolumny zostały dodane do kolekcji schematu indeksów do obsługi nowych typów przestrzennych, filestream i kolumn rozrzedzonych. Te kolumny nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|type_desc|String|Typ indeksu będzie jedną z następujących czynności:<br /><br /> -HEAP<br />— W KLASTRZE<br />-NIEKLASTROWANY<br />-XML<br />-PRZESTRZENNYCH|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, który należy do indeksu.|  
|constraint_schema|String|Schemat, który zawiera indeks.|  
|constraint_name|String|Nazwa indeksu.|  
|table_catalog|String|Nazwa tabeli indeksu jest skojarzony.|  
|table_schema|String|Schemat, który zawiera tabelę indeks jest skojarzony.|  
|nazwa_tabeli|String|Nazwa tabeli.|  
|column_name|String|Nazwa kolumny indeks jest skojarzony.|  
|ordinal_position|Int32|Pozycja liczby porządkowej kolumny.|  
|Właściwość KeyType|Byte|Typ obiektu.|  
|index_name|String|Nazwa indeksu.|  
  
## <a name="procedures"></a>Procedury  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nazwa określonego katalogu.|  
|SPECIFIC_SCHEMA|String|Nazwa określonego schematu.|  
|SPECIFIC_NAME|String|Nazwa określonego katalogu.|  
|ROUTINE_CATALOG|String|Należy katalogu procedury składowanej.|  
|ROUTINE_SCHEMA|String|Schemat, który zawiera procedury składowanej.|  
|ROUTINE_NAME|String|Nazwa procedury składowanej.|  
|ROUTINE_TYPE|String|Zwraca procedury procedur składowanych i funkcji dla funkcji.|  
|UTWORZONE|DataGodzina|Godzina utworzenia procedury.|  
|LAST_ALTERED|DataGodzina|Czas ostatniej modyfikacji procedury.|  
  
## <a name="procedure-parameters"></a>Parametry procedur  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nazwa procedury, dla której jest to parametr w katalogu.|  
|SPECIFIC_SCHEMA|String|Schemat, który zawiera procedury, dla którego ten parametr jest częścią.|  
|SPECIFIC_NAME|String|Nazwa procedury, dla którego ten parametr jest częścią.|  
|ORDINAL_POSITION|Int32|{Numer porządkowy pozycja parametru rozpoczyna się od 1. Wartość zwracana procedury to 0.|  
|PARAMETER_MODE|String|Zwraca w przypadku parametru wejściowego, gdy parametr wyjściowy i INOUT, jeśli parametr wejścia/wyjścia.|  
|IS_RESULT|String|Zwraca tak, jeśli wskazuje wynik tej procedury, która jest funkcją. W przeciwnym razie zwraca nie.|  
|AS_LOCATOR|String|Zwraca tak, jeśli został zadeklarowany jako lokalizatora. W przeciwnym razie zwraca nie.|  
|NAZWA_PARAMETRU|String|Nazwa parametru. Wartość NULL, jeśli odpowiada wartość zwracaną przez funkcję.|  
|DATA_TYPE|String|Typ danych dostarczane przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maksymalna długość w znakach dla typów danych binarnych lub znak. W przeciwnym razie zwraca wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maksymalna długość w bajtach dla typów danych binarnych lub znak. W przeciwnym razie zwraca wartość NULL.|  
|COLLATION_CATALOG|String|Nazwa katalogu sortowania parametru. Jeśli nie jest jednym z typów znaków zwraca wartość NULL.|  
|COLLATION_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|COLLATION_NAME|String|Nazwa sortowania parametru. Jeśli nie jest jednym z typów znaków zwraca wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Nazwa zestawu znaków parametru w katalogu. Jeśli nie jest jednym z typów znaków zwraca wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Nazwa zestawu znaków parametru. Jeśli nie jest jednym z typów znaków zwraca wartość NULL.|  
|NUMERIC_PRECISION|Byte|Dokładność przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zwraca wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Podstawa dokładności przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zwraca wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zwraca wartość NULL.|  
|DATETIME_PRECISION|Int16|Precyzja w ułamkowych części sekundy w przypadku typu parametru datetime lub smalldatetime. W przeciwnym razie zwraca wartość NULL.|  
|INTERVAL_TYPE|String|WARTOŚĆ NULL. Zarezerwowane do użytku w przyszłości przez program SQL Server.|  
|INTERVAL_PRECISION|Int16|WARTOŚĆ NULL. Zarezerwowane do użytku w przyszłości przez program SQL Server.|  
  
## <a name="tables"></a>Tabele  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|TABLE_TYPE|String|Typ tabeli. Może być WIDOKU lub tabeli podstawowej.|  
  
## <a name="columns"></a>Kolumny  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ORDINAL_POSITION|Int32|Numer identyfikacyjny kolumny.|  
|COLUMN_DEFAULT|String|Wartość domyślna kolumny|  
|IS_NULLABLE|String|Dopuszczania wartości null w kolumnie. Jeśli ta kolumna zezwala na wartość NULL, ta funkcja tak. W przeciwnym razie nie jest zwracana.|  
|DATA_TYPE|String|Typ danych dostarczane przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 — Sql8, Int16 — Sql7|Maksymalna długość w znakach dla danych binarnych, dane znakowe lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32 — SQL8, Int16 — Sql7|Maksymalna długość w bajtach dla danych binarnych, dane znakowe lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION|Bajtu bez znaku|Dokładność przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Podstawa dokładności przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|DATETIME_PRECISION|Int16|Podtyp kodu datetime i typy danych SQL 92 interwału. Inne typy danych zwracana jest wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Zwraca główny, wskazującą bazy danych, w której znajduje zestawu znaków, jeśli kolumna danych znakowych lub dane tekstowe typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Zwraca unikatową nazwę dla znaku ustawić, jeśli ta kolumna jest znak danych lub tekst typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|COLLATION_CATALOG|String|Zwraca główny, wskazującą bazy danych, w którym jest zdefiniowany sortowania, jeśli kolumna danych znakowych lub dane tekstowe typu. W przeciwnym razie ta kolumna ma wartość NULL.|  
  
### <a name="columns-sql-server-2008"></a>Kolumny (SQL Server 2008)  
 Począwszy od programu .NET Framework w wersji 3.5 z dodatkiem SP1 i program SQL Server 2008, następujące kolumny zostały dodane do kolekcji schematów kolumn do obsługi nowych typów przestrzennych, filestream i kolumn rozrzedzonych. Te kolumny nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|TAK, jeśli kolumna ma atrybut FILESTREAM.<br /><br /> Nie, jeśli kolumna nie ma atrybutu FILESTREAM.|  
|IS_SPARSE|String|TAK, jeśli kolumna jest kolumną rozrzedzoną.<br /><br /> Nie, jeśli kolumna nie jest kolumną rozrzedzoną.|  
|IS_COLUMN_SET|String|TAK, jeśli kolumna jest kolumnę zestawu kolumn.<br /><br /> Nie, jeśli kolumna nie jest kolumnę zestawu kolumn.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 Począwszy od programu .NET Framework w wersji 3.5 z dodatkiem SP1 i program SQL Server 2008, kolekcji schematów AllColumns dodano do obsługuje kolumn rozrzedzonych. AllColumns nie jest obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.  
  
 AllColumns ma takie same ograniczenia i wynikowy schematu DataTable jako kolekcji schematów kolumn. Jedyna różnica polega na tym, że AllColumns zawiera kolumny zestawu kolumn, które nie znajdują się w kolekcji schematów kolumn. W poniższej tabeli opisano te kolumny.  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ORDINAL_POSITION|Int32|Numer identyfikacyjny kolumny.|  
|COLUMN_DEFAULT|String|Wartość domyślna kolumny|  
|IS_NULLABLE|String|Dopuszczania wartości null w kolumnie. Jeśli ta kolumna zezwala na wartość NULL, ta funkcja tak. W przeciwnym razie nie jest zwracana.|  
|DATA_TYPE|String|Typ danych dostarczane przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maksymalna długość w znakach dla danych binarnych, dane znakowe lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maksymalna długość w bajtach dla danych binarnych, dane znakowe lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION|Bajtu bez znaku|Dokładność przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Podstawa dokładności przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|DATETIME_PRECISION|Int16|Podtyp kodu datetime i typy danych SQL 92 interwału. Inne typy danych zwracana jest wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Zwraca główny, wskazującą bazy danych, w której znajduje zestawu znaków, jeśli kolumna danych znakowych lub dane tekstowe typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Zwraca unikatową nazwę dla znaku ustawić, jeśli ta kolumna jest znak danych lub tekst typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|COLLATION_CATALOG|String|Zwraca główny, wskazującą bazy danych, w którym jest zdefiniowany sortowania, jeśli kolumna danych znakowych lub dane tekstowe typu. W przeciwnym razie ta kolumna ma wartość NULL.|  
|IS_FILESTREAM|String|TAK, jeśli kolumna ma atrybut FILESTREAM.<br /><br /> Nie, jeśli kolumna nie ma atrybutu FILESTREAM.|  
|IS_SPARSE|String|TAK, jeśli kolumna jest kolumną rozrzedzoną.<br /><br /> Nie, jeśli kolumna nie jest kolumną rozrzedzoną.|  
|IS_COLUMN_SET|String|TAK, jeśli kolumna jest kolumnę zestawu kolumn.<br /><br /> Nie, jeśli kolumna nie jest kolumnę zestawu kolumn.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 Począwszy od programu .NET Framework w wersji 3.5 z dodatkiem SP1 i program SQL Server 2008, kolekcji schematów ColumnSetColumns dodano do obsługuje kolumn rozrzedzonych. ColumnSetColumns nie jest obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server. Kolekcja schematów ColumnSetColumns zwraca schematu dla wszystkich kolumn w zestawie kolumn. W poniższej tabeli opisano te kolumny.  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ORDINAL_POSITION|Int32|Numer identyfikacyjny kolumny.|  
|COLUMN_DEFAULT|String|Wartość domyślna kolumny|  
|IS_NULLABLE|String|Dopuszczania wartości null w kolumnie. Jeśli ta kolumna zezwala na wartość NULL, ta funkcja tak. W przeciwnym razie nie jest zwracana.|  
|DATA_TYPE|String|Typ danych dostarczane przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maksymalna długość w znakach dla danych binarnych, dane znakowe lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maksymalna długość w bajtach dla danych binarnych, dane znakowe lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION|Bajtu bez znaku|Dokładność przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Podstawa dokładności przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżonej dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub dane finansowe. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|DATETIME_PRECISION|Int16|Podtyp kodu datetime i typy danych SQL 92 interwału. Inne typy danych zwracana jest wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Zwraca główny, wskazującą bazy danych, w której znajduje zestawu znaków, jeśli kolumna danych znakowych lub dane tekstowe typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Zwraca unikatową nazwę dla znaku ustawić, jeśli ta kolumna jest znak danych lub tekst typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|COLLATION_CATALOG|String|Zwraca główny, wskazującą bazy danych, w którym jest zdefiniowany sortowania, jeśli kolumna danych znakowych lub dane tekstowe typu. W przeciwnym razie ta kolumna ma wartość NULL.|  
|IS_FILESTREAM|String|TAK, jeśli kolumna ma atrybut FILESTREAM.<br /><br /> Nie, jeśli kolumna nie ma atrybutu FILESTREAM.|  
|IS_SPARSE|String|TAK, jeśli kolumna jest kolumną rozrzedzoną.<br /><br /> Nie, jeśli kolumna nie jest kolumną rozrzedzoną.|  
|IS_COLUMN_SET|String|TAK, jeśli kolumna jest kolumnę zestawu kolumn.<br /><br /> Nie, jeśli kolumna nie jest kolumnę zestawu kolumn.|  
  
## <a name="users"></a>Użytkownicy  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|Identyfikator UID|Int16|Identyfikator użytkownika, unikatowe w tej bazie danych. 1 jest właścicielem bazy danych.|  
|nazwa_użytkownika|String|Nazwa użytkownika lub grupy, unikatowa nazwa w tej bazie danych.|  
|CREATEDATE|DataGodzina|Data dodania tego konta.|  
|updatedate|DataGodzina|Data ostatniej zmiany konta.|  
  
## <a name="views"></a>Widoki  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog widoku.|  
|TABLE_SCHEMA|String|Schemat, który zawiera widok.|  
|TABLE_NAME|String|Nazwa widoku.|  
|CHECK_OPTION|String|Typ WITH CHECK OPTION. Jest CASCADE, jeśli oryginalnego widoku został utworzony przy użyciu WITH CHECK OPTION. W przeciwnym razie żadne zwracany.|  
|IS_UPDATABLE|String|Określa, czy widok jest aktualizowalny. Zawsze zwraca nie.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|Katalog widoku.|  
|VIEW_SCHEMA|String|Schemat, który zawiera widok.|  
|VIEW_NAME|String|Nazwa widoku.|  
|TABLE_CATALOG|String|Katalog tabeli, która jest skojarzona z tym widokiem.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę, która jest skojarzona z tym widokiem.|  
|TABLE_NAME|String|Nazwa tabeli, która jest skojarzony z widokiem. Tabeli podstawowej.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|nazwa_zestawu|String|Nazwa pliku zestawu.|  
|udt_name|String|Nazwa klasy dla zestawu.|  
|version_major|Obiekt|Numer wersji głównej.|  
|version_minor|Obiekt|Numer wersji pomocniczej.|  
|version_build|Obiekt|Numer kompilacji.|  
|version_revision|Obiekt|Numer poprawki.|  
|culture_info|Obiekt|Informacje o ustawieniach kulturowych, skojarzone z tym UDT.|  
|public_key|Obiekt|Klucz publiczny używany przez ten zestaw.|  
|is_fixed_length|Boolean|Określa, czy długość typu jest zawsze taki sam jak max_length.|  
|max_length|Int16|Maksymalna długość typu w bajtach.|  
|Create_Date|DataGodzina|Data zestaw został utworzony zarejestrowany.|  
|Permission_set_desc|String|Przyjazna nazwa uprawnienia — zestaw /-poziomu zabezpieczeń dla zestawu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
