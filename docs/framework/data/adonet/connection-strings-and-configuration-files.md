---
title: "Parametry połączenia i pliki konfiguracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 358bc0428a53817e85d5a5e278d8da4e1a8b6927
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="connection-strings-and-configuration-files"></a>Parametry połączenia i pliki konfiguracji
Osadzanie ciągów połączenia w kodzie aplikacji może prowadzić do problemów konserwacji i luk w zabezpieczeniach. Parametry połączenia nieszyfrowanego skompilowana do kodu źródłowego aplikacji można wyświetlić przy użyciu [Ildasm.exe (dezasembler IL)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) narzędzia. Ponadto jeśli kiedykolwiek zmieni się parametry połączenia, aplikacja musi ponownie skompilowana. Z tego względu zalecamy przechowywanie parametrów połączenia w pliku konfiguracyjnym aplikacji.  
  
## <a name="working-with-application-configuration-files"></a>Praca z pliki konfiguracji aplikacji  
 Pliki konfiguracji aplikacji zawierają ustawienia, które są specyficzne dla określonej aplikacji. Na przykład aplikacja ASP.NET może mieć co najmniej jeden **web.config** plików i aplikacji systemu Windows mogą mieć opcjonalny **app.config** pliku. Pliki konfiguracji udostępnianie typowymi elementami, chociaż nazwy i lokalizacji pliku konfiguracyjnego różnić w zależności od aplikacji hosta.  
  
### <a name="the-connectionstrings-section"></a>ConnectionStrings sekcji  
 Parametry połączenia mogą być przechowywane jako pary klucz wartość w **connectionStrings** sekcji **konfiguracji** elementu plik konfiguracji aplikacji. Elementy podrzędne obejmują **dodać**, **wyczyść**, i **Usuń**.  
  
 Poniższy fragment pliku konfiguracji pokazuje schematu i składni do przechowywania parametrów połączenia. **Nazwa** atrybut jest nazwą, która zapewniają do unikatowego identyfikowania ciąg połączenia, dzięki czemu mogą być pobierane w czasie wykonywania. **ProviderName** niezmienna Nazwa dostawcy danych .NET Framework, który jest zarejestrowany w pliku machine.config.  
  
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
>  Można zapisać w ciągu połączenia w pliku konfiguracji i używać <xref:System.Data.Common.DbConnectionStringBuilder> klasę, aby zakończyć je w czasie wykonywania. Jest to przydatne w scenariuszach, w których nie wiadomo, elementy parametry połączenia wcześniejsze lub jeśli nie chcesz zapisać poufnych informacji w pliku konfiguracji. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Za pomocą plików konfiguracji zewnętrznych  
 Pliki konfiguracji zewnętrzne są osobne pliki zawierające fragment składające się z jednej sekcji pliku konfiguracji. Plik konfiguracji zewnętrznych następnie odwołuje się plik konfiguracji głównego. Przechowywanie **connectionStrings** sekcji w pliku osobnych jest przydatne w sytuacjach, w którym można edytować parametry połączenia po wdrożeniu aplikacji. Na przykład standardowe zachowanie ASP.NET jest ponowne uruchomienie domeny aplikacji, gdy zmodyfikowane pliki konfiguracji, co powoduje utratę informacji o stanie. Modyfikowanie pliku konfiguracji zewnętrznych nie powoduje jednak ponowne uruchomienie aplikacji. Pliki konfiguracji zewnętrznych nie są ograniczone do ASP.NET; one mogą również posłużyć aplikacji systemu Windows. Ponadto zabezpieczeń dostępu do plików i uprawnienia można ograniczyć dostęp do plików konfiguracyjnych zewnętrznych. Praca z plikami konfiguracji zewnętrznych w czasie wykonywania jest niewidoczny i wymaga nie kodowania.  
  
 Aby przechowywać parametry połączenia w pliku konfiguracyjnym zewnętrznych, należy utworzyć oddzielny plik, który zawiera tylko **connectionStrings** sekcji. Nie dołączaj wszelkie dodatkowe elementy, sekcje lub atrybutów. Ten przykład przedstawia składnię pliku konfiguracyjnego zewnętrznych.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 W pliku konfiguracyjnym aplikacji głównej, użyj **configSource** atrybutu, aby określić w pełni kwalifikowanej nazwy i lokalizacji pliku zewnętrznego. W tym przykładzie odwołuje się do pliku konfiguracji zewnętrznych o nazwie `connections.config`.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Podczas pobierania parametrów połączenia w czasie wykonywania  
 .NET Framework 2.0 wprowadzono nowe klasy w <xref:System.Configuration> przestrzeni nazw, aby uprościć podczas pobierania parametrów połączenia z pliki konfiguracji w czasie wykonywania. Parametry połączenia można programowo pobrać według nazwy lub nazwa dostawcy.  
  
