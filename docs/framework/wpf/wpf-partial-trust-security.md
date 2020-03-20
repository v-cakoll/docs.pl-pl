---
title: Częściowe zabezpieczenia zaufania
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
ms.openlocfilehash: 99c7d9cfae2b137053ca77d9e3d7055b4674ce5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174579"
---
# <a name="wpf-partial-trust-security"></a>Zabezpieczenie częściowej relacji zaufania WPF
<a name="introduction"></a>Ogólnie rzecz biorąc, aplikacje internetowe powinny mieć ograniczony dostęp do krytycznych zasobów systemowych, aby zapobiec złośliwym uszkodzeniom. Domyślnie języki skryptów html i po stronie klienta nie są w stanie uzyskać dostępu do krytycznych zasobów systemowych. Ponieważ aplikacje hostowane przez przeglądarkę Programu Windows Presentation Foundation (WPF) mogą być uruchamiane z przeglądarki, powinny one być zgodne z podobnym zestawem ograniczeń. Aby wymusić te ograniczenia, WPF WPF opiera się zarówno na zabezpieczeniach dostępu do kodu (CAS), jak i clickonce (zobacz [WPF Security Strategy - Platform Security](wpf-security-strategy-platform-security.md)). Domyślnie aplikacje hostowane przez przeglądarkę żądają zestawu uprawnień CAS strefy internetowej, niezależnie od tego, czy są one uruchamiane z Internetu, lokalnego intranetu czy komputera lokalnego. Aplikacje, które działają z niczego mniej niż pełny zestaw uprawnień mówi się, że są uruchomione z częściowego zaufania.  
  
 WPF WPF zapewnia szeroką gamę obsługi, aby zapewnić, że jak najwięcej funkcji, jak to możliwe, mogą być bezpiecznie używane w częściowym zaufaniu i wraz z CAS, zapewnia dodatkową obsługę programowanie częściowego zaufania.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Funkcja częściowego zaufania funkcji WPF](#WPF_Feature_Partial_Trust_Support)  
  
- [Programowanie częściowego zaufania](#Partial_Trust_Programming)  
  
- [Zarządzanie uprawnieniami](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>
## <a name="wpf-feature-partial-trust-support"></a>Funkcja częściowego zaufania funkcji WPF  
 W poniższej tabeli wymieniono funkcje wysokiego poziomu programu Windows Presentation Foundation (WPF), które można bezpiecznie używać w granicach zestawu uprawnień strefy internetowej.  
  
 Tabela 1: Funkcje WPF, które są bezpieczne w częściowym zaufaniu  
  
|Obszar charakterystyczny|Funkcja|  
|------------------|-------------|  
|Ogólne|Okno przeglądarki<br /><br /> Strona origin access<br /><br /> Izolowanestorage (limit 512 KB)<br /><br /> Dostawcy uiautomation<br /><br /> Komendanta<br /><br /> Edytory Input Method Editor (IME)<br /><br /> Rysik i atrament na tablecie<br /><br /> Symulowane przeciąganie/upuszczanie za pomocą przechwytywania myszy i przenoszenia zdarzeń<br /><br /> Openfiledialog<br /><br /> Deserializacja XAML (za pośrednictwem XamlReader.Load)|  
|Integracja z siecią Web|Okno dialogowe pobierania przeglądarki<br /><br /> Nawigacja inicjowana przez użytkownika najwyższego poziomu<br /><br /> mailto:linki<br /><br /> Jednolite parametry identyfikatora zasobu<br /><br /> HttpWebRequest (HttpWebRequest)<br /><br /> Zawartość WPF hostowana w elementów IFRAME<br /><br /> Hostowanie stron HTML tej samej witryny przy użyciu ramki<br /><br /> Hosting stron HTML tej samej witryny za pomocą WebBrowser<br /><br /> Usługi sieci Web (ASMX)<br /><br /> Usługi sieci Web (przy użyciu programu Windows Communication Foundation)<br /><br /> Wykonywanie skryptów<br /><br /> Model obiektu dokumentu|  
|Wizualizacje|2D i 3D<br /><br /> Animacja<br /><br /> Media (strona pochodzenia i międzydomenowe)<br /><br /> Obrazowanie/audio/wideo|  
|Czytanie|FlowDocuments<br /><br /> Dokumenty XPS<br /><br /> Wbudowane czcionki systemowe &<br /><br /> Czcionki CFF & TrueType|  
|Edytowanie|Sprawdzanie pisowni<br /><br /> RichTextBox<br /><br /> Obsługa zwykłego tekstu i schowka z atramentem<br /><br /> Wklej zainicjowane przez użytkownika<br /><br /> Kopiowanie wybranej zawartości|  
|Kontrolki|Kontrole ogólne|  
  
 Ta tabela obejmuje funkcje WPF na wysokim poziomie. Aby uzyskać bardziej szczegółowe informacje, windows SDK dokumenty uprawnienia, które są wymagane przez każdego członka w WPF. Ponadto następujące funkcje mają bardziej szczegółowe informacje dotyczące częściowego wykonywania zaufania, w tym specjalne zagadnienia.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](patrz [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)).  
  
- Wyskakujące <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>okienka (patrz ).  
  
- Przeciąganie i upuszczanie (zobacz [Omówienie przeciągania i upuszczania).](./advanced/drag-and-drop-overview.md)  
  
- Schowek <xref:System.Windows.Clipboard?displayProperty=nameWithType>(patrz ).  
  
- Obrazowanie <xref:System.Windows.Controls.Image?displayProperty=nameWithType>obrazu (patrz ).  
  
- Serializacja <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>(patrz <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>, ).  
  
- Okno dialogowe Otwieranie pliku (patrz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 W poniższej tabeli przedstawiono funkcje WPF, które nie są bezpieczne do uruchomienia w granicach zestawu uprawnień strefy internet.  
  
 Tabela 2: Funkcje WPF, które nie są bezpieczne w częściowym zaufaniu  
  
|Obszar charakterystyczny|Funkcja|  
|------------------|-------------|  
|Ogólne|Okno (okna zdefiniowane przez aplikację i okna dialogowe)<br /><br /> Savefiledialog<br /><br /> System plików<br /><br /> Dostęp do rejestru<br /><br /> Przeciągnij i opuść<br /><br /> Serializacja XAML (za pośrednictwem XamlWriter.Save)<br /><br /> Klienci uiautomation<br /><br /> Dostęp do okna źródłowego (HwndHost)<br /><br /> Pełna obsługa mowy<br /><br /> Interoperacyjność formularzy systemu Windows|  
|Wizualizacje|Efekty mapy bitowej<br /><br /> Kodowanie obrazów|  
|Edytowanie|Schowek w formacie tekstu sformatowanym<br /><br /> Pełna obsługa XAML|  
  
<a name="Partial_Trust_Programming"></a>
## <a name="partial-trust-programming"></a>Programowanie częściowego zaufania  
 W przypadku aplikacji XBAP kod, który przekracza domyślny zestaw uprawnień będzie miał różne zachowanie w zależności od strefy zabezpieczeń. W niektórych przypadkach użytkownik otrzyma ostrzeżenie podczas próby jego zainstalowania. Użytkownik może kontynuować lub anulować instalację. W poniższej tabeli opisano zachowanie aplikacji dla każdej strefy zabezpieczeń i co należy zrobić, aby aplikacja otrzymała pełne zaufanie.  
  
|Strefa zabezpieczeń|Zachowanie|Pełne zaufanie|  
|-------------------|--------------|------------------------|  
|Komputer lokalny|Automatyczne pełne zaufanie|Nie są potrzebne żadne działania.|  
|Intranet i zaufane witryny|Monitowanie o pełne zaufanie|Podpisz xbap za pomocą certyfikatu, aby użytkownik widział źródło w wierszu polecenia.|  
|Internet|Niepowodzenie z "Zaufanie nie jest przyznane"|Podpisz xbap za pomocą certyfikatu.|  
  
> [!NOTE]
> Zachowanie opisane w poprzedniej tabeli jest dla pełnego zaufania XBAPs, które nie są zgodne z ClickOnce modelu zaufanego wdrożenia.  
  
 Ogólnie rzecz biorąc kod, który może przekroczyć dozwolone uprawnienia może być wspólny kod, który jest współużytkowany między aplikacjami autonomicznymi i hostowanymi w przeglądarce. CAS i WPF oferują kilka technik zarządzania tym scenariuszem.  
  
<a name="Detecting_Permissions_using_CAS"></a>
### <a name="detecting-permissions-using-cas"></a>Wykrywanie uprawnień przy użyciu cas  
 W niektórych sytuacjach jest możliwe dla udostępnionego kodu w zestawach biblioteki do użycia zarówno przez aplikacje autonomiczne i XBAPs. W takich przypadkach kod może wykonywać funkcje, które mogą wymagać więcej uprawnień niż aplikacja przyznane uprawnienia pozwala. Aplikacja może wykryć, czy ma określone uprawnienia przy użyciu zabezpieczeń programu Microsoft .NET Framework. W szczególności można sprawdzić, czy ma określone <xref:System.Security.CodeAccessPermission.Demand%2A> uprawnienia, wywołując metodę w wystąpieniu żądanego uprawnienia. Jest to pokazane w poniższym przykładzie, który zawiera kod, który pyta, czy ma możliwość zapisania pliku na dysku lokalnym:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Jeśli aplikacja nie ma żądanego uprawnienia, <xref:System.Security.CodeAccessPermission.Demand%2A> wywołanie zgłosić wyjątek zabezpieczeń. W przeciwnym razie uprawnienie zostało przyznane. `IsPermissionGranted`hermetyzuje to zachowanie `true` `false` i zwraca lub, w stosownych przypadkach.  
  
<a name="Graceful_Degradation_of_Functionality"></a>
### <a name="graceful-degradation-of-functionality"></a>Wdzięczna degradacja funkcjonalności  
 Możliwość wykrycia, czy kod ma uprawnienia do wykonywania tego, co musi zrobić, jest interesująca dla kodu, który może być wykonywany z różnych stref. Podczas wykrywania strefy to jedno, o wiele lepiej jest zapewnić alternatywę dla użytkownika, jeśli to możliwe. Na przykład aplikacja pełnego zaufania zazwyczaj umożliwia użytkownikom tworzenie plików w dowolnym miejscu, podczas gdy aplikacja częściowego zaufania może tworzyć tylko pliki w izolowanym magazynie. Jeśli kod do utworzenia pliku istnieje w zestawie, który jest współużytkowany zarówno przez aplikacje pełnego zaufania (autonomiczne), jak i aplikacje z częściowym zaufaniem (hostowane przez przeglądarkę), a obie aplikacje chcą, aby użytkownicy mogli tworzyć pliki, udostępniony kod powinien wykryć, czy jest częściowego lub pełnego zaufania przed utworzeniem pliku w odpowiedniej lokalizacji. Poniższy kod demonstruje oba.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 W wielu przypadkach powinieneś być w stanie znaleźć alternatywę częściowego zaufania.  
  
 W kontrolowanym środowisku, takim jak intranet, niestandardowe struktury zarządzane mogą być instalowane w całej bazie klientów w globalnej pamięci podręcznej zestawów (GAC). Biblioteki te mogą wykonywać kod, który wymaga pełnego zaufania i odwoływać się <xref:System.Security.AllowPartiallyTrustedCallersAttribute> do aplikacji, które są dozwolone tylko częściowe zaufanie przy użyciu (aby uzyskać więcej informacji, zobacz [Bezpieczeństwo](security-wpf.md) i [WPF Security Strategy - Platform Security](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>
### <a name="browser-host-detection"></a>Wykrywanie hosta przeglądarki  
 Za pomocą CAS, aby sprawdzić uprawnienia jest odpowiednią techniką, gdy trzeba sprawdzić na podstawie uprawnień. Mimo, że ta technika zależy od przechwytywania wyjątków jako część normalnego przetwarzania, który nie jest ogólnie zalecane i może mieć problemy z wydajnością. Zamiast tego jeśli aplikacja przeglądarki XAML (XBAP) działa tylko w strefie <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> internetowej izolowania, można użyć właściwości, która zwraca true dla aplikacji przeglądarki XAML (XBAPs).  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>rozróżnia tylko, czy aplikacja jest uruchomiona w przeglądarce, a nie zestaw uprawnień, z którymi aplikacja jest uruchomiona.  
  
<a name="Managing_Permissions"></a>
## <a name="managing-permissions"></a>Zarządzanie uprawnieniami  
 Domyślnie XBAPs są uruchamiane z częściowym zaufaniem (domyślny zestaw uprawnień strefy internetowej). Jednak w zależności od wymagań aplikacji, istnieje możliwość zmiany zestawu uprawnień z domyślnego. Na przykład jeśli XBAPs jest uruchamiany z lokalnego intranetu, może skorzystać ze zwiększonego zestawu uprawnień, który jest wyświetlany w poniższej tabeli.  
  
 Tabela 3: Uprawnienia lokalneintranet i internet  
  
|Uprawnienie|Atrybut|Localintranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Dostęp do serwerów DNS|Tak|Nie|  
|Zmienne środowiskowe|Odczyt|Tak|Nie|  
|Okna dialogowe plików|Otwarcie|Tak|Tak|  
|Okna dialogowe plików|Bez ograniczeń|Tak|Nie|  
|Izolowany magazyn|Izolacja zestawu przez użytkownika|Tak|Nie|  
|Izolowany magazyn|Nieznana izolacja|Tak|Tak|  
|Izolowany magazyn|Nieograniczony przydział użytkowników|Tak|Nie|  
|Multimedia|Bezpieczny dźwięk, wideo i obrazy|Tak|Tak|  
|Drukowanie|Drukowanie domyślne|Tak|Nie|  
|Drukowanie|Bezpieczne drukowanie|Tak|Tak|  
|Odbicie|Emitować|Tak|Nie|  
|Zabezpieczenia|Wykonanie kodu zarządzanego|Tak|Tak|  
|Zabezpieczenia|Potwierdzanie przyznanych uprawnień|Tak|Nie|  
|Interfejs użytkownika|Bez ograniczeń|Tak|Nie|  
|Interfejs użytkownika|Bezpieczne okna najwyższego poziomu|Tak|Tak|  
|Interfejs użytkownika|Własny Schowek|Tak|Tak|  
|Przeglądarka internetowa|Bezpieczna nawigacja w ramce do html|Tak|Tak|  
  
> [!NOTE]
> Wytnij i wklej jest dozwolone tylko w częściowym zaufaniu, gdy użytkownik zainicjował.  
  
 Jeśli chcesz zwiększyć uprawnienia, należy zmienić ustawienia projektu i ClickOnce manifest aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie aplikacji przeglądarki WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md). Pomocne mogą być również następujące dokumenty.  
  
- [Mage.exe (Narzędzie do generowania manifestów i edycji)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI.exe (narzędzie do generowania manifestu i edycji, klient graficzny).](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
  
- [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Jeśli xbap wymaga pełnego zaufania, można użyć tych samych narzędzi, aby zwiększyć żądane uprawnienia. Mimo że xbap otrzyma pełne zaufanie tylko wtedy, gdy jest zainstalowany i uruchomiony z komputera lokalnego, intranetu lub z adresu URL, który jest wymieniony w zaufanych lub dozwolonych witrynach przeglądarki. Jeśli aplikacja jest zainstalowana z intranetu lub zaufanej witryny, użytkownik otrzyma standardowy monit ClickOnce informujący o podwyższonych uprawnieniach. Użytkownik może kontynuować lub anulować instalację.  
  
 Alternatywnie można użyć modelu ClickOnce zaufanego wdrożenia dla pełnego wdrożenia zaufania z dowolnej strefy zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview) i [zabezpieczenia](security-wpf.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia](security-wpf.md)
- [Strategia zabezpieczeń WPF — zabezpieczenia platformy](wpf-security-strategy-platform-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
