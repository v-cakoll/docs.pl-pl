---
title: Parametry połączenia w programie ADO.NET Entity Framework
ms.date: 10/15/2018
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
ms.openlocfilehash: 55097e4977111c56cb06c590e305e31ed681fd31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606788"
---
# <a name="connection-strings-in-the-adonet-entity-framework"></a>Parametry połączenia w programie ADO.NET Entity Framework

Parametry połączenia zawierają informacje inicjowania, który jest przekazywany jako parametr od dostawcy danych do źródła danych. Składnia jest zależna od dostawcy danych, a ciąg połączenia jest analizowany podczas próby otwarcia połączenia. Parametry połączenia używane przez program Entity Framework zawiera informacje używane do łączenia z podstawowego dostawcy danych ADO.NET, który obsługuje platformy Entity Framework. Zawierają one informacje o wymaganych modelu i mapowania plików.

Ciąg połączenia jest używany dostawca EntityClient podczas uzyskiwania dostępu do modelu i mapowania metadanych i nawiązania połączenia ze źródłem danych. Parametry połączenia można uzyskać dostępu do lub ustawić za pomocą <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> właściwość <xref:System.Data.EntityClient.EntityConnection>. <xref:System.Data.EntityClient.EntityConnectionStringBuilder> Klasa może być używana do programowego tworzenia lub dostęp do parametrów w parametrach połączenia. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie ciągu połączenia EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).

[Narzędzia modelu Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) wygenerować parametry połączenia, które są przechowywane w pliku konfiguracji aplikacji. <xref:System.Data.Objects.ObjectContext> pobiera informacje o połączeniu automatycznie podczas tworzenia zapytań dotyczących obiektów. <xref:System.Data.EntityClient.EntityConnection> Posługują się <xref:System.Data.Objects.ObjectContext> wystąpienia jest możliwy z <xref:System.Data.Objects.ObjectContext.Connection%2A> właściwości. Aby uzyskać więcej informacji, zobacz [zarządzania połączeniami i transakcje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).

## <a name="connection-string-syntax"></a>Składnia parametrów połączenia

