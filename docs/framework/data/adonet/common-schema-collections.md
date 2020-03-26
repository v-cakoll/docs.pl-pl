---
title: Typowe kolekcje schematów
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: b6c2c89101f3304a0cab014de2def22195541471
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249477"
---
# <a name="common-schema-collections"></a>Typowe kolekcje schematów
Typowe kolekcje schematu są kolekcje schematów, które są implementowane przez każdego z dostawców zarządzanych programu .NET Framework. Można zbadać dostawcę zarządzanego programu .NET Framework, aby określić listę obsługiwanych kolekcji schematu, wywołując metodę **GetSchema** bez argumentów lub o nazwie kolekcji schematu "MetaDataCollections". Spowoduje to <xref:System.Data.DataTable> zwrócenie a z listy obsługiwanych kolekcji schematu, liczba ograniczeń, które obsługują, a liczba części identyfikatorów, które używają. Te kolekcje opisują wszystkie wymagane kolumny. Dostawcy mogą dodawać dodatkowe kolumny, jeśli chcą. Na przykład `SqlClient` `OracleClient` i dodać ParameterName do kolekcji ograniczeń.  
  
 Jeśli dostawca nie jest w stanie określić wartości wymaganej kolumny, zwróci wartość null.  
  
 Aby uzyskać więcej informacji na temat korzystania z metod **GetSchema,** zobacz [Kolekcje GetSchema i Schema](getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections (MetaDataCollections)  
 Ta kolekcja schematów udostępnia informacje o wszystkich kolekcjach schematów obsługiwanych przez dostawcę zarządzanego programu .NET Framework, który jest obecnie używany do łączenia się z bazą danych.  
  
|nazwa_kolumny|typ_danych|Opis|  
|----------------|--------------|-----------------|  
|CollectionName|ciąg|Nazwa kolekcji, aby przekazać do **GetSchema** metody do zwrócenia kolekcji.|  
|LiczbaWycofwyciężeń|int|Liczba ograniczeń, które mogą być określone dla kolekcji.|  
|LiczbaIdentifierParts|int|Liczba części w kompozytowej nazwie obiektu identyfikatora/bazy danych. Na przykład w programie SQL Server byłoby to 3 dla tabel i 4 dla kolumn. W Oracle byłoby to 2 dla tabel i 3 dla kolumn.|  
  
## <a name="datasourceinformation"></a>Datasourceinformation  
 Ta kolekcja schematów udostępnia informacje o źródle danych, z którymi obecnie łączy się dostawca zarządzany programu .NET Framework.  
  
|nazwa_kolumny|typ_danych|Opis|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|ciąg|Wyrażenie regularne, aby dopasować separatory złożone w identyfikatorze złożonym. Na przykład\\" ." (dla programu SQL\@ Server) lub \\"&#124;." (dla Oracle).<br /><br /> Identyfikator złożony jest zazwyczaj używany dla nazwy obiektu bazy danych, na przykład: pubs.dbo.authors lub pubs\@dbo.authors.<br /><br /> W przypadku programu SQL Server\\należy użyć wyrażenia regularnego " .". W przypadku OracleClient\@ użyj "&#124;\\.".<br /><br /> Dla ODBC użyj Catalog_name_seperator.<br /><br /> W przypadku ole db użyj DBLITERAL_CATALOG_SEPARATOR lub DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|ciąg|Nazwa produktu, do który dostawca uzyskuje dostęp, na przykład "Oracle" lub "SQLServer".|  
|DataSourceProductVersion|ciąg|Wskazuje wersję produktu, do którą uzyskuje dostęp dostawca, w formacie macierzystym źródeł danych, a nie w formacie firmy Microsoft.<br /><br /> W niektórych przypadkach DataSourceProductVersion i DataSourceProductVersionNormalized będzie taką samą wartość. W przypadku OLE DB i ODBC te zawsze będą takie same, jak są one mapowane do tego samego wywołania funkcji w podstawowej macierzystego interfejsu API.|  
|DataSourceProductVersionNormalized|ciąg|Znormalizowana wersja dla źródła danych, tak, że można ją porównać z `String.Compare()`. Format tego jest spójny dla wszystkich wersji dostawcy, aby zapobiec wersji 10 z sortowania między wersją 1 i wersją 2.<br /><br /> Na przykład dostawca Oracle używa formatu "nn.nn.nn.nn.nn.nn" dla swojej znormalizowanej wersji, co powoduje, że źródło danych Oracle 8i zwraca "08.01.07.04.01". Sql Server używa typowego formatu Microsoft "nn.nn.nnnn".<br /><br /> W niektórych przypadkach DataSourceProductVersion i DataSourceProductVersionNormalized będzie tej samej wartości. W przypadku OLE DB i ODBC te zawsze będą takie same, jak są one mapowane do tego samego wywołania funkcji w podstawowej macierzystego interfejsu API.|  
|GroupByBehavior ( GroupByBehavior )|<xref:System.Data.Common.GroupByBehavior>|Określa relację między kolumnami w klauzuli GROUP BY a kolumnami niezagregowanymi na liście select.|  
|Wzortern identyfikatora|ciąg|Wyrażenie regularne, które pasuje do identyfikatora i ma wartość dopasowania identyfikatora. Na przykład "[A-Za-z0-9_#$]".|  
|Pokadź identyfikatora|<xref:System.Data.Common.IdentifierCase>|Wskazuje, czy identyfikatory niezacytowane są traktowane jako rozróżniane wielkość liter, czy nie.|  
|OrderByColumnsInSelect|bool|Określa, czy kolumny w klauzuli ORDER BY muszą znajdować się na liście select. Wartość true wskazuje, że muszą one być na liście wyboru, wartość false wskazuje, że nie muszą być na liście select.|  
|ParametrMarkerFormat|ciąg|Ciąg formatu reprezentujący sposób formatowania parametru.<br /><br /> Jeśli nazwane parametry są obsługiwane przez źródło danych, pierwszym symbolem zastępczym w tym ciągu powinien być miejsce, w którym powinna być sformatowana nazwa parametru.<br /><br /> Na przykład jeśli źródło danych oczekuje, że parametry zostaną nazwane i poprzedzone{0}':' będzie to ": ". Podczas formatowania tego o nazwie parametru "p1" wynikowy ciąg jest ":p1".<br /><br /> Jeśli źródło danych oczekuje, że parametry mają\@być poprzedzone ' ', ale{0}nazwy już je zawierają, byłoby to\@' ', a\@wynikiem formatowania parametru o nazwie " p1" byłoby po prostu "p1".<br /><br /> W przypadku źródeł danych, które nie oczekują nazwanych parametrów i oczekują użycia znaku '?', ciąg formatu można określić jako po prostu '?', który ignoruje nazwę parametru. Dla OLE DB zwracamy '?'.|  
|Wzortern parametrów|ciąg|Wyrażenie regularne, które pasuje do znacznika parametru. Będzie miał wartość dopasowania nazwy parametru, jeśli istnieje.<br /><br /> Na przykład, jeśli nazwane parametry\@są obsługiwane ze znakiem wstawki ' , który zostanie uwzględniony w nazwie parametru, będzie to: "(\@[A-Za-z0-9_$#]*)".<br /><br /> Jeśli jednak nazwane parametry są obsługiwane znakiem ':' jako znak wiodący i nie jest to część nazwy parametru, będzie to: ":([A-Za-z0-9_$#]\*)".<br /><br /> Oczywiście, jeśli źródło danych nie obsługuje nazwanych parametrów, byłoby to po prostu "?".|  
|Nazwa parametruMaxLength|int|Maksymalna długość nazwy parametru w znakach. Visual Studio oczekuje, że jeśli nazwy parametrów są obsługiwane, minimalna wartość dla maksymalnej długości wynosi 30 znaków.<br /><br /> Jeśli źródło danych nie obsługuje nazwanych parametrów, ta właściwość zwraca zero.|  
|Nazwa parametruPattern|ciąg|Wyrażenie regularne, które pasuje do prawidłowych nazw parametrów. Różne źródła danych mają różne reguły dotyczące znaków, które mogą być używane dla nazw parametrów.<br /><br /> Program Visual Studio oczekuje, że jeśli obsługiwane są nazwy parametrów, znaki "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" są minimalnym obsługiwanym zestawem znaków, które są prawidłowe dla nazw parametrów.|  
|CytowanyIdentifierPattern|ciąg|Wyrażenie regularne, które pasuje do identyfikatora cytowanego i ma wartość dopasowania samego identyfikatora bez cudzysłowów. Na przykład, jeśli źródło danych używane podwójne cudzysłowy do identyfikacji cytowanych\\identyfikatorów, byłoby \\to: "(([^ "]&#124;"\\")*)".|  
|CytowanyIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Wskazuje, czy identyfikatory cytowane są traktowane jako rozróżniane wielkość liter, czy nie.|  
|StatementSeparatorPattern|ciąg|Wyrażenie regularne, które pasuje do separatora instrukcji.|  
|StringLiteralPattern (Wzortern)|ciąg|Wyrażenie regularne, które pasuje do literału ciągu i ma wartość dopasowania samego literału. Na przykład, jeśli źródło danych użyło pojedynczych cudzysłowów do identyfikacji ciągów, byłoby to: "('([^']&#124;'')*'""'|  
|Obsługiwane operatory łączy|<xref:System.Data.Common.SupportedJoinOperators>|Określa, jakie typy instrukcji sprzężenia SQL są obsługiwane przez źródło danych.|  
  
