---
title: Kolekcje schematów programu SQL Server
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: 79bf9f1253b64863d3eabddff8c33b6ffab70f41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878465"
---
# <a name="sql-server-schema-collections"></a>Kolekcje schematów programu SQL Server
Dostawcy danych programu Microsoft .NET Framework dla programu SQL Server obsługuje kolekcje schematów dodatkowe, oprócz Typowe kolekcje schematów. Kolekcje schematów nieco różnią się zależnie od wersji programu SQL Server, którego używasz. Aby określić listę obsługiwanych schematu kolekcji, należy wywołać **GetSchema** metody bez argumentów lub nazwą kolekcji schematów "MetaDataCollections". Spowoduje to zwrócenie <xref:System.Data.DataTable> z listą kolekcje schematów obsługiwanych, liczba ograniczeń, które obsługują one każdego i części identyfikator, których używają.  
  
## <a name="databases"></a>Bazy danych  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|database_name|String|Nazwa bazy danych.|  
|DBID|Int16|Identyfikator bazy danych.|  
|create_date|DataGodzina|Data utworzenia bazy danych.|  
  
## <a name="foreign-keys"></a>Klucze obce  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|String|Wykaz ograniczenie należą do.|  
|CONSTRAINT_SCHEMA|String|Schemat, który zawiera ograniczenie.|  
|CONSTRAINT_NAME|String|Nazwa.|  
|TABLE_CATALOG|String|Ograniczenie nazwy tabeli jest częścią.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli|  
|CONSTRAINT_TYPE|String|Typ ograniczenia. Dozwolona jest tylko "klucz OBCY".|  
|IS_DEFERRABLE|String|Określa, czy ograniczenie jest deferrable. Nie zwraca.|  
|INITIALLY_DEFERRED|String|Określa, czy ograniczenie jest początkowo deferrable. Nie zwraca.|  
  
## <a name="indexes"></a>Indeksy  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, który należy indeksu.|  
|constraint_schema|String|Schemat, który zawiera indeksu.|  
|constraint_name|String|Nazwa indeksu.|  
|table_catalog|String|Nazwa tabeli indeksu jest skojarzony.|  
|table_schema|String|Schemat, który zawiera tabelę indeks jest skojarzony.|  
|table_name|String|Nazwa tabeli.|  
|index_name|String|Nazwa indeksu.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 Począwszy od .NET Framework w wersji 3.5 z dodatkiem SP1 i SQL Server 2008, następujące kolumny zostały dodane do kolekcji schematów indeksów do obsługi nowych typów przestrzennych, filestream i kolumn rozrzedzonych. Kolumny te nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|type_desc|String|Typ indeksu będzie jedną z następujących czynności:<br /><br /> -HEAP<br />-KLASTRA<br />-NIEKLASTROWANY<br />-XML<br />-PRZESTRZENNE|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, który należy indeksu.|  
|constraint_schema|String|Schemat, który zawiera indeksu.|  
|constraint_name|String|Nazwa indeksu.|  
|table_catalog|String|Nazwa tabeli indeksu jest skojarzony.|  
|table_schema|String|Schemat, który zawiera tabelę indeks jest skojarzony.|  
|table_name|String|Nazwa tabeli.|  
|column_name|String|Nazwa kolumny indeksu jest skojarzony.|  
|ordinal_position|Int32|Położenie porządkowego kolumny.|  
|KeyType|Byte|Typ obiektu.|  
|index_name|String|Nazwa indeksu.|  
  
## <a name="procedures"></a>Procedury  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nazwa określonego katalogu.|  
|SPECIFIC_SCHEMA|String|Specyficzna nazwa schematu.|  
|SPECIFIC_NAME|String|Nazwa określonego katalogu.|  
|ROUTINE_CATALOG|String|Wykaz procedury składowanej należą do.|  
|ROUTINE_SCHEMA|String|Schemat, który zawiera procedurę składowaną.|  
|ROUTINE_NAME|String|Nazwa procedury składowanej.|  
|ROUTINE_TYPE|String|Zwraca procedury dla procedur przechowywanych i funkcji dla funkcji.|  
|UTWORZONE|DataGodzina|Godzina utworzenia procedury.|  
|LAST_ALTERED|DataGodzina|Czas ostatniej modyfikacji procedury.|  
  