> [!NOTE]
>  **Machine.config** plik zawiera także **connectionStrings** sekcja, która zawiera parametry połączenia używane przez program Visual Studio. Podczas pobierania parametrów połączenia o nazwie dostawcy z **app.config** plik w aplikacji Windows, parametry połączenia w **machine.config** uzyskać pierwszy załadowany, a następnie wpisy z **app.config**. Dodawanie **wyczyść** natychmiast po **connectionStrings** element usuwa odwołania wszystkie odziedziczone ze struktury danych w pamięci, dzięki czemu tylko parametry połączenia zdefiniowane w lokalnej **app.config** są traktowane jako plik.  
  
### <a name="working-with-the-configuration-classes"></a>Praca z klasami konfiguracji  
 Począwszy od programu .NET Framework 2.0, <xref:System.Configuration.ConfigurationManager> jest używany podczas pracy z plików konfiguracyjnych na komputerze lokalnym, zastępując przestarzałe <xref:System.Configuration.ConfigurationSettings>. <xref:System.Web.Configuration.WebConfigurationManager>Służy do pracy z plikami konfiguracji ASP.NET. Jest przeznaczona do pracy z plikami konfiguracji na serwerze sieci Web i umożliwia dostęp programistyczny do sekcji pliku konfiguracji, takich jak **system.web**.  
  
> [!NOTE]
>  Uzyskiwanie dostępu do plików konfiguracji w czasie wykonywania wymaga przyznawania uprawnień do wywołującego wymagane uprawnienia są zależne od typu aplikacji, plików konfiguracji i lokalizacji. Aby uzyskać więcej informacji, zobacz [przy użyciu klasy konfiguracji](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc) i <xref:System.Web.Configuration.WebConfigurationManager> dla aplikacji ASP.NET i <xref:System.Configuration.ConfigurationManager> dla aplikacji systemu Windows.  
  
 Można użyć <xref:System.Configuration.ConnectionStringSettingsCollection> można pobrać parametry połączenia z pliki konfiguracji aplikacji. Zawiera kolekcję <xref:System.Configuration.ConnectionStringSettings> obiektów, z których każdy reprezentuje pojedynczy wpis w **connectionStrings** sekcji. Jego właściwości są mapowane na atrybuty ciągu połączenia, co umożliwia pobrać parametry połączenia, określając nazwę lub nazwę dostawcy.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Nazwa ciągu połączenia. Mapuje **nazwa** atrybutu.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Nazwa FQDN dostawcy. Mapuje **providerName** atrybutu.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Parametry połączenia. Mapuje **connectionString** atrybutu.|  
  
### <a name="example-listing-all-connection-strings"></a>Przykład: Wyświetlanie listy wszystkich parametrów połączenia  
 W tym przykładzie iteruje `ConnectionStringSettings` kolekcji i wyświetla <xref:System.Configuration.ConnectionStringSettings.Name%2A>, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>, i <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A> właściwości w oknie konsoli.  
  