Aby uzyskać informacje dotyczące składni ogólnej dla parametrów połączenia, zobacz [składnia ciągu połączenia | Parametry połączenia w ADO.NET](../connection-strings.md#connection-string-syntax).

## <a name="connection-string-parameters"></a>Parametry połączenia

W poniższej tabeli wymieniono prawidłowe nazwy wartości — słowo kluczowe w <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>.

|Słowo kluczowe|Opis|
|-------------|-----------------|
|`Provider`|Jeśli wymagane `Name` — słowo kluczowe nie jest określony. Nazwa dostawcy, która służy do pobierania <xref:System.Data.Common.DbProviderFactory> obiektu źródłowego dostawcy. Ta wartość jest stała.<br /><br /> Gdy `Name` — słowo kluczowe nie jest uwzględniony w parametry połączenia obiektu niepusta wartość dla `Provider` — słowo kluczowe jest wymagana. This — słowo kluczowe jest wzajemnie wykluczających się przy użyciu `Name` — słowo kluczowe.|
|`Provider Connection String`|Opcjonalna. Określa parametry połączenia specyficzne dla dostawcy, który jest przekazywany do bazowego źródła danych. Te parametry połączenia zawiera nieprawidłowy — słowo kluczowe/pary wartości dla dostawcy danych. Nieprawidłowy `Provider Connection String` spowoduje błąd w czasie wykonywania, gdy zostanie on oceniony przez źródło danych.<br /><br /> This — słowo kluczowe jest wzajemnie wykluczających się przy użyciu `Name` — słowo kluczowe.<br /><br /> Upewnij się wprowadzić wartość zgodnie z ogólna składnia [parametry połączenia ADO.NET](../../../../../docs/framework/data/adonet/connection-strings.md). Na przykład rozważmy następujący ciąg połączenia: `Server=serverName; User ID = userID`. Należy zmienić, ponieważ zawiera ona średnikiem. Ponieważ nie zawiera podwójne znaki cudzysłowu, mogą być wykorzystywane do anulowania zapewnianego element:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`|
|`Metadata`|Jeśli wymagane `Name` — słowo kluczowe nie jest określony. Rozdzielany potoku lista katalogów, plików i lokalizacje zasobów, w których warto szukać informacji mapowania i metadanych. Oto przykład:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Spacje na każdej stronie separatora potoku są ignorowane.<br /><br /> This — słowo kluczowe jest wzajemnie wykluczających się przy użyciu `Name` — słowo kluczowe.|
|`Name`|Aplikację można opcjonalnie określić nazwę połączenia w pliku konfiguracyjnym aplikacji, który zawiera wartości parametrów połączeń wymaganych — słowo kluczowe i wartości. W tym przypadku nie podajesz je bezpośrednio w parametrach połączenia. `Name` — Słowo kluczowe nie jest dozwolona w pliku konfiguracji.<br /><br /> Gdy `Name` — słowo kluczowe jest niedostępna w parametrach połączenia, wartości niepuste dostawcy — słowo kluczowe jest wymagana.<br /><br /> This — słowo kluczowe jest wzajemnie wykluczających się przy użyciu wszystkich innych połączenia ciąg słów kluczowych.|

Oto przykład parametrów połączenia umożliwiających [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) przechowywane w pliku konfiguracji aplikacji:

## <a name="model-and-mapping-file-locations"></a>Model i mapowanie lokalizacji plików

`Metadata` Parametr zawiera listę lokalizacji `EntityClient` dostawcy, aby wyszukać modelu i mapowania plików. Modelu i mapowania plików często są wdrażane w tym samym katalogu co plik wykonywalny aplikacji. Te pliki można również wdrożyć w określonej lokalizacji lub dołączone jako zasobu osadzonego w aplikacji.

Zasoby osadzone są określane w następujący sposób:

```
Metadata=res://<assemblyFullName>/<resourceName>.
```

Poniższe opcje są dostępne do definiowania lokalizacji zasobu osadzonego:

|Opcja|Opis|
|-|-|
|`assemblyFullName`|Pełna nazwa zestawu z zasobu osadzonego. Nazwa zawiera prosta nazwa, Nazwa wersji, kultury obsługiwanych i klucz publiczny w następujący sposób:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Zasoby można osadzić w każdym zestawie, który jest dostępny przez aplikację.<br /><br /> Jeśli określono symbolu wieloznacznego (\*) dla `assemblyFullName`, środowisko uruchomieniowe programu Entity Framework umożliwia wyszukiwanie zasobów w następujących lokalizacjach, w następującej kolejności:<br /><br /> 1.  Wywoływanego zestawu.<br />2.  Zestawy występujące w odwołaniach.<br />3.  Zestawy znajdujące się w katalogu bin aplikacji.<br /><br /> Jeśli pliki nie znajdują się w jednej z tych lokalizacji, zostanie zgłoszony wyjątek. **Uwaga:**  Użycie symbolu wieloznacznego (*), platformy Entity Framework musi przejrzeć wszystkie zestawy dla zasobów z poprawną nazwę. Aby zwiększyć wydajność, należy określić nazwę zestawu, zamiast symbolu wieloznacznego.|
|`resourceName`|Nazwa zasobu uwzględnione, na przykład AdventureWorksModel.csdl. Usługi metadanych tylko będzie szukać plików lub zasobów przy użyciu jednego z następujących rozszerzeń: .csdl, ssdl lub MSL albo identyfikatorem. Jeśli `resourceName` nie zostanie określony, zostaną załadowane wszystkie zasoby metadanych. Zasoby powinny mieć unikatowe nazwy w zestawie. Jeśli wiele plików o takiej samej nazwie są zdefiniowane w różnych katalogach w zestawie, `resourceName` mogą zawierać struktury folderów przed nazwą zasobu, na przykład FolderName.FileName.csdl.<br /><br /> `resourceName` nie jest wymagany po określeniu symbolu wieloznacznego (*) dla `assemblyFullName`.|

> [!NOTE]
> Aby zwiększyć wydajność, zasobów osadzonych w zestawie wywołującego, z wyjątkiem w scenariuszach bez sieci Web w przypadku, gdy nie ma żadnego odwołania do bazowego mapowania i metadanych plików w zestawie wywołującego.

Poniższy przykład ładuje wszystkie modelu i mapowania plików w zestawie wywołującego, przywoływanych zestawach i innych zestawów w katalogu bin aplikacji.

```
Metadata=res://*/
```

Poniższy przykład ładuje plik model.csdl z zestawu AdventureWorks i ładuje pliki model.ssdl i model.msl z domyślnego katalogu uruchomionej aplikacji.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl
```

Poniższy przykład załaduje trzy określone zasoby z określonego zestawu.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl
```

Poniższy przykład załaduje zasoby osadzone .csdl rozszerzenia, MSL albo identyfikatorem i ssdl z zestawu.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/
```

Poniższy przykład ładuje wszystkie zasoby w znaku plus ścieżka względna do pliku "datadir\metadata\\" z lokalizacji załadowany zestaw.

```
Metadata=datadir\metadata\
```

Poniższy przykład ładuje wszystkie zasoby w polu Ścieżka względna do pliku z lokalizacji załadowany zestaw.

```
Metadata=.\
```

## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>Obsługa &#124;DataDirectory&#124; ciąg podstawienia i aplikacji sieci Web głównym (~) — Operator

`DataDirectory` i ~ operator są używane w <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> jako część `Metadata` i `Provider Connection String` słów kluczowych. <xref:System.Data.EntityClient.EntityConnection> Przekazuje `DataDirectory` i ~ operatora <xref:System.Data.Metadata.Edm.MetadataWorkspace> i dostawcy magazynu, odpowiednio.

|Termin|Opis|
|----------|-----------------|
|`&#124;DataDirectory&#124;`|Jest rozpoznawana jako ścieżka względna do mapowania i metadanych plików. Jest to wartość, która jest ustawiona za pomocą `AppDomain.SetData("DataDirectory", objValue)` metody. `DataDirectory` Ciąg podstawienia muszą być ujęte w znaki potoku i nie może być dowolny biały obszar między jego nazwy i znakami kreski pionowej. `DataDirectory` Nazwa nie jest rozróżniana wielkość liter.<br /><br /> Jeśli katalog fizyczny o nazwie "DataDirectory" musi być przekazywane jako członek do listy ścieżek metadanych, należy dodać biały znak do jednego lub obu tych stron o nazwie. Na przykład: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Aplikacja ASP.NET jest rozpoznawana jako &#124;DataDirectory&#124; do "\<katalog główny aplikacji > / app_data" folder.|
|~|Jest rozpoznawana jako katalog główny aplikacji sieci Web. ~ Znak na pozycji wiodących jest zawsze interpretowane jako operator główny aplikacji sieci Web (~), chociaż może reprezentować, nieprawidłowy podkatalog lokalnego. Aby odwołać się do podkatalogu lokalnych, użytkownik powinien jawne przekazywanie `./~`.|

`DataDirectory` i ~ operatora, należy określić tylko na początku ścieżki, ich nie są rozpoznawane w innym miejscu. Entity Framework będzie próbował rozpoznać `~/data`, ale traktuje ona `/data/~` jako ścieżki fizycznej.

Ścieżkę, która rozpoczyna się od `DataDirectory` lub ~ operator nie można rozpoznać ścieżki fizycznej poza gałąź `DataDirectory` i ~ operatora. Na przykład, zostanie rozwiązany w następujących ścieżkach: `~` , `~/data` , `~/bin/Model/SqlServer`. Następujące ścieżki nie będzie można rozwiązać: `~/..`, `~/../other`.

`DataDirectory` i ~ operator można rozszerzyć do uwzględnienia podkatalogi, w następujący sposób: `|DataDirectory|\Model`, `~/bin/Model`

Rozdzielczość `DataDirectory` ciąg podstawienia i ~ operator jest cykliczna. Na przykład, gdy `DataDirectory` obejmuje `~` znaków, wystąpi wyjątek. Zapobiega to nieskończoną rekursję.

## <a name="see-also"></a>Zobacz także

- [Praca z dostawcami danymi](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
- [Zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Zarządzania połączeniami i transakcji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [Parametry połączeń](../../../../../docs/framework/data/adonet/connection-strings.md)
