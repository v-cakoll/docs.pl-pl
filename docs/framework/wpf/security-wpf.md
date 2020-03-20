---
title: Zabezpieczenia
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
ms.openlocfilehash: e0a56dcbf8d151fcb0d4f6271ecba15c0ff955a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174618"
---
# <a name="security-wpf"></a>Zabezpieczenia (WPF)
<a name="introduction"></a>Podczas tworzenia programu Windows Presentation Foundation (WPF) autonomiczne i przeglądarki hostowane aplikacje, należy wziąć pod uwagę modelu zabezpieczeń. Autonomiczne aplikacje WPF są wykonywane z nieograniczonymi uprawnieniami (zestaw uprawnień CAS**FullTrust),** niezależnie od tego, czy są wdrażane przy użyciu Instalatora Windows (msi), XCopy lub ClickOnce. Wdrażanie częściowego zaufania, autonomiczne aplikacje WPF z ClickOnce jest nieobsługiwał. Jednak aplikacja hosta pełnego zaufania można utworzyć <xref:System.AppDomain> częściowego zaufania przy użyciu modelu dodatku .NET Framework. Aby uzyskać więcej informacji, zobacz [Omówienie dodatków WPF](./app-development/wpf-add-ins-overview.md).  
  
 Aplikacje hostowane w przeglądarce WPF są hostowane przez program Windows Internet Explorer lub Firefox i [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] mogą być aplikacjami przeglądarki XAML (XBAPs) lub luźnymi dokumentami Aby uzyskać więcej informacji, zobacz [Omówienie aplikacji przeglądarki WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 Aplikacje hostowane przez przeglądarkę WPF są wykonywane domyślnie w obszarze izolowanym zabezpieczeń częściowego zaufania, które są ograniczone do domyślnego zestawu uprawnień strefy**internetowej** CAS. To skutecznie izoluje aplikacje hostowane przez przeglądarkę WPF z komputera klienckiego w taki sam sposób, w jaki można oczekiwać, że typowe aplikacje sieci Web zostaną odizolowane. XBAP może podnieść uprawnienia, do pełnego zaufania, w zależności od strefy zabezpieczeń adresu URL wdrożenia i konfiguracji zabezpieczeń klienta. Aby uzyskać więcej informacji, zobacz [WPF Częściowe zabezpieczenia zaufania](wpf-partial-trust-security.md).  
  
 W tym temacie omówiono model zabezpieczeń dla aplikacji autonomicznych programu Windows Presentation Foundation (WPF) i obsługiwanych przez przeglądarkę.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Bezpieczna nawigacja](#SafeTopLevelNavigation)  
  
- [Ustawienia zabezpieczeń oprogramowania do przeglądania stron internetowych](#InternetExplorerSecuritySettings)  
  
- [Sterowanie brwiami i funkcjami webbrowser](#webbrowser_control_and_feature_controls)  
  
- [Wyłączanie zestawów APTCA dla częściowo zaufanych aplikacji klienckich](#APTCA)  
  
- [Zachowanie piaskownicy dla luźnych plików XAML](#LooseContentSandboxing)  
  
- [Zasoby do tworzenia aplikacji WPF promujących bezpieczeństwo](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>
## <a name="safe-navigation"></a>Bezpieczna nawigacja  
 W przypadku XBAPs WPF wyróżnia dwa typy nawigacji: aplikację i przeglądarkę.  
  
 *Nawigacja aplikacji* to nawigacja między elementami zawartości w aplikacji, która jest obsługiwana przez przeglądarkę. *Nawigacja w przeglądarce* to nawigacja, która zmienia adres URL zawartości i lokalizacji samej przeglądarki. Relacja między nawigacją aplikacji (zazwyczaj XAML) a nawigacją w przeglądarce (zazwyczaj HTML) jest wyświetlana na poniższej ilustracji:
  
 ![Relacja między nawigacją aplikacji a nawigacją w przeglądarce.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 Typ zawartości, która jest uważana za bezpieczną dla XBAP, do którego można przejść, zależy przede wszystkim od tego, czy używana jest nawigacja aplikacji, czy nawigacja w przeglądarce.  
  
<a name="Application_Navigation_Security"></a>
### <a name="application-navigation-security"></a>Zabezpieczenia nawigacji aplikacji  
 Nawigacja po aplikacjach jest uważana za bezpieczną, jeśli można ją zidentyfikować za pomocą pakietu URI, który obsługuje cztery typy zawartości:  
  
|Typ zawartości|Opis|Przykład URI|  
|------------------|-----------------|-----------------|  
|Zasób|Pliki dodawane do projektu z typem kompilacji **Zasobu**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Zawartość|Pliki dodawane do projektu z typem kompilacji **Zawartości**.|`pack://application:,,,/MyContentFile.xaml`|  
|Miejsce pochodzenia|Pliki, które są dodawane do projektu o typie kompilacji **Brak**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Kod aplikacji|Zasoby XAML, które mają skompilowany kod.<br /><br /> — lub —<br /><br /> Pliki XAML, które są dodawane do projektu z typem kompilacji **Page**.|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat plików danych aplikacji i URI pakietu, zobacz [WPF Application Resource, Content, and Data Files](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Pliki tych typów zawartości mogą być nawigowane przez użytkownika lub programowo:  
  
- **Nawigacja użytkownika**. Użytkownik nawiguje, klikając <xref:System.Windows.Documents.Hyperlink> element.  
  
- **Nawigacja programowa**. Aplikacja nawiguje bez angażowania użytkownika, na <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> przykład przez ustawienie właściwości.  
  
<a name="Browser_Navigation_Security"></a>
### <a name="browser-navigation-security"></a>Zabezpieczenia nawigacji w przeglądarce  
 Nawigacja w przeglądarce jest uważana za bezpieczną tylko w następujących warunkach:  
  
- **Nawigacja użytkownika**. Użytkownik nawiguje, klikając <xref:System.Windows.Documents.Hyperlink> element, który <xref:System.Windows.Navigation.NavigationWindow>znajduje się w <xref:System.Windows.Controls.Frame>głównym , a nie w zagnieżdżone .  
  
- **Strefa**. Zawartość, do nadajona jest w Internecie lub w lokalnym intranecie.  
  
- **protokołu**. Używany protokół to **http**, **https**, **file**lub **mailto**.  
  
 Jeśli XBAP próbuje przejść do zawartości w sposób, który nie <xref:System.Security.SecurityException> jest zgodny z tymi warunkami, a jest generowany.  
  
<a name="InternetExplorerSecuritySettings"></a>
## <a name="web-browsing-software-security-settings"></a>Ustawienia zabezpieczeń oprogramowania do przeglądania stron internetowych  
 Ustawienia zabezpieczeń na komputerze określają dostęp do dowolnego oprogramowania do przeglądania sieci Web. Oprogramowanie do przeglądania sieci Web zawiera dowolną aplikację lub składnik korzystający z interfejsów API [WinINet](/windows/win32/wininet/portal) lub [UrlMon,](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) w tym program Internet Explorer i PresentationHost.exe.  
  
 Program Internet Explorer udostępnia mechanizm, za pomocą którego można skonfigurować funkcje, które mogą być wykonywane przez lub z programu Internet Explorer, w tym następujące:  
  
- Składniki zależne od platformy .NET Framework  
  
- Formanty i wtyczki ActiveX  
  
- Pliki do pobrania  
  
- Wykonywanie skryptów  
  
- Uwierzytelnianie użytkowników  
  
 Kolekcja funkcji, które mogą być zabezpieczone w ten sposób jest konfigurowany na podstawie strefy dla **strefy Internet,** **Intranet**, **Zaufane witryny**i **strefy Witryny z ograniczeniami.** W poniższych krokach opisano sposób konfigurowania ustawień zabezpieczeń:  
  
1. Otwórz **Panel sterowania**.  
  
2. Kliknij **pozycję Sieć i Internet,** a następnie kliknij pozycję Opcje **internetowe**.  
  
     Zostanie wyświetlone okno dialogowe Opcje internetowe.  
  
3. On the **Security** tab, select the zone to configure the security settings for.  
  
4. Kliknij przycisk **Poziom niestandardowy.**  
  
     Zostanie wyświetlone okno dialogowe **Ustawienia zabezpieczeń** i można skonfigurować ustawienia zabezpieczeń dla wybranej strefy.  
  
     ![Zrzut ekranu przedstawiający okno dialogowe Ustawienia zabezpieczeń.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> Można również przejść do okna dialogowego Opcje internetowe z programu Internet Explorer. Kliknij pozycję **Narzędzia,** a następnie kliknij pozycję **Opcje internetowe**.  
  
 Począwszy od programu Windows Internet Explorer 7, uwzględniono następujące ustawienia zabezpieczeń przeznaczone dla programu .NET Framework:  
  
- **Luźny XAML**. Określa, czy program Internet [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] Explorer może nawigować do plików i je poluzować. (Opcje Włącz, Wyłącz i Monituj).  
  
- **aplikacje przeglądarki XAML**. Określa, czy program Internet Explorer może nawigować do i uruchamiać xbaps. (Opcje Włącz, Wyłącz i Monituj).  
  
 Domyślnie wszystkie te ustawienia są włączone dla stref **Internet,** **Lokalny intranet**i **Zaufane witryny** i wyłączone dla strefy **Witryny z ograniczeniami.**  
  
<a name="Security_Settings_for_IE6_and_Below"></a>
### <a name="security-related-wpf-registry-settings"></a>Ustawienia rejestru WPF związane z zabezpieczeniami  
 Oprócz ustawień zabezpieczeń dostępnych za pośrednictwem opcji internetowych dostępne są następujące wartości rejestru do selektywnego blokowania wielu funkcji WPF wrażliwych na zabezpieczenia. Wartości są definiowane w następującym kluczu:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 W poniższej tabeli wymieniono wartości, które można ustawić.  
  
|Nazwa wartości|Typ wartości|Dane wartości|  
|----------------|----------------|----------------|  
|XBAPDyallow|REG_DWORD|1, aby nie dozwolnąć; 0, aby umożliwić.|  
|LooseXamlDisallow (LuźnyXamlDisallow)|REG_DWORD|1, aby nie dozwolnąć; 0, aby umożliwić.|  
|Brwi internetoweWydajnik|REG_DWORD|1, aby nie dozwolnąć; 0, aby umożliwić.|  
|MediaAudioDisallow (MediaAudioDisallow)|REG_DWORD|1, aby nie dozwolnąć; 0, aby umożliwić.|  
|MediaImageDisallow (Niemka)|REG_DWORD|1, aby nie dozwolnąć; 0, aby umożliwić.|  
|MediaVideoDisallow (Wideo)|REG_DWORD|1, aby nie dozwolnąć; 0, aby umożliwić.|  
|SkryptInteropDisallow|REG_DWORD|1, aby nie dozwolnąć; 0, aby umożliwić.|  
  
<a name="webbrowser_control_and_feature_controls"></a>
## <a name="webbrowser-control-and-feature-controls"></a>Sterowanie brwiami i funkcjami webbrowser  
 Formant <xref:System.Windows.Controls.WebBrowser> WPF może służyć do hosta zawartości sieci Web. Formant <xref:System.Windows.Controls.WebBrowser> WPF otacza podstawowej webbrowser ActiveX kontroli. WPF WPF zapewnia pewną obsługę zabezpieczania <xref:System.Windows.Controls.WebBrowser> aplikacji, gdy używasz formantu WPF do hostowania niezaufanej zawartości sieci Web. Jednak niektóre funkcje zabezpieczeń muszą być stosowane bezpośrednio <xref:System.Windows.Controls.WebBrowser> przez aplikacje za pomocą formantu. Aby uzyskać więcej informacji na temat formantu ActiveX programu WebBrowser, zobacz [Przeglądy i samouczki dotyczące sterowania przeglądarką WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85)).  
  
> [!NOTE]
> Ta sekcja dotyczy również <xref:System.Windows.Controls.Frame> formantu, <xref:System.Windows.Controls.WebBrowser> ponieważ używa do przechodzenia do zawartości HTML.  
  
 Jeśli kontrolka WPF <xref:System.Windows.Controls.WebBrowser> jest używana do hosta niezaufanej <xref:System.AppDomain> zawartości sieci Web, aplikacja powinna używać częściowego zaufania, aby pomóc w izolacji kodu aplikacji od potencjalnie złośliwego kodu skryptu HTML. Jest to szczególnie ważne, jeśli aplikacja wchodzi w interakcję <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> z <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> hostowanego skryptu przy użyciu metody i właściwości. Aby uzyskać więcej informacji, zobacz [Omówienie dodatków WPF](./app-development/wpf-add-ins-overview.md).  
  
 Jeśli aplikacja używa formantu WPF, <xref:System.Windows.Controls.WebBrowser> innym sposobem zwiększenia zabezpieczeń i łagodzenia ataków jest włączenie formantów funkcji programu Internet Explorer. Formantów funkcji są dodatki do programu Internet Explorer, które umożliwiają administratorom i deweloperom skonfigurować funkcje programu <xref:System.Windows.Controls.WebBrowser> Internet Explorer i aplikacji, które hostują WebBrowser ActiveX kontroli, które więdną formantu WPF. Formantów funkcji można skonfigurować za pomocą [funkcji CoInternetSetFeatureEnabled](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85)) lub zmieniając wartości w rejestrze. Aby uzyskać więcej informacji na temat formantów funkcji, zobacz [Wprowadzenie do kontrolek funkcji](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) i [kontrolek funkcji internetowych](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85)).  
  
 Jeśli tworzysz autonomiczną aplikację WPF, która używa <xref:System.Windows.Controls.WebBrowser> formantu WPF, WPF automatycznie włącza następujące formanty funkcji dla aplikacji.  
  
|Sterowanie funkcjami|  
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
  
 Ponieważ te formanty funkcji są włączone bezwarunkowo, aplikacja pełnego zaufania może być osłabiona przez nich. W takim przypadku, jeśli nie ma zagrożenia bezpieczeństwa dla określonej aplikacji i zawartości, która jest hostująca, można wyłączyć odpowiedni formant funkcji.  
  
 Formanty funkcji są stosowane przez proces tworzenia wystąpienia obiektu ActiveX programu WebBrowser. W związku z tym jeśli tworzysz autonomiczną aplikację, która może przejść do niezaufanej zawartości, należy poważnie rozważyć włączenie dodatkowych formantów funkcji.  
  
> [!NOTE]
> To zalecenie opiera się na ogólnych zaleceniach dotyczących zabezpieczeń hostów MSHTML i SHDOCVW. Aby uzyskać więcej informacji, zobacz [Często zadawane pytania dotyczące zabezpieczeń hosta MSHTML: Część I II](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/) i Często zadawane pytania dotyczące zabezpieczeń [hosta MSHTML: Część II II](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/).  
  
 W przypadku pliku wykonywalnego należy rozważyć włączenie następujących formantów funkcji, ustawiając wartość rejestru na 1.  
  
|Sterowanie funkcjami|  
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
  
 W przypadku pliku wykonywalnego należy rozważyć wyłączenie następującej kontroli funkcji, ustawiając wartość rejestru na 0.  
  
|Sterowanie funkcjami|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Po uruchomieniu częściowej zaufaju aplikacji przeglądarki XAML (XBAP), która zawiera kontrolkę WPF <xref:System.Windows.Controls.WebBrowser> w programie Windows Internet Explorer, WPF WPF hostuje kontrolkę ActiveX programu WebBrowser w przestrzeni adresowej procesu programu Internet Explorer. Ponieważ kontrolka ActiveX programu WebBrowser jest hostowana w procesie programu Internet Explorer, wszystkie formanty funkcji programu Internet Explorer są również włączone dla formantu ActiveX programu WebBrowser.  
  
 XBAPs działające w programie Internet Explorer również uzyskać dodatkowy poziom zabezpieczeń w porównaniu do zwykłych aplikacji autonomicznych. To dodatkowe zabezpieczenia są spowodowane tym, że program Internet Explorer, a zatem kontrolka ActiveX programu WebBrowser, jest domyślnie uruchamiany w trybie chronionym w systemach Windows Vista i Windows 7. Aby uzyskać więcej informacji na temat trybu chronionego, zobacz [Opis i praca w trybie chronionym programu Internet Explorer](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/).  
  
> [!NOTE]
> Jeśli spróbujesz uruchomić XBAP, który <xref:System.Windows.Controls.WebBrowser> zawiera kontrolkę WPF w <xref:System.Security.SecurityException> Firefoksie, podczas gdy w strefie internetowej zostanie rzucony. Jest to spowodowane zasadami zabezpieczeń WPF.  
  
<a name="APTCA"></a>
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Wyłączanie zestawów APTCA dla częściowo zaufanych aplikacji klienckich  
 Gdy zestawy zarządzane są instalowane w globalnej pamięci podręcznej zestawów (GAC), stają się one w pełni zaufane, ponieważ użytkownik musi zapewnić jawne uprawnienia do ich zainstalowania. Ponieważ są one w pełni zaufane, tylko w pełni zaufane zarządzane aplikacje klienckie mogą z nich korzystać. Aby umożliwić częściowo zaufanym aplikacjom korzystanie z <xref:System.Security.AllowPartiallyTrustedCallersAttribute> nich, muszą być oznaczone (APTCA). Tylko zestawy, które zostały przetestowane jako bezpieczne do wykonania w częściowym zaufaniu powinny być oznaczone tym atrybutem.  
  
 Możliwe jest jednak, że zespół APTCA wykazuje lukę w zabezpieczeniach po zainstalowaniu w gac. Po wykryciu luki w zabezpieczeniach wydawcy zestawów mogą utworzyć aktualizację zabezpieczeń, aby rozwiązać problem w istniejących instalacjach i chronić przed instalacjami, które mogą wystąpić po wykryciu problemu. Jedną z opcji aktualizacji jest odinstalowanie zestawu, chociaż może to złamać inne w pełni zaufane aplikacje klienckie, które używają zestawu.  
  
 WPF WPF zapewnia mechanizm, za pomocą którego można wyłączyć zestaw APTCA dla częściowo zaufanych XBAPs bez odinstalowywania zestawu APTCA.  
  
 Aby wyłączyć zestaw APTCA, należy utworzyć specjalny klucz rejestru:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Poniżej przedstawiono przykład:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Ten klucz ustanawia wpis dla zestawu APTCA. Należy również utworzyć wartość w tym kluczu, który włącza lub wyłącza zestawu. Poniżej znajdują się szczegóły wartości:  
  
- Nazwa wartości: **APTCA_FLAG**.  
  
- Typ wartości: **REG_DWORD**.  
  
- Dane wartości: **1,** aby wyłączyć; **0,** aby włączyć.  
  
 Jeśli zestaw musi być wyłączony dla częściowo zaufanych aplikacji klienckich, można napisać aktualizację, która tworzy klucz rejestru i wartość.  
  
> [!NOTE]
> Core .NET Framework zestawy nie są zagrożone przez wyłączenie ich w ten sposób, ponieważ są one wymagane dla zarządzanych aplikacji do uruchomienia. Obsługa wyłączania zestawów APTCA jest przeznaczona przede wszystkim dla aplikacji innych firm.  
  
<a name="LooseContentSandboxing"></a>
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Zachowanie piaskownicy dla luźnych plików XAML  
 Luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki są tylko do oznaczania plików XAML, które nie zależą od kodu, obsługi zdarzeń lub zestawu specyficzne dla aplikacji. Gdy [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] luźne pliki są nawigowane bezpośrednio z przeglądarki, są ładowane do piaskownicy zabezpieczeń na podstawie domyślnego zestawu uprawnień strefy internetowej.  
  
 Jednak zachowanie zabezpieczeń jest inny, gdy luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki <xref:System.Windows.Navigation.NavigationWindow> są <xref:System.Windows.Controls.Frame> nawigowane z aplikacji autonomicznej lub w autonomicznej.  
  
 W obu przypadkach [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] luźny plik, który jest nawigowany, aby dziedziczyć uprawnienia jego aplikacji hosta. Jednak to zachowanie może być niepożądane z punktu widzenia [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zabezpieczeń, szczególnie jeśli luźny plik został wyprodukowany przez jednostkę, która nie jest zaufana lub nieznana. Ten typ zawartości jest znany jako <xref:System.Windows.Controls.Frame> zawartość <xref:System.Windows.Navigation.NavigationWindow> *zewnętrzna*i obie i można ją skonfigurować tak, aby ją wyizolowała podczas przechodzenia do. Izolacja jest osiągana przez ustawienie **sandboxExternalContent** właściwość true, <xref:System.Windows.Controls.Frame> jak <xref:System.Windows.Navigation.NavigationWindow>pokazano w poniższych przykładach dla i:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Przy tym ustawieniu zawartość zewnętrzna zostanie załadowana do procesu, który jest oddzielony od procesu, który hostuje aplikację. Ten proces jest ograniczony do domyślnego zestawu uprawnień strefy internetowej, skutecznie izolując go od aplikacji hostingowej i komputera klienckiego.  
  
> [!NOTE]
> Mimo że nawigacja do poluzowania [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plików z <xref:System.Windows.Navigation.NavigationWindow> lub <xref:System.Windows.Controls.Frame> w autonomicznej aplikacji jest zaimplementowana w oparciu o infrastrukturę hostingową przeglądarki WPF, obejmującą proces PresentationHost, poziom zabezpieczeń jest nieco mniejszy niż wtedy, gdy zawartość jest ładowana bezpośrednio w programie Internet Explorer w systemie Windows Vista i Windows 7 (który nadal będzie za pośrednictwem PresentationHost). Dzieje się tak, ponieważ autonomiczna aplikacja WPF korzystająca z przeglądarki sieci Web nie zapewnia dodatkowej funkcji zabezpieczeń trybu chronionego programu Internet Explorer.  
  
<a name="BestPractices"></a>
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Zasoby do tworzenia aplikacji WPF promujących bezpieczeństwo  
 Poniżej przedstawiono kilka dodatkowych zasobów ułatwiające tworzenie aplikacji WPF, które promują zabezpieczenia:  
  
|Obszar|Zasób|  
|----------|--------------|  
|Kod zarządzany|[Wzorce i praktyki wskazówki dotyczące zabezpieczeń dla aplikacji](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))|  
|CAS|[Zabezpieczenia dostępu kodu](../misc/code-access-security.md)|  
|ClickOnce|[Kliknijonce zabezpieczenia i wdrażanie](/visualstudio/deployment/clickonce-security-and-deployment)|  
|WPF|[Częściowe zabezpieczenia zaufania WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Zobacz też

- [Częściowe zabezpieczenia zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — zabezpieczenia platformy](wpf-security-strategy-platform-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
- [Wzorce i praktyki wskazówki dotyczące zabezpieczeń dla aplikacji](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))
- [Zabezpieczenia dostępu kodu](../misc/code-access-security.md)
- [Kliknijonce zabezpieczenia i wdrażanie](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
