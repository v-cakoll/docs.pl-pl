---
title: Typowe kolekcje schematów
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: 0b23164b56c6fefc6c258f313e9e17b156605518
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786787"
---
# <a name="common-schema-collections"></a>Typowe kolekcje schematów
Typowe kolekcje schematów to kolekcje schematów zaimplementowane przez każdego z .NET Framework zarządzanych dostawców. Można wysłać zapytanie do dostawcy zarządzanego .NET Framework, aby określić listę obsługiwanych kolekcji schematów przez wywołanie metody **GetSchema** bez argumentów lub z nazwą kolekcji schematów "MetaDataCollections". Spowoduje to zwrócenie <xref:System.Data.DataTable> listy obsługiwanych kolekcji schematów, liczbę ograniczeń, które one obsługują, oraz liczbę używanych przez nich części identyfikatora. Kolekcje te opisują wszystkie wymagane kolumny. W razie potrzeby dostawcy mogą dodawać dodatkowe kolumny. Na przykład, `SqlClient` a `OracleClient` następnie Dodaj parametrname do kolekcji ograniczenia.  
  
 Jeśli dostawca nie jest w stanie określić wartości wymaganej kolumny, zwróci wartość null.  
  
 Aby uzyskać więcej informacji o korzystaniu z metod **GetSchema** , zobacz [GetSchema and Schema Collections](getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Ta kolekcja schematów ujawnia informacje o wszystkich kolekcjach schematów obsługiwanych przez .NET Framework dostawcę zarządzanego, który jest obecnie używany do łączenia się z bazą danych.  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|collectionName|string|Nazwa kolekcji do przekazania do metody **GetSchema** w celu zwrócenia kolekcji.|  
|NumberOfRestrictions|int|Liczba ograniczeń, które mogą być określone dla kolekcji.|  
|NumberOfIdentifierParts|int|Liczba części w złożonej identyfikatorze/nazwie obiektu bazy danych. Na przykład w SQL Server będzie to 3 dla tabel i 4 dla kolumn. W oprogramowaniu Oracle w przypadku kolumn w tabelach i 3 zostanie wyszukana 2.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Ta kolekcja schematów zawiera informacje o źródle danych, z którym jest obecnie nawiązywane połączenie z dostawcą zarządzanym przez .NET Framework.  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|string|Wyrażenie regularne dopasowuje złożone separatory w identyfikatorze złożonym. Na przykład "\\." (na SQL Server) lub "\@&#124;\\." (w przypadku oprogramowania Oracle).<br /><br /> Identyfikator złożony jest zazwyczaj używany jako nazwa obiektu bazy danych, na przykład: pubs. dbo. Authors lub pubs\@dbo. Authors.<br /><br /> Aby uzyskać SQL Server, użyj wyrażenia regularnego\\".". W przypadku OracleClient Użyj "\@&#124;\\.".<br /><br /> Dla ODBC Użyj Catalog_name_seperator.<br /><br /> W przypadku OLE DB Użyj DBLITERAL_CATALOG_SEPARATOR lub DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|string|Nazwa produktu, do którego uzyskuje dostęp dostawca, na przykład "Oracle" lub "SQLServer".|  
|DataSourceProductVersion|string|Wskazuje wersję produktu, do której uzyskuje dostęp dostawca, w formacie natywnym źródła danych, a nie w formacie Microsoft.<br /><br /> W niektórych przypadkach DataSourceProductVersion i DataSourceProductVersionNormalized będą takie same. W przypadku OLE DB i ODBC są one zawsze takie same, jak te, które są mapowane na to samo wywołanie funkcji w źródłowym natywnym interfejsie API.|  
|DataSourceProductVersionNormalized|string|Znormalizowana wersja źródła danych, dzięki czemu można ją porównać z `String.Compare()`. Ten format jest spójny dla wszystkich wersji dostawcy, aby zapobiec sortowaniu między wersjami 1 i 2.<br /><br /> Na przykład dostawca Oracle używa formatu "NN. nn. nn. nn. nn" dla jego znormalizowanej wersji, co powoduje, że źródło danych Oracle 8i zwróci wartość "08.01.07.04.01". SQL Server używa typowego formatu "NN. nn. nnnn" firmy Microsoft.<br /><br /> W niektórych przypadkach wartości DataSourceProductVersion i DataSourceProductVersionNormalized będą takie same. W przypadku OLE DB i ODBC są one zawsze takie same, jak są mapowane na to samo wywołanie funkcji w ramach podstawowego natywnego interfejsu API.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Określa relację między kolumnami w klauzuli GROUP BY i niezagregowanymi kolumnami na liście wyboru.|  
|IdentifierPattern|string|Wyrażenie regularne, które pasuje do identyfikatora i ma wartość Match identyfikatora. Na przykład "[A-za-Z0-9_ # $]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Wskazuje, czy identyfikatory nieujęte w cudzysłów są traktowane jako uwzględniające wielkość liter.|  
|OrderByColumnsInSelect|bool|Określa, czy kolumny w klauzuli ORDER BY muszą znajdować się na liście wyboru. Wartość true wskazuje, że muszą znajdować się na liście wyboru, wartość false wskazuje, że nie muszą znajdować się na liście wyboru.|  
|ParameterMarkerFormat|string|Ciąg formatu, który reprezentuje sposób formatowania parametru.<br /><br /> Jeśli nazwane parametry są obsługiwane przez źródło danych, pierwszy symbol zastępczy w tym ciągu powinien być, gdzie nazwa parametru powinna być sformatowana.<br /><br /> Na przykład, jeśli źródło danych oczekuje, że parametry są nazwane i poprzedzone prefiksem ":", może to być ":{0}". Podczas formatowania przy użyciu nazwy parametru "P1" otrzymany ciąg ma wartość ":p 1".<br /><br /> Jeśli źródło danych oczekuje, że parametry są poprzedzone prefiksem\@"", ale te nazwy już je zawierają, może to być "{0}", a wynik formatowania parametru o nazwie "\@P1" będzie po prostu "\@P1".<br /><br /> Dla źródeł danych, które nie oczekują parametrów nazwanych i oczekują użycia "?" znak, ciąg formatu może być określony jako po prostu "?", co spowoduje zignorowanie nazwy parametru. Na OLE DB zwracamy "?".|  
|ParameterMarkerPattern|string|Wyrażenie regularne zgodne ze znacznikiem parametru. Będzie ona mieć wartość odpowiadającą nazwie parametru, jeśli istnieje.<br /><br /> Na przykład jeśli nazwane parametry są obsługiwane za pomocą znaku "\@", który zostanie uwzględniony w nazwie parametru, może to być: "(\@[A-za-Z0-9_ $ #] *)".<br /><br /> Jeśli jednak nazwane parametry są obsługiwane za pomocą znaku ":", jako znak ołowiu i nie jest częścią nazwy parametru, może to być: ":([A-za-Z0-9_ $ #]\*)".<br /><br /> Oczywiście, jeśli źródło danych nie obsługuje parametrów nazwanych, może to być po prostu "?".|  
|ParameterNameMaxLength|int|Maksymalna długość nazwy parametru w znakach. Program Visual Studio oczekuje, że jeśli nazwy parametrów są obsługiwane, minimalna wartość dla maksymalnej długości to 30 znaków.<br /><br /> Jeśli źródło danych nie obsługuje parametrów nazwanych, ta właściwość zwraca wartość zero.|  
|ParameterNamePattern|string|Wyrażenie regularne, które jest zgodne z prawidłowymi nazwami parametrów. Różne źródła danych mają różne reguły dotyczące znaków, które mogą być używane w nazwach parametrów.<br /><br /> Program Visual Studio oczekuje, że jeśli nazwy parametrów są obsługiwane, znaki "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" są minimalnym obsługiwanym zestawem znaków, które są prawidłowe dla nazw parametrów.|  
|QuotedIdentifierPattern|string|Wyrażenie regularne zgodne z identyfikatorem ujętym w cudzysłów i ma wartość dopasowania samego identyfikatora bez cudzysłowów. Na przykład, jeśli źródło danych używa podwójnych cudzysłowów do identyfikacji identyfikatorów w cudzysłowie, może to być: "((\\[^&#124;\\"\\] "") *) ".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Wskazuje, czy identyfikatory ujęte w cudzysłów są traktowane jako uwzględniające wielkość liter.|  
|StatementSeparatorPattern|string|Wyrażenie regularne, które jest zgodne z separatorem instrukcji.|  
|StringLiteralPattern|string|Wyrażenie regularne, które pasuje do literału ciągu i ma wartość Match samego literału. Na przykład, jeśli źródło danych używa pojedynczego cudzysłowu do identyfikacji ciągów, może to być: "(" ([^ "]&#124;" ") *") ""|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Określa, jakie typy instrukcji sprzężenia SQL są obsługiwane przez źródło danych.|  
  
## <a name="datatypes"></a>Typy danych  
 Ta kolekcja schematów ujawnia informacje o typach danych, które są obsługiwane przez bazę danych, z którą jest aktualnie połączony Dostawca zarządzany .NET Framework.  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|TypeName|string|Nazwa typu danych specyficznego dla dostawcy.|  
|ProviderDbType|int|Wartość typu specyficznego dla dostawcy, która ma być używana podczas określania typu parametru. Na przykład SqlDbType. Money lub OracleType. blob.|  
|ColumnSize|long|Długość kolumny lub parametru nieliczbowego oznacza wartość maksymalną lub długość zdefiniowaną dla tego typu przez dostawcę.<br /><br /> W przypadku danych znakowych jest to maksymalna lub zdefiniowana długość w jednostkach zdefiniowanej przez źródło danych. Oracle ma koncepcję określania długości, a następnie określania rzeczywistego rozmiaru magazynu dla niektórych typów danych. Definiuje to tylko długość w jednostkach dla programu Oracle.<br /><br /> W przypadku typów danych daty i godziny jest to długość reprezentująca ciąg (przy założeniu maksymalnej dozwolonej dokładności składnika ułamka sekund).<br /><br /> Jeśli typ danych jest wartością numeryczną, jest to górna granica maksymalnej precyzji typu danych.|  
|CreateFormat|string|Ciąg formatu, który reprezentuje, jak dodać tę kolumnę do instrukcji definicji danych, takiej jak CREATE TABLE. Każdy element w tablicy parametrów musi być reprezentowany przez "znacznik parametru" w ciągu formatu.<br /><br /> Na przykład liczba dziesiętna typu danych SQL wymaga dokładności i skali. W tym przypadku ciąg formatu to "DECIMAL ({0},{1})".|  
|Parametry|string|Parametry tworzenia, które muszą zostać określone podczas tworzenia kolumny tego typu danych. Każdy parametr tworzenia jest wymieniony w ciągu, rozdzielony przecinkami w kolejności, w jakiej mają być dostarczone.<br /><br /> Na przykład liczba dziesiętna typu danych SQL wymaga dokładności i skali. W takim przypadku parametry tworzenia powinny zawierać ciąg "Precision, Scale".<br /><br /> W poleceniu tekstowym, aby utworzyć kolumnę dziesiętną z dokładnością 10 i skalą 2, wartość kolumny w formacie, może być dziesiętna ({0},{1}), a kompletna specyfikacja typu powinna być dziesiętna (10, 2).|  
|DataType|string|Nazwa typu .NET Framework typu danych.|  
|Isautoincrementd|bool|true — wartości tego typu danych mogą być stosowane do autouzupełniania.<br /><br /> false — wartości tego typu danych nie mogą być autouzupełniane.<br /><br /> Należy zauważyć, że to tylko wskazuje, czy kolumna tego typu danych może być podwyższana, a nie że wszystkie kolumny tego typu są autouzupełniane.|  
|IsBestMatch|bool|true — typ danych jest najlepszym dopasowaniem między wszystkimi typami danych w magazynie danych a typem danych .NET Framework wskazywanym przez wartość w kolumnie DataType.<br /><br /> false — typ danych nie jest najlepszym rozwiązaniem.<br /><br /> Dla każdego zestawu wierszy, w których wartość kolumny DataType jest taka sama, kolumna IsBestMatch ma wartość true tylko w jednym wierszu.|  
|IsCaseSensitive|bool|true — typ danych jest typem znaku i jest rozróżniana wielkość liter.<br /><br /> false — typ danych nie jest typem znaku lub nie jest rozróżniana wielkość liter.|  
|SqlFacetAttribute|bool|true — kolumny tego typu danych utworzone za pomocą języka definicji danych (DDL) mają stałą długość.<br /><br /> FAŁSZ — kolumny tego typu danych utworzone za pomocą DDL będą mieć zmienną długość.<br /><br /> DBNull. value — nie wiadomo, czy dostawca mapuje to pole z kolumną o stałej długości lub o zmiennej długości.|  
|IsFixedPrecisionScale|bool|true — typ danych ma stałą precyzję i skalę.<br /><br /> false — typ danych nie ma stałej precyzji i skali.|  
|ISLONG|bool|true — typ danych zawiera bardzo długie dane; Definicja bardzo długich danych jest specyficzna dla dostawcy.<br /><br /> false — typ danych nie zawiera bardzo długich danych.|  
|IsNullable|bool|true — typ danych dopuszcza wartość null.<br /><br /> false — typ danych nie dopuszcza wartości null.<br /><br /> DBNull. value — nie wiadomo, czy typ danych dopuszcza wartość null.|  
|Issearch|bool|true — typ danych może być używany w klauzuli WHERE z dowolnym operatorem, z wyjątkiem predykatu LIKE.<br /><br /> false — typ danych nie może być używany w klauzuli WHERE z dowolnym operatorem, z wyjątkiem predykatu LIKE.|  
|IsSearchableWithLike|bool|true — typ danych może być używany z predykatem LIKE<br /><br /> false — typ danych nie może być używany z predykatem LIKE.|  
|IsSigned|bool|true — typ danych jest niepodpisany.<br /><br /> false — typ danych jest podpisany.<br /><br /> DBNull. value — nie ma zastosowania do typu danych.|  
|MaximumScale|short|Jeśli wskaźnik typu jest typem liczbowym, jest to maksymalna liczba cyfr dozwolona z prawej strony punktu dziesiętnego. W przeciwnym razie jest to DBNull. Value.|  
|MinimumScale|short|Jeśli wskaźnik typu jest typem liczbowym, jest to minimalna liczba cyfr dozwolona z prawej strony punktu dziesiętnego. W przeciwnym razie jest to DBNull. Value.|  
|IsConcurrencyType|bool|true — typ danych jest aktualizowany przez bazę danych za każdym razem, gdy wiersz zostanie zmieniony i wartość kolumny różni się od wszystkich poprzednich wartości<br /><br /> false — typ danych oznacza, że baza danych jest aktualizowana za każdym razem, gdy wiersz został zmieniony<br /><br /> DBNull. Value — baza danych nie obsługuje tego typu danych.|  
|IsLiteralSupported|bool|true — typ danych może być wyrażony jako literał<br /><br /> false — typ danych nie może być wyrażony jako literał|  
|LiteralPrefix|string|Prefiks zastosowany do danego literału.|  
|LiteralSuffix|string|Sufiks stosowany do danego literału.|  
|NativeDataType|String|NativeDataType to OLE DB określona kolumna do uwidaczniania typu OLE DB danych.|  
  
## <a name="restrictions"></a>Ograniczenia  
 Ta kolekcja schematów uwidaczniaa informacje o ograniczeniach, które są obsługiwane przez .NET Framework dostawcę zarządzanego, który jest obecnie używany do łączenia się z bazą danych.  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|collectionName|string|Nazwa kolekcji, do której mają zastosowanie te ograniczenia.|  
|Ograniczeniename|string|Nazwa ograniczenia w kolekcji.|  
|RestrictionDefault|string|Ignorowane.|  
|RestrictionNumber|int|Rzeczywista lokalizacja w kolekcjach ogranicza, w których znajduje się to określone ograniczenie.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Ta kolekcja schematów zawiera informacje o wyrazach, które są zarezerwowane przez bazę danych, z którą jest aktualnie połączony dostawca .NET Framework.  
  
|ColumnName|DataType|Opis|  
|----------------|--------------|-----------------|  
|ReservedWord|string|Zastrzeżone słowo specyficzne dla dostawcy.|  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)
- [GetSchema i kolekcje schematów](getschema-and-schema-collections.md)
- [Omówienie ADO.NET](ado-net-overview.md)