## <a name="procedure-parameters"></a>Parametry procedury  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nazwa procedury, dla której jest parametrem wykazu.|  
|SPECIFIC_SCHEMA|String|Schemat, który zawiera procedury, dla którego ten parametr jest częścią.|  
|SPECIFIC_NAME|String|Nazwa procedury, dla którego ten parametr jest częścią.|  
|ORDINAL_POSITION|Int32|Porządkowym parametru rozpoczyna się od 1. Wartość zwracana przez procedurę jest to wartość 0.|  
|PARAMETER_MODE|String|Zwraca w przypadku parametru wejściowego, gdy parametr wyjściowy i INOUT, jeśli parametr input/output.|  
|IS_RESULT|String|Zwraca tak, jeśli wskazuje wynik procedury, która jest funkcją. W przeciwnym razie zwraca nie.|  
|AS_LOCATOR|String|Zwraca tak, jeśli są zadeklarowane jako lokalizatora. W przeciwnym razie zwraca nie.|  
|PARAMETER_NAME|String|Nazwa parametru. Wartość NULL, jeśli odpowiada to wartość zwracana przez funkcję.|  
|DATA_TYPE|String|Typ danych dostarczane przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maksymalna długość w znakach dla typów danych binarnych lub znak. W przeciwnym razie zwraca wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maksymalna długość w bajtach dla typów danych binarnych lub znak. W przeciwnym razie zwraca wartość NULL.|  
|COLLATION_CATALOG|String|Nazwa wykazu sortowania parametru. W przeciwnym razie zwraca jeden z typów znaków o wartości NULL.|  
|COLLATION_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|COLLATION_NAME|String|Nazwa sortowania parametru. W przeciwnym razie zwraca jeden z typów znaków o wartości NULL.|  
|CHARACTER_SET_CATALOG|String|Nazwa zestawu znaków parametru wykazu. W przeciwnym razie zwraca jeden z typów znaków o wartości NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Nazwa zestawu znaków parametru. W przeciwnym razie zwraca jeden z typów znaków o wartości NULL.|  
|NUMERIC_PRECISION|Byte|Dokładność przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zwraca wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Podstawy dokładności przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zwraca wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zwraca wartość NULL.|  
|DATETIME_PRECISION|Int16|Precyzja w ułamków sekund, jeśli typ parametru to datetime lub smalldatetime. W przeciwnym razie zwraca wartość NULL.|  
|INTERVAL_TYPE|String|NULL. Zarezerwowane do użytku w przyszłości przez program SQL Server.|  
|INTERVAL_PRECISION|Int16|NULL. Zarezerwowane do użytku w przyszłości przez program SQL Server.|  
  
## <a name="tables"></a>Tabele  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|TABLE_TYPE|String|Typ tabeli. Może być WIDOKU lub tabeli podstawowej.|  
  
## <a name="columns"></a>Kolumny  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ORDINAL_POSITION|Int32|Numer identyfikacyjny kolumny.|  
|COLUMN_DEFAULT|String|Wartość domyślna dla kolumny|  
|IS_NULLABLE|String|Dopuszczanie wartości null dla kolumny. W tej kolumnie, jeśli ta kolumna dopuszcza wartość NULL, zwraca tak. W przeciwnym razie nie jest zwracana.|  
|DATA_TYPE|String|Typ danych dostarczane przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|Maksymalna długość w znakach dla danych binarnych, znak danych lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|Maksymalna długość w bajtach dla danych binarnych, znak danych lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION|Bajtów bez znaku|Dokładność przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Podstawy dokładności przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|DATETIME_PRECISION|Int16|Kod dla daty/godziny i typy danych programu SQL 92 interwał podtypu. Dla innych typów danych jest zwracana wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Zwraca główny, wskazujący bazę danych, w którym znajduje zestaw znaków, jeśli kolumna ma znak danych lub danych tekstowych typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Zwraca unikatową nazwę dla znaku Ustaw, jeśli ta kolumna znajduje się znak danych lub danych tekstowych typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|COLLATION_CATALOG|String|Zwraca główny, wskazujący bazę danych, w którym zdefiniowano sortowania, jeśli kolumna ma znak danych lub danych tekstowych typu. W przeciwnym razie ta kolumna ma wartość NULL.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  
 Począwszy od .NET Framework w wersji 3.5 z dodatkiem SP1 i SQL Server 2008, następujące kolumny zostały dodane do kolekcji schematów kolumn do obsługi nowych typów przestrzennych, filestream i kolumn rozrzedzonych. Kolumny te nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|TAK, jeśli kolumna ma atrybut FILESTREAM.<br /><br /> Nie, jeśli kolumna nie ma atrybut FILESTREAM.|  
