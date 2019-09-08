---
title: Kolekcje schematów programu SQL Server
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: 0f65bbf2534eb7167baacb1405a8ce6e9769c23f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794331"
---
# <a name="sql-server-schema-collections"></a>Kolekcje schematów programu SQL Server
Microsoft .NET Framework Dostawca danych for SQL Server obsługuje dodatkowe kolekcje schematów oprócz wspólnych kolekcji schematów. Kolekcje schematów różnią się nieco od używanej wersji SQL Server. Aby określić listę obsługiwanych kolekcji schematów, wywołaj metodę **GetSchema** bez argumentów lub z nazwą kolekcji schematów "MetaDataCollections". Spowoduje to zwrócenie <xref:System.Data.DataTable> listy obsługiwanych kolekcji schematów, liczbę ograniczeń, które one obsługują, oraz liczbę używanych przez nich części identyfikatora.  
  
## <a name="databases"></a>Bazy danych  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|database_name|String|Nazwa bazy danych.|  
|DBID|Int16|Identyfikator bazy danych.|  
|create_date|DataGodzina|Data utworzenia bazy danych.|  
  
## <a name="foreign-keys"></a>Klucze obce  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|String|Katalog, do którego należy ograniczenie.|  
|CONSTRAINT_SCHEMA|String|Schemat zawierający ograniczenie.|  
|CONSTRAINT_NAME|String|Nazwij.|  
|TABLE_CATALOG|String|Ograniczenie nazwy tabeli jest częścią.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli|  
|CONSTRAINT_TYPE|String|Typ ograniczenia. Dozwolony jest tylko "klucz obcy".|  
|IS_DEFERRABLE|String|Określa, czy ograniczenie jest opóźnione. Zwraca wartość nie.|  
|INITIALLY_DEFERRED|String|Określa, czy ograniczenie jest początkowo odroczone. Zwraca wartość nie.|  
  
## <a name="indexes"></a>Zwiększa  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, do którego należy indeks.|  
|constraint_schema|String|Schemat, który zawiera indeks.|  
|constraint_name|String|Nazwa indeksu.|  
|table_catalog|String|Nazwa tabeli, z którą jest skojarzony indeks.|  
|table_schema|String|Schemat zawierający tabelę, z którą skojarzona jest indeks.|  
|table_name|String|Nazwa tabeli.|  
|index_name|String|Nazwa indeksu.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 Począwszy od .NET Framework w wersji 3,5 SP1 i SQL Server 2008, następujące kolumny zostały dodane do kolekcji schematów indeksów w celu obsługi nowych typów przestrzennych, FILESTREAM i kolumn rozrzedzonych. Te kolumny nie są obsługiwane we wcześniejszych wersjach .NET Framework i SQL Server.  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|type_desc|String|Typ indeksu będzie jednym z następujących:<br /><br /> -STERTA<br />-KLASTROWANE<br />-NIEKLASTROWANE<br />-XML<br />-PRZESTRZENNY|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, do którego należy indeks.|  
|constraint_schema|String|Schemat, który zawiera indeks.|  
|constraint_name|String|Nazwa indeksu.|  
|table_catalog|String|Nazwa tabeli, z którą jest skojarzony indeks.|  
|table_schema|String|Schemat zawierający tabelę, z którą skojarzona jest indeks.|  
|table_name|String|Nazwa tabeli.|  
|column_name|String|Nazwa kolumny, z którą jest skojarzony indeks.|  
|ordinal_position|Int32|Pozycja porządkowa kolumny.|  
|KeyType|Byte|Typ obiektu.|  
|index_name|String|Nazwa indeksu.|  
  
## <a name="procedures"></a>Procedury  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Określona nazwa katalogu.|  
|SPECIFIC_SCHEMA|String|Określona nazwa schematu.|  
|SPECIFIC_NAME|String|Określona nazwa katalogu.|  
|ROUTINE_CATALOG|String|Katalog, do którego należy procedura składowana.|  
|ROUTINE_SCHEMA|String|Schemat zawierający procedurę składowaną.|  
|ROUTINE_NAME|String|Nazwa procedury składowanej.|  
|ROUTINE_TYPE|String|Zwraca procedurę dla procedur składowanych i funkcji dla funkcji.|  
|UTWORZONY|DataGodzina|Czas utworzenia procedury.|  
|LAST_ALTERED|DataGodzina|Czas ostatniej modyfikacji procedury.|  
  
