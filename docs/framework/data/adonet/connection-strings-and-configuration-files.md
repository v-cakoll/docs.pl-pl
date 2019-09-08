---
title: Parametry połączenia i pliki konfiguracji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: a98239886d6745bbb6e13e71a12764008460cdd7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785676"
---
# <a name="connection-strings-and-configuration-files"></a>Parametry połączenia i pliki konfiguracji
Osadzanie parametrów połączenia w kodzie aplikacji może prowadzić do luk w zabezpieczeniach i problemów z konserwacją. Nieszyfrowane parametry połączenia skompilowane w kodzie źródłowym aplikacji można wyświetlić za pomocą narzędzia [Ildasm. exe (Il dezasembler)](../../tools/ildasm-exe-il-disassembler.md) . Ponadto w przypadku zmiany parametrów połączenia należy ponownie skompilować aplikację. Z tego powodu zalecamy przechowywanie parametrów połączenia w pliku konfiguracyjnym aplikacji.  
  
## <a name="working-with-application-configuration-files"></a>Praca z plikami konfiguracji aplikacji  
 Pliki konfiguracji aplikacji zawierają ustawienia specyficzne dla określonej aplikacji. Na przykład aplikacja ASP.NET może mieć jeden lub więcej plików **Web. config** , a aplikacja systemu Windows może mieć opcjonalny plik **App. config** . Pliki konfiguracji współużytkują wspólne elementy, chociaż nazwa i lokalizacja pliku konfiguracji różnią się w zależności od hosta aplikacji.  
  
