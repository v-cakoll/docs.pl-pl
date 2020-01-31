---
title: Zabezpieczenia częściowej relacji zaufania
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
ms.openlocfilehash: 0d9bbcc32eea49afc6ecc713b0cf005b4434a67d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743340"
---
# <a name="wpf-partial-trust-security"></a>Zabezpieczenie częściowej relacji zaufania WPF
<a name="introduction"></a>Ogólnie rzecz biorąc, aplikacje internetowe powinny być ograniczone przez bezpośredni dostęp do krytycznych zasobów systemowych, aby zapobiec złośliwym szkodom. Domyślnie języki skryptów HTML i po stronie klienta nie mogą uzyskać dostępu do krytycznych zasobów systemowych. Ponieważ aplikacje hostowane w przeglądarce Windows Presentation Foundation (WPF) mogą być uruchamiane z przeglądarki, powinny one być zgodne z podobnym zestawem ograniczeń. Aby wymusić te ograniczenia, WPF korzysta z zabezpieczeń dostępu kodu (CAS) i ClickOnce (zobacz [strategia zabezpieczeń WPF-platforma Security](wpf-security-strategy-platform-security.md)). Domyślnie aplikacje hostowane w przeglądarce żądają zestawu uprawnień strefy Internetu, niezależnie od tego, czy są uruchamiane z Internetu, lokalnego intranetu, czy komputera lokalnego. Aplikacje działające z dowolnym elementem mniejszym niż pełny zestaw uprawnień są uznawane za działające z częściowym zaufaniem.  
  
 WPF zapewnia szeroką gamę pomocy technicznej, aby zapewnić, że możliwie największej funkcjonalności można bezpiecznie używać w częściowej relacji zaufania, a także w przypadku urzędów certyfikacji zapewnia dodatkową pomoc techniczną w zakresie programowania częściowego zaufania.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Obsługa częściowego zaufania funkcji WPF](#WPF_Feature_Partial_Trust_Support)  
  
- [Programowanie częściowej relacji zaufania](#Partial_Trust_Programming)  
  
- [Zarządzanie uprawnieniami](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Obsługa częściowego zaufania funkcji WPF  
 W poniższej tabeli wymieniono funkcje wysokiego poziomu Windows Presentation Foundation (WPF), które są bezpieczne do użycia w granicach zestawu uprawnień strefy internetowej.  
  
 Tabela 1: funkcje WPF, które są bezpieczne w częściowej relacji zaufania  
  
|Obszar funkcji|Funkcja|  
|------------------|-------------|  
|Ogólne|Okno przeglądarki<br /><br /> Dostęp do lokacji pochodzenia<br /><br /> IsolatedStorage (limit 512 KB)<br /><br /> Dostawcy UIAutomation<br /><br /> Przegląd<br /><br /> Edytory Input Method Editor (IME)<br /><br /> Pióro i atrament<br /><br /> Symulowane przeciąganie/upuszczanie przy użyciu funkcji przechwytywania i przenoszenia myszy<br /><br /> OpenFileDialog<br /><br /> Deserializacja XAML (za pośrednictwem XamlReader. Load)|  
|Integracja z siecią Web|Okno dialogowe pobierania przeglądarki<br /><br /> Nawigacja zainicjowana przez użytkownika najwyższego poziomu<br /><br /> mailto: linki<br /><br /> Parametry Uniform Resource Identifier<br /><br /> HTTPWebRequest<br /><br /> Zawartość WPF hostowana w elemencie IFRAME<br /><br /> Hosting stron HTML na tej samej stronie przy użyciu ramki<br /><br /> Hosting tych samych stron HTML witryny przy użyciu przeglądarki WebBrowser<br /><br /> Usługi sieci Web (ASMX)<br /><br /> Usługi sieci Web (przy użyciu Windows Communication Foundation)<br /><br /> Obsługa skryptów<br /><br /> Document Object Model|  
|Wizualizacji|2D i 3W<br /><br /> Animacja<br /><br /> Nośnik (lokacja źródłowa i międzydomenowa)<br /><br /> Przetwarzanie obrazów/audio/wideo|  
|Odczytu|FlowDocuments<br /><br /> Dokumenty XPS<br /><br /> Osadzone & czcionki systemowe<br /><br /> CFF & czcionki TrueType|  
|Edytowanie|Sprawdzanie pisowni<br /><br /> RichTextBox<br /><br /> Obsługa przezroczystego tekstu i schowka<br /><br /> Wklej zainicjowany przez użytkownika<br /><br /> Kopiowanie wybranej zawartości|  
|Formanty|Formanty ogólne|  
  
 Ta tabela obejmuje funkcje WPF na wysokim poziomie. Aby uzyskać bardziej szczegółowe informacje, Windows SDK dokumentuje uprawnienia, które są wymagane przez każdy element członkowski w WPF. Ponadto poniższe funkcje zawierają bardziej szczegółowe informacje dotyczące częściowego wykonywania zaufania, w tym zagadnienia specjalne.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (zobacz [XAML — Omówienie (WPF)](../../desktop-wpf/fundamentals/xaml.md)).  
  
- Okna podręczne (zobacz <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
- Przeciągnij i upuść (zobacz [Przegląd przeciągania i upuszczania](./advanced/drag-and-drop-overview.md)).  
  
- Schowek (zobacz <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
- Imaging (zobacz <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
- Serializacja (zobacz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
- Otwórz plik — okno dialogowe (zobacz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 W poniższej tabeli opisano funkcje WPF, które nie są bezpieczne do uruchomienia w ramach limitów zestawu uprawnień strefy internetowej.  
  
 Tabela 2: funkcje WPF, które nie są bezpieczne w częściowej relacji zaufania  
  
|Obszar funkcji|Funkcja|  
|------------------|-------------|  
|Ogólne|Okno (zdefiniowane przez aplikację okna i okna dialogowe)<br /><br /> SaveFileDialog<br /><br /> System plików<br /><br /> Dostęp do rejestru<br /><br /> Przeciągnij i opuść<br /><br /> Serializacja XAML (za pośrednictwem XamlWriter. Save)<br /><br /> UIAutomation klienci<br /><br /> Dostęp do okna źródłowego (HwndHost)<br /><br /> Pełna pomoc techniczna mowy<br /><br /> Współdziałanie Windows Forms|  
|Wizualizacji|Efekty mapy bitowej<br /><br /> Kodowanie obrazu|  
|Edytowanie|Schowek formatu tekstu sformatowanego<br /><br /> Pełna obsługa XAML|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programowanie częściowej relacji zaufania  
 W przypadku aplikacji XBAP kod, który przekracza domyślny zestaw uprawnień, będzie miał inne zachowanie w zależności od strefy zabezpieczeń. W niektórych przypadkach podczas próby zainstalowania tego użytkownika zostanie wyświetlone ostrzeżenie. Użytkownik może wybrać opcję kontynuowania lub anulowania instalacji. W poniższej tabeli opisano zachowanie aplikacji dla każdej strefy zabezpieczeń i czynności, które należy wykonać, aby aplikacja mogła uzyskać pełne zaufanie.  
  
|Strefa zabezpieczeń|Zachowanie|Pobieranie pełnego zaufania|  
|-------------------|--------------|------------------------|  
|Komputer lokalny|Automatyczne pełne zaufanie|Nie trzeba wykonywać żadnych czynności.|  
|Intranet i Zaufane witryny|Monituj o pełne zaufanie|Podpisz element XBAP przy użyciu certyfikatu, aby użytkownik widział źródło w monicie.|  
|Internet|Niepowodzenie z "zaufaniem nieudzielonym"|Podpisz element XBAP przy użyciu certyfikatu.|  
  
> [!NOTE]
> Zachowanie opisane w poprzedniej tabeli służy do pełnego zaufania XBAP, które nie są zgodne z zaufanym modelem wdrażania ClickOnce.  
  
 Ogólnie rzecz biorąc, kod, który może przekroczyć dozwolone uprawnienia, prawdopodobnie będzie typowym kodem, który jest współużytkowany przez aplikacje autonomiczne i hostowane w przeglądarce. Urzędy certyfikacji i WPF oferują kilka technik związanych z zarządzaniem tym scenariuszem.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Wykrywanie uprawnień przy użyciu urzędów certyfikacji  
 W niektórych sytuacjach istnieje możliwość, że współużytkowany kod w zestawach bibliotek ma być używany przez aplikacje autonomiczne i XBAP. W takich przypadkach kod może wykonywać funkcje, które mogą wymagać większej liczby uprawnień niż przyznany zestaw uprawnień aplikacji. Aplikacja może wykryć, czy ma określone uprawnienie przy użyciu zabezpieczeń Microsoft .NET Framework. W konkretnym przypadku można sprawdzić, czy ma określone uprawnienie przez wywołanie metody <xref:System.Security.CodeAccessPermission.Demand%2A> w wystąpieniu żądanego uprawnienia. Jest to pokazane w poniższym przykładzie, który zawiera kod, który umożliwia zaoszczędzenie pliku na dysku lokalnym:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Jeśli aplikacja nie ma żądanego uprawnienia, wywołanie do <xref:System.Security.CodeAccessPermission.Demand%2A> spowoduje zgłoszenie wyjątku zabezpieczeń. W przeciwnym razie przyznano uprawnienie. `IsPermissionGranted` hermetyzuje to zachowanie i zwraca odpowiednio `true` lub `false`.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Bezpieczne obniżenie funkcjonalności  
 Możliwość wykrycia, czy kod ma uprawnienia do wykonywania czynności, które należy wykonać, jest interesujący dla kodu, który może być wykonywany z różnych stref. Wykrywanie strefy jest jednym z nich, dlatego znacznie lepiej jest udostępnić alternatywę dla użytkownika, jeśli jest to możliwe. Na przykład aplikacja z pełnym zaufaniem zwykle umożliwia użytkownikom tworzenie plików w dowolnym miejscu, podczas gdy aplikacja częściowej zaufania może tworzyć tylko pliki w izolowanym magazynie. Jeśli kod, który ma zostać utworzony, istnieje w zestawie, który jest współużytkowany przez zarówno aplikacje pełnego zaufania (autonomiczne), jak i częściowe zaufanie (hostowane w przeglądarce), a obie aplikacje chcą, aby użytkownicy mogli tworzyć pliki, kod współużytkowany powinien wykryć, czy jest Uruchamianie w częściowej lub pełnej relacji zaufania przed utworzeniem pliku w odpowiedniej lokalizacji. Poniższy kod ilustruje obie.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 W wielu przypadkach powinno być możliwe znalezienie częściowej alternatywy zaufania.  
  
 W środowisku kontrolowanym, takim jak intranet, niestandardowe platformy zarządzane można zainstalować w ramach bazy klientów w ramach globalnej pamięci podręcznej zestawów (GAC). Te biblioteki mogą wykonywać kod, który wymaga pełnego zaufania, i mogą być przywoływane z aplikacji, które są dozwolone tylko częściowej relacji zaufania przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (Aby uzyskać więcej informacji, zobacz temat [Security](security-wpf.md) and [WPF Security strategi-platform Security](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Wykrywanie hosta przeglądarki  
 Korzystanie z urzędów certyfikacji do sprawdzania uprawnień jest odpowiednią techniką w przypadku konieczności sprawdzenia poszczególnych uprawnień. Chociaż ta technika jest zależna od przechwytywania wyjątków w ramach normalnego przetwarzania, co nie jest ogólnie zalecane i może mieć problemy z wydajnością. Zamiast tego, jeśli aplikacja przeglądarki XAML (XBAP) działa tylko w obszarze piaskownicy strefy internetowej, można użyć właściwości <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>, która zwraca wartość true dla aplikacji przeglądarki XAML (XBAP).  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> odróżnia tylko, czy aplikacja działa w przeglądarce, a nie zestaw uprawnień, z którymi aplikacja działa.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Zarządzanie uprawnieniami  
 Domyślnie aplikacje XBAP działają z częściowym zaufaniem (ustawienie domyślne strefy internetowej). Jednakże, w zależności od wymagań aplikacji, można zmienić zestaw uprawnień z domyślnego. Na przykład jeśli aplikacje XBAP są uruchamiane z lokalnego intranetu, może skorzystać z większego zestawu uprawnień, który jest przedstawiony w poniższej tabeli.  
  
 Tabela 3: LocalIntranet i uprawnienia internetowe  
  
|Uprawnienie|Atrybut|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|systemem DNS,|Dostęp do serwerów DNS|Tak|Nie|  
|Zmienne środowiskowe|Odczyt|Tak|Nie|  
|Okna dialogowe plików|Otwarcie|Tak|Tak|  
|Okna dialogowe plików|Nieograniczone|Tak|Nie|  
|Izolowany magazyn|Izolacja zestawu przez użytkownika|Tak|Nie|  
|Izolowany magazyn|Nieznana izolacja|Tak|Tak|  
|Izolowany magazyn|Nieograniczony limit przydziału użytkowników|Tak|Nie|  
|Nośnik|Bezpieczne audio, wideo i obrazy|Tak|Tak|  
|Drukowanie|Drukowanie domyślne|Tak|Nie|  
|Drukowanie|Bezpieczne drukowanie|Tak|Tak|  
|Odbicie|Wysyłać|Tak|Nie|  
|Zabezpieczenia|Wykonywanie kodu zarządzanego|Tak|Tak|  
|Zabezpieczenia|Potwierdzenie przyznanych uprawnień|Tak|Nie|  
|Interfejs użytkownika|Nieograniczone|Tak|Nie|  
|Interfejs użytkownika|Bezpieczne okna najwyższego poziomu|Tak|Tak|  
|Interfejs użytkownika|Własny schowek|Tak|Tak|  
|Przeglądarki sieci Web|Bezpieczne nawigowanie po ramce do kodu HTML|Tak|Tak|  
  
> [!NOTE]
> Operacje wycinania i wklejania są dozwolone tylko w częściowej relacji zaufania po zainicjowaniu użytkownika.  
  
 Jeśli musisz zwiększyć uprawnienia, musisz zmienić ustawienia projektu i manifest aplikacji ClickOnce. Aby uzyskać więcej informacji, zobacz [Omówienie aplikacji w przeglądarce WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md). Pomocne mogą być również następujące dokumenty.  
  
- Program [Mage. exe (narzędzie tworzenia i edycji manifestów)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI. exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Jeśli Twoje aplikacje XBAP wymagają pełnego zaufania, możesz użyć tych samych narzędzi, aby zwiększyć żądane uprawnienia. Chociaż usługa XBAP będzie otrzymywać pełne zaufanie, jeśli jest zainstalowana na komputerze lokalnym, w intranecie lub z adresu URL, który znajduje się na liście zaufanych lub dozwolonych witryn w przeglądarce. Jeśli aplikacja jest zainstalowana z intranetu lub zaufanej witryny, użytkownik otrzyma standardowy monit ClickOnce o podniesionych uprawnieniach. Użytkownik może wybrać opcję kontynuowania lub anulowania instalacji.  
  
 Alternatywnie można użyć zaufanego modelu wdrażania ClickOnce do pełnego wdrożenia zaufania z dowolnej strefy zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview) i [zabezpieczenia](security-wpf.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia](security-wpf.md)
- [Strategia zabezpieczeń WPF — zabezpieczenia platformy](wpf-security-strategy-platform-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
