---
title: Parametry połączenia i pliki konfiguracji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 8862aa34c2d2677f5bc3e737c01cc61036c243e1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345062"
---
# <a name="connection-strings-and-configuration-files"></a>Parametry połączenia i pliki konfiguracji

Osadzanie ciągów połączeń w kodzie aplikacji może prowadzić do luk w zabezpieczeniach i problemów z konserwacją. Niezaszyfrowane parametry połączenia skompilowane do kodu źródłowego aplikacji można przeglądać za pomocą narzędzia [Ildasm.exe (IL Disassembler).](../../tools/ildasm-exe-il-disassembler.md) Ponadto jeśli ciąg połączenia kiedykolwiek się zmieni, aplikacja musi zostać ponownie skompilowana. Z tych powodów zaleca się przechowywanie ciągów połączeń w pliku konfiguracji aplikacji.  
  
## <a name="working-with-application-configuration-files"></a>Praca z plikami konfiguracji aplikacji  
 Pliki konfiguracji aplikacji zawierają ustawienia specyficzne dla określonej aplikacji. Na przykład aplikacja ASP.NET może mieć jeden lub więcej plików **web.config,** a aplikacja systemu Windows może mieć opcjonalny plik **app.config.** Pliki konfiguracyjne współużytkować wspólne elementy, chociaż nazwa i lokalizacja pliku konfiguracji różnią się w zależności od hosta aplikacji.  
  
