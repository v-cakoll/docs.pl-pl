---
title: Typowe kolekcje schematów
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: 29ccd2af4268a86ae4c2047ad2523f68b0f6489e
ms.sourcegitcommit: a474397fd4de822f0d878d86d907e49763872b0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "37072127"
---
# <a name="common-schema-collections"></a>Typowe kolekcje schematów
Typowe kolekcje schematów są kolekcjami schematu, które są implementowane przez wszystkich dostawców zarządzanych w programie .NET Framework. Można tworzyć zapytania zarządzanego dostawcy .NET Framework, aby określić listę kolekcje schematów obsługiwanych przez wywołanie metody **GetSchema** metody bez argumentów lub nazwą kolekcji schematów "MetaDataCollections". Spowoduje to zwrócenie <xref:System.Data.DataTable> z listą kolekcje schematów obsługiwanych, liczba ograniczeń, które obsługują one każdego i części identyfikator, których używają. Kolekcje te opisują wszystkich wymaganych kolumn. Dostawcy są bezpłatne dodać dodatkowe kolumny, jeśli chcesz, aby ich. Na przykład `SqlClient` i `OracleClient` ParameterName można dodać do kolekcji ograniczenia.  
  
 Dostawca nie mógł określić wartości wymaganej kolumny, będzie zwracać wartość null.  
  
 Aby uzyskać więcej informacji o korzystaniu z **GetSchema** metod, zobacz [GetSchema i kolekcje schematów](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Ta kolekcja schematów udostępnia informacje na temat wszystkich kolekcje schematów, obsługiwane przez zarządzanego dostawcy .NET Framework, który jest obecnie używany do łączenia z bazą danych.  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|collectionName|string|Nazwa kolekcji do przekazania do **GetSchema** metodę, aby powrócić do kolekcji.|  
|NumberOfRestrictions|int|Liczba ograniczeń, które mogą być określone dla kolekcji.|  
|NumberOfIdentifierParts|int|Numer części w nazwie obiektu złożonego identyfikator/bazy danych. Na przykład w programie SQL Server, będzie to 3 dla tabel i 4 dla kolumny. Oracle byłoby 2 dla tabel i 3 dla kolumny.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Ta kolekcja schematów udostępnia informacje o źródle danych, łączyć się z zarządzanego dostawcy jest obecnie dostępna w programie .NET Framework.  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|string|Wyrażenie regularne, aby dopasować złożonego separatory złożone identyfikator. Na przykład "\\." (dla programu SQL Server) lub "\@&#124;\\." (w przypadku bazy danych Oracle).<br /><br /> Złożone identyfikator ma przeważnie format do czego służy nazwa obiektu bazy danych, na przykład: pubs.dbo.authors lub pubs\@dbo.authors.<br /><br /> Dla programu SQL Server, należy użyć wyrażenia regularnego "\\.". W przypadku programu OracleClient, użyj "\@&#124;\\.".<br /><br /> Do użytku ODBC Catalog_name_seperator.<br /><br /> Dla OLE DB użyj DBLITERAL_CATALOG_SEPARATOR lub DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|string|Nazwa produktu, używane przez dostawcę, takiego jak "Oracle" lub "SQLServer".|  
|DataSourceProductVersion|string|Wskazuje wersję produktu, używane przez dostawcę, w formacie natywnym źródeł danych i nie jest w formacie Microsoft.<br /><br /> W niektórych przypadkach DataSourceProductVersion i DataSourceProductVersionNormalized będzie mieć taką samą wartość. W przypadku usług OLE DB i ODBC są zawsze będą takie same jak są mapowane do tego samego wywołania funkcji w podstawowych natywnych interfejsów API.|  
|DataSourceProductVersionNormalized|string|Znormalizowana wersji danych źródła, takie, że może zostać porównane z `String.Compare()`. Format ten jest spójna we wszystkich wersjach dostawcy, aby uniemożliwić sortowania między wersjami 1 i 2 w wersji 10.<br /><br /> Na przykład dostawcy Oracle używa formatu "nn.nn.nn.nn.nn" dla wersji znormalizowany, co powoduje, że źródła danych programu Oracle 8i do zwrócenia "08.01.07.04.01". Program SQL Server używa typowy format "nn.nn.nnnn" firmy Microsoft.<br /><br /> W niektórych przypadkach DataSourceProductVersion i DataSourceProductVersionNormalized będzie mieć taką samą wartość. W przypadku usług OLE DB i ODBC są zawsze będą takie same jak są mapowane do tego samego wywołania funkcji w podstawowych natywnych interfejsów API.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Określa relację między kolumn w klauzuli GROUP BY i niezagregowanego kolumn na liście wyboru.|  
|IdentifierPattern|string|Wyrażenie regularne, który jest zgodny z identyfikatorem i ma wartość dopasowania identyfikatora. Na przykład "[A-Za-z0-9_ #$]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Wskazuje, czy-cytowane identyfikatory są traktowane jako wielkość liter czy nie.|  
|OrderByColumnsInSelect|bool|Określa, czy kolumny w klauzuli ORDER BY muszą być na liście wyboru. Wartość true wskazuje, że są one wymagane w liście wyboru, wartość false wskazuje, nie są wymagane na liście wybierz opcję.|  
|ParameterMarkerFormat|string|Ciąg formatu, który reprezentuje sposób formatowania parametru.<br /><br /> Jeśli parametry nazwane są obsługiwane przez źródło danych, pierwszy symbol zastępczy w tym ciągu powinna być gdzie powinny być sformatowane nazwy parametru.<br /><br /> Na przykład, jeśli źródło danych oczekuje parametrów o nazwie i z prefiksem ":" to ":{0}". Podczas formatowania to nazwą parametru "p1" wynikowy ciąg jest ": p1".<br /><br /> Jeśli źródło danych oczekuje, że parametry prefiksem "\@", ale nazwy już je uwzględnić, będzie to "{0}" oraz wynikiem formatowanie parametr o nazwie "\@p1" będzie po prostu "\@p1".<br /><br /> Dla źródeł danych, które nie oczekują nazwanych parametrów i oczekiwane użycie "?" znak, ciąg formatu, który można określić tylko '?', która będzie ignorować nazwę parametru. Dla OLE DB zostanie zwrócona '?'.|  
|ParameterMarkerPattern|string|Wyrażenie regularne dopasowuje znacznika parametrów. Ma wartość dopasowania nazwy parametru, jeśli istnieje.<br /><br /> Na przykład, jeśli parametry nazwane są obsługiwane w "\@" znaku wiodącego, która zostanie dodana w nazwie parametru to: "(\@[A-Za-z0-9_ ##] *)".<br /><br /> Jednak jeśli parametry nazwane są obsługiwane za pomocą ":" znaku wiodącego i nie jest częścią nazwy parametru, będzie to: ": ([A-Za-z0-9_$ #]\*)".<br /><br /> Oczywiście, jeśli źródło danych nie obsługuje parametrów nazwanych, po prostu to "?".|  
|ParameterNameMaxLength|int|Maksymalna długość nazwy parametru w znakach. Program Visual Studio oczekuje, że jeśli nazwy parametrów są obsługiwane, wartość minimalna, maksymalna długość to 30 znaków.<br /><br /> Jeśli źródło danych nie obsługuje parametrów nazwanych, ta właściwość zwraca wartość zero.|  
|ParameterNamePattern|string|Wyrażenie regularne pasuje do nazwy prawidłowego parametru. Różne źródła danych mają różne reguły dotyczące znaków, które mogą być używane dla nazw parametrów.<br /><br /> Visual Studio oczekuje, że jeśli nazwy parametrów są obsługiwane, znaki "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" są Minimalny obsługiwany zestaw znaków, które są prawidłowe dla nazw parametrów.|  
|QuotedIdentifierPattern|string|Wyrażenie regularne, który odpowiada cytowanego identyfikatora i wartością dopasowania identyfikatora bez cudzysłowów. Na przykład, jeśli źródło danych podwójne cudzysłowy są używane do identyfikowania identyfikatory w cudzysłowach, będzie to: "(([^\\"]&#124;\\"\\") *) ".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Wskazuje, czy identyfikatory w cudzysłowach, są traktowane jako wielkość liter czy nie.|  
|StatementSeparatorPattern|string|Wyrażenie regularne dopasowuje separatorem instrukcji.|  
|StringLiteralPattern|string|Wyrażenie regularne pasuje do ciągu literału i ma wartość dopasowania sam literału. Na przykład, jeśli źródło danych używane pojedynczym cudzysłowie, aby zidentyfikować ciągi, będzie to: "('([^']&#124;'') *") ""|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Określa, jakie rodzaje instrukcji join SQL są obsługiwane przez źródło danych.|  
  
