---
title: "Typowe kolekcje schematów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 893093900b3fc4276f9bd7143b1f235a5ba98f90
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="common-schema-collections"></a>Typowe kolekcje schematów
Typowe kolekcje schematów są kolekcji schematu, które są implementowane przez każdego z dostawców zarządzane w programie .NET Framework. Można zbadać zarządzanego dostawcy .NET Framework, można ustalić listy kolekcji schematu obsługiwanych przez wywołanie metody **GetSchema** metody bez argumentów lub nazwą kolekcji schematów "MetaDataCollections". Spowoduje to zwrócenie <xref:System.Data.DataTable> z listą kolekcji obsługiwanych schematu, liczba ograniczeń obsługiwanych przez każdy z nich i części identyfikatora, które korzystają z. Te kolekcje, opis wszystkich wymaganych kolumn. Aby dodać dodatkowe kolumny, jeśli chcą mogą dostawców. Na przykład `SqlClient` i `OracleClient` ParameterName można dodać do kolekcji ograniczeń.  
  
 Jeśli nie można ustalić wartości kolumny wymagane jest dostawcę, zwróci wartość null.  
  
 Aby uzyskać więcej informacji o korzystaniu z **GetSchema** metod, zobacz [GetSchema i kolekcje schematów](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Ta kolekcja schematu przedstawia informacje o wszystkich kolekcji schematu obsługiwane przez zarządzanego dostawcy .NET Framework, która jest aktualnie używana do łączenia z bazą danych.  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|CollectionName|string|Nazwa kolekcji do przekazania do **GetSchema** metodę, aby powrócić do kolekcji.|  
|NumberOfRestrictions|int|Liczba ograniczeń, które mogą zostać określone dla kolekcji.|  
|NumberOfIdentifierParts|int|Liczba części w nazwie obiektu złożonego identyfikator/bazy danych. Na przykład w programie SQL Server, będzie to 3 dla tabel i 4 dla kolumn. W oprogramowaniu Oracle byłoby 2 dla tabel i 3 dla kolumn.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Ta kolekcja schematu przedstawia informacje o źródle danych, podłączoną do zarządzanego dostawcy jest obecnie w programie .NET Framework.  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|string|Wyrażenie regularne do dopasowania złożonego separatorów w identyfikatorze złożonego. Na przykład "\\." (dla programu SQL Server) lub "@&#124; \\." (dla Oracle).<br /><br /> Identyfikator złożony jest zwykle do czego służy nazwa obiektu bazy danych, na przykład: pubs.dbo.authors lub pubs@dbo.authors.<br /><br /> Dla programu SQL Server, należy użyć wyrażenia regularnego "\\.". OracleClient, użyj "@&#124; \\.".<br /><br /> Użyj Catalog_name_seperator dla ODBC.<br /><br /> OLE DB używaj DBLITERAL_CATALOG_SEPARATOR lub DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|string|Nazwa produktu, dostęp do dostawcy, takie jak "Oracle" lub "SQLServer".|  
|DataSourceProductVersion|string|Wskazuje wersję produktu, dostęp do dostawcy, w formacie native źródeł danych, a nie w formacie Microsoft.<br /><br /> W niektórych przypadkach DataSourceProductVersion i DataSourceProductVersionNormalized będzie mieć taką samą wartość. W przypadku OLE DB i ODBC są jest zawsze taki sam są mapowane na to samo wywołanie funkcji w podstawowym natywnego interfejsu API.|  
|DataSourceProductVersionNormalized|string|Znormalizowane wersji danych źródła, w taki sposób, że mogą zostać porównane z `String.Compare()`. Ten format jest zgodny dla wszystkich wersji dostawcy, aby zapobiec sortowania między 1 a wersją 2 w wersji 10.<br /><br /> Na przykład dostawca programu Oracle używa formatu "nn.nn.nn.nn.nn" dla wersji znormalizowane, co powoduje, że źródła danych Oracle 8i do zwrócenia "08.01.07.04.01". Program SQL Server używa typowy format "nn.nn.nnnn" firmy Microsoft.<br /><br /> W niektórych przypadkach DataSourceProductVersion i DataSourceProductVersionNormalized będzie mieć taką samą wartość. W przypadku OLE DB i ODBC są jest zawsze taki sam są mapowane na to samo wywołanie funkcji w podstawowym natywnego interfejsu API.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Określa relację między kolumn w klauzuli GROUP BY i poszczególnych kolumn na liście wyboru.|  
|IdentifierPattern|string|Wyrażenie regularne, który jest zgodny z identyfikatorem i ma wartość dopasowania identyfikatora. Na przykład "[A-Za-z0-9_ #$]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Wskazuje, czy-cytowane identyfikatory są traktowane jako wielkość liter, czy nie.|  
|OrderByColumnsInSelect|bool|Określa, czy na liście wyboru musi być kolumn w klauzuli ORDER BY. Wartość true wskazuje, że są one wymagane na liście wybierz wartość false wskazuje, nie są wymagane się na liście wyboru.|  
|ParameterMarkerFormat|string|Ciąg formatu, który reprezentuje sposób formatowania parametr.<br /><br /> Jeśli nazwane parametry są obsługiwane przez źródło danych, pierwszego symbolu zastępczego w tym ciągu powinna być gdzie powinien być sformatowany nazwę parametru.<br /><br /> Na przykład, jeśli źródło danych oczekuje parametrów o nazwie i jest poprzedzony prefiksem ":" to ": {0}". Podczas formatowania to nazwa parametru "p1" powstałe w ten sposób jest ciąg ": p1".<br /><br /> Jeśli źródło danych oczekuje parametrów się prefiksem "@", ale nazwy już je uwzględnić, będzie to wartość równa "{0}" i wynik formatowania parametr o nazwie "@p1"po prostu byłoby"@p1".<br /><br /> Dla źródeł danych, które nie oczekują nazwane parametry i oczekują użycie "?" Ciąg formatu, który można określić tylko znak "?", który będzie ignorować nazwę parametru. Dla OLE DB zwróconych '?'.|  
|ParameterMarkerPattern|string|Wyrażenie regularne dopasowuje znacznika parametru. Jeśli będzie mieć wartość dopasowania nazwę parametru.<br /><br /> Na przykład, jeśli nazwane parametry są obsługiwane przez "@" wiodącego znak, który zostanie uwzględniony w nazwie parametru to: "(@[A-Za-z0-9_ ##] *)".<br /><br /> Jednak jeśli nazwane parametry są obsługiwane przez ":" jak wiodącego znaków i nie jest częścią nazwy parametru, to: ": ([A-Za-z0-9_$ #]\*)".<br /><br /> Oczywiście jeśli źródło danych nie obsługuje parametrów nazwanych, po prostu to "?".|  
|ParameterNameMaxLength|int|Maksymalna długość nazwy parametru w znakach. Visual Studio oczekuje, że jeśli nazwy parametrów są obsługiwane, wartość minimalna długość jest 30 znaków.<br /><br /> Jeśli źródło danych nie obsługuje parametrów nazwanych, ta właściwość zwraca zero.|  
|ParameterNamePattern|string|Wyrażenie regularne pasuje do nazw poprawny parametr. Różnych źródeł danych mają różne zasady dotyczące znaków, które mogą być używane dla nazw parametrów.<br /><br /> Visual Studio oczekuje, że jeśli nazwy parametrów są obsługiwane, znaki "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" są obsługiwane minimalnego zestawu znaków, które są prawidłowe dla nazw parametrów.|  
|QuotedIdentifierPattern|string|Wyrażenie regularne dopasowuje identyfikatora ujętego w cudzysłów, który ma wartość dopasowania identyfikatora bez cudzysłowów. Na przykład, jeśli źródło danych używane podwójnych cudzysłowów do identyfikowania identyfikatory w cudzysłowach, to: "(([^\\"] &#124;\\" \\")*)".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Wskazuje, czy identyfikatory w cudzysłowach są traktowane jako wielkość liter, czy nie.|  
|StatementSeparatorPattern|string|Wyrażenie regularne dopasowuje separatora instrukcji.|  
|StringLiteralPattern|string|Wyrażenie regularne odpowiada literału ciągu, który ma wartość literal, sam dopasowania. Na przykład, jeśli źródło danych umożliwia identyfikowanie ciągi przez pojedynczego cudzysłowu, to: "(" ([^'] &#124; ") *')"'|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Określa, jakie typy instrukcji SQL sprzężenia są obsługiwane przez źródło danych.|  
  
## <a name="datatypes"></a>Typy danych  
 Te informacje ujawnia kolekcji schematu o typach danych, które są obsługiwane przez bazę danych czy programu .NET Framework zarządzanego dostawcy jest aktualnie połączony z.  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|TypeName|string|Nazwa typu danych specyficznych dla dostawcy.|  
|ProviderDbType|int|Wartość typu specyficznych dla dostawcy, które mają być używane podczas określania typu parametru. Na przykład SqlDbType.Money lub OracleType.Blob.|  
|ColumnSize|long|Długość nieliczbowy kolumna lub parametr odwołuje się do maksymalnej lub długość dla tego typu zdefiniowano przez dostawcę.<br /><br /> Dla danych znakowych jest maksymalną lub zdefiniowana długość w jednostkach, zdefiniowany przez źródło danych. Oracle korzysta z koncepcji określania długości, a następnie określając rozmiar rzeczywisty magazyn dla niektórych typów danych znakowych. To definiuje tylko w jednostkach dla programu Oracle.<br /><br /> Dla typów danych daty i godziny to długość ciągu reprezentującego (przy założeniu dozwolonych precyzja maksymalna części ułamkowych części sekundy).<br /><br /> Jeśli typ danych liczbowych, jest górna granica precyzja maksymalna typu danych.|  
|CreateFormat|string|Ciąg formatu, który reprezentuje jak dodać tę kolumnę do instrukcji definicji danych, takie jak CREATE TABLE. Każdy element tablicy tworzenie powinny być reprezentowane przez "parametr znacznik" w ciągu formatu.<br /><br /> Na przykład SQL typu danych dziesiętnych musi dokładności i skali. Ciąg formatu, który będzie w tym przypadku "DECIMAL({0},{1})".|  
|CreateParameters|string|Parametry tworzenia, które można określić podczas tworzenia tego typu danych kolumny. Każdy parametr tworzenia znajduje się w ciągu, rozdzielone przecinkami w kolejności, które mają być dostarczone.<br /><br /> Na przykład SQL typu danych dziesiętnych musi dokładności i skali. W takim przypadku parametry tworzenia powinny zawierać ciąg "dokładność, skala".<br /><br /> W poleceniu tekstowym, aby utworzyć kolumnę DZIESIĘTNĄ z 10 dokładności i skali 2, wartość kolumny CreateFormat może być DECIMAL({0},{1}) "i specyfikacja typu pełną byłaby DECIMAL(10,2).|  
|Typ danych|string|Nazwa typu .NET Framework typu danych.|  
|IsAutoincrementable|bool|TRUE — wartości tego typu danych może być zwiększany automatycznie.<br /><br /> FALSE — wartości tego typu danych nie może być zwiększany automatycznie.<br /><br /> Należy pamiętać, że to jedynie wskazuje, czy kolumny tego typu danych mogą być automatycznie zwiększany nie że wszystkie kolumny tego typu są automatycznie przyrostową.|  
|IsBestMatch|bool|TRUE — typ danych jest najlepszego dopasowania wszystkich typów danych w magazynie danych i typ danych .NET Framework, określony przez wartość w kolumnie typu danych.<br /><br /> FALSE — typ danych nie jest najlepsze dopasowanie.<br /><br /> Dla każdego zestawu wierszy, w których wartość elementu DataType kolumny jest taka sama kolumna IsBestMatch ma ustawioną wartość true tylko w jednym wierszu.|  
|IsCaseSensitive|bool|TRUE — typ danych jest typu znaków i jest rozróżniana wielkość liter.<br /><br /> FALSE — typ danych nie jest typem znaku lub nie jest rozróżniana wielkość liter.|  
|IsFixedLength|bool|TRUE — kolumny tego typu danych utworzone za pomocą języka definicji danych (DDL) będą miały o stałej długości.<br /><br /> FALSE — będzie kolumny tego typu danych utworzone przy użyciu kodu DDL o zmiennej długości.<br /><br /> DBNull.Value—It nie jest znany, czy dostawca przypisze to pole z kolumną o stałej długości lub o zmiennej długości.|  
|IsFixedPrecisionScale|bool|TRUE — typ danych ma stały precyzję i skalę.<br /><br /> FALSE — typ danych nie ma stałej precyzję i skalę.|  
|IsLong|bool|TRUE — typ danych zawiera bardzo dużo danych. Definicja bardzo dużo danych jest specyficznych dla dostawcy.<br /><br /> FALSE — typ danych nie zawiera bardzo dużo danych.|  
|IsNullable|bool|TRUE — typ danych dopuszcza wartość null.<br /><br /> FALSE — typ danych nie jest dopuszczalna.<br /><br /> DBNull.Value—It nie jest znany, czy typ danych dopuszcza wartość null.|  
|IsSearchable|bool|TRUE — typ danych może służyć w klauzuli WHERE z dowolnego operatora except w predykacie LIKE.<br /><br /> FALSE — typ danych nie można używać w klauzuli WHERE z dowolnego operatora except w predykacie LIKE.|  
|IsSearchableWithLike|bool|TRUE — typu danych można używać z klauzulą LIKE<br /><br /> FALSE — typ danych nie można używać z klauzulą LIKE.|  
|IsUnsigned|bool|TRUE — typ danych nie jest podpisany.<br /><br /> FALSE — typ danych jest podpisany.<br /><br /> DBNull.Value—Not dla typu danych.|  
|MaximumScale|short|Jeśli typ wskaźnika typu liczbowego, to maksymalna liczba cyfr z prawej strony punktu dziesiętnego. W przeciwnym razie jest to DBNull.Value.|  
|MinimumScale|short|Jeśli typ wskaźnika typu liczbowego, to minimalną liczbę cyfr z prawej strony punktu dziesiętnego. W przeciwnym razie jest to DBNull.Value.|  
|IsConcurrencyType|bool|PRAWDA — typ danych jest aktualizowany przez bazę danych, za każdym razem wiersza zostanie zmieniona i wartość kolumny różni się od wszystkie poprzednie wartości<br /><br /> FAŁSZ — typ danych jest Uwaga zaktualizowane przez bazę danych, za każdym razem, gdy wiersza zostanie zmieniona.<br /><br /> DBNull.Value — bazy danych nie obsługuje tego typu typu danych|  
|IsLiteralSupported|bool|PRAWDA — typ danych może zostać wyrażona jako literału<br /><br /> FAŁSZ — typ danych nie może zostać wyrażona jako literału|  
|LiteralPrefix|string|Prefiks stosowany do danej literału.|  
|LiteralSuffix|string|Sufiks stosowane do danej literału.|  
|NativeDataType|String|NativeDataType jest kolumną określonych OLE DB dla udostępnianie typu OLE DB o typie danych.|  
  
## <a name="restrictions"></a>Ograniczenia  
 Ta kolekcja schematu widoczne informacji na temat ograniczeń, które są obsługiwane przez zarządzanego dostawcy .NET Framework, która jest aktualnie używana do łączenia z bazą danych.  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|CollectionName|string|Nazwa kolekcji, którego dotyczą te ograniczenia.|  
|RestrictionName|string|Nazwa ograniczenia w kolekcji.|  
|RestrictionDefault|string|Ignorowane.|  
|RestrictionNumber|int|Rzeczywista lokalizacja ograniczenia kolekcje, które znajduje się w szczególności ograniczenie.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Ta kolekcja schemat przedstawia informacji na temat słów, które zostały zastrzeżone przez bazę danych programu .NET Framework zarządzanego dostawcy, który jest aktualnie połączony z.  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|ReservedWord|string|Słowa zarezerwowanego właściwe dla dostawcy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [GetSchema i kolekcje schematów](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