### <a name="the-connectionstrings-section"></a>Sekcja connectionStrings  
 Parametry połączenia mogą być przechowywane jako pary klucz/wartość w sekcji **connectionStrings** elementu **konfiguracji** w pliku konfiguracyjnym aplikacji. Elementy podrzędne obejmują **Dodawanie**, **czyszczenie**i **usuwanie**.  
  
 Poniższy fragment pliku konfiguracji ilustruje schemat i składnię przechowywania parametrów połączenia. Atrybut **name** jest udostępnianą nazwą, aby jednoznacznie identyfikować parametry połączenia, aby można było ją pobrać w czasie wykonywania. **ProviderName** jest niezmienną nazwą dostawcy danych .NET Framework, która jest zarejestrowana w pliku Machine. config.  
  
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
> Możesz zapisać część parametrów połączenia w pliku konfiguracji i użyć <xref:System.Data.Common.DbConnectionStringBuilder> klasy, aby ukończyć ją w czasie wykonywania. Jest to przydatne w scenariuszach, w których nie są znane elementy parametrów połączenia przed czasem, lub jeśli nie chcesz zapisywać poufnych informacji w pliku konfiguracyjnym. Aby uzyskać więcej informacji, zobacz [konstruktory parametrów połączenia](connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Używanie zewnętrznych plików konfiguracji  
 Zewnętrzne pliki konfiguracji to oddzielne pliki, które zawierają fragment pliku konfiguracji składający się z jednej sekcji. Plik konfiguracji zewnętrznej jest następnie przywoływany przez główny plik konfiguracji. Przechowywanie sekcji **connectionStrings** w fizycznie osobnym pliku jest przydatne w sytuacjach, w których parametry połączenia mogą być edytowane po wdrożeniu aplikacji. Na przykład standardowe zachowanie ASP.NET polega na ponownym uruchomieniu domeny aplikacji po zmodyfikowaniu plików konfiguracji, co spowoduje utratę informacji o stanie. Jednak modyfikowanie zewnętrznego pliku konfiguracji nie powoduje ponownego uruchomienia aplikacji. Zewnętrzne pliki konfiguracji nie są ograniczone do ASP.NET; mogą być również używane przez aplikacje systemu Windows. Ponadto zabezpieczenia dostępu do plików i uprawnienia mogą służyć do ograniczania dostępu do zewnętrznych plików konfiguracji. Praca z zewnętrznymi plikami konfiguracji w czasie wykonywania jest niewidoczna i nie wymaga specjalnego kodowania.  
  
 Aby przechowywać parametry połączenia w zewnętrznym pliku konfiguracji, należy utworzyć oddzielny plik, który zawiera tylko sekcję **connectionStrings** . Nie dołączaj żadnych dodatkowych elementów, sekcji lub atrybutów. Ten przykład pokazuje składnię zewnętrznego pliku konfiguracji.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 W pliku konfiguracji aplikacji głównej należy użyć atrybutu **configSource** , aby określić w pełni kwalifikowaną nazwę i lokalizację pliku zewnętrznego. Ten przykład odnosi się do zewnętrznego pliku konfiguracji `connections.config`o nazwie.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Pobieranie parametrów połączenia w czasie wykonywania  
 W .NET Framework 2,0 wprowadzono nowe klasy w <xref:System.Configuration> przestrzeni nazw, aby uprościć pobieranie parametrów połączenia z plików konfiguracji w czasie wykonywania. Można programowo pobrać parametry połączenia według nazwy lub nazwy dostawcy.  
  
> [!NOTE]
> Plik **Machine. config** zawiera również sekcję **connectionStrings** , która zawiera parametry połączenia używane przez program Visual Studio. Podczas pobierania parametrów połączenia według nazwy dostawcy z pliku **App. config** w aplikacji systemu Windows, w pierwszej kolejności zostaną załadowane parametry połączenia w **Machine. config** , a następnie wpisy w **pliku App. config**. Dodanie **Clear** zaraz po elemencie **connectionStrings** usuwa wszystkie Odziedziczone odwołania ze struktury danych w pamięci, dzięki czemu są brane pod uwagę tylko parametry połączenia zdefiniowane w lokalnym pliku **App. config** .  
  
### <a name="working-with-the-configuration-classes"></a>Praca z klasami konfiguracji  
 Począwszy od .NET Framework 2,0, <xref:System.Configuration.ConfigurationManager> jest używany podczas pracy z plikami konfiguracyjnymi na komputerze lokalnym, zastępując <xref:System.Configuration.ConfigurationSettings>przestarzałe. <xref:System.Web.Configuration.WebConfigurationManager>służy do pracy z plikami konfiguracji ASP.NET. Jest przeznaczony do pracy z plikami konfiguracyjnymi na serwerze sieci Web i umożliwia programowy dostęp do sekcji pliku konfiguracji, takich jak **System. Web**.  
  
> [!NOTE]
> Uzyskiwanie dostępu do plików konfiguracji w czasie wykonywania wymaga udzielenia uprawnień dla obiektu wywołującego; wymagane uprawnienia są zależne od typu aplikacji, pliku konfiguracji i lokalizacji. Aby uzyskać więcej informacji, zobacz [Korzystanie z klas konfiguracji](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100)) i <xref:System.Web.Configuration.WebConfigurationManager> aplikacji ASP.NET oraz <xref:System.Configuration.ConfigurationManager> dla aplikacji systemu Windows.  
  
 Możesz użyć, <xref:System.Configuration.ConnectionStringSettingsCollection> aby pobrać parametry połączenia z plików konfiguracji aplikacji. Zawiera kolekcję <xref:System.Configuration.ConnectionStringSettings> obiektów, z których każdy reprezentuje pojedynczy wpis w sekcji **connectionStrings** . Jego właściwości są mapowane na atrybuty parametrów połączenia, co pozwala na pobranie parametrów połączenia przez określenie nazwy lub nazwy dostawcy.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Nazwa parametrów połączenia. Mapuje do atrybutu **name** .|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|W pełni kwalifikowana nazwa dostawcy. Mapuje na atrybut **ProviderName** .|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Parametry połączenia. Mapuje do atrybutu **ConnectionString** .|  
  
### <a name="example-listing-all-connection-strings"></a>Przykład: Wyświetlanie listy wszystkich parametrów połączenia  
 Ten przykład wykonuje iterację przez <xref:System.Configuration.ConnectionStringSettingsCollection> i <xref:System.Configuration.ConnectionStringSettings.Name%2A?displayProperty=nameWithType>wyświetla właściwości, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A?displayProperty=nameWithType>, i <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A?displayProperty=nameWithType> w oknie konsoli.  
  