## <a name="datatypes"></a>Typy danych  
 Ta kolekcja schematów udostępnia informacje o typach danych, które są obsługiwane przez bazę danych, z którą obecnie jest połączony dostawca zarządzany programu .NET Framework.  
  
|nazwa_kolumny|typ_danych|Opis|  
|----------------|--------------|-----------------|  
|TypeName|ciąg|Nazwa typu danych specyficznych dla dostawcy.|  
|Typ bazy dostawcy|int|Wartość typu specyficzne dla dostawcy, który powinien być używany podczas określania typu parametru. Na przykład SqlDbType.Money lub OracleType.Blob.|  
|Columnsize|long|Długość kolumny lub parametru nienumerycznego odnosi się do maksymalnej lub długości zdefiniowanej dla tego typu przez dostawcę.<br /><br /> W przypadku danych znakowych jest to maksymalna lub zdefiniowana długość w jednostkach, zdefiniowana przez źródło danych. Oracle ma koncepcję określania długości, a następnie określania rzeczywistego rozmiaru magazynu dla niektórych typów danych znaków. Definiuje tylko długość w jednostkach dla Oracle.<br /><br /> W przypadku typów danych data-godzina jest to długość reprezentacji ciągu (przy założeniu maksymalnej dozwolonej precyzji składnika ułamków sekund).<br /><br /> Jeśli typ danych jest numeryczny, jest to górna granica maksymalnej precyzji typu danych.|  
|Utwórzformat|ciąg|Formatuj ciąg reprezentujący sposób dodawania tej kolumny do instrukcji definicji danych, takiej jak CREATE TABLE. Każdy element w tablicy CreateParameter powinien być reprezentowany przez "znacznik parametru" w ciągu formatu.<br /><br /> Na przykład typ danych SQL DECIMAL wymaga precyzji i skali. W takim przypadku ciąg formatu będzie "DECIMAL({0},{1})".|  
|Tworzenieparametrów|ciąg|Parametry tworzenia, które muszą być określone podczas tworzenia kolumny tego typu danych. Każdy parametr tworzenia jest wymieniony w ciągu, oddzielony przecinkiem w kolejności, w jakiej mają być dostarczone.<br /><br /> Na przykład typ danych SQL DECIMAL wymaga precyzji i skali. W takim przypadku parametry tworzenia powinny zawierać ciąg "precyzja, skala".<br /><br /> W poleceniu tekstowym, aby utworzyć kolumnę DECIMAL z dokładnością do 10 i skalą 2, wartość kolumny CreateFormat może być decimal({0},{1})" i pełna specyfikacja typu będzie DECIMAL(10,2).|  
|typ_danych|ciąg|Nazwa typu .NET Framework typu danych.|  
|Isautoincrementable|bool|true — wartości tego typu danych mogą zwiększać się automatycznie.<br /><br /> false — wartości tego typu danych mogą nie zwiększać się automatycznie.<br /><br /> Należy zauważyć, że to tylko wskazuje, czy kolumna tego typu danych może być automatyczne zwiększanie, a nie, że wszystkie kolumny tego typu są automatyczne zwiększanie.|  
|IsBestMatch (właśc.|bool|true — typ danych jest najlepiej dopasowany między wszystkimi typami danych w magazynie danych a typem danych .NET Framework wskazanym przez wartość w kolumnie DataType.<br /><br /> false — typ danych nie jest najlepszym dopasowaniem.<br /><br /> Dla każdego zestawu wierszy, w których wartość datatype kolumny jest taka sama, IsBestMatch kolumna jest ustawiona na true tylko w jednym wierszu.|  
|IsCaseSensitive (IsCaseSensitive)|bool|true — typ danych jest typem znaku i jest rozróżniany wielkość liter.<br /><br /> false — typ danych nie jest typem znaku lub nie jest rozróżniany wielkość liter.|  
|IsFixedLength (IsFixedLength)|bool|true — kolumny tego typu danych utworzone przez język definicji danych (DDL) będą mieć stałą długość.<br /><br /> false — kolumny tego typu danych utworzone przez DDL będą mieć zmienną długość.<br /><br /> DBNull.Value — nie wiadomo, czy dostawca zamapuje to pole za pomocą kolumny o stałej długości lub o zmiennej długości.|  
|IsFixedPrecisionScale (Skala najprawocniejsza do)|bool|true — typ danych ma stałą precyzję i skalę.<br /><br /> false — typ danych nie ma stałej precyzji i skali.|  
|IsLong (Długi)|bool|true — typ danych zawiera bardzo długie dane; definicja bardzo długich danych jest specyficzna dla dostawcy.<br /><br /> false — typ danych nie zawiera bardzo długich danych.|  
|Isnullable|bool|true — typ danych jest nullable.<br /><br /> false — typ danych nie jest nullable.<br /><br /> DBNull.Value — nie wiadomo, czy typ danych jest nullable.|  
|IsSearchable (Możliwe do wyszukania)|bool|true — typ danych może być używany w klauzuli WHERE z dowolnym operatorem z wyjątkiem predykatu LIKE.<br /><br /> false — typ danych nie może być używany w klauzuli WHERE z żadnym operatorem z wyjątkiem predykatu LIKE.|  
|IsSearchableWithLike (Np.|bool|true — typ danych może być używany z predykatem LIKE<br /><br /> false — nie można użyć typu danych z predykatem LIKE.|  
|IsNiepodpisane|bool|true — typ danych jest niepodpisany.<br /><br /> false — typ danych jest podpisany.<br /><br /> DBNull.Value — nie dotyczy typu danych.|  
|Maksymalna skala|short|Jeśli wskaźnik typu jest typem liczbowym, jest to maksymalna liczba cyfr dozwolona po prawej stronie przecinka dziesiętnego. W przeciwnym razie jest to DBNull.Value.|  
|Minimalna skala|short|Jeśli wskaźnik typu jest typem liczbowym, jest to minimalna liczba cyfr dozwolona po prawej stronie przecinka dziesiętnego. W przeciwnym razie jest to DBNull.Value.|  
|Typ IsConcurrency|bool|true – typ danych jest aktualizowany przez bazę danych za każdym razem, gdy wiersz jest zmieniany, a wartość kolumny różni się od wszystkich poprzednich wartości<br /><br /> false – typ danych jest aktualizowany przez bazę danych za każdym razem, gdy wiersz jest zmieniany<br /><br /> DBNull.Value — baza danych nie obsługuje tego typu danych|  
|IsLiteralSupportowane|bool|true – typ danych może być wyrażony jako literał<br /><br /> false – typ danych nie może być wyrażony jako literał|  
|DosłownaPrefix|ciąg|Prefiks zastosowany do danego literału.|  
|Dosłownysuchysk|ciąg|Sufiks zastosowany do danego literału.|  
|Typ danych macierzystych|Ciąg|NativeDataType jest kolumną specyficzną dla bazy danych OLE do blokowania typu danych typu OLE DB.|  
  
## <a name="restrictions"></a>Ograniczenia  
 Ta kolekcja schematu ujawniła informacje o ograniczeniach obsługiwanych przez dostawcę zarządzanego programu .NET Framework, który jest obecnie używany do łączenia się z bazą danych.  
  
|nazwa_kolumny|typ_danych|Opis|  
|----------------|--------------|-----------------|  
|CollectionName|ciąg|Nazwa kolekcji, do których mają zastosowanie te ograniczenia.|  
|Nazwa ograniczenia|ciąg|Nazwa ograniczenia w kolekcji.|  
|OgraniczenieDefault|ciąg|Ignorowane.|  
|Numer ograniczenia|int|Rzeczywista lokalizacja w ograniczeniach kolekcji, w których owaje się to określone ograniczenie.|  
  
## <a name="reservedwords"></a>ReservedWords (Words)  
 Ta kolekcja schematów udostępnia informacje o słowach, które są zarezerwowane przez bazę danych, z którą ma obecnie połączony dostawca zarządzany programu .NET Framework.  
  
|nazwa_kolumny|typ_danych|Opis|  
|----------------|--------------|-----------------|  
|ZastrzeżonyWord|ciąg|Słowo zastrzeżone specyficzne dla dostawcy.|  
  
## <a name="see-also"></a>Zobacz też

- [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)
- [GetSchema i kolekcje schematów](getschema-and-schema-collections.md)
- [Omówienie ADO.NET](ado-net-overview.md)
