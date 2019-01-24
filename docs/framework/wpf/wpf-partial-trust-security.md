---
title: Zabezpieczenie częściowej relacji zaufania WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
ms.openlocfilehash: ec3c7a15627cf423d27221b870286009a8f7606f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534799"
---
# <a name="wpf-partial-trust-security"></a>Zabezpieczenie częściowej relacji zaufania WPF
<a name="introduction"></a> Ogólnie rzecz biorąc aplikacje internetowe powinny być ograniczone z mających bezpośredni dostęp do krytycznych zasobów systemu, aby uniemożliwić złośliwym uszkodzeniem. Domyślnie [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] i języków skryptów po stronie klienta nie będą mogli uzyskiwać dostęp do zasobów systemu. Ponieważ za pomocą przeglądarki można uruchamiać aplikacje hostowane w przeglądarce Windows Presentation Foundation (WPF), powinna być zgodna z zestawem podobnych ograniczeń. Aby wymusić ograniczenia te [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] opiera się na obu [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] i [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] (zobacz [strategia zabezpieczeń WPF - zabezpieczenia platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Domyślnie aplikacje hostowane w przeglądarce żądań strefy Internet [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] zestaw uprawnień, niezależnie od tego, czy będą uruchamiane z sieci Internet, lokalny intranet lub komputera lokalnego. Aplikacje uruchamiane w każdym innym mniejszą niż pełny zestaw uprawnień, mówi się, że jest uruchomiona z częściowej relacji zaufania.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] oferuje szeroką gamę pomocy technicznej, aby upewnić się, że tylu funkcji, jak to możliwe może być używany w częściowej relacji zaufania, a wraz z [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)], zapewnia dodatkową obsługę programowania częściowej relacji zaufania.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Obsługa częściowego zaufania funkcji WPF](#WPF_Feature_Partial_Trust_Support)  
  
-   [Programowanie w częściowej relacji zaufania](#Partial_Trust_Programming)  
  
-   [Zarządzanie uprawnieniami](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Obsługa częściowego zaufania funkcji WPF  
 W poniższej tabeli wymieniono funkcje wysokiego poziomu systemu Windows Presentation Foundation (WPF), które są bezpiecznie korzystać w granicach zestawu uprawnień strefy Internet.  
  
 Tabela 1: Funkcje WPF, które są bezpieczne w trybie częściowego zaufania  
  
|Obszar funkcji|Funkcja|  
|------------------|-------------|  
|Ogólne|Okno przeglądarki<br /><br /> Witryna pochodzenia dostępu<br /><br /> IsolatedStorage (Limit: 512KB)<br /><br /> Biblioteki UIAutomation dostawców<br /><br /> Polecenia<br /><br /> Edytory Input Method Editor (IME)<br /><br /> Tablet pióra i pisma odręcznego<br /><br /> Symulowane przeciągania i upuszczania za pomocą przechwytywanie myszy i Przenieś zdarzenia<br /><br /> OpenFileDialog<br /><br /> Deserializacja XAML (za pośrednictwem XamlReader.Load)|  
|Integracja z siecią Web|Okno dialogowe pobierania przeglądarki<br /><br /> Górny pasek nawigacji, które są inicjowane przez użytkownika<br /><br /> mailto:Links<br /><br /> Parametry identyfikatora URI<br /><br /> HTTPWebRequest<br /><br /> Zawartość WPF hostowanej w elemencie IFRAME wybranie<br /><br /> Hosting w tej samej lokacji stron HTML przy użyciu klatek<br /><br /> Hosting w tej samej lokacji stron HTML przy użyciu WebBrowser<br /><br /> Web Services (ASMX)<br /><br /> Usługi sieci Web (przy użyciu programu Windows Communication Foundation)<br /><br /> Wykonywanie skryptów<br /><br /> Model obiektu dokumentu|  
|Elementy wizualne|2D i 3D<br /><br /> Animacja<br /><br /> Nośnika (witryna pochodzenia i międzydomenowe)<br /><br /> Tworzenie obrazów i Audio/wideo|  
|Odczytywanie|FlowDocuments<br /><br /> Dokumenty XPS<br /><br /> Osadzony & czcionki systemowe<br /><br /> CFF & czcionki TrueType|  
|Edytowanie|Sprawdzanie pisowni<br /><br /> RichTextBox<br /><br /> Zwykły tekst oraz Obsługa schowka pisma odręcznego<br /><br /> Wklej zainicjowanego przez użytkownika<br /><br /> Kopiowanie zaznaczenia zawartości|  
|Formanty|Formanty ogólne|  
  
 W tej tabeli opisano [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] funkcje na wysokim poziomie. Aby uzyskać szczegółowe informacje, [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] dokumenty uprawnienia, które są wymagane przez każdy element członkowski w [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Ponadto następujące funkcje uzyskać bardziej szczegółowe informacje dotyczące wykonania częściowej relacji zaufania, w tym uwagi.  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (zobacz [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)).  
  
-   Wyskakujące okienka (zobacz <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
-   Przeciąganie i upuszczanie (zobacz [przeciągania i upuszczania Przegląd](../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)).  
  
-   Schowek (zobacz <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
-   Tworzenie obrazu (zobacz <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
-   Serializacja (zobacz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
-   Otwórz okno dialogowe pliku (zobacz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 W poniższej tabeli przedstawiono [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] funkcje, które nie są bezpieczne uruchamianie w ramach Internetu strefa zestaw uprawnień.  
  
 Tabela 2: Funkcje WPF, które są nie są bezpieczne w trybie częściowego zaufania  
  
|Obszar funkcji|Funkcja|  
|------------------|-------------|  
|Ogólne|Okno (Windows określonych aplikacji i okien dialogowych)<br /><br /> SaveFileDialog<br /><br /> System plików<br /><br /> Dostęp do rejestru<br /><br /> Przeciągnij i opuść<br /><br /> Serializacja XAML (za pośrednictwem XamlWriter.Save)<br /><br /> Biblioteki UIAutomation klientów<br /><br /> Dostęp do okna źródłowego (HwndHost)<br /><br /> Obsługa pełnego mowy<br /><br /> Windows Forms współdziałanie|  
|Elementy wizualne|Efekty mapy bitowej<br /><br /> Kodowanie obrazów|  
|Edytowanie|Tekst sformatowany Format Schowka<br /><br /> Pełna obsługa w XAML|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programowanie w częściowej relacji zaufania  
 Aby uzyskać [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] aplikacje, kod, który przekracza domyślny zestaw uprawnień mają inne zachowanie w zależności od strefy zabezpieczeń. W niektórych przypadkach użytkownik zostanie wyświetlone ostrzeżenie, gdy próbują zainstalować ją. Użytkownik może zdecydować kontynuować, lub Anuluj instalację. W poniższej tabeli opisano zachowanie aplikacji dla każdej strefy zabezpieczeń i co należy zrobić dla aplikacji otrzymać pełne zaufanie.  
  
|Strefa zabezpieczeń|Zachowanie|Pobieranie pełnego zaufania|  
|-------------------|--------------|------------------------|  
|Komputer lokalny|Automatyczne pełnego zaufania|Jest wymagana żadna akcja.|  
|W intranecie i zaufanych witryn|Monituj o pełnym zaufaniu|Zaloguj się XBAP przy użyciu certyfikatu, tak, aby użytkownik zobaczy źródła w wierszu polecenia.|  
|Internet|Kończy się błędem "Nie udzielono zaufania"|Zaloguj się XBAP przy użyciu certyfikatu.|  
  
> [!NOTE]
>  Zachowanie opisane w poprzedniej tabeli jest pełne zaufanie aplikacji XBAP, które nie są zgodne z modelu wdrażania zaufanych ClickOnce.  
  
 Ogólnie rzecz biorąc kod, który może być dłuższe niż dozwolone uprawnienia prawdopodobnie będzie wspólny kod, która jest udostępniana między zarówno autonomiczne, jak i aplikacji hostowanych w przeglądarce. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] i [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] oferuje kilka technik do zarządzania w tym scenariuszu.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Wykrywanie uprawnień przy użyciu urzędów certyfikacji  
 W niektórych przypadkach istnieje możliwość, że kod udostępniony w zestawach biblioteki ma być używany przez obie aplikacje autonomiczne i [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. W takich przypadkach kod może wykonywać funkcji, które mogą być potrzebne większe uprawnienia niż zezwala na zestaw uprawnień udzielonych aplikacji. Aplikacja może wykryć, czy nie ma określonych uprawnień przy użyciu zabezpieczeń platformy Microsoft .NET Framework. W szczególności można sprawdzić, czy ma określone uprawnienia, wywołując <xref:System.Security.CodeAccessPermission.Demand%2A> metody w wystąpieniu żądane uprawnienia. Jest to pokazane w poniższym przykładzie, który zawiera kod z tego zapytania dotyczące tego, czy ma możliwość zapisania pliku na dysku lokalnym:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Jeśli aplikacja nie ma żądane uprawnienie, wywołanie <xref:System.Security.CodeAccessPermission.Demand%2A> zgłosi wyjątek zabezpieczeń. W przeciwnym razie udzielono uprawnień. `IsPermissionGranted` to zachowanie jest hermetyzowany i zwraca `true` lub `false` odpowiednio.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Bezpiecznie obniżenie funkcjonalności  
 Możliwość wykrywania, czy kod ma uprawnienia, aby zrobić to, czego potrzebuje robić jest interesujące dla kodu, które mogą być wykonywane w różnych strefach. Podczas wykrywania strefa jest jedną z rzeczy, jest znacznie lepiej jako alternatywa dla użytkownika, jeśli jest to możliwe. Na przykład aplikacji pełne zaufanie zwykle umożliwia użytkownikom tworzenie plików w dowolne miejsce chcą, podczas gdy częściowo zaufanych aplikacji można tworzyć pliki tylko w wydzielonej pamięci masowej. Jeśli kod, aby utworzyć plik istnieje w zestawie, który jest współużytkowany przez w pełni zaufane (autonomiczne) aplikacje i aplikacje (obsługiwane w przeglądarce) częściowej relacji zaufania, a obie aplikacje chcesz, aby użytkownicy mogli tworzyć pliki, kod udostępniony powinien wykrywa, czy jest uruchomiony w trybie częściowego lub pełnego zaufania, przed utworzeniem pliku w odpowiedniej lokalizacji. Poniższy kod ilustruje obie.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 W wielu przypadkach można znaleźć alternatywna częściowej relacji zaufania.  
  
 W kontrolowanym środowisku, takich jak intranet niestandardowe struktury zarządzanej można zainstalować w podstawowej do klienta [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]. Te biblioteki można wykonać kod wymagający pełnego zaufania, a można odwoływać się z aplikacji, które są dozwolone tylko częściowej relacji zaufania za pomocą <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (Aby uzyskać więcej informacji, zobacz [zabezpieczeń](../../../docs/framework/wpf/security-wpf.md) i [zabezpieczeń WPF Strategia - zabezpieczenia platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Wykrywania hosta przeglądarki  
 Za pomocą [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] pod kątem uprawnienia to technika odpowiednie, jeśli trzeba sprawdzić w oparciu o niskich uprawnieniach. Mimo że ta technika jest zależna od połowowe wyjątki jako część normalnego przetwarzania, które nie jest zalecane, ogólnie rzecz biorąc i może mieć problemy z wydajnością. Zamiast tego Jeśli Twoja [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] jest uruchamiane tylko wtedy w piaskownicy strefy Internet, można użyć <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> właściwość, która zwraca wartość true dla [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> wyróżnia tylko, czy aplikacja działa w przeglądarce nie który zestaw uprawnień aplikacji został uruchomiony z.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Zarządzanie uprawnieniami  
 Domyślnie [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] uruchamiane z częściowej relacji zaufania (zestaw uprawnień strefy Internet domyślną). Jednak w zależności od wymagań aplikacji istnieje możliwość zmiany zestaw uprawnień z domyślnego. Na przykład jeśli [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] jest uruchamiany z lokalny intranet, może korzystać z zestawu uprawnień zwiększona, który jest pokazany w poniższej tabeli.  
  
 Tabela 3: LocalIntranet i uprawnienia Internet  
  
|Uprawnienie|Atrybut|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Dostęp do serwerów DNS|Tak|Nie|  
|Zmienne środowiskowe|Odczyt|Tak|Nie|  
|Okna dialogowe pliku|Otwarcie|Tak|Tak|  
|Okna dialogowe pliku|Bez ograniczeń|Tak|Nie|  
|Izolowany magazyn|Zestaw Izolacja według użytkownika|Tak|Nie|  
|Izolowany magazyn|Nieznany izolacji|Tak|Tak|  
|Izolowany magazyn|Limit przydziału użytkownika bez ograniczeń|Tak|Nie|  
|Nośnik|Bezpieczne audio, wideo i obrazy|Tak|Tak|  
|Drukowanie|Drukowanie domyślne|Tak|Nie|  
|Drukowanie|Bezpieczne drukowanie|Tak|Tak|  
|Odbicie|Emituj|Tak|Nie|  
|Zabezpieczenia|Wykonywanie kodu zarządzanego|Tak|Tak|  
|Zabezpieczenia|Asercja udzielone uprawnienia|Tak|Nie|  
|Interfejs użytkownika|Bez ograniczeń|Tak|Nie|  
|Interfejs użytkownika|Bezpieczne najwyższego poziomu systemu windows|Tak|Tak|  
|Interfejs użytkownika|Właścicielem Schowka|Tak|Tak|  
|Przeglądarki sieci Web|Nawigacji w ramce awaryjny w formacie HTML|Tak|Tak|  
  
> [!NOTE]
>  Wycinanie i wklejanie jest dozwolona tylko w częściowej relacji zaufania, gdy zainicjowane przez użytkownika.  
  
 Jeśli chcesz zwiększyć uprawnienia, musisz zmienić ustawienia projektu i manifest aplikacji ClickOnce. Aby uzyskać więcej informacji, zobacz [WPF XAML Browser Applications Overview](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md). Następujące dokumenty mogą być również przydatne.  
  
-   [Mage.exe (manifestu narzędzie generowania i edytowania)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
-   [MageUI.exe (Manifest narzędzie generowania i edytowania, graficzny klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
-   [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Jeśli Twoje [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] wymaga pełnego zaufania, można użyć tych samych narzędzi, aby zwiększyć żądane uprawnienia. Mimo że [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] tylko otrzyma pełnego zaufania, jeśli jest zainstalowana na i uruchomić z komputera lokalnego intranetu, lub adres URL, który znajduje się w przeglądarce zaufane lub uprawnione witryny. Jeśli aplikacja jest zainstalowana z sieci intranet lub Zaufane witryny, użytkownik otrzyma standardowego wiersza ClickOnce informacją z podwyższonym poziomem uprawnień. Użytkownik może zdecydować kontynuować, lub Anuluj instalację.  
  
 Alternatywnie można użyć modelu wdrażania zaufanych ClickOnce do wdrożenia pełnego zaufania z żadnej strefy zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) i [zabezpieczeń](../../../docs/framework/wpf/security-wpf.md).  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia](../../../docs/framework/wpf/security-wpf.md)
- [Strategia zabezpieczeń WPF — zabezpieczenia platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