|IS_SPARSE|String|TAK, jeśli kolumna jest kolumną rozrzedzoną.<br /><br /> Nie, jeśli kolumna nie jest kolumną rozrzedzoną.|  
|IS_COLUMN_SET|String|TAK, jeśli kolumna ma kolumnę zestawu kolumn.<br /><br /> Nie, jeśli kolumna nie ma kolumnę zestawu kolumn.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 Począwszy od .NET Framework w wersji 3.5 z dodatkiem SP1 i SQL Server 2008, kolekcja schematów AllColumns dodano do obsługuje kolumn rozrzedzonych. AllColumns nie jest obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.  
  
 AllColumns ma te same ograniczenia i wynikowy schematu elementu DataTable jako kolekcja schematów kolumn. Jedyna różnica polega na tym, że AllColumns zawiera kolumny zestawu kolumn, które nie są uwzględnione w kolekcji schematów kolumn. W poniższej tabeli opisano te kolumny.  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ORDINAL_POSITION|Int32|Numer identyfikacyjny kolumny.|  
|COLUMN_DEFAULT|String|Wartość domyślna dla kolumny|  
|IS_NULLABLE|String|Dopuszczanie wartości null dla kolumny. W tej kolumnie, jeśli ta kolumna dopuszcza wartość NULL, zwraca tak. W przeciwnym razie nie jest zwracana.|  
|DATA_TYPE|String|Typ danych dostarczane przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maksymalna długość w znakach dla danych binarnych, znak danych lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maksymalna długość w bajtach dla danych binarnych, znak danych lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION|Bajtów bez znaku|Dokładność przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Podstawy dokładności przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|DATETIME_PRECISION|Int16|Kod dla daty/godziny i typy danych programu SQL 92 interwał podtypu. Dla innych typów danych jest zwracana wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Zwraca główny, wskazujący bazę danych, w którym znajduje zestaw znaków, jeśli kolumna ma znak danych lub danych tekstowych typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Zwraca unikatową nazwę dla znaku Ustaw, jeśli ta kolumna znajduje się znak danych lub danych tekstowych typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|COLLATION_CATALOG|String|Zwraca główny, wskazujący bazę danych, w którym zdefiniowano sortowania, jeśli kolumna ma znak danych lub danych tekstowych typu. W przeciwnym razie ta kolumna ma wartość NULL.|  
|IS_FILESTREAM|String|TAK, jeśli kolumna ma atrybut FILESTREAM.<br /><br /> Nie, jeśli kolumna nie ma atrybut FILESTREAM.|  
|IS_SPARSE|String|TAK, jeśli kolumna jest kolumną rozrzedzoną.<br /><br /> Nie, jeśli kolumna nie jest kolumną rozrzedzoną.|  
|IS_COLUMN_SET|String|TAK, jeśli kolumna ma kolumnę zestawu kolumn.<br /><br /> Nie, jeśli kolumna nie ma kolumnę zestawu kolumn.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 Począwszy od .NET Framework w wersji 3.5 z dodatkiem SP1 i SQL Server 2008, kolekcja schematów ColumnSetColumns dodano do obsługuje kolumn rozrzedzonych. ColumnSetColumns nie jest obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server. Kolekcja schematów ColumnSetColumns zwraca schematu dla wszystkich kolumn w zestawie kolumn. W poniższej tabeli opisano te kolumny.  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ORDINAL_POSITION|Int32|Numer identyfikacyjny kolumny.|  
|COLUMN_DEFAULT|String|Wartość domyślna dla kolumny|  
|IS_NULLABLE|String|Dopuszczanie wartości null dla kolumny. W tej kolumnie, jeśli ta kolumna dopuszcza wartość NULL, zwraca tak. W przeciwnym razie nie jest zwracana.|  
|DATA_TYPE|String|Typ danych dostarczane przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maksymalna długość w znakach dla danych binarnych, znak danych lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maksymalna długość w bajtach dla danych binarnych, znak danych lub danych tekstowych i obrazów. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION|Bajtów bez znaku|Dokładność przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Podstawy dokładności przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżony dane liczbowe, dokładne dane liczbowe, danych liczb całkowitych lub pieniężnych danych. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|DATETIME_PRECISION|Int16|Kod dla daty/godziny i typy danych programu SQL 92 interwał podtypu. Dla innych typów danych jest zwracana wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Zwraca główny, wskazujący bazę danych, w którym znajduje zestaw znaków, jeśli kolumna ma znak danych lub danych tekstowych typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Zwraca unikatową nazwę dla znaku Ustaw, jeśli ta kolumna znajduje się znak danych lub danych tekstowych typu. W przeciwnym razie zostanie zwrócona wartość NULL.|  
|COLLATION_CATALOG|String|Zwraca główny, wskazujący bazę danych, w którym zdefiniowano sortowania, jeśli kolumna ma znak danych lub danych tekstowych typu. W przeciwnym razie ta kolumna ma wartość NULL.|  
|IS_FILESTREAM|String|TAK, jeśli kolumna ma atrybut FILESTREAM.<br /><br /> Nie, jeśli kolumna nie ma atrybut FILESTREAM.|  
|IS_SPARSE|String|TAK, jeśli kolumna jest kolumną rozrzedzoną.<br /><br /> Nie, jeśli kolumna nie jest kolumną rozrzedzoną.|  
|IS_COLUMN_SET|String|TAK, jeśli kolumna ma kolumnę zestawu kolumn.<br /><br /> Nie, jeśli kolumna nie ma kolumnę zestawu kolumn.|  
  
