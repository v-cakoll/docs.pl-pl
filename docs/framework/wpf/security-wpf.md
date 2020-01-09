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
ms.openlocfilehash: 612b99354310c18030cefce4e6f02fab8ed20f83
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636775"
---
# <a name="security-wpf"></a>Zabezpieczenia (WPF)
<a name="introduction"></a>Podczas opracowywania aplikacji autonomicznych i hostowanych przez program Windows Presentation Foundation (WPF) należy wziąć pod uwagę model zabezpieczeń. Aplikacje autonomiczne WPF są wykonywane z nieograniczonymi uprawnieniami (zestaw uprawnień CAS**FullTrust** ), niezależnie od tego, czy wdrożono przy użyciu Instalator Windows (. msi), XCOPY lub ClickOnce. Wdrożenie częściowego zaufania, autonomiczne aplikacje WPF za pomocą technologii ClickOnce nie jest obsługiwane. Jednak w pełni zaufane aplikacje hosta mogą utworzyć <xref:System.AppDomain> relacji zaufania z użyciem .NET Framework modelu dodatków. Aby uzyskać więcej informacji, zobacz [Omówienie dodatków WPF](./app-development/wpf-add-ins-overview.md).  
  
 Aplikacje hostowane w przeglądarce WPF są hostowane w programie Windows Internet Explorer lub Firefox i mogą być aplikacjami przeglądarki XAML (XBAP) lub luźno [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] dokumenty, aby uzyskać więcej informacji, zobacz [Omówienie aplikacji przeglądarki XAML w języku WPF](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 Aplikacje hostowane w przeglądarce WPF działają w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania, domyślnie, co jest ograniczone do domyślnego zestawu uprawnień strefy**internetowej** CAS. W ten sam sposób izoluje aplikacje hostowane w przeglądarce WPF z komputera klienckiego w taki sam sposób, w jaki można oczekiwać, że typowe aplikacje sieci Web mają być izolowane. Aplikacje XBAP mogą podwyższyć poziom uprawnień, do pełnego zaufania, w zależności od strefy zabezpieczeń w adresie URL wdrożenia i konfiguracji zabezpieczeń klienta. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](wpf-partial-trust-security.md).  
  
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
 W przypadku aplikacji XBAP funkcja WPF rozróżnia dwa typy nawigacji: aplikacja i przeglądarka.  
  
 *Nawigowanie po aplikacji* to nawigacja między elementami zawartości w aplikacji hostowanej w przeglądarce. *Nawigacja w przeglądarce* to Nawigacja, która zmienia zawartość i adres URL w przeglądarce. Relacja między nawigacją aplikacji (zazwyczaj XAML) i nawigacją przeglądarki (zwykle HTML) pokazano na poniższej ilustracji:
  
 ![Relacja między nawigacją aplikacji a nawigacją przeglądarki.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 Typ zawartości uznawany za bezpieczny dla aplikacji XBAP do przechodzenia jest określany przede wszystkim na podstawie tego, czy używana jest nawigacja aplikacji czy Nawigacja w przeglądarce.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Zabezpieczenia nawigacji aplikacji  
 Nawigowanie po aplikacji jest uznawane za bezpieczne, jeśli może być identyfikowane za pomocą identyfikatora URI pakietu, który obsługuje cztery typy zawartości:  
  
|Typ zawartości|Opis|Przykład identyfikatora URI|  
|------------------|-----------------|-----------------|  
|Zasób|Pliki, które są dodawane do projektu z typem kompilacji **zasobu**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Zawartość|Pliki, które są dodawane do projektu z typem kompilacji **zawartości**.|`pack://application:,,,/MyContentFile.xaml`|  
|Lokacja pochodzenia|Pliki, które są dodawane do projektu z typem kompilacji **Brak**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Kod aplikacji|Zasoby XAML, które mają skompilowany kod w tle.<br /><br /> lub<br /><br /> Pliki XAML, które są dodawane do projektu z typem kompilacji **strony**.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat plików danych aplikacji i identyfikatorów URI pakietów, zobacz artykuł [Aplikacja WPF, zawartość i pliki danych](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Pliki tych typów zawartości mogą być przechodzenie przez użytkownika lub programowo:  
  
- **Nawigacja użytkownika**. Użytkownik przechodzi przez kliknięcie elementu <xref:System.Windows.Documents.Hyperlink>.  
  
- **Nawigacja programowa**. Aplikacja nawiguje bez udziału użytkownika, na przykład przez ustawienie właściwości <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Zabezpieczenia nawigacji przeglądarki  
 Nawigacja w przeglądarce jest uważana za bezpieczną tylko w następujących warunkach:  
  
- **Nawigacja użytkownika**. Użytkownik przechodzi przez kliknięcie elementu <xref:System.Windows.Documents.Hyperlink>, który znajduje się w głównym <xref:System.Windows.Navigation.NavigationWindow>, a nie w <xref:System.Windows.Controls.Frame>zagnieżdżonym.  
  
- **Strefa**. Zawartość, do której nastąpi przejście, znajduje się w Internecie lub w lokalnym intranecie.  
  
- **Protokół**. Używanym protokołem jest **http**, **https**, **File**lub **mailto**.  
  
 Jeśli usługa XBAP podejmie próbę przejścia do zawartości w sposób niezgodny z tymi warunkami, zostanie zgłoszony <xref:System.Security.SecurityException>.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Ustawienia zabezpieczeń oprogramowania do przeglądania sieci Web  
 Ustawienia zabezpieczeń na komputerze określają dostęp do dowolnego oprogramowania do przeglądania sieci Web. Oprogramowanie do przeglądania sieci Web obejmuje dowolną aplikację lub składnik korzystający z interfejsów API [WinInet](/windows/win32/wininet/portal) lub [Urlmon](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) , w tym programów Internet Explorer i PresentationHost. exe.  
  
 Program Internet Explorer oferuje mechanizm, za pomocą którego można skonfigurować funkcje, które mogą być wykonywane przez program lub z programu Internet Explorer, w tym następujące:  
  
- Składniki zależne .NET Framework  
  
- Kontrolki ActiveX i wtyczki  
  
- Pliki do pobrania  
  
- Obsługa skryptów  
  
- Uwierzytelnianie użytkownika  
  
 Zbiór funkcji, które mogą być zabezpieczane w ten sposób, jest skonfigurowany dla każdej strefy dla strefy **Internet**, **intranet**, **Zaufane witryny**i **witryny z ograniczeniami** . Poniższe kroki opisują sposób konfigurowania ustawień zabezpieczeń:  
  
1. Otwórz **Panel sterowania**.  
  
2. Kliknij pozycję **Sieć i Internet** , a następnie kliknij pozycję **Opcje internetowe**.  
  
     Zostanie wyświetlone okno dialogowe Opcje internetowe.  
  
3. Na karcie **zabezpieczenia** wybierz strefę, dla której mają zostać skonfigurowane ustawienia zabezpieczeń.  
  
4. Kliknij przycisk **Poziom niestandardowy** .  
  
     Zostanie wyświetlone okno dialogowe **Ustawienia zabezpieczeń** , w którym można skonfigurować ustawienia zabezpieczeń dla wybranej strefy.  
  
     ![Zrzut ekranu przedstawiający okno dialogowe Ustawienia zabezpieczeń.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> Możesz również przejść do okna dialogowego Opcje internetowe w programie Internet Explorer. Kliknij pozycję **Narzędzia** , a następnie kliknij pozycję **Opcje internetowe**.  
  
 Począwszy od programu Windows Internet Explorer 7, dostępne są następujące ustawienia zabezpieczeń przeznaczone dla .NET Framework:  
  
- **Luźny kod XAML**. Określa, czy program Internet Explorer może przechodzić do i luźno [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki. (Włącz, wyłącz i Monituj opcje).  
  
- **Aplikacje przeglądarki XAML**. Określa, czy program Internet Explorer może przechodzić do i uruchamiać aplikacje XBAP. (Włącz, wyłącz i Monituj opcje).  
  
 Domyślnie te ustawienia są włączone dla strefy **Internet**, **Lokalny intranet**i **Zaufane witryny** oraz wyłączone dla strefy **witryn z ograniczeniami** .  
  
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
 Formant <xref:System.Windows.Controls.WebBrowser> WPF może służyć do hostowania zawartości sieci Web. Formant <xref:System.Windows.Controls.WebBrowser> WPF otacza podstawową kontrolkę ActiveX WebBrowser. WPF udostępnia pewne wsparcie w zakresie zabezpieczania aplikacji przy użyciu kontrolki <xref:System.Windows.Controls.WebBrowser> WPF do hostowania niezaufanej zawartości sieci Web. Jednak niektóre funkcje zabezpieczeń muszą być stosowane bezpośrednio przez aplikacje przy użyciu kontrolki <xref:System.Windows.Controls.WebBrowser>. Aby uzyskać więcej informacji na temat kontrolki ActiveX WebBrowser, zobacz [przeglądanie i samouczki kontrolki WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85)).  
  
> [!NOTE]
> Ta sekcja ma zastosowanie również do kontrolki <xref:System.Windows.Controls.Frame>, ponieważ używa <xref:System.Windows.Controls.WebBrowser> do nawigowania do zawartości HTML.  
  
 Jeśli formant <xref:System.Windows.Controls.WebBrowser> WPF jest używany do hostowania niezaufanej zawartości sieci Web, aplikacja powinna używać <xref:System.AppDomain> częściowej relacji zaufania, aby pomóc w izolowaniu kodu aplikacji od potencjalnie złośliwego kodu skryptu HTML. Jest to szczególnie prawdziwe, jeśli aplikacja działa z hostowanym skryptem za pomocą metody <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> i właściwości <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>. Aby uzyskać więcej informacji, zobacz [Omówienie dodatków WPF](./app-development/wpf-add-ins-overview.md).  
  
 Jeśli aplikacja używa kontrolki <xref:System.Windows.Controls.WebBrowser> WPF, inny sposób zwiększania bezpieczeństwa i ograniczania ataków polega na włączeniu formantów funkcji programu Internet Explorer. Formanty funkcji to dodatki do programu Internet Explorer, które umożliwiają administratorom i deweloperom Konfigurowanie funkcji programu Internet Explorer i aplikacji obsługujących formant ActiveX WebBrowser, które są zawijane przez formant <xref:System.Windows.Controls.WebBrowser> WPF. Formanty funkcji można skonfigurować za pomocą funkcji [CoInternetSetFeatureEnabled](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85)) lub zmieniając wartości w rejestrze. Aby uzyskać więcej informacji na temat kontrolek funkcji, zobacz [wprowadzenie do kontrolek funkcji](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) i [kontrolek funkcji internetowych](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85)).  
  
 Jeśli tworzysz autonomiczną aplikację WPF, która używa kontrolki <xref:System.Windows.Controls.WebBrowser> WPF, WPF automatycznie włącza następujące kontrolki funkcji dla aplikacji.  
  
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
> To zalecenie jest oparte na ogólnych zaleceniach dotyczących zabezpieczeń hosta MSHTML i SHDOCVW. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [zabezpieczeń hosta MSHTML często zadawanych pytań: część I z II](https://msrc-blog.microsoft.com/archive/2009/04/02/the-mshtml-host-security-faq.aspx) i informacje o [zabezpieczeniach hosta MSHTML — często zadawane pytania: część II z II](https://msrc-blog.microsoft.com/archive/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii.aspx).  
  
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
  
 Jeśli uruchamiasz aplikację przeglądarki XAML z częściowym zaufaniem (XBAP), która zawiera formant <xref:System.Windows.Controls.WebBrowser> WPF w programie Windows Internet Explorer, WPF hostuje formant ActiveX WebBrowser w przestrzeni adresowej procesu programu Internet Explorer. Ponieważ Kontrolka ActiveX WebBrowser jest hostowana w procesie programu Internet Explorer, wszystkie formanty funkcji dla programu Internet Explorer również są włączone dla kontrolki ActiveX WebBrowser.  
  
 Aplikacje XBAP działające w programie Internet Explorer również uzyskują dodatkowy poziom zabezpieczeń w porównaniu z normalnymi aplikacjami autonomicznymi. To dodatkowe zabezpieczenia wynika z faktu, że program Internet Explorer i w związku z tym Kontrolka ActiveX WebBrowser są domyślnie uruchamiane w trybie chronionym w systemach Windows Vista i Windows 7. Aby uzyskać więcej informacji na temat trybu chronionego, zobacz [Opis i praca w trybie chronionym programu Internet Explorer](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/).  
  
> [!NOTE]
> Jeśli spróbujesz uruchomić aplikację XBAP, która zawiera kontrolkę <xref:System.Windows.Controls.WebBrowser> WPF w przeglądarce Firefox, w strefie Internet zostanie wygenerowany <xref:System.Security.SecurityException>. Jest to spowodowane zasadami zabezpieczeń WPF.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Wyłączanie zestawów APTCA dla częściowo zaufanych aplikacji klienckich  
 Gdy zarządzane zestawy są zainstalowane w globalnej pamięci podręcznej zestawów (GAC), stają się w pełni zaufane, ponieważ użytkownik musi podać jawne uprawnienia, aby je zainstalować. Ponieważ są one w pełni zaufane, mogą z nich korzystać tylko w pełni zaufane zarządzane aplikacje klienckie. Aby umożliwić ich używanie częściowo zaufanych aplikacji, muszą one być oznaczone przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Tylko zestawy, które zostały przetestowane pod kątem bezpiecznego wykonywania w częściowej relacji zaufania, powinny być oznaczone tym atrybutem.  
  
 Jednak w przypadku zestawu APTCA może zostać wystawiona Luka w zabezpieczeniach po zainstalowaniu w pamięci podręcznej GAC. Po znalezieniu usterki zabezpieczeń wydawcy zestawu mogą utworzyć aktualizację zabezpieczeń, aby rozwiązać problem z istniejącymi instalacjami oraz chronić przed instalacjami, które mogą wystąpić po wykryciu problemu. Jedną z opcji aktualizacji jest odinstalowanie zestawu, chociaż może to spowodować uszkodzenie innych w pełni zaufanych aplikacji klienckich korzystających z zestawu.  
  
 WPF udostępnia mechanizm, za pomocą którego można wyłączyć zestaw APTCA dla częściowo zaufanych aplikacji XBAP bez odinstalowywania zestawu APTCA.  
  
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
> Nie ma to wpływu na podstawowe zestawy .NET Framework, ponieważ są one wymagane do uruchomienia aplikacji zarządzanych. Obsługa wyłączania zestawów APTCA jest przeznaczona głównie dla aplikacji innych firm.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Zachowanie piaskownicy dla luźnych plików XAML  
 Luźne pliki [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] są plikami XAML, które nie są zależne od żadnego kodu, programu obsługi zdarzeń lub zestawu specyficznego dla aplikacji. Gdy luźne pliki [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] są przechodzenia bezpośrednio z przeglądarki, są one ładowane w piaskownicy zabezpieczeń na podstawie domyślnego zestawu uprawnień strefy internetowej.  
  
 Zachowanie zabezpieczeń jest jednak inne, gdy luźne pliki [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] są przechodzenia do <xref:System.Windows.Navigation.NavigationWindow> lub <xref:System.Windows.Controls.Frame> w aplikacji autonomicznej.  
  
 W obu przypadkach luźny plik [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)], do którego prowadzi Nawigacja, dziedziczy uprawnienia aplikacji hosta. Jednak takie zachowanie może być niepożądane z perspektywy zabezpieczeń, szczególnie jeśli luźny plik [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] został wyprodukowany przez jednostkę, która nie jest zaufana lub nieznana. Ten typ zawartości jest znany jako *zawartość zewnętrzna*i zarówno <xref:System.Windows.Controls.Frame>, jak i <xref:System.Windows.Navigation.NavigationWindow> można skonfigurować tak, aby izoluje ją podczas przejścia do. Izolacja jest uzyskiwana przez ustawienie właściwości **SandboxExternalContent** na true, jak pokazano w poniższych przykładach dla <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 W przypadku tego ustawienia zawartość zewnętrzna zostanie załadowana do procesu, który jest oddzielony od procesu, który obsługuje aplikację. Ten proces jest ograniczony do domyślnego zestawu uprawnień strefy internetowej, co skutecznie izoluje go od aplikacji hostingu i komputera klienckiego.  
  
> [!NOTE]
> Mimo że nawigacja do luźnych plików [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] z <xref:System.Windows.Navigation.NavigationWindow> lub <xref:System.Windows.Controls.Frame> w aplikacji autonomicznej jest zaimplementowana na podstawie infrastruktury hostingu w przeglądarce WPF, obejmującej proces PresentationHost, poziom zabezpieczeń jest nieco mniejszy niż w przypadku załadowania zawartości bezpośrednio w programie Internet Explorer w systemach Windows Vista i Windows 7 (które nadal można wykonać za pośrednictwem PresentationHost). Wynika to z faktu, że autonomiczna aplikacja WPF korzystająca z przeglądarki sieci Web nie zapewnia dodatkowej funkcji zabezpieczeń trybu chronionego programu Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Zasoby służące do opracowywania aplikacji WPF promujących zabezpieczenia  
 Poniżej przedstawiono kilka dodatkowych zasobów, które ułatwiają opracowywanie aplikacji WPF, które promują zabezpieczenia:  
  
|Obszar|Zasób|  
|----------|--------------|  
|Kod zarządzany|[Wskazówki dotyczące zabezpieczeń wzorców i praktyk dotyczących aplikacji](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))|  
|CAS|[Zabezpieczenia dostępu kodu](../misc/code-access-security.md)|  
|ClickOnce|[Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)|  
|WPF|[Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — zabezpieczenia platformy](wpf-security-strategy-platform-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
- [Wskazówki dotyczące zabezpieczeń wzorców i praktyk dotyczących aplikacji](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))
- [Zabezpieczenia dostępu kodu](../misc/code-access-security.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
