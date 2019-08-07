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
ms.openlocfilehash: 6bd597cd2719fb96b8633f724da46a76e416b454
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817893"
---
# <a name="security-wpf"></a>Zabezpieczenia (WPF)
<a name="introduction"></a>Podczas opracowywania aplikacji autonomicznych i hostowanych przez program Windows Presentation Foundation (WPF) należy wziąć pod uwagę model zabezpieczeń. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]Aplikacje autonomiczne są wykonywane z nieograniczonymi uprawnieniami (zestaw uprawnień CAS**FullTrust** ), niezależnie od tego, czy wdrożono przy użyciu Instalator Windows (. msi), XCOPY lub ClickOnce. Wdrożenie częściowego zaufania, autonomiczne aplikacje WPF za pomocą technologii ClickOnce nie jest obsługiwane. Jednak w pełni zaufane aplikacje hosta mogą utworzyć częściowe zaufanie <xref:System.AppDomain> przy użyciu modelu dodatku .NET Framework. Aby uzyskać więcej informacji, zobacz [Omówienie dodatków WPF](./app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]aplikacje hostowane w przeglądarce są hostowane przez program Windows Internet Explorer lub Firefox i mogą [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] być albo [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] swobodne dokumenty, aby uzyskać więcej informacji, zobacz [Omówienie aplikacji w przeglądarce WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]aplikacje hostowane w przeglądarce działają w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania, domyślnie, co jest ograniczone do domyślnego zestawu uprawnień strefy**internetowej** CAS. Pozwala to efektywnie izolować [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje hostowane w przeglądarce od komputera klienckiego w taki sam sposób, w jaki można oczekiwać, że typowe aplikacje sieci Web mają być izolowane. Aplikacje XBAP mogą podwyższyć poziom uprawnień, do pełnego zaufania, w zależności od strefy zabezpieczeń w adresie URL wdrożenia i konfiguracji zabezpieczeń klienta. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](wpf-partial-trust-security.md).  
  
 W tym temacie omówiono model zabezpieczeń dla aplikacji autonomicznych i hostowanych przez przeglądarkę dla Windows Presentation Foundation (WPF).  
  
 Ten temat zawiera następujące sekcje:  
  