## <a name="users"></a>Użytkownicy  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|Identyfikator UID|Int16|Identyfikator użytkownika, unikatowe w tej bazie danych. 1 jest właściciel bazy danych.|  
|user_name|String|Nazwa użytkownika lub grupy, unikatowa nazwa w tej bazie danych.|  
|CREATEDATE|DataGodzina|Data dodania konta.|  
|updatedate|DataGodzina|Data ostatniej zmiany konta.|  
  
## <a name="views"></a>Widoki  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog widoku.|  
|TABLE_SCHEMA|String|Schemat, który zawiera widok.|  
|TABLE_NAME|String|Nazwa widoku.|  
|CHECK_OPTION|String|Typ WITH CHECK OPTION. Jest CASCADE, jeśli oryginalny widok został utworzony przy użyciu WITH CHECK OPTION. W przeciwnym razie nie jest zwracana.|  
|IS_UPDATABLE|String|Określa, czy widok jest aktualizowalny. Zawsze zwraca nie.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|Katalog widoku.|  
|VIEW_SCHEMA|String|Schemat, który zawiera widok.|  
|VIEW_NAME|String|Nazwa widoku.|  
|TABLE_CATALOG|String|Katalog tabelę, która jest skojarzona z tym widokiem.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę, która jest skojarzona z tym widokiem.|  
|TABLE_NAME|String|Nazwa tabeli, który jest skojarzony z widokiem. Tabeli podstawowej.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|NazwaKolumny|DataType|Opis|  
|----------------|--------------|-----------------|  
|assembly_name|String|Nazwa pliku zestawu.|  
|udt_name|String|Nazwa klasy dla zestawu.|  
|version_major|Obiekt|Główny numer wersji.|  
|version_minor|Obiekt|Pomocniczy numer wersji.|  
|version_build|Obiekt|Numer kompilacji.|  
|version_revision|Obiekt|Numer poprawki.|  
|culture_info|Obiekt|Informacji o kulturze, skojarzone z tym UDT.|  
|public_key|Obiekt|Klucz publiczny używany przez ten zestaw.|  
|is_fixed_length|Boolean|Określa, czy długość typu jest zawsze taki sam jak max_length.|  
|max_length|Int16|Maksymalna długość tego typu w bajtach.|  
|Create_Date|DataGodzina|Data zestaw został utworzony zarejestrowany.|  
|Permission_set_desc|String|Przyjazna nazwa zestaw/security poziom uprawnień dla zestawu.|  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