### <a name="the-connectionstrings-section"></a>Sekcja connectionStrings  
 Parametry połączenia mogą być przechowywane jako pary klucz/wartość w sekcji **connectionStrings** elementu **konfiguracji** pliku konfiguracji aplikacji. Elementy podrzędne obejmują **dodawanie,** **wyczyszczenie**i **usuwanie**.  
  
 Poniższy fragment pliku konfiguracji demonstruje schemat i składnię do przechowywania ciągu połączenia. Atrybut **name** jest nazwą, która jest podawania w celu jednoznacznej identyfikacji ciągu połączenia, dzięki czemu można go pobrać w czasie wykonywania. **ProviderName** jest niezmienną nazwą dostawcy danych .NET Framework, który jest zarejestrowany w pliku machine.config.  
  
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
> Można zapisać część ciągu połączenia w pliku konfiguracyjnym i użyć <xref:System.Data.Common.DbConnectionStringBuilder> klasy, aby zakończyć go w czasie wykonywania. Jest to przydatne w scenariuszach, w których nie znasz elementów ciągu połączenia z wyprzedzeniem lub gdy nie chcesz zapisywać poufnych informacji w pliku konfiguracyjnym. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączeń](connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Korzystanie z zewnętrznych plików konfiguracyjnych  
 Zewnętrzne pliki konfiguracyjne to oddzielne pliki zawierające fragment pliku konfiguracyjnego składający się z pojedynczej sekcji. Zewnętrzny plik konfiguracyjny jest następnie przywołytym przez główny plik konfiguracyjny. Przechowywanie **connectionStrings** sekcji w fizycznie oddzielny plik jest przydatne w sytuacjach, gdy parametry połączenia mogą być edytowane po wdrożeniu aplikacji. Na przykład standardowe zachowanie ASP.NET jest ponowne uruchomienie domeny aplikacji, gdy pliki konfiguracyjne są modyfikowane, co powoduje utratę informacji o stanie. Jednak modyfikacja zewnętrznego pliku konfiguracji nie powoduje ponownego uruchomienia aplikacji. Zewnętrzne pliki konfiguracyjne nie są ograniczone do ASP.NET; mogą być również używane przez aplikacje windows. Ponadto zabezpieczenia dostępu do plików i uprawnienia mogą służyć do ograniczania dostępu do zewnętrznych plików konfiguracyjnych. Praca z zewnętrznymi plikami konfiguracyjnymi w czasie wykonywania jest przejrzysta i nie wymaga specjalnego kodowania.  
  
 Aby przechowywać parametry połączenia w zewnętrznym pliku konfiguracyjnym, należy utworzyć oddzielny plik zawierający tylko sekcję **connectionStrings.** Nie należy dołączać żadnych dodatkowych elementów, sekcji ani atrybutów. W tym przykładzie przedstawiono składnię zewnętrznego pliku konfiguracyjnego.  
  
```xml  
<connectionStrings>  
  <add name="Name"
   providerName="System.Data.ProviderName"
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 W głównym pliku konfiguracji aplikacji można użyć atrybutu **configSource,** aby określić w pełni kwalifikowaną nazwę i lokalizację pliku zewnętrznego. W tym przykładzie odnosi się `connections.config`do zewnętrznego pliku konfiguracji o nazwie .  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Pobieranie ciągów połączeń w czasie wykonywania  
 Program .NET Framework 2.0 wprowadził <xref:System.Configuration> nowe klasy w obszarze nazw, aby uprościć pobieranie ciągów połączeń z plików konfiguracyjnych w czasie wykonywania. Można programowo pobrać parametry połączenia według nazwy lub nazwy dostawcy.  
  
> [!NOTE]
> Plik **machine.config** zawiera również **connectionStrings** sekcji, która zawiera parametry połączenia używane przez program Visual Studio. Podczas pobierania ciągów połączeń według nazwy dostawcy z pliku **app.config** w aplikacji systemu Windows parametry połączenia w **pliku machine.config** są najpierw ładowane, a następnie wpisy z **pliku app.config**. Dodanie **wyczyszczenie** natychmiast po **connectionStrings** element usuwa wszystkie dziedziczone odwołania ze struktury danych w pamięci, tak aby uwzględniane są tylko parametry połączenia zdefiniowane w lokalnym pliku **app.config.**  
  
### <a name="working-with-the-configuration-classes"></a>Praca z klasami konfiguracji  
 Począwszy od programu .NET Framework <xref:System.Configuration.ConfigurationManager> 2.0, jest używany podczas pracy z <xref:System.Configuration.ConfigurationSettings>plikami konfiguracyjnymi na komputerze lokalnym, zastępując przestarzałe . <xref:System.Web.Configuration.WebConfigurationManager>służy do pracy z ASP.NET plikami konfiguracyjnymi. Jest przeznaczony do pracy z plikami konfiguracyjnymi na serwerze sieci Web i umożliwia programowy dostęp do sekcji plików konfiguracyjnych, takich jak **system.web**.  
  
> [!NOTE]
> Uzyskiwanie dostępu do plików konfiguracyjnych w czasie wykonywania wymaga przyznania uprawnień do obiektu wywołującego; wymagane uprawnienia zależą od typu aplikacji, pliku konfiguracyjnego i lokalizacji. Aby uzyskać więcej informacji, zobacz [Korzystanie z klas konfiguracji](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100)) i <xref:System.Web.Configuration.WebConfigurationManager> ASP.NET aplikacji oraz <xref:System.Configuration.ConfigurationManager> dla aplikacji systemu Windows.  
  
 Można użyć <xref:System.Configuration.ConnectionStringSettingsCollection> do pobierania ciągów połączeń z plików konfiguracji aplikacji. Zawiera kolekcję <xref:System.Configuration.ConnectionStringSettings> obiektów, z których każdy reprezentuje pojedynczy wpis w **connectionStrings** sekcji. Jego właściwości mapują atrybuty ciągu połączenia, umożliwiając pobranie ciągu połączenia, określając nazwę lub nazwę dostawcy.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Nazwa ciągu połączenia. Mapy do atrybutu **nazwa.**|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|W pełni kwalifikowana nazwa dostawcy. Mapy do atrybutu **providerName.**|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Parametry połączenia. Mapy do **connectionString** atrybut.|  
  
### <a name="example-listing-all-connection-strings"></a>Przykład: wyświetlanie listy wszystkich ciągów połączeń  
 W tym przykładzie <xref:System.Configuration.ConnectionStringSettingsCollection> iteruje <xref:System.Configuration.ConnectionStringSettings.Name%2A?displayProperty=nameWithType> <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A?displayProperty=nameWithType>i <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A?displayProperty=nameWithType> wyświetla , i właściwości w oknie konsoli.  
  
> [!NOTE]
> System.Configuration.dll nie jest uwzględniony we wszystkich typach projektów i może być konieczne ustawienie odwołania do niego w celu użycia klas konfiguracji. Nazwa i lokalizacja pliku konfiguracji określonej aplikacji zależy od typu aplikacji i procesu hostingu.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Przykład: Pobieranie ciągu połączenia według nazwy  
 W tym przykładzie pokazano, jak pobrać ciąg połączenia z pliku konfiguracji, określając jego nazwę. Kod tworzy <xref:System.Configuration.ConnectionStringSettings> obiekt, pasujący do podanego parametru <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> wejściowego do nazwy. Jeśli nie zostanie znaleziona pasująca`Nothing` nazwa, funkcja zwraca (w `null` języku Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Przykład: Pobieranie ciągu połączenia według nazwy dostawcy  
 W tym przykładzie pokazano, jak pobrać parametry połączenia, określając nazwę dostawcy niezmienną w formacie *System.Data.ProviderName*. Kod iteruje za <xref:System.Configuration.ConnectionStringSettingsCollection> pośrednictwem i zwraca parametry <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> połączenia dla pierwszego znalezionego. Jeśli nazwa dostawcy nie zostanie znaleziona, funkcja zwraca `null` (w`Nothing` języku Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Szyfrowanie sekcji plików konfiguracji przy użyciu konfiguracji chronionej  
 ASP.NET 2.0 wprowadzono nową funkcję, zwaną *konfiguracją chronioną,* która umożliwia szyfrowanie poufnych informacji w pliku konfiguracyjnym. Chociaż konfiguracja chroniona jest przeznaczona głównie do ASP.NET, może być również używana do szyfrowania sekcji plików konfiguracji w aplikacjach systemu Windows. Aby uzyskać szczegółowy opis chronionych funkcji konfiguracji, zobacz [Szyfrowanie informacji o konfiguracji przy użyciu chronionej konfiguracji](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
 Poniższy fragment pliku konfiguracji pokazuje **connectionStrings** sekcji po jego zaszyfrowaniu. **ConfigProtectionProvider** określa chronionego dostawcy konfiguracji używane do szyfrowania i odszyfrowywania ciągów połączeń. Sekcja **EncryptedData** zawiera tekst szyfru.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Po pobraniu zaszyfrowanego ciągu połączenia w czasie wykonywania program .NET Framework używa określonego dostawcy do odszyfrowania **funkcji CipherValue** i udostępnienia go aplikacji. Nie trzeba pisać żadnego dodatkowego kodu do zarządzania procesem odszyfrowywania.  
  
### <a name="protected-configuration-providers"></a>Dostawcy konfiguracji chronionej  
 Dostawcy konfiguracji chronionej są zarejestrowani w sekcji **configProtectedData** pliku **machine.config** na komputerze lokalnym, jak pokazano na poniższym fragmencie, który pokazuje dwóch chronionych dostawców konfiguracji dostarczanych z programem .NET Framework. Wartości pokazane w tym miejscu zostały obcięty dla czytelności.  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"
      type="System.Configuration.RsaProtectedConfigurationProvider" />  
    <add name="DataProtectionConfigurationProvider"
      type="System.Configuration.DpapiProtectedConfigurationProvider" />  
  </providers>  
</configProtectedData>  
```  
  
 Dodatkowych dostawców konfiguracji chronionych można skonfigurować, dodając je do pliku **machine.config.** Można również utworzyć własny dostawca konfiguracji chronionej <xref:System.Configuration.ProtectedConfigurationProvider> dziedzicząc z klasy podstawowej abstrakcyjne. W poniższej tabeli opisano dwa pliki konfiguracyjne dołączone do programu .NET Framework.  
  
|Dostawca|Opis|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|Używa algorytmu szyfrowania RSA do szyfrowania i odszyfrowywania danych. Algorytm RSA może być używany zarówno do szyfrowania klucza publicznego, jak i podpisów cyfrowych. Jest również znany jako "klucz publiczny" lub szyfrowanie asymetryczne, ponieważ wykorzystuje dwa różne klucze. Narzędzia rejestracji [usług ASP.NET IIS (Aspnet_regiis.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)) można używać do szyfrowania sekcji w pliku Web.config i zarządzania kluczami szyfrowania. ASP.NET odszyfrowuje plik konfiguracyjny podczas przetwarzania pliku. Tożsamość aplikacji ASP.NET musi mieć dostęp do odczytu klucza szyfrowania, który jest używany do szyfrowania i odszyfrowywania zaszyfrowanych sekcji.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Używa interfejsu API ochrony danych systemu Windows (DPAPI) do szyfrowania sekcji konfiguracji. Korzysta z wbudowanych usług kryptograficznych systemu Windows i może być skonfigurowany do ochrony specyficznej dla komputera lub konta użytkownika. Ochrona specyficzne dla komputera jest przydatna w przypadku wielu aplikacji na tym samym serwerze, które muszą udostępniać informacje. Ochrona specyficzne dla konta użytkownika może być używana z usługami, które są uruchamiane z określoną tożsamością użytkownika, taką jak udostępnione środowisko hostingowe. Każda aplikacja działa w ramach oddzielnej tożsamości, która ogranicza dostęp do zasobów, takich jak pliki i bazy danych.|  
  
 Obaj dostawcy oferują silne szyfrowanie danych. Jeśli jednak planujesz używać tego samego zaszyfrowanego pliku konfiguracyjnego na wielu <xref:System.Configuration.RsaProtectedConfigurationProvider> serwerach, takich jak farma sieci Web, tylko klucze szyfrowania używane do szyfrowania danych i importowanie ich na inny serwer. Aby uzyskać więcej informacji, zobacz [Importowanie i eksportowanie kontenerów kluczy RSA konfiguracji chronionej](https://docs.microsoft.com/previous-versions/aspnet/yxw286t2(v=vs.100)).  
  
### <a name="using-the-configuration-classes"></a>Korzystanie z klas konfiguracji  
 Obszar <xref:System.Configuration> nazw udostępnia klasy do pracy z ustawieniami konfiguracji programowo. Klasa <xref:System.Configuration.ConfigurationManager> zapewnia dostęp do plików konfiguracyjnych komputera, aplikacji i użytkownika. Jeśli tworzysz aplikację ASP.NET, możesz użyć <xref:System.Web.Configuration.WebConfigurationManager> tej klasy, która zapewnia tę samą funkcjonalność, a jednocześnie umożliwia dostęp do ustawień unikatowych dla ASP.NET aplikacji, takich jak te znalezione w ** \<>system.web **.  
  
> [!NOTE]
> Obszar <xref:System.Security.Cryptography> nazw zawiera klasy, które zapewniają dodatkowe opcje szyfrowania i odszyfrowywania danych. Użyj tych klas, jeśli potrzebujesz usług kryptograficznych, które nie są dostępne przy użyciu chronionej konfiguracji. Niektóre z tych klas są otoki dla niezarządzanych Microsoft CryptoAPI, podczas gdy inne są czysto zarządzane implementacje. Aby uzyskać więcej informacji, zobacz [Usługi kryptograficzne](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/93bskf9z(v=vs.90)).  
  
### <a name="appconfig-example"></a>Przykład pliku App.config  
 W tym przykładzie pokazano, jak przełączać szyfrowanie **sekcji connectionStrings** w pliku **app.config** dla aplikacji systemu Windows. W tym przykładzie procedura przyjmuje nazwę aplikacji jako argument, na przykład "MyApplication.exe". Plik **app.config** zostanie zaszyfrowany i skopiowany do folderu zawierającego plik wykonywalny pod nazwą "MyApplication.exe.config".  
  
> [!NOTE]
> Parametry połączenia można odszyfrować tylko na komputerze, na którym został zaszyfrowany.  
  
 Kod <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> używa metody, aby otworzyć plik **app.config** do <xref:System.Configuration.ConfigurationManager.GetSection%2A> edycji, a metoda zwraca **connectionStrings** sekcji. Kod następnie sprawdza <xref:System.Configuration.SectionInformation.IsProtected%2A> właściwość, <xref:System.Configuration.SectionInformation.ProtectSection%2A> wywołując do zaszyfrowania sekcji, jeśli nie jest zaszyfrowany. Metoda <xref:System.Configuration.SectionInformation.UnprotectSection%2A> jest wywoływana w celu odszyfrowania sekcji. Metoda <xref:System.Configuration.Configuration.Save%2A> kończy operację i zapisuje zmiany.  
  
> [!NOTE]
> Należy ustawić odwołanie `System.Configuration.dll` w projekcie, aby kod do uruchomienia.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Przykład web.config  
 W tym przykładzie użyto <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> metody . `WebConfigurationManager` Należy zauważyć, że w takim przypadku można podać ścieżkę względną do pliku **Web.config** przy użyciu tyldy. Kod wymaga odwołania do `System.Web.Configuration` klasy.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Aby uzyskać więcej informacji na temat zabezpieczania aplikacji ASP.NET, zobacz [Zabezpieczanie ASP.NET witrynach sieci Web](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz też

- [Konstruktorzy parametrów połączeń](connection-string-builders.md)
- [Ochrona informacji o połączeniu](protecting-connection-information.md)
- [Korzystanie z klas konfiguracji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms228063(v=vs.90))
- [Konfigurowanie aplikacji](../../configure-apps/index.md)
- [ASP.NET administrowanie witryną sieci Web](https://docs.microsoft.com/previous-versions/aspnet/6hy1xzbw(v=vs.100))
- [Omówienie ADO.NET](ado-net-overview.md)
