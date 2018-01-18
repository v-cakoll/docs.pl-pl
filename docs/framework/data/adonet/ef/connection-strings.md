---
title: "Parametry połączenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c83c1883d00db1da8f0e7945d9cda5f2eb3f56a0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="connection-strings"></a>Parametry połączenia
Parametry połączenia zawierają informacje inicjowania jest przekazywana jako parametr z dostawcy danych do źródła danych. Składnia jest zależna od dostawcy danych, a podczas próby otwarcia połączenia jest przeanalizować parametrów połączenia. Parametry połączenia używane przez program Entity Framework zawierają informacje używane do łączenia się z podstawowej dostawcy danych ADO.NET, która obsługuje programu Entity Framework. Zawierają one również informacje dotyczące wymaganego modelu i mapowania plików.  
  
 Ciąg połączenia jest używany dostawca EntityClient podczas uzyskiwania dostępu do modelu i mapowania metadanych i łączenia ze źródłem danych. Parametry połączenia można uzyskać dostępu do lub ustawiana za pośrednictwem <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> właściwość <xref:System.Data.EntityClient.EntityConnection>. <xref:System.Data.EntityClient.EntityConnectionStringBuilder> Klasa może być używana do programowego tworzenia lub dostęp do parametrów w parametrach połączenia. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie ciągu połączenia EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
 [Modelu Entity Data Model tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) Generowanie parametry połączenia, które są przechowywane w pliku konfiguracji aplikacji. <xref:System.Data.Objects.ObjectContext>Podczas tworzenia obiektu kwerend automatycznie pobiera informacje o połączeniu. <xref:System.Data.EntityClient.EntityConnection> Używane przez <xref:System.Data.Objects.ObjectContext> wystąpienia są dostępne z <xref:System.Data.Objects.ObjectContext.Connection%2A> właściwości. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcje](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="connection-string-parameters"></a>Parametry ciągu połączenia  
 Format ciągu połączenia jest rozdzielaną średnikami listę par klucz/wartość parametru:  
  
 `keyword1=value; keyword2=value;`  
  
 Znak równości (=) łączy każde słowo kluczowe i jego wartość. Słowa kluczowe nie jest uwzględniana wielkość liter i spacji między pary klucz wartość są ignorowane. Jednak wartości mogą być uwzględniana wielkość liter, w zależności od źródła danych. Wszelkie wartości zawierające średnika, pojedynczy cudzysłów lub podwójny cudzysłów musi być ujęta w znaki podwójnego cudzysłowu. W poniższej tabeli wymieniono prawidłowe nazwy wartości słów kluczowych w <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>.  
  
|Keyword|Opis|  
|-------------|-----------------|  
|`Provider`|Jeśli wymagane `Name` nie zostanie określone słowo kluczowe. Nazwa dostawcy, która służy do pobierania <xref:System.Data.Common.DbProviderFactory> obiektu dla źródłowego dostawcy. Ta wartość jest stała.<br /><br /> Gdy `Name` — słowo kluczowe nie ma parametrów połączenia jednostki, niepustą wartość dla `Provider` — słowo kluczowe jest wymagana. To słowo kluczowe jest wykluczają się wzajemnie z `Name` — słowo kluczowe.|  
|`Provider Connection String`|Opcjonalny. Określa parametry połączenia specyficznych dla dostawcy, który zostanie przekazany do źródła danych. Ten ciąg połączenia jest wyrażona przy użyciu pary prawidłową — słowo kluczowe/wartość dla dostawcy danych. Nieprawidłowy `Provider Connection String` spowoduje błąd w czasie wykonywania, gdy jest obliczane przez źródło danych.<br /><br /> To słowo kluczowe jest wykluczają się wzajemnie z `Name` — słowo kluczowe.<br /><br /> Wartość `Provider Connection String` musi być ujęte w cudzysłowy. Oto przykład:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`<br /><br /> Poniższy przykład nie będzie działać:<br /><br /> `Provider Connection String =Server=serverName; User ID = userID`|  
|`Metadata`|Jeśli wymagane `Name` nie zostanie określone słowo kluczowe. Rozdzielany potoku lista katalogów, plików i lokalizacje zasobów w którym informacji metadanych i mapowania. Oto przykład:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Spacje z każdej strony separatora potoku są ignorowane.<br /><br /> To słowo kluczowe jest wykluczają się wzajemnie z `Name` — słowo kluczowe.|  
|`Name`|Aplikację można opcjonalnie określić nazwę połączenia w pliku konfiguracyjnym aplikacji, która udostępnia wartości parametrów połączeń wymagane słowo kluczowe i wartości. W takim przypadku nie można ich podać bezpośrednio w parametrach połączenia. `Name` Słów kluczowych jest niedozwolone w pliku konfiguracji.<br /><br /> Gdy `Name` — słowo kluczowe nie jest uwzględniona w parametrach połączenia, a nie jest puste wartości dla słowa kluczowego dostawcy jest wymagana.<br /><br /> To słowo kluczowe jest wykluczają się wzajemnie z wszystkich innych słowa kluczowe parametrów połączenia.|  
  
 Oto przykład parametrów połączenia dla [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) przechowywane w pliku konfiguracyjnym aplikacji:  
  
  
  
## <a name="model-and-mapping-file-locations"></a>Model i mapowanie lokalizacji plików  
 `Metadata` Parametr zawiera listę lokalizacji `EntityClient` dostawcy wyszukiwania dla modelu i mapowania plików. Model i mapowania plików często są wdrażane w tym samym katalogu co plik wykonywalny aplikacji. Te pliki można również wdrożone w określonej lokalizacji lub dołączone jako osadzony zasób w aplikacji.  
  
 Zasoby osadzone są określane w następujący sposób:  
  
```  
Metadata=res://<assemblyFullName>/<resourceName>.   
```  
  
 Poniższe opcje są dostępne do definiowania lokalizację osadzonego zasobu:  
  
|Opcja|Opis|  
|-|-|  
|`assemblyFullName`|Pełna nazwa zestawu z zasobu osadzonego. Nazwa zawiera prosta nazwa, Nazwa wersji, kultury obsługiwane i klucz publiczny w następujący sposób:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Zasoby mogą być osadzone w zestawu, który jest dostępny przez aplikację.<br /><br /> Jeśli określisz symbolu wieloznacznego (\*) dla `assemblyFullName`, środowiska uruchomieniowego programu Entity Framework zostaną wyszukane zasoby w następujących lokalizacjach w następującej kolejności:<br /><br /> 1.  Zestaw wywołujący.<br />2.  Zestawy występujące w odwołaniach.<br />3.  Zestawy w katalogu bin aplikacji.<br /><br /> Jeśli pliki nie znajdują się w jednej z tych lokalizacji, zostanie zgłoszony wyjątek. **Uwaga:** użycie symbolu wieloznacznego (*), ma Przejrzyj wszystkie zestawy zasobów z poprawną nazwą programu Entity Framework. Aby zwiększyć wydajność, należy określić nazwę zestawu, zamiast symbolu wieloznacznego.|  
|`resourceName`|Nazwa zasobu dołączone, takich jak AdvendtureWorksModel.csdl. Usługi metadanych tylko będzie szukać plików lub zasobów z jednego z następujących rozszerzeń: CSDL, ssdl lub MSL. Jeśli `resourceName` nie zostanie określony, zostaną załadowane wszystkie zasoby metadanych. Zasoby powinny mieć unikatowe nazwy w zestawie. Jeśli zdefiniowano wiele plików o takiej samej nazwie w różnych katalogach w zestawie, `resourceName` musi zawierać struktury folderów przed nazwą zasobu, na przykład FolderName.FileName.csdl.<br /><br /> `resourceName`nie jest wymagany po określeniu symbolu wieloznacznego (*) dla `assemblyFullName`.|  
  
> [!NOTE]
>  Aby zwiększyć wydajność, osadzanie zasobów w zestawie wywołującego, z wyjątkiem w scenariuszach bez sieci Web w przypadku, gdy istnieje żadne odwołanie do podstawowej mapowania i metadanych plików w zestawie wywołującego.  
  
 Poniższy przykład załaduje modelu i mapowania plików w wywołującego zestawu zestawów występujących w odwołaniach i innych zestawów w katalogu bin aplikacji.  
  
```  
Metadata=res://*/  
```  
  
 Poniższy przykład ładuje plik model.csdl z zestawu AdventureWorks i ładuje model.ssdl i model.msl plików z katalogu w uruchomionej aplikacji.  
  
```  
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl  
```  
  
 Poniższy przykład załaduje trzy określone zasoby z określonego zestawu.  
  
```  
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|   
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|   
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl  
```  
  
 Poniższy przykład ładuje wszystkie zasoby osadzone .csdl rozszerzeń, MSL i ssdl z zestawu.  
  
```  
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/  
```  
  
 Poniższy przykład ładuje wszystkie zasoby w ścieżce względnej plus "datadir\metadata\\" z lokalizacji załadowanego zestawu.  
  
```  
Metadata=datadir\metadata\  
```  
  
 Poniższy przykład ładuje wszystkie zasoby w ścieżce względnej pliku z lokalizacji załadowanego zestawu.  
  
```  
Metadata=.\  
```  
  
## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>Obsługa &#124; DataDirectory &#124; Ciąg podstawienia i operatora główny aplikacji sieci Web (~)  
 `DataDirectory`i ~ operator są używane w <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> jako część `Metadata` i `Provider Connection String` słów kluczowych. <xref:System.Data.EntityClient.EntityConnection> Przekazuje `DataDirectory` i ~ operatora <xref:System.Data.Metadata.Edm.MetadataWorkspace> i dostawcy magazynu odpowiednio.  
  
|Termin|Opis|  
|----------|-----------------|  
|`&#124;DataDirectory&#124;`|Rozpoznaje jako ścieżka względna do plików mapowania i metadanych. Jest to wartość, która jest ustawiana za pośrednictwem `AppDomain.SetData("DataDirectory", objValue)` metody. `DataDirectory` Ciąg podstawienia muszą być ujęte w znaki potoku i nie może być dowolnym odstępu między jego nazwa i znaki potoku. `DataDirectory` Nazwa nie jest rozróżniana wielkość liter.<br /><br /> Jeśli katalog fizyczny o nazwie "DataDirectory" musi być przekazywane jako element członkowski listy ścieżek metadanych, należy dodać odstępu powinna po stronie lub obu stron nazwy, na przykład: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Aplikacja ASP.NET jest rozpoznawana &#124; DataDirectory &#124; Aby "\<katalog główny aplikacji > / app_data" folderu.|  
|~|Jest rozpoznawana jako katalog główny aplikacji sieci Web. ~ Znak na pozycji wiodące zawsze jest interpretowana jako operator główny aplikacji sieci Web (~), chociaż może reprezentować Nieprawidłowy podkatalog lokalnego. Odwołać się do podkatalogu lokalnym, użytkownik powinien jawnego przesłania `./~`.|  
  
 `DataDirectory`i ~ operator należy określić tylko na początku ścieżki, ich nie są rozpoznawane w innym miejscu. Entity Framework będzie próbował rozpoznać `~/data`, ale traktuje ona `/data/~` jako ścieżki fizycznej.  
  
 Ścieżki, która rozpoczyna się od `DataDirectory` lub ~ operatora nie można rozpoznać ścieżki fizycznej poza Rozgałęzienie `DataDirectory` i ~ operatora. Na przykład rozwiąże następujących ścieżkach: `~` , `~/data` , `~/bin/Model/SqlServer`. Następujące ścieżki nie będzie można rozwiązać: `~/..`, `~/../other`.  
  
 `DataDirectory`i ~ operator może zostać rozszerzony do obejmują podkatalogi, w następujący sposób: `|DataDirectory|\Model`,`~/bin/Model`  
  
 Rozpoznanie `DataDirectory` ciąg podstawienia i ~ operator jest niecykliczne. Na przykład, jeśli `DataDirectory` obejmuje `~` znak, wystąpi wyjątek. Zapobiega to nieskończoną rekursję.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z dostawcami danymi](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)  
 [Zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Zarządzanie połączeniami i transakcji](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [Parametry połączeń](../../../../../docs/framework/data/adonet/connection-strings.md)
