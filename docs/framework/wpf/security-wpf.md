---
title: Zabezpieczenia (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- XAML files [WPF], sandbox behavior
- browser-hosted application security [WPF]
- application security [WPF]
- navigation security [WPF]
- loose XAML files [WPF], sandbox behavior
- WPF security [WPF]
- WebBrowser control [WPF], security
- feature controls [WPF], security
- XBAP security [WPF]
- Internet Explorer security settings [WPF]
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
ms.openlocfilehash: 968913a52a1d86746498aed7c97b63594d346a31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696914"
---
# <a name="security-wpf"></a>Zabezpieczenia (WPF)
<a name="introduction"></a> Podczas tworzenia autonomicznego Windows Presentation Foundation (WPF) i aplikacjami hostowanymi w przeglądarce, należy wziąć pod uwagę modelu zabezpieczeń. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje samodzielne są wykonywane z nieograniczonymi uprawnieniami ( [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **FullTrust** zestaw uprawnień), czy wdrożyć przy użyciu Instalatora Windows (msi), polecenia XCopy, lub [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]. Wdrażanie częściowego zaufania, autonomiczne aplikacje WPF za pomocą technologii ClickOnce jest nieobsługiwany. Jednak utworzyć aplikację hosta pełnego zaufania częściowego zaufania <xref:System.AppDomain> przy użyciu modelu — w programie .NET Framework. Aby uzyskać więcej informacji, zobacz [Przegląd dodatki WPF](./app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje obsługiwane przez przeglądarki są obsługiwane przez [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] lub Firefox, i może być [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] lub luźne [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] dokumenty, aby uzyskać więcej informacji, zobacz [WPF XAML Browser Applications Overview](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje hostowane w przeglądarce wykonaj w izolowanym częściowej relacji zaufania, domyślnie, co jest ograniczona do domyślnego [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **Internet** strefa zestaw uprawnień. W ten sposób skutecznie izoluje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje obsługiwane w przeglądarce z poziomu komputera klienckiego w taki sam sposób, można oczekiwać typowych aplikacjach sieci Web były izolowane. XBAP podnieść poziom uprawnień do pełnego zaufania, w zależności od strefy zabezpieczeń, adres URL wdrożenia i konfiguracji zabezpieczeń klienta. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](wpf-partial-trust-security.md).  
  
 W tym temacie omówiono model zabezpieczeń Windows Presentation Foundation (WPF), jak i aplikacji hostowanych w przeglądarce.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Bezpieczne nawigacji](#SafeTopLevelNavigation)  
  
- [Ustawienia zabezpieczeń oprogramowania przeglądania sieci Web](#InternetExplorerSecuritySettings)  
  
- [WebBrowser — formant i formanty funkcji](#webbrowser_control_and_feature_controls)  
  
- [Wyłączanie zestawów APTCA dla aplikacji klienckich częściowo zaufanych](#APTCA)  
  
- [Zachowanie piaskownicy dla plików XAML luźne](#LooseContentSandboxing)  
  
- [Zasoby używane do tworzenia aplikacji WPF, które promują bezpieczeństwo](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Bezpieczne nawigacji  
 Aby uzyskać [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] wyróżnia dwa rodzaje nawigacji: aplikacji i przeglądarki.  
  
 *Aplikacja nawigacji* jest nawigacja między elementami zawartości w aplikacji, która jest obsługiwana przez przeglądarkę. *Nawigacja przeglądarki* jest nawigacyjne zmiany zawartości i lokalizacji adresu URL samej przeglądarki. Na poniższej ilustracji pokazano relację między nawigację w aplikacji (zwykle XAML) i nawigacja przeglądarki (zazwyczaj HTML):
  
 ![Relacja między nawigacji w aplikacji i nawigacja przeglądarki.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 Typ zawartości, który jest uważany za bezpieczny dla [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] można przejść do przede wszystkim zależy od tego, czy jest używana aplikacja nawigacji lub Nawigacja przeglądarki.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Zabezpieczenia nawigacji w aplikacji  
 Aplikacja nawigacji jest uważany za bezpieczny, jeśli można go zidentyfikować z pakietem [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)], który obsługuje cztery typy zawartości:  
  
|Typ zawartości|Opis|Przykład identyfikatora URI|  
|------------------|-----------------|-----------------|  
|Zasób|Pliki, które są dodawane do projektu o typie kompilacji **zasobów**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Zawartość|Pliki, które są dodawane do projektu o typie kompilacji **zawartości**.|`pack://application:,,,/MyContentFile.xaml`|  
|Witryna pochodzenia|Pliki, które są dodawane do projektu o typie kompilacji **Brak**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Kod aplikacji|Zasoby XAML, które zostały skompilowane kodem.<br /><br /> —lub—<br /><br /> Pliki XAML, które są dodawane do projektu o typie kompilacji **strony**.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat plików danych aplikacji i dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)], zobacz [zasoby aplikacji WPF, zawartość i pliki danych](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Pliki te typy zawartości można nawigować do przez użytkownika lub programowo:  
  
- **Użytkownik nawigacji**. Użytkownik przechodzi przez kliknięcie przycisku <xref:System.Windows.Documents.Hyperlink> elementu.  
  
- **Nawigacja programowa**. Aplikacja przechodzi bez angażowania użytkowników, na przykład, ustawiając <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> właściwości.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Zabezpieczenia nawigacji przeglądarki  
 Nawigacja przeglądarki jest uznawane za bezpieczne tylko w następujących warunkach:  
  
- **Użytkownik nawigacji**. Użytkownik przechodzi przez kliknięcie przycisku <xref:System.Windows.Documents.Hyperlink> element, który znajduje się w głównym <xref:System.Windows.Navigation.NavigationWindow>, nie w zagnieżdżonych <xref:System.Windows.Controls.Frame>.  
  
- **Strefa**. Zawartość do znajduje się w sieci Internet lub lokalny intranet.  
  
- **Protokół**. Protokół używany jest **http**, **https**, **pliku**, lub **mailto**.  
  
 Jeśli [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] próbuje przejdź do zawartości w taki sposób, który nie jest zgodne z tych warunków <xref:System.Security.SecurityException> zgłaszany.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Ustawienia zabezpieczeń oprogramowania przeglądania sieci Web  
 Ustawienia zabezpieczeń na komputerze określają dostępu, który otrzymuje dowolnego oprogramowania do przeglądania w sieci Web. Oprogramowania do przeglądania sieci Web zawiera dowolną aplikację lub składnik, który używa [WinINet](https://go.microsoft.com/fwlink/?LinkId=179379) lub [UrlMon](https://go.microsoft.com/fwlink/?LinkId=179383) interfejsów API, w tym program Internet Explorer i PresentationHost.exe.  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] udostępnia mechanizm, za pomocą którego można skonfigurować funkcje, które może być wykonywane przez lub z [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)], w tym następujące czynności:  
  
- Składniki zależne framework .NET  
  
- Kontrolki ActiveX i wtyczek  
  
- Pliki do pobrania  
  
- Wykonywanie skryptów  
  
- Uwierzytelnianie użytkownika  
  
 Zbiór funkcji, które mogą być chronione w ten sposób jest skonfigurowany na podstawie stref dla **Internet**, **Intranet**, **Zaufane witryny**, i  **Witryn z ograniczeniami** strefy. W poniższych krokach opisano sposób konfigurowania ustawień zabezpieczeń:  
  
1. Otwórz **Panel sterowania**.  
  
2. Kliknij przycisk **sieć i Internet** a następnie kliknij przycisk **Opcje internetowe**.  
  
     Zostanie wyświetlone okno dialogowe Opcje internetowe.  
  
3. Na **zabezpieczeń** , a następnie wybierz strefy, aby skonfigurować ustawienia zabezpieczeń.  
  
4. Kliknij przycisk **Poziom niestandardowy** przycisku.  
  
     **Ustawienia zabezpieczeń** pojawi się okno dialogowe i można skonfigurować ustawienia zabezpieczeń dla wybranej strefy.  
  
     ![Zrzut ekranu pokazujący okno dialogowe Ustawienia zabezpieczeń.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
>  Okno dialogowe Opcje internetowe można uzyskać również z programu Internet Explorer. Kliknij przycisk **narzędzia** a następnie kliknij przycisk **Opcje internetowe**.  
  
 Począwszy od [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], uwzględnione są następujące ustawienia zabezpieczeń specjalnie dla programu .NET Framework:  
  
- **Utrata XAML**. Formanty czy [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] można przejść do i luźno [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plików. (Włączanie, wyłączanie i wyświetlenie monitu opcje).  
  
- **Aplikacje przeglądarek XAML**. Formanty czy [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] można przejdź do, a następnie uruchom [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. (Włączanie, wyłączanie i wyświetlenie monitu opcje).  
  
 Domyślnie te ustawienia są włączone dla **Internet**, **lokalny intranet**, i **Zaufane witryny** stref i wyłączone dla **witryn z ograniczeniami**  strefy.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>Ustawienia rejestru związanych z zabezpieczeniami WPF  
 Oprócz ustawienia zabezpieczeń dostępne za pośrednictwem Opcje internetowe dostępne selektywnego blokowania pewną liczbę funkcji WPF istotnymi dla zabezpieczeń są następujące wartości rejestru. Wartości są zdefiniowane w następującym kluczu:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 W poniższej tabeli wymieniono wartości, które mogą być ustawione.  
  
|Nazwa wartości|Typ wartości|Dane wartości|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|1, aby uniemożliwić; 0 — zezwolenie.|  
|LooseXamlDisallow|REG_DWORD|1, aby uniemożliwić; 0 — zezwolenie.|  
|WebBrowserDisallow|REG_DWORD|1, aby uniemożliwić; 0 — zezwolenie.|  
|MediaAudioDisallow|REG_DWORD|1, aby uniemożliwić; 0 — zezwolenie.|  
|MediaImageDisallow|REG_DWORD|1, aby uniemożliwić; 0 — zezwolenie.|  
|MediaVideoDisallow|REG_DWORD|1, aby uniemożliwić; 0 — zezwolenie.|  
|ScriptInteropDisallow|REG_DWORD|1, aby uniemożliwić; 0 — zezwolenie.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>WebBrowser — formant i formanty funkcji  
 WPF <xref:System.Windows.Controls.WebBrowser> kontroli może służyć do hostowania zawartości sieci Web. WPF <xref:System.Windows.Controls.WebBrowser> kontroli opakowuje źródłowego formantu WebBrowser ActiveX. WPF obsługuje niektóre zabezpieczania aplikacji, korzystając z WPF <xref:System.Windows.Controls.WebBrowser> kontrolki hosta niezaufanych zawartości sieci Web. Jednak niektóre funkcje zabezpieczeń muszą być stosowane bezpośrednio przez aplikacje używające <xref:System.Windows.Controls.WebBrowser> kontroli. Aby uzyskać więcej informacji na temat formantu WebBrowser ActiveX, zobacz [WebBrowser — formant omówienia i samouczki](https://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
>  Ta sekcja ma zastosowanie także do <xref:System.Windows.Controls.Frame> kontrolować, ponieważ używa <xref:System.Windows.Controls.WebBrowser> można przejść do zawartości HTML.  
  
 Jeśli WPF <xref:System.Windows.Controls.WebBrowser> formant jest używany do hostowania niezaufaną zawartość sieci Web, aplikacja powinna używać częściowego zaufania <xref:System.AppDomain> ułatwiające związane z kod skryptu HTML potencjalnie złośliwy kod aplikacji. Jest to szczególnie istotne, jeśli aplikacja prowadzi interakcję z hostowanej skryptu za pomocą <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> metody i <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> właściwości. Aby uzyskać więcej informacji, zobacz [Przegląd dodatki WPF](./app-development/wpf-add-ins-overview.md).  
  
 Jeśli aplikacja używa WPF <xref:System.Windows.Controls.WebBrowser> kontrolki, inny sposób, aby zwiększyć bezpieczeństwo i ograniczenie liczby ataków jest włączenie formanty funkcji programu Internet Explorer. Formanty funkcji to dodatki do programu Internet Explorer, umożliwiające Administratorzy i deweloperzy skonfigurować funkcje programu Internet Explorer i aplikacje obsługujące formantu WebBrowser ActiveX, który WPF <xref:System.Windows.Controls.WebBrowser> kontrolować zawija. Formanty funkcji, można skonfigurować za pomocą [CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394) funkcji lub zmieniając wartości rejestru. Aby uzyskać więcej informacji na temat funkcji kontrolek, zobacz [wprowadzenie do kontrolek funkcji](https://go.microsoft.com/fwlink/?LinkId=179390) i [formanty funkcji Internet](https://go.microsoft.com/fwlink/?LinkId=179392).  
  
 Jeśli tworzysz aplikację WPF autonomicznego, która używa WPF <xref:System.Windows.Controls.WebBrowser> formant, WPF automatycznie włącza następujące elementy sterujące funkcji w aplikacji.  
  
|Funkcja kontroli|  
|---------------------|  
|FEATURE_MIME_HANDLING|  
|FEATURE_MIME_SNIFFING|  
|FEATURE_OBJECT_CACHING|  
|FEATURE_SAFE_BINDTOOBJECT|  
|FEATURE_WINDOW_RESTRICTIONS|  
|FEATURE_ZONE_ELEVATION|  
|FEATURE_RESTRICT_FILEDOWNLOAD|  
|FEATURE_RESTRICT_ACTIVEXINSTALL|  
|FEATURE_ADDON_MANAGEMENT|  
|FEATURE_HTTP_USERNAME_PASSWORD_DISABLE|  
|FEATURE_SECURITYBAND|  
|FEATURE_UNC_SAVEDFILECHECK|  
|FEATURE_VALIDATE_NAVIGATE_URL|  
|FEATURE_DISABLE_TELNET_PROTOCOL|  
|FEATURE_WEBOC_POPUPMANAGEMENT|  
|FEATURE_DISABLE_LEGACY_COMPRESSION|  
|FEATURE_SSLUX|  
  
 Ponieważ te formanty funkcji są włączone bezwarunkowo, aplikacja pełnego zaufania może ujemnie je. W takim przypadku nie ma ryzyka zabezpieczeń dla określonej aplikacji oraz zawartość, którą obsługuje on można wyłączyć odpowiedni formant funkcji.  
  
 Formanty funkcji są stosowane przez proces tworzenia wystąpienia obiektu WebBrowser ActiveX. W związku z tym Jeśli tworzysz autonomiczna aplikacja, która można przejść do niezaufaną zawartość należy naszych użytkowników bardzo poważnie rozważyć włączenie dodatkowych funkcji kontroli.  
  
> [!NOTE]
>  To zalecenie bazuje na ogólne zalecenia dotyczące zabezpieczeń hosta MSHTML i SHDOCVW. Aby uzyskać więcej informacji, zobacz [zabezpieczeń hosta MSHTML — często zadawane pytania: Część II](https://go.microsoft.com/fwlink/?LinkId=179396) i [zabezpieczenia hosta MSHTML — często zadawane pytania: Część II II](https://go.microsoft.com/fwlink/?LinkId=179415).  
  
 Dla Twojego pliku wykonywalnego należy rozważyć włączenie następujących kontrolek funkcji, ustawiając wartość rejestru na wartość 1.  
  
|Funkcja kontroli|  
|---------------------|  
|FEATURE_ACTIVEX_REPURPOSEDETECTION|  
|FEATURE_BLOCK_LMZ_IMG|  
|FEATURE_BLOCK_LMZ_OBJECT|  
|FEATURE_BLOCK_LMZ_SCRIPT|  
|FEATURE_RESTRICT_RES_TO_LMZ|  
|FEATURE_RESTRICT_ABOUT_PROTOCOL_IE7|  
|FEATURE_SHOW_APP_PROTOCOL_WARN_DIALOG|  
|FEATURE_LOCALMACHINE_LOCKDOWN|  
|FEATURE_FORCE_ADDR_AND_STATUS|  
|FEATURE_RESTRICTED_ZONE_WHEN_FILE_NOT_FOUND|  
  
 Plik wykonywalny Rozważ wyłączenie następujących sterowania funkcją, ustawiając wartość rejestru na 0.  
  
|Funkcja kontroli|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Jeśli uruchamiasz częściowego zaufania [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] zawierającej WPF <xref:System.Windows.Controls.WebBrowser> w kontrolce [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)], WPF obsługuje formant WebBrowser ActiveX w przestrzeni adresowej procesu programu Internet Explorer. Ponieważ formantu WebBrowser ActiveX znajduje się w [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] przetwarzanie wszystkich kontrolek funkcji programu Internet Explorer są również włączone dla formantu WebBrowser ActiveX.  
  
 XBAP uruchomiony w programie Internet Explorer również Uzyskaj dodatkowy poziom bezpieczeństwa w porównaniu do aplikacje autonomiczne normalnego. To dodatkowe zabezpieczenie jest fakt, że program Internet Explorer i w związku z tym formantu WebBrowser ActiveX działają chronionym tryb domyślnie [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] i [!INCLUDE[win7](../../../includes/win7-md.md)]. Aby uzyskać więcej informacji na temat trybu chronionego, zobacz [zrozumienie i współpracę w chroniony programu Internet Explorer trybu](https://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
>  Jeśli zostanie podjęta próba uruchomienia XBAP, która obejmuje WPF <xref:System.Windows.Controls.WebBrowser> sterowania w programie Firefox znajduje się w strefie Internet <xref:System.Security.SecurityException> zostanie zgłoszony. Jest to spowodowane zasady zabezpieczeń WPF.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Wyłączanie zestawów APTCA dla aplikacji klienckich częściowo zaufanych  
 Podczas instalowania zestawów zarządzanych do [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)], staną się całkowicie zaufanym, ponieważ użytkownik musi podać jawne uprawnienia do zainstalowania go. Ponieważ są one w pełni zaufany, można użyć tylko w pełni zaufanych klientów zarządzanych aplikacji je. Aby zezwolić na częściowo zaufane aplikacje z nich korzystać, musi być oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Powinien być oznaczony tylko zestawy, które zostały przetestowane jako bezpieczne do wykonywania w częściowej relacji zaufania z tym atrybutem.  
  
 Jednak jest możliwe zestawie APTCA do następującej liczby etapów stwierdzono lukę w zabezpieczeniach po zainstalowaniu na [!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)]. Po odnalezieniu lukę w zabezpieczeniach zestawu wydawcy mogą wygenerować aktualizacji zabezpieczeń, aby rozwiązać ten problem w przypadku istniejących instalacji i aby zapewnić ochronę przed instalacji, które mogą wystąpić po problem został odnaleziony. Jedną z opcji aktualizacji jest do odinstalowywania zestawu, mimo że, może to spowodować przerwanie inne aplikacje klienckie w pełni zaufany, korzystających z zestawu.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] udostępnia mechanizm, za pomocą którego można wyłączyć zestawie APTCA dla częściowo zaufanego [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] bez odinstalowania zestawów APTCA.  
  
 Aby wyłączyć zestawie APTCA, należy utworzyć klucz rejestru specjalne:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Poniżej przedstawiono przykład:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Ten klucz ustanawia wpis dla zestawu APTCA. Musisz także utworzyć wartość tego klucza, która włącza lub wyłącza zestaw. Poniżej przedstawiono szczegółowe informacje o wartości:  
  
- Nazwa wartości: **APTCA_FLAG**.  
  
- Typ wartości: **REG_DWORD**.  
  
- Dane wartości: **1** wyłączyć; **0** włączyć.  
  
 Jeśli zestaw ma wyłączone dla aplikacji klienckich częściowo zaufany, można napisać aktualizację, która tworzy klucz rejestru i wartości.  
  
> [!NOTE]
>  Nie wpływają podstawowych zestawów .NET Framework, wyłączając je w ten sposób, ponieważ są one wymagane do działania aplikacji zarządzanych. Obsługa wyłączanie zestawów APTCA jest przeznaczony głównie dla aplikacji innych firm.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Zachowanie piaskownicy dla plików XAML luźne  
 Luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki są tylko pliki XAML, które nie są zależne od dowolnego związanym z kodem, program obsługi zdarzeń lub zestawu specyficzne dla aplikacji. Gdy luźno [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki są przejście bezpośrednio z przeglądarki, są one załadowane w izolowanym, w oparciu o zestaw uprawnień strefy Internet domyślne.  
  
 Zachowania zabezpieczeń różni się jednak w przypadku luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki są przejście z poziomu <xref:System.Windows.Navigation.NavigationWindow> lub <xref:System.Windows.Controls.Frame> w aplikacji autonomicznej.  
  
 W obu przypadkach luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliku, który jest przejście dziedziczy uprawnienia swojej aplikacji hosta. Jednak to zachowanie może być niepożądane z punktu widzenia zabezpieczeń, szczególnie, jeśli jest to luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plik został utworzony przez jednostkę, która nie jest zaufany lub nieznany. Ten typ zawartości jest znany jako *zawartość zewnętrzną*, a oba <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> można skonfigurować do izolowania ją podczas przejście. Izolacja odbywa się przez ustawienie **SandboxExternalContent** właściwości na wartość true, jak pokazano w poniższych przykładach dotyczących <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 To ustawienie, zewnętrzną zawartość zostanie załadowany do procesu, który jest oddzielony od procesu, który jest hostem aplikacji. Ten proces jest ograniczona do domyślnego internetowego strefy zestawu uprawnień, efektywnie izolując ją od hostowania aplikacji i komputera klienckiego.  
  
> [!NOTE]
>  Mimo że nawigacja do luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plików z poziomu <xref:System.Windows.Navigation.NavigationWindow> lub <xref:System.Windows.Controls.Frame> w samodzielnej aplikacji jest implementowany opartych na przeglądarce WPF hostingu infrastruktury, obejmujące proces PresentationHost poziom zabezpieczeń jest nieco mniej niż gdy zawartość jest ładowany bezpośrednio w programie Internet Explorer na [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] i [!INCLUDE[win7](../../../includes/win7-md.md)] (które nadal będą za pośrednictwem PresentationHost). Jest to spowodowane autonomicznej aplikacji WPF przy użyciu przeglądarki sieci Web nie zapewnia dodatkowych funkcji zabezpieczeń tryb chroniony programu Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Zasoby używane do tworzenia aplikacji WPF, które promują bezpieczeństwo  
 Poniżej przedstawiono dodatkowe zasoby pomagające w tworzeniu [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje, które promują bezpieczeństwo:  
  
|Obszar|Zasób|  
|----------|--------------|  
|Kod zarządzany|[Wzorce i rozwiązania dotyczące zabezpieczeń dla aplikacji](https://go.microsoft.com/fwlink/?LinkId=117426)|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[Zabezpieczenia dostępu kodu](../misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — zabezpieczenia platformy](wpf-security-strategy-platform-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
- [Wzorce i rozwiązania dotyczące zabezpieczeń dla aplikacji](https://go.microsoft.com/fwlink/?LinkId=117426)
- [Zabezpieczenia dostępu kodu](../misc/code-access-security.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przegląd XAML (WPF)](./advanced/xaml-overview-wpf.md)