- [Bezpieczna nawigacja](#SafeTopLevelNavigation)  
  
- [Ustawienia zabezpieczeń oprogramowania do przeglądania sieci Web](#InternetExplorerSecuritySettings)  
  
- [Kontrolki WebBrowser i kontrolki funkcji](#webbrowser_control_and_feature_controls)  
  
- [Wyłączanie zestawów APTCA dla częściowo zaufanych aplikacji klienckich](#APTCA)  
  
- [Zachowanie piaskownicy dla luźnych plików XAML](#LooseContentSandboxing)  
  
- [Zasoby służące do opracowywania aplikacji WPF promujących zabezpieczenia](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Bezpieczna nawigacja  
 W przypadku [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]programu rozróżniadwatypynawigacji:aplikacjaiprzeglądarka.[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]  
  
 *Nawigowanie po aplikacji* to nawigacja między elementami zawartości w aplikacji hostowanej w przeglądarce. *Nawigacja w przeglądarce* to Nawigacja, która zmienia zawartość i adres URL w przeglądarce. Relacja między nawigacją aplikacji (zazwyczaj XAML) i nawigacją przeglądarki (zwykle HTML) pokazano na poniższej ilustracji:
  
 ![Relacja między nawigacją aplikacji a nawigacją przeglądarki.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 Typ zawartości uznawany za bezpieczny dla elementu [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] , do którego można przejść, jest określany głównie przez określenie, czy używana jest nawigacja aplikacji czy Nawigacja w przeglądarce.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Zabezpieczenia nawigacji aplikacji  
 Nawigowanie po aplikacji jest uznawane za bezpieczne, jeśli można je [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)]zidentyfikować za pomocą pakietu, który obsługuje cztery typy zawartości:  
  
|Typ zawartości|Opis|Przykład identyfikatora URI|  
|------------------|-----------------|-----------------|  
|Zasób|Pliki, które są dodawane do projektu z typem kompilacji **zasobu**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Zawartość|Pliki, które są dodawane do projektu z typem kompilacji **zawartości**.|`pack://application:,,,/MyContentFile.xaml`|  
|Lokacja pochodzenia|Pliki, które są dodawane do projektu z typem kompilacji **Brak**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Kod aplikacji|Zasoby XAML, które mają skompilowany kod w tle.<br /><br /> —lub—<br /><br /> Pliki XAML, które są dodawane do projektu z typem kompilacji **strony**.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat plików danych aplikacji [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)]i pakietu, zobacz artykuł w [aplikacji WPF, zawartość i pliki danych](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Pliki tych typów zawartości mogą być przechodzenie przez użytkownika lub programowo:  
  
- **Nawigacja użytkownika**. Użytkownik przechodzi przez kliknięcie <xref:System.Windows.Documents.Hyperlink> elementu.  
  
- **Nawigacja programowa**. Aplikacja nawiguje bez udziału użytkownika, na przykład przez ustawienie <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> właściwości.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Zabezpieczenia nawigacji przeglądarki  
 Nawigacja w przeglądarce jest uważana za bezpieczną tylko w następujących warunkach:  
  
- **Nawigacja użytkownika**. Użytkownik przechodzi przez kliknięcie <xref:System.Windows.Documents.Hyperlink> elementu znajdującego się w obszarze głównym <xref:System.Windows.Navigation.NavigationWindow>, a nie w języku zagnieżdżonym <xref:System.Windows.Controls.Frame>.  
  
- **Strefa**. Zawartość, do której nastąpi przejście, znajduje się w Internecie lub w lokalnym intranecie.  
  
- **Protokół**. Używanym protokołem jest **http**, **https**, **File**lub **mailto**.  
  
 Jeśli <xref:System.Security.SecurityException> zostanie [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] podjęta próba przejścia do zawartości w sposób niezgodny z tymi warunkami, zgłaszany jest wyjątek.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Ustawienia zabezpieczeń oprogramowania do przeglądania sieci Web  
 Ustawienia zabezpieczeń na komputerze określają dostęp do dowolnego oprogramowania do przeglądania sieci Web. Oprogramowanie do przeglądania sieci Web obejmuje dowolną aplikację lub składnik korzystający z interfejsów API [WinInet](https://go.microsoft.com/fwlink/?LinkId=179379) lub [Urlmon](https://go.microsoft.com/fwlink/?LinkId=179383) , w tym programów Internet Explorer i PresentationHost. exe.  
  
 Program Internet Explorer oferuje mechanizm, za pomocą którego można skonfigurować funkcje, które mogą być wykonywane przez program lub z programu Internet Explorer, w tym następujące:  
  
- Składniki zależne .NET Framework  
  
- Kontrolki ActiveX i wtyczki  
  
- Pliki do pobrania  
  
- Wykonywanie skryptów  
  
- Uwierzytelnianie użytkownika  
  
 Zbiór funkcji, które mogą być zabezpieczane w ten sposób, jest skonfigurowany dla każdej strefy dla strefy **Internet**, **intranet**, **Zaufane witryny**i **witryny** z ograniczeniami. Poniższe kroki opisują sposób konfigurowania ustawień zabezpieczeń:  
  
1. Otwórz **Panel sterowania**.  
  
2. Kliknij pozycję **Sieć i Internet** , a następnie kliknij pozycję **Opcje internetowe**.  
  
     Zostanie wyświetlone okno dialogowe Opcje internetowe.  
  
3. Na karcie **zabezpieczenia** wybierz strefę, dla której mają zostać skonfigurowane ustawienia zabezpieczeń.  
  
4. Kliknij przycisk **Poziom niestandardowy** .  
  
     Zostanie wyświetlone okno dialogowe **Ustawienia zabezpieczeń** , w którym można skonfigurować ustawienia zabezpieczeń dla wybranej strefy.  
  
     ![Zrzut ekranu przedstawiający okno dialogowe Ustawienia zabezpieczeń.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
>  Możesz również przejść do okna dialogowego Opcje internetowe w programie Internet Explorer. Kliknij pozycję **Narzędzia** , a następnie kliknij pozycję **Opcje internetowe**.  
  
 Począwszy od programu Windows Internet Explorer 7, dostępne są następujące ustawienia zabezpieczeń przeznaczone dla .NET Framework:  
  
- **Luźny kod XAML**. Określa, czy program Internet Explorer może nawigować do [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] i luźne pliki. (Włącz, wyłącz i Monituj opcje).  
  
- **Aplikacje przeglądarki XAML**. Określa, czy program Internet Explorer może przechodzić [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]do i uruchamiać. (Włącz, wyłącz i Monituj opcje).  
  
 Domyślnie te ustawienia są włączone dla strefy **Internet**, **Lokalny intranet**i **Zaufane witryny** oraz wyłączone dla strefy **witryn** z ograniczeniami.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>Ustawienia rejestru WPF powiązane z zabezpieczeniami  
 Oprócz ustawień zabezpieczeń dostępnych za pomocą opcji internetowych, w przypadku selektywnego blokowania wielu funkcji WPF z uwzględnieniem zabezpieczeń, dostępne są następujące wartości rejestru. Wartości są zdefiniowane w następującym kluczu:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 Poniższa tabela zawiera listę wartości, które można ustawić.  
  
|Nazwa wartości|Typ wartości|Dane wartości|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|1, aby nie zezwalać; 0, aby zezwolić.|  
|LooseXamlDisallow|REG_DWORD|1, aby nie zezwalać; 0, aby zezwolić.|  
|WebBrowserDisallow|REG_DWORD|1, aby nie zezwalać; 0, aby zezwolić.|  
|MediaAudioDisallow|REG_DWORD|1, aby nie zezwalać; 0, aby zezwolić.|  
|MediaImageDisallow|REG_DWORD|1, aby nie zezwalać; 0, aby zezwolić.|  
|MediaVideoDisallow|REG_DWORD|1, aby nie zezwalać; 0, aby zezwolić.|  
|ScriptInteropDisallow|REG_DWORD|1, aby nie zezwalać; 0, aby zezwolić.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>Kontrolki WebBrowser i kontrolki funkcji  
 Kontrolka <xref:System.Windows.Controls.WebBrowser> WPF może służyć do hostowania zawartości sieci Web. Kontrolka <xref:System.Windows.Controls.WebBrowser> WPF otacza podstawową kontrolkę ActiveX WebBrowser. WPF zapewnia obsługę zabezpieczania aplikacji podczas używania kontrolki WPF <xref:System.Windows.Controls.WebBrowser> do hostowania niezaufanej zawartości sieci Web. Jednak niektóre funkcje zabezpieczeń muszą być stosowane bezpośrednio przez aplikacje korzystające z tej <xref:System.Windows.Controls.WebBrowser> kontrolki. Aby uzyskać więcej informacji na temat kontrolki ActiveX WebBrowser, zobacz [przeglądanie i samouczki kontrolki WebBrowser](https://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
>  Ta sekcja ma zastosowanie również do <xref:System.Windows.Controls.Frame> kontrolki, ponieważ <xref:System.Windows.Controls.WebBrowser> używa ona do nawigowania do zawartości HTML.  
  
 Jeśli formant WPF <xref:System.Windows.Controls.WebBrowser> jest używany do hostowania niezaufanej zawartości sieci Web, aplikacja powinna używać częściowej relacji zaufania <xref:System.AppDomain> , aby pomóc w izolowaniu kodu aplikacji od potencjalnie złośliwego kodu skryptu HTML. Jest to szczególnie prawdziwe, jeśli aplikacja działa z hostowanym skryptem przy użyciu <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> metody <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> i właściwości. Aby uzyskać więcej informacji, zobacz [Omówienie dodatków WPF](./app-development/wpf-add-ins-overview.md).  
  
 Jeśli aplikacja używa formantu WPF <xref:System.Windows.Controls.WebBrowser> , inny sposób zwiększania bezpieczeństwa i zmniejszania ataków polega na włączeniu kontroli funkcji programu Internet Explorer. Formanty funkcji to dodatki do programu Internet Explorer, które umożliwiają administratorom i deweloperom Konfigurowanie funkcji programu Internet Explorer i aplikacji obsługujących formant ActiveX WebBrowser, które <xref:System.Windows.Controls.WebBrowser> są zawijane przez formant WPF. Formanty funkcji można skonfigurować za pomocą funkcji [CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394) lub zmieniając wartości w rejestrze. Aby uzyskać więcej informacji na temat kontrolek funkcji, zobacz [wprowadzenie do kontrolek funkcji](https://go.microsoft.com/fwlink/?LinkId=179390) i [kontrolek funkcji internetowych](https://go.microsoft.com/fwlink/?LinkId=179392).  
  
 Jeśli tworzysz autonomiczną aplikację WPF, która używa kontrolki WPF <xref:System.Windows.Controls.WebBrowser> , WPF automatycznie włącza następujące kontrolki funkcji dla aplikacji.  
  
|Kontrola funkcji|  
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
  
 Ponieważ te kontrolki funkcji są włączone bezwarunkowo, może to oznaczać, że w pełni zaufane aplikacje. W takim przypadku, jeśli nie ma ryzyka związanego z zabezpieczeniami dla konkretnej aplikacji i zawartości, która jest obsługiwana, można wyłączyć odpowiedni formant funkcji.  
  
 Kontrolki funkcji są stosowane przez proces tworzenia wystąpienia obiektu ActiveX WebBrowser. W związku z tym, jeśli tworzysz aplikację autonomiczną, która może nawigować do niezaufanej zawartości, należy rozważyć włączenie dodatkowych kontroli funkcji.  
  
> [!NOTE]
>  To zalecenie jest oparte na ogólnych zaleceniach dotyczących zabezpieczeń hosta MSHTML i SHDOCVW. Aby uzyskać więcej informacji, [Zobacz sekcję Często zadawane pytania dotyczące zabezpieczeń hosta MSHTML: Część I II](https://go.microsoft.com/fwlink/?LinkId=179396) i [zabezpieczenia hosta MSHTML — często zadawane pytania: Część II II](https://go.microsoft.com/fwlink/?LinkId=179415).  
  
 W przypadku pliku wykonywalnego Rozważ włączenie następujących kontrolek funkcji przez ustawienie wartości rejestru na 1.  
  
|Kontrola funkcji|  
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
  
 W przypadku pliku wykonywalnego rozważ wyłączenie następującej kontrolki funkcji przez ustawienie wartości rejestru na 0.  
  
|Kontrola funkcji|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 W przypadku uruchomienia częściowego zaufania [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] zawierającego formant WPF <xref:System.Windows.Controls.WebBrowser> w programie Windows Internet Explorer, WPF hostuje formant ActiveX WebBrowser w przestrzeni adresowej procesu programu Internet Explorer. Ponieważ Kontrolka ActiveX WebBrowser jest hostowana w procesie programu Internet Explorer, wszystkie formanty funkcji dla programu Internet Explorer również są włączone dla kontrolki ActiveX WebBrowser.  
  
 Aplikacje XBAP działające w programie Internet Explorer również uzyskują dodatkowy poziom zabezpieczeń w porównaniu z normalnymi aplikacjami autonomicznymi. To dodatkowe zabezpieczenia wynika z faktu, że program Internet Explorer i w związku z tym Kontrolka ActiveX WebBrowser domyślnie [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] działa [!INCLUDE[win7](../../../includes/win7-md.md)]w trybie chronionym w systemach i. Aby uzyskać więcej informacji na temat trybu chronionego, zobacz [Opis i praca w trybie chronionym programu Internet Explorer](https://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
>  Jeśli spróbujesz uruchomić aplikację XBAP, która zawiera formant WPF <xref:System.Windows.Controls.WebBrowser> w przeglądarce Firefox, <xref:System.Security.SecurityException> zostanie zgłoszony w strefie Internet. Jest to spowodowane zasadami zabezpieczeń WPF.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Wyłączanie zestawów APTCA dla częściowo zaufanych aplikacji klienckich  
 Gdy zarządzane zestawy są zainstalowane w globalnej pamięci podręcznej zestawów (GAC), stają się w pełni zaufane, ponieważ użytkownik musi podać jawne uprawnienia, aby je zainstalować. Ponieważ są one w pełni zaufane, mogą z nich korzystać tylko w pełni zaufane zarządzane aplikacje klienckie. Aby umożliwić ich używanie częściowo zaufanych aplikacji, muszą one być oznaczone przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Tylko zestawy, które zostały przetestowane pod kątem bezpiecznego wykonywania w częściowej relacji zaufania, powinny być oznaczone tym atrybutem.  
  
 Jednak w przypadku zestawu APTCA może zostać wystawiona Luka w zabezpieczeniach po zainstalowaniu w pamięci podręcznej GAC. Po znalezieniu usterki zabezpieczeń wydawcy zestawu mogą utworzyć aktualizację zabezpieczeń, aby rozwiązać problem z istniejącymi instalacjami oraz chronić przed instalacjami, które mogą wystąpić po wykryciu problemu. Jedną z opcji aktualizacji jest odinstalowanie zestawu, chociaż może to spowodować uszkodzenie innych w pełni zaufanych aplikacji klienckich korzystających z zestawu.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]zapewnia mechanizm, za pomocą którego można wyłączyć zestaw APTCA dla częściowo zaufanych [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] bez odinstalowywania zestawu APTCA.  
  
 Aby wyłączyć zestaw APTCA, należy utworzyć specjalny klucz rejestru:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Poniżej przedstawiono przykład:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Ten klucz ustanawia wpis dla zestawu APTCA. Należy również utworzyć wartość w tym kluczu, która włącza lub wyłącza zestaw. Poniżej znajdują się szczegółowe informacje o wartości:  
  
- Nazwa wartości: **APTCA_FLAG**.  
  
- Typ wartości: **REG_DWORD**.  
  
- Dane wartości: **1** , aby wyłączyć; **0** , aby włączyć.  
  
 Jeśli zestaw musi być wyłączony dla częściowo zaufanych aplikacji klienckich, można napisać aktualizację, która tworzy klucz rejestru i wartość.  
  
> [!NOTE]
>  Nie ma to wpływu na podstawowe zestawy .NET Framework, ponieważ są one wymagane do uruchomienia aplikacji zarządzanych. Obsługa wyłączania zestawów APTCA jest przeznaczona głównie dla aplikacji innych firm.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Zachowanie piaskownicy dla luźnych plików XAML  
 Luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki są plikami XAML, które nie są zależne od żadnego kodu, programu obsługi zdarzeń lub zestawu specyficznego dla aplikacji. Gdy luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki są przechodzenia bezpośrednio z przeglądarki, są one ładowane w piaskownicy zabezpieczeń na podstawie domyślnego zestawu uprawnień strefy internetowej.  
  
 Zachowanie zabezpieczeń różni się jednak w przypadku, gdy [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] w przypadku swobodnych plików są przechodzenia <xref:System.Windows.Navigation.NavigationWindow> do <xref:System.Windows.Controls.Frame> programu lub w aplikacji autonomicznej.  
  
 W obu przypadkach luźny [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plik, który jest przeznaczony do przychodzenia do dziedziczy uprawnienia aplikacji hosta. Jednak takie zachowanie może być niepożądane z perspektywy zabezpieczeń, szczególnie jeśli luźny [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plik został wyprodukowany przez jednostkę, która nie jest zaufana lub nieznana. Ten typ zawartości jest znany jako *zawartość zewnętrzna*i obie <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> można skonfigurować w taki sposób, aby izoluje ją po przejściu do. Izolacja jest uzyskiwana przez ustawienie właściwości **SandboxExternalContent** na true, jak pokazano w poniższych przykładach <xref:System.Windows.Controls.Frame> dla <xref:System.Windows.Navigation.NavigationWindow>i:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 W przypadku tego ustawienia zawartość zewnętrzna zostanie załadowana do procesu, który jest oddzielony od procesu, który obsługuje aplikację. Ten proces jest ograniczony do domyślnego zestawu uprawnień strefy internetowej, co skutecznie izoluje go od aplikacji hostingu i komputera klienckiego.  
  
> [!NOTE]
>  Mimo że nawigacja do luźnych [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plików z <xref:System.Windows.Navigation.NavigationWindow> lub <xref:System.Windows.Controls.Frame> do aplikacji autonomicznej jest implementowana na podstawie infrastruktury hostingu w przeglądarce WPF, obejmującej proces PresentationHost, poziom zabezpieczeń to nieco mniejsze niż w przypadku załadowania zawartości bezpośrednio w programie Internet Explorer [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] w [!INCLUDE[win7](../../../includes/win7-md.md)] systemach i (które nadal są w PresentationHost). Wynika to z faktu, że autonomiczna aplikacja WPF korzystająca z przeglądarki sieci Web nie zapewnia dodatkowej funkcji zabezpieczeń trybu chronionego programu Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Zasoby służące do opracowywania aplikacji WPF promujących zabezpieczenia  
 Poniżej przedstawiono kilka dodatkowych zasobów, które ułatwiają [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] opracowywanie aplikacji, które promują zabezpieczenia:  
  
|Obszar|Zasób|  
|----------|--------------|  
|Kod zarządzany|[Wskazówki dotyczące zabezpieczeń wzorców i praktyk dotyczących aplikacji](https://go.microsoft.com/fwlink/?LinkId=117426)|  
|CAS|[Zabezpieczenia dostępu kodu](../misc/code-access-security.md)|  
|ClickOnce|[Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — zabezpieczenia platformy](wpf-security-strategy-platform-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
- [Wskazówki dotyczące zabezpieczeń wzorców i praktyk dotyczących aplikacji](https://go.microsoft.com/fwlink/?LinkId=117426)
- [Zabezpieczenia dostępu kodu](../misc/code-access-security.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przegląd XAML (WPF)](./advanced/xaml-overview-wpf.md)
