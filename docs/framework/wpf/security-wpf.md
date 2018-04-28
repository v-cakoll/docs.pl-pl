---
title: Zabezpieczenia (WPF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 38
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 134efba11742ab9cc8da2dfab77c233b52f1bcf1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="security-wpf"></a>Zabezpieczenia (WPF)
<a name="introduction"></a> Podczas tworzenia [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] autonomiczne i aplikacje obsługiwane w przeglądarce, należy wziąć pod uwagę modelu zabezpieczeń. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Aplikacje autonomiczne wykonywane za pomocą nieograniczonych uprawnień ( [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **FullTrust** zestaw uprawnień), czy wdrożyć przy użyciu Instalatora Windows (msi), XCopy, lub [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]. Częściowo zaufane, aplikacje autonomiczne WPF za pomocą technologii ClickOnce do wdrażania nie jest obsługiwane. Jednak utworzyć aplikację hosta pełnego zaufania częściowego zaufania <xref:System.AppDomain> przy użyciu modelu dodatku programu .NET Framework. Aby uzyskać więcej informacji, zobacz [omówienie Add-Ins WPF](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje obsługiwane w przeglądarce są obsługiwane przez [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] lub Firefox, i mogą być [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] lub utracić [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] dokumentów, aby uzyskać więcej informacji, zobacz [przeglądu aplikacje przeglądarki XAML w WPF](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje obsługiwane w przeglądarce wykonania w częściowej relacji zaufania izolowanym, domyślnie, który ogranicza domyślną [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **Internet** uprawnień zestawu stref. Efektywne zidentyfikowany [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje obsługiwane w przeglądarce na komputerze klienckim w taki sam sposób, można oczekiwać odizolowanie typowych aplikacji sieci Web. XBAP podnieść poziom uprawnień do pełnego zaufania, w zależności od strefy zabezpieczeń adres URL wdrożenia i konfiguracji zabezpieczeń klienta. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
 W tym temacie omówiono model zabezpieczeń [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] autonomicznych i aplikacje obsługiwane w przeglądarce.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Bezpieczne nawigacji](#SafeTopLevelNavigation)  
  
-   [Ustawienia zabezpieczeń oprogramowania przeglądania sieci Web](#InternetExplorerSecuritySettings)  
  
-   [Formant WebBrowser i kontrolek funkcji](#webbrowser_control_and_feature_controls)  
  
-   [Wyłączanie zestawów APTCA dla aplikacji klienckich częściowo zaufanych](#APTCA)  
  
-   [Zachowanie piaskownicy dla plików XAML utracić](#LooseContentSandboxing)  
  
-   [Zasoby do tworzenia aplikacji WPF, które wspierają zabezpieczeń](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Bezpieczne nawigacji  
 Aby uzyskać [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] odróżnia dwa rodzaje nawigacji: aplikacji i przeglądarki.  
  
 *Aplikacja nawigacji* jest nawigacji między elementami zawartości wewnątrz aplikacji, która jest obsługiwana przez przeglądarkę. *Nawigacja przeglądarki* jest nawigacji zmiany zawartości i lokalizacji URL przeglądarkę. Relacja między nawigacji aplikacji (zwykle XAML) i nawigację przeglądarki (zwykle HTML) przedstawiono na poniższej ilustracji:
  
 ![Diagram nawigacji](../../../docs/framework/wpf/media/safetoplevelnavigationfigure.png "SafeTopLevelNavigationFigure")  
  
 Typ zawartości, która jest uznawane za bezpieczne dla [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] można przejść do przede wszystkim jest określany przez czy używany jest nawigacji aplikacji lub nawigację przeglądarki.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Zabezpieczenia aplikacji nawigacji  
 Aplikacja nawigacji jest uznawane za bezpieczne, jeśli można go zidentyfikować z pakietem [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)], który obsługuje cztery typy zawartości:  
  
|Typ zawartości|Opis|Przykład identyfikatora URI|  
|------------------|-----------------|-----------------|  
|Zasób|Pliki, które są dodawane do projektu o typie kompilacji **zasobów**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Zawartość|Pliki, które są dodawane do projektu o typie kompilacji **zawartości**.|`pack://application:,,,/MyContentFile.xaml`|  
|Witryny pochodzenia|Pliki, które są dodawane do projektu o typie kompilacji **Brak**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Kod aplikacji|Zasoby XAML, które zostały skompilowane kodem.<br /><br /> —lub—<br /><br /> Pliki XAML, które są dodawane do projektu o typie kompilacji **strony**.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat pliki danych aplikacji i dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)], zobacz [zasób w aplikacji WPF, zawartość i pliki danych](../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Pliki te typy zawartości, może zostać przesłane do przez użytkownika lub programowo:  
  
-   **Użytkownik nawigacji**. Użytkownik przechodzi przez kliknięcie przycisku <xref:System.Windows.Documents.Hyperlink> elementu.  
  
-   **Programowe nawigacji**. Aplikacja przechodzi nie angażując użytkownika, na przykład przez ustawienie <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> właściwości.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Poziom zabezpieczeń przeglądarki nawigacji  
 Nawigacja przeglądarki jest uznawane za bezpieczne tylko w następujących warunkach:  
  
-   **Użytkownik nawigacji**. Użytkownik przechodzi przez kliknięcie przycisku <xref:System.Windows.Documents.Hyperlink> element, który znajduje się w głównym <xref:System.Windows.Navigation.NavigationWindow>nie w zagnieżdżonych <xref:System.Windows.Controls.Frame>.  
  
-   **Strefy**. Zawartość do znajduje się w sieci Internet lub lokalny intranet.  
  
-   **Protokół**. Jest używany protokół **http**, **https**, **pliku**, lub **mailto**.  
  
 Jeśli [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] próbuje przejdź do zawartości w taki sposób, który nie jest zgodne z tych warunków, <xref:System.Security.SecurityException> jest generowany.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Ustawienia zabezpieczeń oprogramowania przeglądania sieci Web  
 Ustawienia zabezpieczeń na komputerze określają dostępu, który został udzielony dowolnej sieci Web oprogramowania do przeglądania. Oprogramowania do przeglądania sieci Web zawiera dowolną aplikację lub składnik, który używa [WinINet](http://go.microsoft.com/fwlink/?LinkId=179379) lub [UrlMon](http://go.microsoft.com/fwlink/?LinkId=179383) interfejsów API, w tym programu Internet Explorer i PresentationHost.exe.  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] udostępnia mechanizm, za pomocą którego można skonfigurować funkcje, które może być wykonywane przez lub z [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)], takie jak:  
  
-   Składniki zależne framework .NET  
  
-   Formanty ActiveX i dodatki plug-in  
  
-   Pliki do pobrania  
  
-   Wykonywanie skryptów  
  
-   Uwierzytelnianie użytkownika  
  
 Kolekcja funkcji, które mogą być chronione w ten sposób jest skonfigurowany na podstawie stref dla **Internet**, **Intranet**, **Zaufane witryny**, i  **Ograniczone witryn** strefy. W poniższych krokach opisano sposób konfigurowania ustawień zabezpieczeń:  
  
1.  Otwórz **Panel sterowania**.  
  
2.  Kliknij przycisk **sieć i Internet** , a następnie kliknij przycisk **Opcje internetowe**.  
  
     Zostanie wyświetlone okno dialogowe Opcje internetowe.  
  
3.  Na **zabezpieczeń** , a następnie wybierz strefy, aby skonfigurować ustawienia zabezpieczeń.  
  
4.  Kliknij przycisk **Poziom niestandardowy** przycisku.  
  
     **Ustawienia zabezpieczeń** zostanie wyświetlone okno dialogowe i można skonfigurować ustawienia zabezpieczeń dla wybranej strefy.  
  
     ![Okno dialogowe Ustawienia zabezpieczeń](../../../docs/framework/wpf/media/wpfsecurityfigure1.PNG "WPFSecurityFigure1")  
  
> [!NOTE]
>  Możesz również uzyskać do okna dialogowego Opcje internetowe w programie Internet Explorer. Kliknij przycisk **narzędzia** , a następnie kliknij przycisk **Opcje internetowe**.  
  
 Począwszy od [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], uwzględnione są następujące ustawienia zabezpieczeń specjalnie dla programu .NET Framework:  
  
-   **Utrata XAML**. Formanty czy [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] można przejść do i luźno [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plików. (Włączanie i wyłączanie i monitu opcje).  
  
-   **Aplikacje przeglądarki XAML**. Formanty czy [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] można przejść do i uruchomić [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. (Włączanie i wyłączanie i monitu opcje).  
  
 Domyślnie te ustawienia są włączone dla **Internet**, **lokalny intranet**, i **Zaufane witryny** stref i wyłączony **ograniczone witryn**  strefy.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>Ustawienia rejestru związanych z zabezpieczeniami WPF  
 Oprócz ustawień zabezpieczeń dostępne opcje internetowe następujące wartości rejestru są dostępne dla selektywnego blokowania szereg istotnych dla zabezpieczeń funkcji WPF. Wartości są określone w następującym kluczu:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 W poniższej tabeli wymieniono wartości, które można ustawić.  
  
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
## <a name="webbrowser-control-and-feature-controls"></a>Formant WebBrowser i kontrolek funkcji  
 WPF <xref:System.Windows.Controls.WebBrowser> formant może służyć do obsługi zawartości sieci Web. WPF <xref:System.Windows.Controls.WebBrowser> kontrolki koduje podstawowej formantu WebBrowser ActiveX. WPF obsługuje niektóre zabezpieczania aplikacji, korzystając z WPF <xref:System.Windows.Controls.WebBrowser> formantu do hosta niezaufanych zawartości sieci Web. Jednak niektóre funkcje zabezpieczeń muszą być stosowane bezpośrednio przez aplikacje przy użyciu <xref:System.Windows.Controls.WebBrowser> formantu. Aby uzyskać więcej informacji na temat formantu WebBrowser ActiveX, zobacz [WebBrowser — formant omówienia i samouczki](http://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
>  Ta sekcja ma również zastosowanie do <xref:System.Windows.Controls.Frame> kontroli, ponieważ używa <xref:System.Windows.Controls.WebBrowser> można przejść do zawartość HTML.  
  
 Jeśli WPF <xref:System.Windows.Controls.WebBrowser> kontroli jest używana do hostowania niezaufaną zawartość sieci Web, aplikacji należy używać częściowo zaufanym <xref:System.AppDomain> aby pomóc zabezpieczyć kod aplikacji z kod potencjalnie złośliwy skrypt HTML. Jest to szczególnie istotne, jeśli aplikacja prowadzi interakcję z hostowanej skryptu za pomocą <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> — metoda i <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> właściwości. Aby uzyskać więcej informacji, zobacz [omówienie Add-Ins WPF](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Jeśli aplikacja używa WPF <xref:System.Windows.Controls.WebBrowser> kontroli, inny sposób, aby zwiększyć bezpieczeństwo i ograniczenie liczby ataków jest umożliwienie kontrolek funkcji programu Internet Explorer. Formanty funkcji to dodatki do programu Internet Explorer, umożliwiających Administratorzy i deweloperzy skonfigurować funkcje programu Internet Explorer i aplikacji, które kontrolki WebBrowser ActiveX hosta którego WPF <xref:System.Windows.Controls.WebBrowser> kontrolować zawija. Formanty funkcji można skonfigurować przy użyciu [CoInternetSetFeatureEnabled](http://go.microsoft.com/fwlink/?LinkId=179394) funkcji lub zmieniając wartości rejestru. Aby uzyskać więcej informacji na temat kontrolek funkcji, zobacz [wprowadzenie do kontrolek funkcji](http://go.microsoft.com/fwlink/?LinkId=179390) i [kontrolek funkcji Internet](http://go.microsoft.com/fwlink/?LinkId=179392).  
  
 Jeśli tworzysz aplikacja WPF autonomiczna, która używa WPF <xref:System.Windows.Controls.WebBrowser> kontroli, WPF automatycznie włącza następujących kontrolek funkcji aplikacji.  
  
|Funkcja sterowania|  
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
  
 Ponieważ bezwarunkowo włączonych tych funkcji kontroli aplikacji pełnego zaufania może ujemnie je. W takim przypadku jeśli nie występuje ryzyko zabezpieczeń dla określonych aplikacji oraz zawartość, którą obsługuje on, można wyłączyć odpowiedniego sterowania funkcją.  
  
 Formanty funkcji są stosowane przez proces tworzenia wystąpienia obiektu WebBrowser ActiveX. Dlatego w przypadku tworzenia aplikacji autonomicznej, który można przejść do niezaufaną zawartość należy poważnie rozważyć włączenie dodatkowych funkcji kontroli.  
  
> [!NOTE]
>  To zalecenie opiera się na ogólne zalecenia dotyczące zabezpieczeń hosta MSHTML i SHDOCVW. Aby uzyskać więcej informacji, zobacz [zabezpieczeń hosta MSHTML — często zadawane pytania: I część II](http://go.microsoft.com/fwlink/?LinkId=179396) i [zabezpieczeń hosta MSHTML — często zadawane pytania: część II II](http://go.microsoft.com/fwlink/?LinkId=179415).  
  
 Dla pliku wykonywalnego należy rozważyć włączenie następujących funkcji formantów za pomocą ustawienia wartości rejestru na wartość 1.  
  
|Funkcja sterowania|  
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
  
 Dla pliku wykonywalnego Rozważ wyłączenie następującego formantu funkcji za pomocą ustawienia wartości rejestru na 0.  
  
|Funkcja sterowania|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Po uruchomieniu częściowym zaufaniem [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] zawierającą WPF <xref:System.Windows.Controls.WebBrowser> kontroli w [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)], WPF obsługuje formant WebBrowser ActiveX w przestrzeni adresowej procesu programu Internet Explorer. Ponieważ formant WebBrowser ActiveX znajduje się w [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] proces, wszystkie formanty funkcji dla programu Internet Explorer są również włączone dla formantu WebBrowser ActiveX.  
  
 XBAP uruchomiony w programie Internet Explorer również pobrać dodatkowy poziom bezpieczeństwa w porównaniu do normalnej autonomicznej aplikacji. Jest to dodatkowe zabezpieczenia programu Internet Explorer i w związku z tym formant WebBrowser ActiveX jest uruchamiana chronionym tryb domyślnie na [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] i [!INCLUDE[win7](../../../includes/win7-md.md)]. Aby uzyskać więcej informacji na temat trybu chronionego, zobacz [opis i pracy w chroniony programu Internet Explorer trybu](http://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
>  Jeśli zostanie podjęta próba uruchomienia XBAP, która obejmuje WPF <xref:System.Windows.Controls.WebBrowser> sterowania w programie Firefox, znajduje się w strefie Internet <xref:System.Security.SecurityException> zostanie wygenerowany. Jest to spowodowane WPF zasady zabezpieczeń.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Wyłączanie zestawów APTCA dla aplikacji klienckich częściowo zaufanych  
 Podczas instalowania zarządzanych zestawów do [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)], stają się całkowicie zaufane, ponieważ użytkownik musi podać jawne uprawnienia mają być instalowane. Ponieważ są one całkowicie zaufane, można używać tylko klient zarządzany pełni zaufane aplikacje ich. Aby zezwolić na częściowo zaufane aplikacje z nich korzystać, musi być oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Powinna być oznaczona tylko zestawy, które zostały przetestowane jako bezpieczne do wykonywania w częściowej relacji zaufania z tym atrybutem.  
  
 Jednak jest możliwe w dla zestawu APTCA wykazują lukę w zabezpieczeniach po zainstalowaniu na [!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)]. Po lukę w zabezpieczeniach zostanie odnaleziony, wydawców zestawu powodują aktualizację zabezpieczeń, aby rozwiązać ten problem w przypadku istniejących instalacji i ochronę przed instalacji, które mogą wystąpić, gdy zostanie wykryta. Jedną z opcji aktualizacji jest odinstalować zestawu, mimo że mogą być dzielone inne aplikacje klienckie pełni zaufany, korzystających z zestawu.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] udostępnia mechanizm, za pomocą którego można wyłączyć zestawem APTCA, częściowo zaufany [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] bez odinstalowania zestawem APTCA.  
  
 Aby wyłączyć zestawem APTCA, należy utworzyć klucz rejestru specjalne:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Poniżej przedstawiono przykład:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Ten klucz ustanawia wpis dla zestawu APTCA. Należy także utworzyć wartość tego klucza, która włącza lub wyłącza zestawu. Dane dotyczące wartości są następujące:  
  
-   Nazwa wartości: **APTCA_FLAG**.  
  
-   Typ wartości: **REG_DWORD**.  
  
-   Dane wartości: **1** wyłączyć; **0** do włączenia.  
  
 Jeśli zestawu ma być wyłączone dla aplikacji klienckich częściowo zaufany, można napisać aktualizacji, która tworzy kluczy rejestru i wartości.  
  
> [!NOTE]
>  Podstawowe zestawy .NET Framework nie dotyczy wyłączyć je w ten sposób, ponieważ są one wymagane do działania aplikacji zarządzanych. Obsługa wyłączenie zestawy APTCA jest przeznaczony głównie dla aplikacji innych firm.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Zachowanie piaskownicy dla plików XAML utracić  
 Luźne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki są tylko do znaczników plików XAML, które nie są zależne od dowolnego związane z kodem, program obsługi zdarzeń lub zestawu specyficzne dla aplikacji. Gdy luźno [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki są przejście bezpośrednio z przeglądarki, są załadowane w izolowanym, na podstawie zestawu uprawnień strefy Internet domyślne.  
  
 Jednak działanie zabezpieczeń jest inny, gdy utracić [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliki są przejście z jednej <xref:System.Windows.Navigation.NavigationWindow> lub <xref:System.Windows.Controls.Frame> w autonomicznej aplikacji.  
  
 W obu przypadkach utracić [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliku, który jest przejście dziedziczy uprawnienia jego aplikacji hosta. Jednak to działanie może być niepożądane z punktu widzenia zabezpieczeń, zwłaszcza w wypadku utracić [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plik został utworzony przez jednostkę, która nie jest zaufany lub jest nieznany. Tego typu zawartości jest znany jako *zawartość zewnętrzną*, a oba <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> można skonfigurować w celu gdy przejście odizolować. Jest to osiągane przez ustawienie izolacji **właściwości SandboxExternalContent** właściwości na wartość true, jak pokazano w poniższych przykładach dotyczących <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 To ustawienie, zawartość zewnętrzną zostanie załadowany do procesu, który różni się od procesu, który jest hostem aplikacji. Ten proces jest ograniczone do domyślnego Internet strefy zestaw uprawnień, efektywnie izolując ją od hostingu aplikacji i komputera klienckiego.  
  
> [!NOTE]
>  Mimo że nawigacji można utracić [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] plików z poziomu <xref:System.Windows.Navigation.NavigationWindow> lub <xref:System.Windows.Controls.Frame> w autonomicznej aplikacji jest zaimplementowana opartych na przeglądarce WPF hosting infrastruktury, obejmujący proces PresentationHost poziom zabezpieczeń jest nieco mniej niż kiedy zawartość jest ładowane bezpośrednio w programie Internet Explorer na [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] i [!INCLUDE[win7](../../../includes/win7-md.md)] (które nadal będą za pośrednictwem PresentationHost). Jest to spowodowane autonomicznej aplikacji WPF przy użyciu przeglądarki sieci Web nie zapewnia dodatkowych funkcji zabezpieczeń tryb chroniony programu Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Zasoby do tworzenia aplikacji WPF, które wspierają zabezpieczeń  
 Poniżej przedstawiono dodatkowe zasoby pomagające w tworzeniu [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacji, które podwyższyć poziom zabezpieczeń:  
  
|Obszar|Zasób|  
|----------|--------------|  
|Zarządzany kod|[Wzorce i wskazówki dotyczące zabezpieczeń rozwiązań dla aplikacji](http://go.microsoft.com/fwlink/?LinkId=117426)|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[Zabezpieczenie częściowej relacji zaufania WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenie częściowej relacji zaufania WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [Strategia zabezpieczeń WPF — zabezpieczenia platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Strategia zabezpieczeń WPF — projekt zabezpieczeń](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)  
 [Wzorce i wskazówki dotyczące zabezpieczeń rozwiązań dla aplikacji](http://go.microsoft.com/fwlink/?LinkId=117426)  
 [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)  
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