## <a name="datatypes"></a>Typy danych  
 Ta kolekcja ujawnia informacji o schemacie o typach danych, które są obsługiwane przez bazę danych programu .NET Framework ostawca zarządzany jest obecnie połączony.  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|TypeName|string|Nazwa typu danych specyficznego dla dostawcy.|  
|ProviderDbType|int|Wartość typu właściwe dla dostawcy, które mają być używane podczas określania typu parametru. Na przykład SqlDbType.Money lub OracleType.Blob.|  
|ColumnSize|long|Długość nieliczbową kolumna lub parametr odnosi się do maksymalnej lub długość dla tego typu zdefiniowano przez dostawcę.<br /><br /> Danych znakowych jest maksymalną lub zdefiniowana długości w jednostkach, zdefiniowane przez źródło danych. Oracle korzysta z koncepcji określając długość, a następnie określając rozmiar rzeczywisty magazyn dla niektórych typów danych znakowych. Definiuje tylko długości w jednostkach na oprogramowanie Oracle.<br /><br /> Dla typów danych daty i godziny to długość reprezentacji w postaci ciągu (przy założeniu precyzja maksymalna dozwolona składnika ułamków sekund).<br /><br /> Jeśli typ danych jest wartością liczbową, jest górną granicę na maksymalna dokładność typu danych.|  
|CreateFormat|string|Ciąg formatu, który pozwala dodać tę kolumnę do instrukcji definicji danych, takie jak CREATE TABLE. Każdy element w tablicy tworzenie powinna być reprezentowana przez "parametr znacznik" w ciągu formatu.<br /><br /> Na przykład SQL typ danych dziesiętnych musi dokładności i skali. W tym przypadku wyniesie ciąg formatu "DZIESIĘTNY ({0},{1})".|  
|CreateParameters|string|Parametry tworzenia, które należy określić podczas tworzenia tego typu danych kolumny. Każdy parametr tworzenia znajduje się w ciągu, rozdzielone przecinkami w kolejności, w której mają być dostarczone.<br /><br /> Na przykład SQL typ danych dziesiętnych musi dokładności i skali. W tym przypadku parametry tworzenia powinien zawierać ciąg "dokładność, skala".<br /><br /> Za pomocą polecenia tekstu do utworzenia DZIESIĘTNĄ kolumny z 10 dokładności i skali 2 wartości kolumny CreateFormat może być dziesiętnych ({0},{1}) "i DECIMAL(10,2) specyfikacji kompletnego typu.|  
|Typ danych|string|Nazwa typu .NET Framework o typie danych.|  
|IsAutoincrementable|bool|TRUE — wartości danych tego typu może być zwiększenie automatycznie.<br /><br /> FALSE — wartości danych tego typu może nie być zwiększenie automatycznie.<br /><br /> Należy pamiętać, że to jedynie wskazuje, czy kolumnę danych tego typu mogą być automatyczne zwiększanie nie, że wszystkie kolumny tego typu są automatycznie — zwiększanie.|  
|IsBestMatch|bool|TRUE — typ danych jest najlepsze dopasowanie między wszystkie typy danych w magazynie danych i typ danych .NET Framework, które są wskazywane przez wartość w kolumnie Typ danych.<br /><br /> FALSE — typ danych nie jest najlepsze dopasowanie.<br /><br /> Dla każdego zestawu wierszy, w których wartość kolumny typu danych jest taka sama kolumna IsBestMatch jest ustawiona wartość true tylko w jednym wierszu.|  
|IsCaseSensitive|bool|TRUE — typ danych to typ znaku i jest uwzględniana wielkość liter.<br /><br /> FALSE — typ danych nie jest to typ znaku lub nie jest rozróżniana wielkość liter.|  
|IsFixedLength|bool|TRUE — kolumny tego typu danych, utworzonych przez języka definicji danych (DDL) będą miały o stałej długości.<br /><br /> FALSE — kolumny tego typu danych, utworzonych przez aparat DDL będą się o zmiennej długości.<br /><br /> DBNull.Value—It jest nieznany, czy dostawca będzie zmapowana to pole z kolumną o stałej długości lub o zmiennej długości.|  
|IsFixedPrecisionScale|bool|TRUE — typ danych ma stały dokładności i skali.<br /><br /> FALSE — typ danych nie ma stałej dokładności i skali.|  
|IsLong|bool|TRUE — typ danych zawiera bardzo dużo danych. Definicja bardzo dużo danych jest specyficzny dla dostawcy.<br /><br /> FALSE — typ danych nie zawiera bardzo dużo danych.|  
|IsNullable|bool|TRUE — typ danych ma wartość null.<br /><br /> FALSE — typ danych nie jest null.<br /><br /> DBNull.Value—It jest nieznany, czy typ danych ma wartość null.|  
|IsSearchable|bool|TRUE — typ danych może być używany w klauzuli WHERE, za pomocą dowolnego operatora except w predykacie LIKE.<br /><br /> FALSE — typ danych nie można używać w klauzuli WHERE, za pomocą dowolnego operatora except w predykacie LIKE.|  
|IsSearchableWithLike|bool|TRUE — typ danych może być używany z klauzulą LIKE<br /><br /> FALSE — typ danych nie można używać z klauzulą LIKE.|  
|IsUnsigned|bool|TRUE — typ danych jest niepodpisany.<br /><br /> FALSE — typ danych jest podpisany.<br /><br /> DBNull.Value—Not mające zastosowanie do typu danych.|  
|MaximumScale|short|Jeśli wskaźnik typu jest typu liczbowego, to maksymalną liczbę cyfr po prawej stronie przecinka dziesiętnego. W przeciwnym razie jest to DBNull.Value.|  
|MinimumScale|short|Jeśli wskaźnik typu jest typu liczbowego, to minimalną liczbę cyfr po prawej stronie przecinka dziesiętnego. W przeciwnym razie jest to DBNull.Value.|  
|IsConcurrencyType|bool|PRAWDA — typ danych jest aktualizowana przez bazę danych, za każdym razem, gdy wiersz jest zmienione, a wartość kolumny różni się od wszystkie poprzednie wartości<br /><br /> FALSE — typ danych jest Uwaga zaktualizowane przez bazę danych, za każdym razem, gdy zostanie zmieniony wiersz<br /><br /> DBNull.Value — baza danych nie obsługuje tego typu, typu danych|  
|IsLiteralSupported|bool|PRAWDA — typ danych może być wyrażona jako literał<br /><br /> FALSE — typ danych nie może być wyrażona jako literał|  
|LiteralPrefix|string|Prefiks stosowany do danej literału.|  
|LiteralSuffix|string|Sufiks zastosowane do danej literału.|  
|NativeDataType|String|NativeDataType jest OLE DB określonej kolumny do udostępniania typ OLE DB o typie danych.|  
  
## <a name="restrictions"></a>Ograniczenia  
 Ta kolekcja schematów udostępnianych informacji dotyczących ograniczeń, które są obsługiwane przez zarządzanego dostawcy .NET Framework, który jest obecnie używany do łączenia z bazą danych.  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|collectionName|string|Nazwa kolekcji, która dotyczy tych ograniczeń.|  
|RestrictionName|string|Nazwa ograniczenia w kolekcji.|  
|RestrictionDefault|string|Ignorowane.|  
|RestrictionNumber|int|Rzeczywistej lokalizacji ograniczenia kolekcje, które to ograniczenie konkretnego, który znajduje się w.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Ta kolekcja schematów udostępnia informacji na temat słów, które są zarezerwowane przez bazę danych programu .NET Framework zarządzanego dostawcy, który jest obecnie połączony.  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|ReservedWord|string|Słowa zarezerwowanego właściwe dla dostawcy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [GetSchema i kolekcje schematów](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](http://go.microsoft.com/fwlink/?LinkId=217917)