> [!NOTE]
>  System.Configuration.dll nie znajduje się na wszystkie typy projektu, i może być konieczne Ustaw odwołanie do niej, aby można było używać klas konfiguracji. Nazwa i lokalizacja pliku konfiguracji aplikacji jest zależna od typu aplikacji i proces hostingu.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Przykład: Podczas pobierania ciągu połączenia według nazwy  
 W tym przykładzie pokazano, jak pobrać parametry połączenia w pliku konfiguracji, określając jej nazwę. Kod tworzy <xref:System.Configuration.ConnectionStringSettings> obiektu podany parametr wejściowy do dopasowania <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> nazwy. Jeśli nie pasującej nazwie zostanie znaleziony, funkcja zwraca `null` (`Nothing` w języku Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Przykład: Podczas pobierania ciągu połączenia według nazwy dostawcy  
 W tym przykładzie pokazano, jak pobrać parametry połączenia, określając dostawca niezmiennej nazwy w formacie *System.Data.ProviderName*. Iteruje po kodzie <xref:System.Configuration.ConnectionStringSettingsCollection> i zwraca ciąg połączenia dla pierwszego <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> znaleziono. Jeśli nazwa dostawcy nie zostanie znaleziony, funkcja zwraca `null` (`Nothing` w języku Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Szyfrowanie sekcji pliku konfiguracji przy użyciu chronione konfiguracji  
 ASP.NET 2.0 wprowadzono nową funkcję o nazwie *chronione konfiguracji*, który umożliwia szyfrowanie poufnych informacji w pliku konfiguracji. Chociaż przeznaczony głównie dla platformy ASP.NET, konfiguracji chronionych można również zaszyfrować sekcji pliku konfiguracji w aplikacjach systemu Windows. Aby uzyskać szczegółowy opis możliwości konfiguracji chronionych, zobacz [szyfrowania informacji przy użyciu chronione Konfiguracja](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
 Pokazuje fragmentu następującego pliku konfiguracji **connectionStrings** sekcji po został zaszyfrowany. **ConfigProtectionProvider** określa dostawcę konfiguracji chronionych, używany do szyfrowania i odszyfrowywania parametry połączenia. **EncryptedData** sekcja zawiera tekst zaszyfrowany.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Po pobraniu parametrów zaszyfrowanego połączenia w czasie wykonywania programu .NET Framework używa określonego dostawcy do odszyfrowania **CipherValue** i udostępnienie go do aplikacji. Nie trzeba zapisać jakiegokolwiek dodatkowego kodu do zarządzania procesem odszyfrowywania.  
  
### <a name="protected-configuration-providers"></a>Dostawcy konfiguracji chronionych  
 Dostawcy konfiguracji chronione są zarejestrowane w **configProtectedData** sekcji **machine.config** plików na komputerze lokalnym, jak pokazano w poniższy fragment, który zawiera dwa chronione dostarczonego z programem .NET Framework dostawców konfiguracji. Aby można było czytać zostały obcięte pokazanych tu wartości.  
  
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
  
 Możesz skonfigurować dodatkowe czynności konfiguracyjne chronionych dostawców przez dodanie ich do **machine.config** pliku. Można również utworzyć własnego dostawcę konfiguracji chronionych przez dziedziczenie z <xref:System.Configuration.ProtectedConfigurationProvider> abstrakcyjnej klasy podstawowej. W poniższej tabeli opisano konfiguracji dwóch plików uwzględnionych w programie .NET Framework.  
  
|Dostawcy|Opis|  
|--------------|-----------------|  
|<!--zz<xref:System.Configuration.RSAProtectedConfigurationProvider>-->`System.Configuration.RSAProtectedConfigurationProvider`|Używa algorytmu szyfrowania RSA do szyfrowania i odszyfrowywania danych. Algorytm RSA może służyć do publicznego klucza szyfrowania i podpisy cyfrowe. Jest także znana jako "klucza publicznego" lub szyfrowanie asymetryczne ponieważ wykorzystuje on dwa różne klucze. Można użyć [narzędzie rejestracji programu ASP.NET usług IIS (Aspnet_regiis.exe)](http://msdn.microsoft.com/library/6491c41e-e2b0-481f-9863-db3614d5f96b) do szyfrowania sekcji w pliku Web.config i zarządzać kluczami szyfrowania. ASP.NET odszyfrowuje pliku konfiguracji podczas przetwarzania pliku. Tożsamość aplikacji ASP.NET musi mieć dostęp do odczytu do klucza szyfrowania używanego do szyfrowania i odszyfrowywania zaszyfrowanych sekcje.|  
|<!--zz<xref:System.Configuration.DPAPIProtectedConfigurationProvider>-->`System.Configuration.DPAPIProtectedConfigurationProvider`|Używa interfejsu API ochrony danych systemu Windows (DPAPI) do szyfrowania sekcji konfiguracyjnych. Używa wbudowanych usług kryptograficznych systemu Windows, a można skonfigurować ochrony komputera lub określonego konta użytkownika. Ochrona komputera jest przydatne w przypadku wielu aplikacji na tym samym serwerze, które są potrzebne do udostępniania informacji. Ochrona określonego konta użytkownika może być stosowana z usług, które działają z określona tożsamość użytkownika, takich jak udostępnione środowiska macierzystego. Każda aplikacja działa w ramach oddzielnego tożsamości, ogranicza dostęp do zasobów, takich jak pliki i baz danych.|  
  
 Zarówno dostawców oferują silne szyfrowanie danych. Jednak jeśli planujesz używać tego samego pliku konfiguracji zaszyfrowanej na wielu serwerach, takich jak farmy sieci Web, tylko `RsaProtectedConfigurationProvider` umożliwia eksportowanie kluczy szyfrowania używany do szyfrowania danych i zaimportuj je na innym serwerze. Aby uzyskać więcej informacji, zobacz [importowanie i eksportowanie chronione konfiguracji RSA klucza kontenery](http://msdn.microsoft.com/library/f3022b39-f17f-48c1-b067-025eab0ce8bc).  
  
### <a name="using-the-configuration-classes"></a>Używanie klas konfiguracji  
 <xref:System.Configuration> Przestrzeń nazw zawiera klasy do współdziałania z ustawieniami konfiguracji programowo. <xref:System.Configuration.ConfigurationManager> Klasy zapewnia dostęp do plików konfiguracji komputera, aplikacji i użytkownika. Jeśli tworzysz aplikację ASP.NET, możesz użyć <xref:System.Web.Configuration.WebConfigurationManager> klasy, która zapewnia te same funkcje podczas umożliwiającego dostęp do ustawień, które są unikatowe dla aplikacji ASP.NET, takich jak znajdują się w  **\< System.Web >**.  
  
> [!NOTE]
>  <xref:System.Security.Cryptography> Przestrzeń nazw zawiera klasy, które zapewniają dodatkowe opcje dotyczące szyfrowania i odszyfrowywania danych. Korzystając z tych klas, jeśli potrzebujesz usługi kryptograficzne, które nie są dostępne przy użyciu zabezpieczoną konfiguracji. Niektóre z tych klas są otoki dla niezarządzanego CryptoAPI firmy Microsoft, a inne implementacje czysto zarządzanych. Aby uzyskać więcej informacji, zobacz [usługi kryptograficzne](http://msdn.microsoft.com/en-us/68a1e844-c63c-44af-9247-f6716eb23781).  
  
### <a name="appconfig-example"></a>Przykład App.config  
 W tym przykładzie pokazano, jak Przełącz szyfrowania **connectionStrings** sekcji **app.config** pliku dla aplikacji systemu Windows. W tym przykładzie nazwa aplikacji jako argument, na przykład "MyApplication.exe" przyjmowane przez procedurę. **App.config** pliku będą szyfrowane i skopiowane do folderu, który zawiera plik wykonywalny pod nazwą "MyApplication.exe.config".  
  
> [!NOTE]
>  Parametry połączenia mogą być odszyfrowane tylko na komputerze, na którym został zaszyfrowany.  
  
 W kodzie użyto <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> metodę, aby otworzyć **app.config** pliku do edycji i <xref:System.Configuration.ConfigurationManager.GetSection%2A> metoda zwraca **connectionStrings** sekcji. Sprawdza kod <xref:System.Configuration.SectionInformation.IsProtected%2A> właściwości, wywołania <xref:System.Configuration.SectionInformation.ProtectSection%2A> można zaszyfrować sekcji, jeśli nie jest zaszyfrowany. <xref:System.Configuration.SectionInformation.UnprotectSection%2A> Metoda wywoływana w celu odszyfrowania sekcji. <xref:System.Configuration.Configuration.Save%2A> Metoda wykonuje tę operację i zapisuje zmiany.  
  
> [!NOTE]
>  Musisz ustawić odwołanie `System.Configuration.dll` w projekcie kodu do uruchomienia.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Przykład pliku Web.config  
 W tym przykładzie użyto <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> metody `WebConfigurationManager`. Należy pamiętać, że w takim przypadku można podać ścieżkę względną do **Web.config** pliku przy użyciu tyldy. Kod wymaga odwołania do `System.Web.Configuration` klasy.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Aby uzyskać więcej informacji, zabezpieczanie aplikacji ASP.NET, zobacz [NIB: zabezpieczenia w programie ASP.NET](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d) i [ASP.NET 2.0 rozwiązania jeden rzut oka](http://go.microsoft.com/fwlink/?LinkId=59997) w Centrum deweloperów platformy ASP.NET.  
  
## <a name="see-also"></a>Zobacz też  
 [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Używanie klas konfiguracji](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [Konfigurowanie aplikacji](../../../../docs/framework/configure-apps/index.md)  
 [Administrowanie witryną sieci Web ASP.NET](http://msdn.microsoft.com/library/1298034b-5f7d-464d-abd1-ad9e6b3eeb7e)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