## <a name="procedure-parameters"></a>Parametry procedury  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nazwa katalogu procedury, dla której jest parametrem.|  
|SPECIFIC_SCHEMA|String|Schemat zawierający procedurę, do której należy ten parametr.|  
|SPECIFIC_NAME|String|Nazwa procedury, której częścią jest ten parametr.|  
|ORDINAL_POSITION|Int32|Pozycja porządkowa parametru, rozpoczynając od 1. Dla wartości zwracanej procedury jest to 0.|  
|PARAMETER_MODE|String|Zwraca wartość w przypadku parametru wejściowego, jeśli parametr wyjściowy, i INOUT, jeśli parametr Input/Output.|  
|IS_RESULT|String|Zwraca wartość tak, jeśli wskazuje wynik procedury, która jest funkcją. W przeciwnym razie zwraca wartość nie.|  
|AS_LOCATOR|String|Zwraca wartość tak, jeśli jest zadeklarowana jako lokalizator. W przeciwnym razie zwraca wartość nie.|  
|PARAMETER_NAME|String|Nazwa parametru. Wartość NULL, jeśli odpowiada wartości zwracanej funkcji.|  
|DATA_TYPE|String|Typ danych dostarczany przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maksymalna długość w znakach dla binarnego lub znakowego typu danych. W przeciwnym razie zwraca wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maksymalna długość (w bajtach) dla typów danych binarnych lub znakowych. W przeciwnym razie zwraca wartość NULL.|  
|COLLATION_CATALOG|String|Nazwa katalogu sortowania parametru. Jeśli nie jest to jeden z typów znaków, zwraca wartość NULL.|  
|COLLATION_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|COLLATION_NAME|String|Nazwa sortowania parametru. Jeśli nie jest to jeden z typów znaków, zwraca wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Nazwa katalogu zestawu znaków parametru. Jeśli nie jest to jeden z typów znaków, zwraca wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Nazwa zestawu znaków parametru. Jeśli nie jest to jeden z typów znaków, zwraca wartość NULL.|  
|NUMERIC_PRECISION|Byte|Precyzja przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwraca wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Precyzja podstawy przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwraca wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwraca wartość NULL.|  
|DATETIME_PRECISION|Int16|Dokładność w częściach sekund, jeśli typ parametru to DateTime lub smalldatetime. W przeciwnym razie zwraca wartość NULL.|  
|INTERVAL_TYPE|String|NULL. Zarezerwowane do użytku w przyszłości przez SQL Server.|  
|INTERVAL_PRECISION|Int16|NULL. Zarezerwowane do użytku w przyszłości przez SQL Server.|  
  
## <a name="tables"></a>Tabelę  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|TABLE_TYPE|String|Typ tabeli. Może być widokiem lub TABELą podstawową.|  
  
## <a name="columns"></a>Kolumny  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ORDINAL_POSITION|Int32|Numer identyfikacyjny kolumny.|  
|COLUMN_DEFAULT|String|Wartość domyślna kolumny|  
|IS_NULLABLE|String|Wartość zerowa dla kolumny. Jeśli ta kolumna dopuszcza wartość NULL, ta kolumna zwraca wartość tak. W przeciwnym razie nie jest zwracana.|  
|DATA_TYPE|String|Typ danych dostarczany przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 — Sql8, Int16 – Sql7|Maksymalna długość w znakach, w przypadku danych binarnych, danych znakowych lub danych tekstowych i obrazów. W przeciwnym razie zwracana jest wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32 — SQL8, Int16 – Sql7|Maksymalna długość (w bajtach) dla danych binarnych, danych znakowych lub danych tekstowych i obrazów. W przeciwnym razie zwracana jest wartość NULL.|  
|NUMERIC_PRECISION|Bajt bez znaku|Precyzja przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwracana jest wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Precyzja podstawy przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwracana jest wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwracana jest wartość NULL.|  
|DATETIME_PRECISION|Int16|Kod podtypu dla typów danych interwału DateTime i SQL-92. W przypadku innych typów danych zwracana jest wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Zwraca wzorzec, wskazujący bazę danych, w której znajduje się zestaw znaków, jeśli kolumna zawiera dane znakowe lub dane typu Text. W przeciwnym razie zwracana jest wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Zwraca unikatową nazwę zestawu znaków, jeśli ta kolumna zawiera dane znakowe lub typ danych tekstowych. W przeciwnym razie zwracana jest wartość NULL.|  
|COLLATION_CATALOG|String|Zwraca wzorzec wskazujący bazę danych, w której jest zdefiniowane sortowanie, jeśli kolumna zawiera dane znakowe lub dane tekstowe. W przeciwnym razie ta kolumna ma wartość NULL.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  
 Począwszy od .NET Framework wersji 3,5 SP1 i SQL Server 2008, następujące kolumny zostały dodane do kolekcji schematów kolumn, aby obsługiwały nowe typy przestrzenne, FILESTREAM i kolumny rozrzedzone. Te kolumny nie są obsługiwane we wcześniejszych wersjach .NET Framework i SQL Server.  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|TAK, jeśli kolumna ma atrybut FILESTREAM.<br /><br /> NIE, jeśli kolumna nie ma atrybutu FILESTREAM.|  