> [!NOTE]
> Element System. Configuration. dll nie jest uwzględniony we wszystkich typach projektów i może być konieczne ustawienie dla niego odwołania w celu użycia klas konfiguracji. Nazwa i lokalizacja określonego pliku konfiguracyjnego aplikacji różnią się w zależności od typu aplikacji i procesu hostingu.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Przykład: Pobieranie parametrów połączenia według nazwy  
 W tym przykładzie pokazano, jak pobrać parametry połączenia z pliku konfiguracji, określając jego nazwę. Kod tworzy <xref:System.Configuration.ConnectionStringSettings> obiekt pasujący <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> do podanego parametru wejściowego do nazwy. Jeśli nie zostanie znaleziona zgodna nazwa, funkcja zwróci `null` wartość`Nothing` (w Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Przykład: Pobieranie parametrów połączenia według nazwy dostawcy  
 W tym przykładzie pokazano, jak pobrać parametry połączenia przez określenie niezmiennej nazwy dostawcy w formacie *System. Data. ProviderName*. Kod wykonuje iterację <xref:System.Configuration.ConnectionStringSettingsCollection> i zwraca parametry połączenia dla pierwszego <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> znalezionego elementu. Jeśli nazwa dostawcy nie zostanie znaleziona, funkcja zwróci wartość `null` (`Nothing` w Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Szyfrowanie sekcji pliku konfiguracji przy użyciu konfiguracji chronionej  
 W ASP.NET 2,0 wprowadzono nową funkcję o nazwie *chroniona konfiguracja*, która umożliwia szyfrowanie poufnych informacji w pliku konfiguracji. Mimo że program przeznaczony głównie do ASP.NET, konfiguracja chroniona może być również używana do szyfrowania sekcji plików konfiguracyjnych w aplikacjach systemu Windows. Aby uzyskać szczegółowy opis możliwości konfiguracji chronionych, zobacz [szyfrowanie informacji o konfiguracji za pomocą konfiguracji chronionej](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
 Poniższy fragment pliku konfiguracji przedstawia sekcję **connectionStrings** po jej zaszyfrowaniu. **ConfigProtectionProvider** określa chronionego dostawcę konfiguracji używany do szyfrowania i odszyfrowywania parametrów połączenia. Sekcja **EncryptedData** zawiera tekst szyfru.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Gdy szyfrowane parametry połączenia są pobierane w czasie wykonywania, .NET Framework używa określonego dostawcy do odszyfrowania **CipherValue** i udostępnienia aplikacji. Nie trzeba pisać żadnego dodatkowego kodu w celu zarządzania procesem odszyfrowywania.  
  
### <a name="protected-configuration-providers"></a>Dostawcy konfiguracji chronionej  
 Dostawcy chronionej konfiguracji są zarejestrowani w sekcji **configProtectedData** pliku **Machine. config** na komputerze lokalnym, jak pokazano w poniższym fragmencie, który pokazuje dwóch chronionych dostawców konfiguracji dostarczonych z programem .NET Framework. Podane tutaj wartości zostały obcięte na potrzeby czytelności.  
  
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
  
 Dodatkowe chronione dostawcy konfiguracji można skonfigurować przez dodanie ich do pliku **Machine. config** . Możesz również utworzyć własnego dostawcę konfiguracji chronionej przez dziedziczenie z <xref:System.Configuration.ProtectedConfigurationProvider> abstrakcyjnej klasy podstawowej. W poniższej tabeli opisano dwa pliki konfiguracji dołączone do .NET Framework.  
  
|Dostawca|Opis|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|Szyfruje i odszyfrowuje dane przy użyciu algorytmu szyfrowania RSA. Algorytmu RSA można używać zarówno w przypadku szyfrowania klucza publicznego, jak i podpisów cyfrowych. Jest on również znany jako "klucz publiczny" lub asymetryczne szyfrowanie, ponieważ wykorzystuje dwa różne klucze. Za pomocą [narzędzia rejestracji programu ASP.NET IIS (Aspnet_regiis. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)) można szyfrować sekcje w pliku Web. config i zarządzać kluczami szyfrowania. ASP.NET odszyfrowuje plik konfiguracji podczas przetwarzania pliku. Tożsamość aplikacji ASP.NET musi mieć dostęp do odczytu do klucza szyfrowania używanego do szyfrowania i odszyfrowywania zaszyfrowanych sekcji.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Program używa interfejsu API ochrony danych systemu Windows (DPAPI) do szyfrowania sekcji konfiguracyjnych. Używa wbudowanej usługi kryptograficznej systemu Windows i można ją skonfigurować dla ochrony specyficznej dla komputera lub użytkownika. Ochrona specyficzna dla maszyn jest przydatna w przypadku wielu aplikacji na tym samym serwerze, które muszą udostępniać informacje. Ochrona specyficzna dla konta użytkownika może być używana z usługami, które działają z określoną tożsamością użytkownika, taką jak udostępnione środowisko hostingu. Każda aplikacja działa w ramach oddzielnej tożsamości, która ogranicza dostęp do zasobów, takich jak pliki i bazy danych.|  
  
 Obaj dostawcy oferują silne szyfrowanie danych. Jeśli jednak planujesz używać tego samego zaszyfrowanego pliku konfiguracji na wielu serwerach, takich jak Farma sieci Web, tylko <xref:System.Configuration.RsaProtectedConfigurationProvider> program umożliwia eksportowanie kluczy szyfrowania używanych do szyfrowania danych i importowanie ich na inny serwer. Aby uzyskać więcej informacji, zobacz [Importowanie i eksportowanie kontenerów kluczy RSA konfiguracji chronionej](https://docs.microsoft.com/previous-versions/aspnet/yxw286t2(v=vs.100)).  
  
### <a name="using-the-configuration-classes"></a>Korzystanie z klas konfiguracji  
 <xref:System.Configuration> Przestrzeń nazw zawiera klasy do programistycznego działania z ustawieniami konfiguracji. <xref:System.Configuration.ConfigurationManager> Klasa zapewnia dostęp do plików konfiguracji komputera, aplikacji i użytkownika. W przypadku tworzenia aplikacji ASP.NET można użyć <xref:System.Web.Configuration.WebConfigurationManager> klasy, która zapewnia te same funkcje, a także umożliwia dostęp do ustawień unikatowych dla aplikacji ASP.NET, takich jak te znajdujące się w **\<> System. Web**.  
  
> [!NOTE]
> <xref:System.Security.Cryptography> Przestrzeń nazw zawiera klasy, które udostępniają dodatkowe opcje szyfrowania i odszyfrowywania danych. Użyj tych klas, jeśli są wymagane usługi kryptograficzne, które nie są dostępne przy użyciu konfiguracji chronionej. Niektóre z tych klas są otokami dla niezarządzanego interfejsu CryptoAPI firmy Microsoft, podczas gdy inne są całkowicie zarządzane. Aby uzyskać więcej informacji, zobacz [usługi kryptograficzne](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/93bskf9z(v=vs.90)).  
  
### <a name="appconfig-example"></a>Przykład pliku App. config  
 W tym przykładzie pokazano, jak przełączyć szyfrowanie sekcji **connectionStrings** w pliku **App. config** dla aplikacji systemu Windows. W tym przykładzie procedura przyjmuje nazwę aplikacji jako argument, na przykład "aplikacja. exe". Plik **App. config** będzie następnie szyfrowany i kopiowany do folderu, który zawiera plik wykonywalny pod nazwą "WebApplication. exe. config".  
  
> [!NOTE]
> Parametry połączenia można odszyfrować tylko na komputerze, na którym został zaszyfrowany.  
  
 Kod używa <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> metody do otwierania pliku **App. config** do <xref:System.Configuration.ConfigurationManager.GetSection%2A> edycji, a metoda zwraca sekcję **connectionStrings** . Następnie kod sprawdza <xref:System.Configuration.SectionInformation.IsProtected%2A> właściwość, <xref:System.Configuration.SectionInformation.ProtectSection%2A> wywołując, aby zaszyfrować sekcję, jeśli nie jest zaszyfrowana. <xref:System.Configuration.SectionInformation.UnprotectSection%2A> Metoda jest wywoływana w celu odszyfrowania sekcji. <xref:System.Configuration.Configuration.Save%2A> Metoda wykonuje operację i zapisuje zmiany.  
  
> [!NOTE]
> Aby kod mógł zostać uruchomiony, `System.Configuration.dll` należy ustawić odwołanie do elementu w projekcie.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Przykład pliku Web. config  
 W tym przykładzie zastosowano <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> metodę. `WebConfigurationManager` Należy zauważyć, że w takim przypadku można podać ścieżkę względną do pliku **Web. config** przy użyciu tyldy. Kod wymaga odwołania do `System.Web.Configuration` klasy.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Aby uzyskać więcej informacji na temat zabezpieczania aplikacji ASP.NET, zobacz [zabezpieczanie ASP.NET witryn sieci Web](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- [Konstruktorzy parametrów połączeń](connection-string-builders.md)
- [Ochrona informacji o połączeniu](protecting-connection-information.md)
- [Korzystanie z klas konfiguracji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms228063(v=vs.90))
- [Konfigurowanie aplikacji](../../configure-apps/index.md)
- [Administrowanie witryną sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6hy1xzbw(v=vs.100))
- [Omówienie ADO.NET](ado-net-overview.md)
