---
title: Parametry połączenia i pliki konfiguracji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 8030c0323a2f742de19a4761e24c66294c6dd5d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405978"
---
# <a name="connection-strings-and-configuration-files"></a>Parametry połączenia i pliki konfiguracji
Osadzanie ciągów połączenia w kodzie twojej aplikacji może prowadzić do problemów konserwacji i luk w zabezpieczeniach. Parametry połączenia nieszyfrowanego kompilowane do kodu źródłowego aplikacji można przeglądać za pomocą [Ildasm.exe (dezasembler IL)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) narzędzia. Ponadto jeśli nigdy nie zmieni się parametry połączenia, aplikacji musi być ponownie kompilowana. Z tego względu zalecamy przechowywanie parametrów połączenia w pliku konfiguracji aplikacji.  
  
## <a name="working-with-application-configuration-files"></a>Praca z plikami konfiguracji aplikacji  
 Pliki konfiguracyjne aplikacji zawierają ustawienia, które są specyficzne dla określonej aplikacji. Na przykład aplikacja ASP.NET może mieć jedną lub więcej **web.config** plików i aplikacji Windows może mieć opcjonalną **app.config** pliku. Pliki konfiguracji udostępniać typowe elementy, chociaż nazwę i lokalizację pliku konfiguracji różnią się w zależności od aplikacji hosta.  
  
### <a name="the-connectionstrings-section"></a>ConnectionStrings sekcji  
 Parametry połączenia mogą być przechowywane jako pary klucz/wartość w **connectionStrings** części **konfiguracji** element pliku konfiguracji aplikacji. Elementy podrzędne zawierają **Dodaj**, **wyczyść**, i **Usuń**.  
  
 Poniższy fragment plik konfiguracji pokazuje schematu i składni, do przechowywania parametrów połączenia. **Nazwa** atrybut jest nazwą, która zapewnia do unikatowego identyfikowania parametry połączenia, dzięki czemu mogą być pobierane w czasie wykonywania. **ProviderName** to niezmienna Nazwa dostawcy danych .NET Framework, który jest zarejestrowany w pliku machine.config.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
  <configuration>  
    <connectionStrings>  
      <clear />  
      <add name="Name"   
       providerName="System.Data.ProviderName"   
       connectionString="Valid Connection String;" />  
    </connectionStrings>  
  </configuration>  