|IS_SPARSE|String|TAK, jeśli kolumna jest kolumną rozrzedzoną.<br /><br /> NIE, jeśli kolumna nie jest kolumną rozrzedzoną.|  
|IS_COLUMN_SET|String|TAK, jeśli kolumna jest kolumną zestawu kolumn.<br /><br /> NIE, jeśli kolumna nie jest kolumną zestawu kolumn.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 Począwszy od .NET Framework wersji 3,5 SP1 i SQL Server 2008, kolekcja schematów AllColumns została dodana do obsługi kolumn rozrzedzonych. AllColumns nie jest obsługiwane we wcześniejszych wersjach .NET Framework i SQL Server.  
  
 AllColumns ma takie same ograniczenia i wynikający ze schematu DataTable jako kolekcję schematów kolumn. Jedyną różnicą jest to, że AllColumns zawiera kolumny zestawu kolumn, które nie są uwzględnione w kolekcji schematów kolumn. W poniższej tabeli opisano te kolumny.  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ORDINAL_POSITION|Int32|Numer identyfikacyjny kolumny.|  
|COLUMN_DEFAULT|String|Wartość domyślna kolumny|  
|IS_NULLABLE|String|Wartość zerowa dla kolumny. Jeśli ta kolumna dopuszcza wartość NULL, ta kolumna zwraca wartość tak. W przeciwnym razie nie jest zwracana.|  
|DATA_TYPE|String|Typ danych dostarczany przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maksymalna długość w znakach, w przypadku danych binarnych, danych znakowych lub danych tekstowych i obrazów. W przeciwnym razie zwracana jest wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maksymalna długość (w bajtach) dla danych binarnych, danych znakowych lub danych tekstowych i obrazów. W przeciwnym razie zwracana jest wartość NULL.|  
|NUMERIC_PRECISION|Bajt bez znaku|Precyzja przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwracana jest wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Precyzja podstawy przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwracana jest wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwracana jest wartość NULL.|  
|DATETIME_PRECISION|Int16|Kod podtypu dla typów danych interwału DateTime i SQL-92. W przypadku innych typów danych zwracana jest wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Zwraca wzorzec, wskazujący bazę danych, w której znajduje się zestaw znaków, jeśli kolumna zawiera dane znakowe lub dane typu Text. W przeciwnym razie zwracana jest wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Zwraca unikatową nazwę zestawu znaków, jeśli ta kolumna zawiera dane znakowe lub typ danych tekstowych. W przeciwnym razie zwracana jest wartość NULL.|  
|COLLATION_CATALOG|String|Zwraca wzorzec wskazujący bazę danych, w której jest zdefiniowane sortowanie, jeśli kolumna zawiera dane znakowe lub dane tekstowe. W przeciwnym razie ta kolumna ma wartość NULL.|  
|IS_FILESTREAM|String|TAK, jeśli kolumna ma atrybut FILESTREAM.<br /><br /> NIE, jeśli kolumna nie ma atrybutu FILESTREAM.|  
|IS_SPARSE|String|TAK, jeśli kolumna jest kolumną rozrzedzoną.<br /><br /> NIE, jeśli kolumna nie jest kolumną rozrzedzoną.|  
|IS_COLUMN_SET|String|TAK, jeśli kolumna jest kolumną zestawu kolumn.<br /><br /> NIE, jeśli kolumna nie jest kolumną zestawu kolumn.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 Począwszy od .NET Framework wersji 3,5 SP1 i SQL Server 2008, kolekcja schematów ColumnSetColumns została dodana do obsługi kolumn rozrzedzonych. ColumnSetColumns nie jest obsługiwane we wcześniejszych wersjach .NET Framework i SQL Server. Kolekcja schematów ColumnSetColumns zwraca schemat dla wszystkich kolumn w zestawie kolumn. W poniższej tabeli opisano te kolumny.  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabeli.|  
|TABLE_SCHEMA|String|Schemat, który zawiera tabelę.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ORDINAL_POSITION|Int32|Numer identyfikacyjny kolumny.|  
|COLUMN_DEFAULT|String|Wartość domyślna kolumny|  
|IS_NULLABLE|String|Wartość zerowa dla kolumny. Jeśli ta kolumna dopuszcza wartość NULL, ta kolumna zwraca wartość tak. W przeciwnym razie nie jest zwracana.|  
|DATA_TYPE|String|Typ danych dostarczany przez system.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maksymalna długość w znakach, w przypadku danych binarnych, danych znakowych lub danych tekstowych i obrazów. W przeciwnym razie zwracana jest wartość NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maksymalna długość (w bajtach) dla danych binarnych, danych znakowych lub danych tekstowych i obrazów. W przeciwnym razie zwracana jest wartość NULL.|  
|NUMERIC_PRECISION|Bajt bez znaku|Precyzja przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwracana jest wartość NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Precyzja podstawy przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwracana jest wartość NULL.|  
|NUMERIC_SCALE|Int32|Skala przybliżonych danych liczbowych, dokładne dane liczbowe, dane całkowite lub dane pieniężne. W przeciwnym razie zwracana jest wartość NULL.|  
|DATETIME_PRECISION|Int16|Kod podtypu dla typów danych interwału DateTime i SQL-92. W przypadku innych typów danych zwracana jest wartość NULL.|  
|CHARACTER_SET_CATALOG|String|Zwraca wzorzec, wskazujący bazę danych, w której znajduje się zestaw znaków, jeśli kolumna zawiera dane znakowe lub dane typu Text. W przeciwnym razie zwracana jest wartość NULL.|  
|CHARACTER_SET_SCHEMA|String|Zawsze zwraca wartość NULL.|  
|CHARACTER_SET_NAME|String|Zwraca unikatową nazwę zestawu znaków, jeśli ta kolumna zawiera dane znakowe lub typ danych tekstowych. W przeciwnym razie zwracana jest wartość NULL.|  
|COLLATION_CATALOG|String|Zwraca wzorzec wskazujący bazę danych, w której jest zdefiniowane sortowanie, jeśli kolumna zawiera dane znakowe lub dane tekstowe. W przeciwnym razie ta kolumna ma wartość NULL.|  
|IS_FILESTREAM|String|TAK, jeśli kolumna ma atrybut FILESTREAM.<br /><br /> NIE, jeśli kolumna nie ma atrybutu FILESTREAM.|  
|IS_SPARSE|String|TAK, jeśli kolumna jest kolumną rozrzedzoną.<br /><br /> NIE, jeśli kolumna nie jest kolumną rozrzedzoną.|  
|IS_COLUMN_SET|String|TAK, jeśli kolumna jest kolumną zestawu kolumn.<br /><br /> NIE, jeśli kolumna nie jest kolumną zestawu kolumn.|  
  
