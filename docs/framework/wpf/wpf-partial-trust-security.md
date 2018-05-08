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
ms.openlocfilehash: 27934f782d6c1efde69794c73d653b57b287341f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-partial-trust-security"></a>Zabezpieczenie częściowej relacji zaufania WPF
<a name="introduction"></a> Ogólnie rzecz biorąc można ograniczyć aplikacji internetowych, z mające bezpośredni dostęp do zasobów systemowych krytyczne, aby zapobiec uszkodzeniu złośliwe. Domyślnie [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] i języki skryptów po stronie klienta nie będą mogli uzyskiwać dostęp do zasobów systemu. Ponieważ aplikacje obsługiwane w przeglądarce Windows Presentation Foundation (WPF) można uruchomić w przeglądarce, powinna być zgodna z zestawem podobne ograniczenia. Aby wymusić ograniczenia te [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] opiera się na obu [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] i [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] (zobacz [strategii zabezpieczeń WPF - zabezpieczeń platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Domyślnie aplikacje obsługiwane w przeglądarce żądań strefy internetowej [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] zestaw uprawnień, niezależnie od tego, czy są one uruchamiane z Internetu, lokalnego intranetu lub komputera lokalnego. Aplikacje uruchamiane przy użyciu innych mniej niż pełny zestaw uprawnień są określane jako działać z częściowa relacja zaufania.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] oferuje szeroką gamę pomocy technicznej, aby upewnić się, że tylu funkcji, jak to możliwe może być używany w częściowej relacji zaufania, wraz z [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)], zapewnia dodatkowe obsługę programowania częściowej relacji zaufania.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Obsługa częściowej relacji zaufania funkcja WPF](#WPF_Feature_Partial_Trust_Support)  
  
-   [Programowanie w częściowej relacji zaufania](#Partial_Trust_Programming)  
  
-   [Zarządzanie uprawnieniami](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Obsługa częściowej relacji zaufania funkcja WPF  
 W poniższej tabeli wymieniono funkcje wysokiego poziomu o Windows Presentation Foundation (WPF), które są bezpiecznie korzystać w granicach zestaw uprawnień w strefie Internet.  
  
 Tabela 1: WPF funkcje, które są bezpieczne w przypadku zaufania częściowego  
  
|Obszar funkcji|Funkcja|  
|------------------|-------------|  
|Ogólne|Okno przeglądarki<br /><br /> Witryny pochodzenia dostępu<br /><br /> IsolatedStorage (Limit to 512KB)<br /><br /> Biblioteki UIAutomation dostawców<br /><br /> Wydawanie poleceń<br /><br /> Edytory Input Method Editor (IME)<br /><br /> Pióro Tablet i odręcznego<br /><br /> Symulowane przeciągnij i upuść przy użyciu przechwytywanie myszy i Przenieś zdarzenia<br /><br /> OpenFileDialog<br /><br /> Deserializacja XAML (za pośrednictwem metoda XamlReader.Load)|  
|Integracja sieci Web|Okno dialogowe pobierania przeglądarki<br /><br /> Użytkownik zainicjował nawigacji najwyższego poziomu<br /><br /> mailto:Links<br /><br /> Parametry identyfikatora URI<br /><br /> HTTPWebRequest<br /><br /> Obsługiwane w trybie IFRAME zawartości WPF<br /><br /> Hosting w tej samej lokacji stron HTML za pomocą ramki<br /><br /> Hosting w tej samej lokacji stron HTML przy użyciu WebBrowser<br /><br /> Usługi sieci Web (ASMX)<br /><br /> Usługi sieci Web (przy użyciu programu Windows Communication Foundation)<br /><br /> Wykonywanie skryptów<br /><br /> Model obiektów dokumentu|  
|Elementy wizualne|2W i 3W<br /><br /> Animacja<br /><br /> Nośnik (witryny pochodzenia i międzydomenowego)<br /><br /> Tworzenie obrazów/Audio/wideo|  
|Odczyt|FlowDocuments<br /><br /> Dokumenty XPS<br /><br /> Osadzony & czcionek systemowych<br /><br /> CFF & czcionki TrueType|  
|Edytowanie|Sprawdzanie pisowni<br /><br /> RichTextBox<br /><br /> W postaci zwykłego tekstu oraz Obsługa schowka odręcznego<br /><br /> Wklej zainicjowane przez użytkownika<br /><br /> Kopiowanie zaznaczenia zawartości|  
|Formanty|Formanty ogólne|  
  
 Ta tabela zawiera [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] funkcje na wysokim poziomie. Aby uzyskać szczegółowe informacje, [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] omówiono uprawnienia, które są wymagane przez każdy element członkowski w [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Ponadto następujące funkcje uzyskać bardziej szczegółowe informacje dotyczące wykonywania częściowej relacji zaufania, w tym uwagi.  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (zobacz [omówienie XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)).  
  
-   Wyskakujące okienka (zobacz <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
-   Przeciąganie i upuszczanie (zobacz [przeciągania i upuszczania omówienie](../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)).  
  
-   Schowek (zobacz <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
-   Tworzenie obrazu (zobacz <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
-   Serializacja (zobacz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
-   Otwórz plik — okno dialogowe (zobacz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 W poniższej tabeli przedstawiono [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] funkcje, które nie są bezpiecznie uruchamiać w granicach Internet strefy zestawu uprawnień.  
  
 Tabela 2: WPF funkcje, które są nie bezpieczne w przypadku zaufania częściowego  
  
|Obszar funkcji|Funkcja|  
|------------------|-------------|  
|Ogólne|Okna (okien zdefiniowanych w aplikacji i okien dialogowych)<br /><br /> SaveFileDialog<br /><br /> System plików<br /><br /> Dostęp do rejestru<br /><br /> Przeciągnij i opuść<br /><br /> Serializacja XAML (za pośrednictwem XamlWriter.Save)<br /><br /> Biblioteki UIAutomation klientów<br /><br /> Dostęp do okna źródła (element HwndHost)<br /><br /> Obsługa pełnego mowy<br /><br /> Współdziałanie formularzy systemu Windows|  
|Elementy wizualne|Efekty mapy bitowej<br /><br /> Kodowanie obrazu|  
|Edytowanie|Tekst sformatowany formatu Schowka<br /><br /> Pełna obsługa w XAML|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programowanie w częściowej relacji zaufania  
 Aby uzyskać [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] aplikacje, kod, który przekracza domyślny zestaw uprawnień ma inaczej w zależności od strefy zabezpieczeń. W niektórych przypadkach użytkownik otrzyma ostrzeżenie po podjęciu próby go zainstalować. Użytkownik może wybrać kontynuować, lub Anuluj instalację. W poniższej tabeli opisano zachowanie aplikacji dla każdej strefy zabezpieczeń i co trzeba zrobić dla aplikacji do otrzymania pełnego zaufania.  
  
|Strefa zabezpieczeń|Zachowanie|Pobieranie pełnego zaufania|  
|-------------------|--------------|------------------------|  
|Komputer lokalny|Automatyczne pełnego zaufania|Nie jest potrzebne nie działanie.|  
|W intranecie i zaufanych witryn|Monituj o pełnym zaufaniu|Podpisywać XBAP przy użyciu certyfikatu, użytkownik zobaczy źródła w wierszu.|  
|Internet|Nie powiodło się "Nieudzielenia zaufania"|Zaloguj się XBAP przy użyciu certyfikatu.|  
  
> [!NOTE]
>  Zachowanie opisane w poprzedniej tabeli dotyczy pełne zaufanie XBAP, które nie są zgodne z modelu wdrażania zaufanych ClickOnce.  
  
 Ogólnie rzecz biorąc kodu, która przekracza dozwolone uprawnienia jest prawdopodobnie typowy kod współużytkowanych zarówno autonomiczne, jak i aplikacje obsługiwane w przeglądarce. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] i [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] oferuje kilka technik do zarządzania tym scenariuszu.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Wykrywanie uprawnień urzędy certyfikacji  
 W niektórych sytuacjach jest możliwe w dla udostępnionego kodu w zestawach biblioteki ma być używany przez obie aplikacje autonomiczne i [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. W takich przypadkach kodu mogą realizować funkcje, które może wymagać więcej uprawnień niż zestaw uprawnień udzielonych aplikacji. Aplikacja może wykryć, czy ma określone uprawnienia za pomocą zabezpieczeń systemu Microsoft .NET Framework. W szczególności można sprawdzić, czy ma określone uprawnienia, wywołując <xref:System.Security.CodeAccessPermission.Demand%2A> metody w wystąpieniu odpowiednie uprawnienia. Przedstawiono to w poniższym przykładzie ma kod tego zapytania dotyczące tego, czy ma możliwość zapisania pliku na dysku lokalnym:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Jeśli aplikacja nie ma odpowiednie uprawnienia, wywołanie <xref:System.Security.CodeAccessPermission.Demand%2A> zgłosi wyjątek zabezpieczeń. W przeciwnym razie udzielono uprawnień. `IsPermissionGranted` hermetyzuje to zachowanie i zwraca `true` lub `false` odpowiednio.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Bezpieczne spadek funkcjonalności  
 Jest w stanie wykryć, czy kod ma uprawnienie do wykonywania, co należy zrobić to interesujące dla kodu, który może zostać wykonany w różnych strefach. Podczas wykrywania strefa jest jedyną operacją, znacznie lepiej alternatywą dla użytkownika, jeśli to możliwe. Na przykład aplikacji pełne zaufanie zwykle umożliwia użytkownikom tworzenie plików z dowolnego miejsca chcą, gdy aplikacja częściowej relacji zaufania tylko może tworzyć pliki w magazynie izolowanym. Jeśli kod, aby utworzyć plik istnieje w zestawie, który jest współużytkowany przez zarówno aplikacje pełnego zaufania (autonomiczna), jak i częściowo zaufane aplikacje (obsługiwane w przeglądarce) i obie aplikacje mają użytkowników, aby można było utworzyć pliki, udostępniony kod powinien wykrywa, czy jest działa w pełnych lub relacji zaufania, przed utworzeniem pliku w odpowiedniej lokalizacji. Poniższy kod przedstawia jednocześnie.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 W wielu przypadkach można znaleźć alternatywne częściowej relacji zaufania.  
  
 W środowisku kontrolowanym, takich jak intranet, można zainstalować niestandardowych struktur zarządzanych przez klienta do podstawowej [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]. Te biblioteki może uruchomić kod, który wymaga pełnego zaufania, a także można odwoływać się z aplikacji, które są dozwolone tylko częściowej relacji zaufania przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (Aby uzyskać więcej informacji, zobacz [zabezpieczeń](../../../docs/framework/wpf/security-wpf.md) i [zabezpieczeń WPF Strategia - zabezpieczeń platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Wykrywanie hosta przeglądarki  
 Przy użyciu [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] do sprawdzania uprawnień to technika odpowiednie, gdy trzeba sprawdzić na podstawie na uprawnienia. Mimo że ta metoda jest zależna od połowowe wyjątków w ramach normalnego przetwarzania, co nie jest zalecane, ogólnie rzecz biorąc i może mieć problemy z wydajnością. Zamiast tego Jeśli Twoje [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] działa tylko w piaskownicy strefy Internetu, można użyć <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> właściwość, która zwraca wartość true dla [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> tylko odróżnia, czy aplikacja jest uruchomiona w przeglądarce nie który zestaw uprawnień aplikacji został uruchomiony z.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Zarządzanie uprawnieniami  
 Domyślnie [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] Uruchom z częściowej relacji zaufania (zestaw uprawnień strefy Internetu domyślną). Jednak w zależności od wymagań aplikacji jest możliwa zmiana zestawu uprawnień niż domyślny. Na przykład jeśli [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] jest uruchamiana z lokalny intranet, może korzystać z zestaw uprawnień zwiększona, które przedstawiono w poniższej tabeli.  
  
 Tabela 3: LocalIntranet i uprawnienia Internet  
  
|Uprawnienie|Atrybut|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Dostęp do serwerów DNS|Tak|Nie|  
|Zmienne środowiskowe|Odczyt|Tak|Nie|  
|Okna dialogowe pliku|Otwarcie|Tak|Tak|  
|Okna dialogowe pliku|Bez ograniczeń|Tak|Nie|  
|Izolowany magazyn|Izolacja zestawu przez użytkownika|Tak|Nie|  
|Izolowany magazyn|Nieznany izolacji|Tak|Tak|  
|Izolowany magazyn|Przydział nieograniczoną liczbę użytkowników|Tak|Nie|  
|Nośnik|Bezpieczne audio, wideo i obrazów|Tak|Tak|  
|Drukowanie|Drukowanie domyślne|Tak|Nie|  
|Drukowanie|Bezpieczne drukowanie|Tak|Tak|  
|Odbicie|Emituj|Tak|Nie|  
|Zabezpieczenia|Wykonanie kodu zarządzanego|Tak|Tak|  
|Zabezpieczenia|Uprawnienia nadanego Assert|Tak|Nie|  
|Interfejs użytkownika|Bez ograniczeń|Tak|Nie|  
|Interfejs użytkownika|Bezpieczne najwyższego poziomu z systemem windows|Tak|Tak|  
|Interfejs użytkownika|Własne Schowka|Tak|Tak|  
|Przeglądarki sieci Web|Bezpieczne ramki nawigacji w formacie HTML|Tak|Tak|  
  
> [!NOTE]
>  Wycinanie i wklejanie jest dozwolona tylko w częściowej relacji zaufania, gdy zainicjowane przez użytkownika.  
  
 Należy zwiększyć uprawnień, należy zmienić ustawienia projektu i manifestu aplikacji ClickOnce. Aby uzyskać więcej informacji, zobacz [przeglądu aplikacje przeglądarki XAML w WPF](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md). Poniższe dokumenty mogą być również przydatne.  
  
-   [Mage.exe (Generowanie manifestu i edytowania narzędzie)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
-   [MageUI.exe (Generowanie manifestu i edytowania narzędzia, klient grafiki)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
-   [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Jeśli Twoje [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] wymaga pełnego zaufania, można użyć tych samych narzędzi do zwiększenia żądanych uprawnień. Mimo że [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] tylko otrzymają pełnego zaufania, jeśli jest zainstalowana na i uruchamiana z komputera lokalnego intranetu, lub adres URL, który znajduje się w przeglądarce zaufanych lub dozwolone witryny. Jeśli aplikacja jest zainstalowana z sieci intranet lub zaufanych lokacji, zostanie wyświetlony standardowy wiersza ClickOnce informacją o podwyższonym poziomem uprawnień. Użytkownik może wybrać kontynuować, lub Anuluj instalację.  
  
 Alternatywnie można użyć modelu wdrażania zaufanych ClickOnce do wdrożenia pełnego zaufania z dowolnej strefie zabezpieczeń. Aby uzyskać więcej informacji, zobacz [zaufane Omówienie wdrożenia aplikacji](/visualstudio/deployment/trusted-application-deployment-overview) i [zabezpieczeń](../../../docs/framework/wpf/security-wpf.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia](../../../docs/framework/wpf/security-wpf.md)  
 [Strategia zabezpieczeń WPF — zabezpieczenia platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Strategia zabezpieczeń WPF — projekt zabezpieczeń](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