```  
  
> [!NOTE]
>  Możesz zapisać części ciągu połączenia w pliku konfiguracji i używać <xref:System.Data.Common.DbConnectionStringBuilder> klasy do jego wykonania w czasie wykonywania. Jest to przydatne w scenariuszach, w których nie znasz elementy ciągu połączenia wcześniej, lub gdy nie chcesz zapisać poufnych informacji w pliku konfiguracji. Aby uzyskać więcej informacji, zobacz [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Za pomocą plików konfiguracji zewnętrznego  
 Konfiguracja zewnętrzna pliki są oddzielne pliki, które zawierają fragmenty składające się z jednej sekcji pliku konfiguracji. Plik konfiguracyjny zewnętrznych następnie odwołuje się to główny plik konfiguracji. Przechowywanie **connectionStrings** sekcji w pliku fizycznie oddzielnymi jest przydatne w sytuacjach, w której parametry połączenia można edytować po wdrożeniu aplikacji. Na przykład standardowe zachowanie programu ASP.NET jest ponowne uruchomienie domenę aplikacji, gdy zmodyfikowane pliki konfiguracyjne, które powoduje utratę informacji o stanie. Modyfikowanie pliku konfiguracji zewnętrznego nie spowoduje jednak ponowne uruchomienie aplikacji. Pliki konfiguracji zewnętrznych nie są ograniczone do platformy ASP.NET; one może również przez aplikacje Windows. Ponadto zabezpieczenia dostępu do pliku i uprawnienia może służyć do ograniczania dostępu do plików zewnętrznych konfiguracji. Praca z plikami konfiguracji zewnętrznych w czasie wykonywania jest niewidoczna i wymaga bez kodowania.  
  
 Aby przechowywać parametry połączenia w pliku konfiguracji zewnętrznej, należy utworzyć oddzielny plik, zawierający tylko **connectionStrings** sekcji. Nie dołączaj żadnych dodatkowych elementów, sekcji lub atrybutów. Ten przykład przedstawia składnię plik konfiguracji zewnętrznego.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 W pliku konfiguracji aplikacji głównej, użyj **configSource** atrybutu, aby określić w pełni kwalifikowaną nazwę i lokalizację pliku zewnętrznego. W tym przykładzie odwołuje się do pliku zewnętrznego konfiguracji o nazwie `connections.config`.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Pobieranie parametrów połączenia w czasie wykonywania  
 .NET Framework 2.0 wprowadzono nowe klasy w <xref:System.Configuration> przestrzeni nazw w celu uproszczenia podczas pobierania parametrów połączenia z plików konfiguracji w czasie wykonywania. Według nazwy lub nazwa dostawcy, można programowo pobrać parametry połączenia.  
  
> [!NOTE]
>  **Machine.config** plik zawiera także **connectionStrings** sekcję, która zawiera parametry połączenia używane przez program Visual Studio. Podczas pobierania parametrów połączenia, nazwa dostawcy z **app.config** pliku w aplikacji Windows, parametry połączenia w **machine.config** uzyskiwanie pierwszezaładowane,anastępniepozycje**app.config**. Dodawanie **wyczyść** natychmiast po **connectionStrings** elementu usuwa wszystkie odziedziczone odwołania ze struktury danych w pamięci, tak aby tylko parametry połączenia zdefiniowane w lokalnym **app.config** pliku są traktowane jako.  
  
### <a name="working-with-the-configuration-classes"></a>Praca z klas konfiguracji  
 Począwszy od programu .NET Framework 2.0, <xref:System.Configuration.ConfigurationManager> jest używany podczas pracy z plikami konfiguracji na komputerze lokalnym, zastępując przestarzałego <xref:System.Configuration.ConfigurationSettings>. <xref:System.Web.Configuration.WebConfigurationManager> Służy do pracy z plikami konfiguracji platformy ASP.NET. Jest przeznaczona do pracy z plikami konfiguracji na serwerze sieci Web i umożliwia dostęp programistyczny do sekcji w pliku konfiguracji, takich jak **system.web**.  
  
> [!NOTE]
>  Uzyskiwanie dostępu do plików konfiguracji w czasie wykonywania wymaga udzielanie uprawnień do obiektu wywołującego wymagane uprawnienia zależą od typu aplikacji, pliku konfiguracji i lokalizacji. Aby uzyskać więcej informacji, zobacz [przy użyciu klas konfiguracji](https://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc) i <xref:System.Web.Configuration.WebConfigurationManager> dla aplikacji ASP.NET i <xref:System.Configuration.ConfigurationManager> dla aplikacji Windows.  
  
 Możesz użyć <xref:System.Configuration.ConnectionStringSettingsCollection> można pobrać parametry połączenia z plików konfiguracji aplikacji. Zawiera on zbiór <xref:System.Configuration.ConnectionStringSettings> obiektów, z których każdy reprezentuje jeden wpis **connectionStrings** sekcji. Jego właściwości są mapowane na atrybuty ciągu połączenia, dzięki czemu możesz pobrać parametry połączenia, określając nazwę lub nazwę dostawcy.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Nazwa parametrów połączenia. Mapuje **nazwa** atrybutu.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Nazwa FQDN dostawcy. Mapuje **providerName** atrybutu.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Parametry połączenia. Mapuje **connectionString** atrybutu.|  
  
### <a name="example-listing-all-connection-strings"></a>Przykład: Wyświetlanie listy wszystkich parametrów połączenia  
 Ten przykład wykonuje iterację przez `ConnectionStringSettings` kolekcji i wyświetla <xref:System.Configuration.ConnectionStringSettings.Name%2A>, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>, i <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A> właściwości w oknie konsoli.  
  
> [!NOTE]
>  System.Configuration.dll nie są objęte wszystkich typów projektów i może być konieczne Ustaw odwołanie do niej, aby można było używać klas konfiguracji. Nazwę i lokalizację pliku konfiguracji określonej aplikacji jest zależna od typu aplikacji i proces hostingu.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Przykład: Pobieranie parametrów połączenia o nazwie  
 W tym przykładzie pokazano, jak pobrać parametry połączenia z pliku konfiguracji, określając jej nazwę. Ten kod tworzy <xref:System.Configuration.ConnectionStringSettings> obiektem, dostarczony parametr danych wejściowych do dopasowania <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> nazwy. Jeśli nie pasującej nazwie zostanie znaleziony, funkcja zwraca `null` (`Nothing` w języku Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Przykład: Pobieranie parametrów połączenia, nazwa dostawcy  
 W tym przykładzie pokazano, jak pobrać parametry połączenia, określając nazwę dostawcy we wszystkich kulturach w formacie *System.Data.ProviderName*. Kod wykonuje iterację przez <xref:System.Configuration.ConnectionStringSettingsCollection> i zwraca ciąg połączenia dla pierwszego <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> znaleziono. Jeśli nazwa dostawcy nie zostanie znaleziony, funkcja zwraca `null` (`Nothing` w języku Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Szyfrowanie przy użyciu sekcji pliku konfiguracji chronionych konfiguracji  
 ASP.NET 2.0 wprowadzono nową funkcję o nazwie *chronione konfiguracji*, która umożliwia szyfrowanie poufnych informacji w pliku konfiguracji. Mimo że przeznaczony głównie dla platformy ASP.NET, konfiguracji chronionych można również zaszyfrować sekcji pliku konfiguracji w aplikacji Windows. Aby uzyskać szczegółowy opis możliwości konfiguracji chronionych, zobacz [szyfrowania informacji przy użyciu chronione Konfiguracja](https://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
 Następujący plik konfiguracji fragment przedstawia **connectionStrings** sekcji po został zaszyfrowany. **ConfigProtectionProvider** określa dostawcę konfiguracji chronionych, używany do szyfrowania i odszyfrowywania parametry połączenia. **Element EncryptedData** sekcja zawiera zaszyfrowanego tekstu.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Po pobraniu zaszyfrowanego połączenia w czasie wykonywania programu .NET Framework używa określonego dostawcy do odszyfrowania **element CipherValue** i udostępnić je do aplikacji. Nie ma potrzeby pisania dodatkowego kodu do zarządzania procesem odszyfrowywanie.  
  
### <a name="protected-configuration-providers"></a>Dostawcy konfiguracji chronionych  
 Dostawcy konfiguracji chronionych są zarejestrowane w usłudze **configProtectedData** części **machine.config** pliku na komputerze lokalnym, jak pokazano w poniższy fragment przedstawia dwa chronione dostawcy konfiguracji dostarczone z programem .NET Framework. Aby zwiększyć czytelność zostały obcięte pokazanych tu wartości.  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"   
      type="System.Configuration.RsaProtectedConfigurationProvider, ... />  
    <add name="DataProtectionConfigurationProvider"   
      type="System.Configuration.DpapiProtectedConfigurationProvider, ... />  
  </providers>  
</configProtectedData>  
```  
  
 Możesz skonfigurować dostawców dodatkowej konfiguracji chronionych przez dodanie ich do **machine.config** pliku. Możesz również utworzyć własnego dostawcę konfiguracji chronionych przez dziedziczenie z <xref:System.Configuration.ProtectedConfigurationProvider> abstrakcyjna klasa bazowa. W poniższej tabeli opisano pliki dwóch konfiguracji dołączone do programu .NET Framework.  
  