## <a name="users"></a>Użytkownicy  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|UID|Int16|Unikatowy identyfikator użytkownika w tej bazie danych. 1 jest właścicielem bazy danych.|  
|user_name|String|Nazwa użytkownika lub grupy, unikatowa w tej bazie danych.|  
|Data i godzina|DataGodzina|Data dodania konta.|  
|updatedate|DataGodzina|Data ostatniej zmiany konta.|  
  
## <a name="views"></a>Widoki  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog widoku.|  
|TABLE_SCHEMA|String|Schemat, który zawiera widok.|  
|TABLE_NAME|String|Nazwa widoku.|  
|CHECK_OPTION|String|Typ elementu WITH CHECK OPTION. Jest KASKADowy, jeśli oryginalny widok został utworzony przy użyciu opcji WITH CHECK. W przeciwnym razie nie jest zwracana żadna wartość.|  
|IS_UPDATABLE|String|Określa, czy widok jest aktualizowalny. Zawsze zwraca wartość nie.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|Katalog widoku.|  
|VIEW_SCHEMA|String|Schemat, który zawiera widok.|  
|VIEW_NAME|String|Nazwa widoku.|  
|TABLE_CATALOG|String|Wykaz tabeli, która jest skojarzona z tym widokiem.|  
|TABLE_SCHEMA|String|Schemat zawierający tabelę, która jest skojarzona z tym widokiem.|  
|TABLE_NAME|String|Nazwa tabeli, która jest skojarzona z widokiem. Tabela podstawowa.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|assembly_name|String|Nazwa pliku zestawu.|  
|udt_name|String|Nazwa klasy zestawu.|  
|version_major|Obiekt|Główny numer wersji.|  
|version_minor|Obiekt|Pomocniczy numer wersji.|  
|version_build|Obiekt|Numer kompilacji.|  
|version_revision|Obiekt|Numer poprawki.|  
|culture_info|Obiekt|Informacje o kulturze skojarzone z tym UDT.|  
|public_key|Obiekt|Klucz publiczny używany przez ten zestaw.|  
|is_fixed_length|Boolean|Określa, czy długość typu jest zawsze taka sama jak max_length.|  
|max_length|Int16|Maksymalna długość typu w bajtach.|  
|Create_Date|DataGodzina|Data utworzenia/zarejestrowania zestawu.|  
|Permission_set_desc|String|Przyjazna nazwa dla zestawu uprawnień/poziomu zabezpieczeń dla zestawu.|  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)
- [Omówienie ADO.NET](ado-net-overview.md)