|Dostawcy|Opis|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|Używa algorytmu szyfrowania RSA do szyfrowania i odszyfrowywania danych. Algorytm RSA może służyć do szyfrowanie kluczem publicznym i podpisy cyfrowe. Jest także znana jako "klucz publiczny" lub szyfrowanie asymetryczne ponieważ wykorzystuje on dwa różne klucze. Możesz użyć [narzędzie rejestracji programu ASP.NET usług IIS (Aspnet_regiis.exe)](https://msdn.microsoft.com/library/6491c41e-e2b0-481f-9863-db3614d5f96b) do szyfrowania sekcji w pliku Web.config i zarządzać kluczami szyfrowania. ASP.NET odszyfrowuje plik konfiguracyjny podczas przetwarzania pliku. Tożsamość aplikacji ASP.NET musi mieć dostęp do odczytu do klucza szyfrowania, który jest używany do szyfrowania i odszyfrowywania zaszyfrowanych sekcje.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Używa interfejsu API ochrony danych Windows (DPAPI) do szyfrowania sekcji konfiguracji. Używa wbudowanych usług kryptograficznych Windows i mogą być skonfigurowane dla ochrony specyficzny dla komputera lub konta — specyficzne dla użytkownika. Ochrona specyficzny dla komputera jest przydatne w przypadku wielu aplikacji na tym samym serwerze, który muszą udostępniać informacje. Ochrona konta — specyficzne dla użytkownika może być stosowana z usługami, które działają z określona tożsamość użytkownika, takie jak udostępnione Środowisko hostingu. Każda aplikacja uruchamiana osobne tożsamości, która ogranicza dostęp do zasobów, takich jak pliki i bazy danych.|  
  
 Obaj dostawcy oferują silnego szyfrowania danych. Jednakże jeśli planujesz użyć tego samego pliku konfiguracji zaszyfrowane na wielu serwerach, np. kolektywu serwerów sieci Web, tylko `RsaProtectedConfigurationProvider` umożliwia eksportowanie kluczy szyfrowania używany do szyfrowania danych i zaimportuj je na innym serwerze. Aby uzyskać więcej informacji, zobacz [importowanie i eksportowanie chronione Konfiguracja RSA kontenery kluczy](https://msdn.microsoft.com/library/f3022b39-f17f-48c1-b067-025eab0ce8bc).  
  
### <a name="using-the-configuration-classes"></a>Przy użyciu klas konfiguracji  
 <xref:System.Configuration> Przestrzeń nazwy udostępnia klasy do pracy z ustawieniami konfiguracji programowo. <xref:System.Configuration.ConfigurationManager> Klasy zapewnia dostęp do plików konfiguracji komputera, aplikacji i użytkownika. Jeśli tworzysz aplikację ASP.NET, możesz użyć <xref:System.Web.Configuration.WebConfigurationManager> klasy, która zawiera te same funkcje, podczas umożliwiającego dostęp do ustawień, które są unikatowe dla aplikacji ASP.NET, takich jak znajdują się w  **\< System.Web >**.  
  
> [!NOTE]
>  <xref:System.Security.Cryptography> Przestrzeń nazw zawiera klasy, które zapewniają dodatkowe opcje dotyczące szyfrowania i odszyfrowywania danych. Korzystając z tych klas, w razie potrzeby usługi kryptograficzne, które nie są dostępne za pośrednictwem chronioną konfiguracji. Niektóre z tych klas są otoki dla niezarządzanych CryptoAPI firmy Microsoft, a inne wyłącznie zarządzanej implementacji. Aby uzyskać więcej informacji, zobacz [usługi kryptograficzne](https://msdn.microsoft.com/library/68a1e844-c63c-44af-9247-f6716eb23781).  
  
### <a name="appconfig-example"></a>Przykład pliku App.config  
 W tym przykładzie pokazano, jak przełączać szyfrowania **connectionStrings** sekcji **app.config** pliku dla aplikacji Windows. W tym przykładzie nazwa aplikacji jako argument, na przykład "MyApplication.exe" przyjmowane przez procedurę. **App.config** plik zostanie następnie zaszyfrowana i kopiowane do folderu, który zawiera plik wykonywalny pod nazwą "MyApplication.exe.config".  
  
> [!NOTE]
>  Parametry połączenia odszyfrować je mogą tylko na komputerze, na którym został zaszyfrowany.  
  
 Kod używa <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> metodę, aby otworzyć **app.config** plik do edycji, a <xref:System.Configuration.ConfigurationManager.GetSection%2A> metoda zwraca **connectionStrings** sekcji. Kodzie następnie sprawdza <xref:System.Configuration.SectionInformation.IsProtected%2A> właściwość, wywoływania <xref:System.Configuration.SectionInformation.ProtectSection%2A> do szyfrowania w sekcji, jeśli nie jest zaszyfrowany. <xref:System.Configuration.SectionInformation.UnprotectSection%2A> Metoda jest wywoływana w celu odszyfrowania w sekcji. <xref:System.Configuration.Configuration.Save%2A> Metoda wykonuje operację i zapisuje zmiany.  
  
> [!NOTE]
>  Należy ustawić odwołanie `System.Configuration.dll` w projekcie kodu do uruchomienia.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Przykład pliku Web.config  
 W tym przykładzie użyto <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> metody `WebConfigurationManager`. Należy pamiętać, że w takim przypadku można podać ścieżkę względną do **Web.config** plików przy użyciu tyldy. Kod wymaga odwołania do `System.Web.Configuration` klasy.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Aby uzyskać więcej informacji, zabezpieczanie aplikacji platformy ASP.NET, zobacz [NIB: zabezpieczenia programu ASP.NET](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d) i [wskazówki dotyczące zabezpieczeń w wersji 2.0 programu ASP.NET w skrócie](https://go.microsoft.com/fwlink/?LinkId=59997) w Centrum deweloperów platformy ASP.NET.  
  
## <a name="see-also"></a>Zobacz też  
 [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Przy użyciu klas konfiguracji](https://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [Konfigurowanie aplikacji](../../../../docs/framework/configure-apps/index.md)  
 [Administrowanie witryną sieci Web platformy ASP.NET](https://msdn.microsoft.com/library/1298034b-5f7d-464d-abd1-ad9e6b3eeb7e)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
