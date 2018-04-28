---
title: Strategia zabezpieczeń WPF - zabezpieczenia platformy
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61197255c11745c2c3f6f60db084b96dc812cb00
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="wpf-security-strategy---platform-security"></a>Strategia zabezpieczeń WPF - zabezpieczenia platformy
Gdy [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] udostępnia wiele usług zabezpieczeń on również korzysta z funkcji zabezpieczeń w podstawowej platformy, który zawiera system operacyjny, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], i [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)]. Te warstwy połączyć zapewnienie [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] model zabezpieczeń silne, obrony zabezpieczeń, podejmowanych w celu uniknięcia dowolnego pojedynczego punktu awarii, jak pokazano na poniższej ilustracji:  
  
 ![Ilustracja przedstawiająca zabezpieczenia WPF](../../../docs/framework/wpf/media/windowplatformsecurity.PNG "windowplatformsecurity")  
  
 W pozostałej części w tym temacie omówiono funkcje w każdym z tych warstw, które odnoszą się do [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] specjalnie.  
  

  
<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>Zabezpieczenia systemu operacyjnego  
 Minimalny poziom systemu operacyjnego, który jest wymagany przez [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jest [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]. Najważniejsza część [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] zawiera kilka funkcji zabezpieczeń, które stanowią podstawę zabezpieczeń dla wszystkich aplikacji systemu Windows, łącznie z tymi skompilowanej za pomocą [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] zawiera funkcje zabezpieczeń [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] i rozszerza je dalej. W tym temacie omówiono szerokość te funkcje zabezpieczeń, które są ważne dla [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], a także [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] integruje się z nimi w celu zapewnienia dalszego obrony zabezpieczeń.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Oprócz ogólnego przeglądu i wzmocnienie systemu Windows, istnieją trzy najważniejsze funkcje z [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] który omówimy w tym temacie:  
  
-   Kompilacja/GS  
  
-   [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>Kompilacja/GS  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] zapewnia ochronę przez kompilację wiele podstawowe biblioteki systemu, wraz ze wszystkimi [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zależności, takich jak [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], aby ułatwić uniknięcie przepełnienia buforu. Jest to osiągane przy użyciu parametru/GS z wiersza polecenia kompilatora C/C++. Mimo że można jawnie uniknąć przepełnienia buforu, / GS kompilacji zawiera przykład obrony zabezpieczeń przed potencjalnych luk w zabezpieczeniach przypadkowego lub umyślnego tworzonych przez nich.  
  
 W przeszłości przepełnienia buforu zostały Przyczyna wielu lukami w zabezpieczeniach dużym znaczeniu. Przepełnienie buforu występuje, gdy osoba atakująca wykorzystuje kodu, który umożliwia uruchomienie złośliwego kodu, który zapisuje poza granice tego buforu. Pozwala to następnie osobie atakującej przejąć kontrolę nad procesu wykonuje kod, zastępując adres zwrotny funkcji, aby spowodować wykonanie kodu przez osobę atakującą. Wynik jest złośliwy kod, który wykonuje dowolny kod takie same uprawnienia jak proces hijacked.  
  
 Na wysokim poziomie Flaga kompilator/GS chroni przed niektórych potencjalnego przepełnienia buforu przez wstrzykiwanie plik cookie zabezpieczeń specjalne chronić adres zwrotny funkcji, która ma lokalnego ciągu buforów. Po powrocie z funkcji plik cookie zabezpieczeń jest porównywana z poprzedniej wartości. Jeśli wartość została zmieniona, może wystąpić przepełnienie buforu, a proces jest zatrzymany warunek błędu. Zatrzymywanie procesu uniemożliwia wykonywanie potencjalnie złośliwego kodu. Zobacz [/GS (Sprawdzanie zabezpieczeń bufora)](http://msdn.microsoft.com/library/8dbf701c.aspx) więcej szczegółów.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jest skompilowana przy użyciu flagi/GS można dodać jeszcze inną warstwa obrony w celu [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Ulepszenia aktualizacji systemu Microsoft Windows  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] Ulepszono również w [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] w celu uproszczenia procesu pobierania i instalowania aktualizacji. Te zmiany znacząco poprawić zabezpieczenia [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] klientów dzięki zapewnieniu, że ich systemy są aktualne, szczególnie w odniesieniu do aktualizacji zabezpieczeń.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Użytkownicy [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] będzie korzystać z ulepszeń dodatkowych zabezpieczeń systemu operacyjnego "Uprawnień dostępu użytkownika" Sprawdzanie integralności kodu, w tym i uprawnień izolacji.  
  
#### <a name="user-account-control-uac"></a>Kontrola konta użytkownika (UAC)  
 Obecnie użytkownicy systemu Windows często uruchomione z uprawnieniami administratora, ponieważ wiele aplikacji wymaga ich instalacji lub wykonywania, lub obie. Możliwość zapisu domyślne ustawienia aplikacji w rejestrze jest jednym z przykładów.  
  
 Uruchomione z uprawnieniami administratora naprawdę oznacza, że aplikacje wykonywania z procesów, które są przyznawane uprawnienia administratora. Wpływ zabezpieczeń jest złośliwy kod, który hijacks proces uruchomiony z uprawnieniami administratora automatycznie odziedziczy te uprawnienia, łącznie z dostępem do zasobów systemowych krytyczne.  
  
 Jednym ze sposobów ochrony przed zagrożeniem bezpieczeństwa jest uruchomienie aplikacji z najmniejszą ilością uprawnień, które są wymagane. To jest znany jako zasadą najniższych uprawnień i jest funkcją core [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] systemu operacyjnego. Ta funkcja jest wywoływana kontroli konta użytkownika (UAC) i jest używany przez [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] funkcji Kontrola konta użytkownika na dwa sposoby klucza:  
  
-   Aby uruchamiać większość aplikacji z uprawnieniami funkcji Kontrola konta użytkownika domyślnie, nawet jeśli użytkownik jest administratorem; tylko aplikacje, które są wymagane uprawnienia administratora zostanie uruchomiony z uprawnieniami administratora. Do uruchamiania z uprawnieniami administracyjnymi, aplikacje muszą być jawnie oznaczone w jednej aplikacji manifestu lub jako wpis w zasadach zabezpieczeń.  
  
-   Aby zapewnić zgodność rozwiązań, takich jak wirtualizacji. Na przykład wiele aplikacji próbuje zapisać ograniczeniami lokalizacji C:\Program Files. Dla aplikacji wykonywanych w ramach kontroli konta użytkownika lokalizacji użytkownika alternatywnych istnieje, która nie wymaga uprawnień administratora do zapisu. Dla aplikacji do uruchamiania funkcji Kontrola konta użytkownika C:\Program Files Wirtualizuje funkcji Kontrola konta użytkownika, dzięki czemu aplikacje, które wydaje się, że są one zapisywania do niego są faktycznie zapisu do lokalizacji alternatywnej, na użytkownika. Tego rodzaju pracy zgodności umożliwia uruchamianie wielu aplikacji, które wcześniej nie można uruchomić w funkcji kontroli konta użytkownika systemu operacyjnego.  
  
#### <a name="code-integrity-checks"></a>Sprawdzanie integralności kodu  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] zawiera bardziej sprawdzania integralności kodu zapobiega jest dodane do systemu plików lub jądra w czasie ładowania/uruchamiania złośliwego kodu. To wykracza poza ochrony plików systemowych.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Proces ograniczone prawa aplikacje obsługiwane w przeglądarce  
 Obsługiwane w przeglądarce [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje wykonywane w piaskownicy strefy Internet. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Integracja z [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] rozszerza tę ochronę z obsługą dodatkowych.  
  
#### <a name="internet-explorer-6-service-pack-2-and-internet-explorer-7-for-xp"></a>Internet Explorer 6 Service Pack 2 i przeglądarki Internet Explorer 7 dla XP  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] wykorzystuje zabezpieczeń systemu operacyjnego przez ograniczenie uprawnień procesów dla [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] dla dalszego ochrony. Przed przeglądarki hostowanej [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacja jest uruchamiana, system operacyjny tworzy procesu hosta, która spowoduje usunięcie niepotrzebnych uprawnień z tokenu procesu. Przykłady uprawnień, które zostały usunięte obejmują możliwość zamknąć komputera użytkownika, sterowniki obciążenia i dostęp do odczytu do wszystkich plików na komputerze.  
  
#### <a name="internet-explorer-7-for-vista"></a>Internet Explorer 7, Vista  
 W [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje uruchamiane w trybie chronionym. W szczególności [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] Uruchom z integralnością średniego poziomu.  
  
#### <a name="defense-in-depth-layer"></a>Warstwy zabezpieczeń obrony  
 Ponieważ [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] są zazwyczaj piaskownicy za pośrednictwem Internetu zestaw uprawnień strefy, usuwanie tych uprawnień nie uszkodzić [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] z punktu widzenia zgodności. Zamiast tego jest tworzony dodatkową warstwę zabezpieczeń obrony; Jeśli piaskownicy aplikacji jest w stanie wykorzystać innych warstw i przejąć proces, proces będzie nadal tylko ma ograniczone uprawnienia.  
  
 Zobacz [przy użyciu konta użytkownika uprzywilejowanego najmniej](http://technet.microsoft.com/library/cc700846.aspx).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Typowe zabezpieczeń środowiska wykonawczego języka  
 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] Oferuje wiele korzyści klucza zabezpieczeń, które obejmują sprawdzania poprawności i weryfikacji, [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]i metodologii krytyczne zabezpieczeń.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Sprawdzanie poprawności i weryfikacji  
 Zapewnienie izolacji zestawu i integralności, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] używa procesu sprawdzania poprawności. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] Sprawdzanie poprawności zapewnia, że zestawy są izolowane weryfikując ich formacie przenośnego pliku wykonawczego (PE) adresów, które wskazują poza zestaw. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] Sprawdzanie poprawności weryfikuje również integralność metadanych, który jest osadzony w zestawie.  
  
 Aby zapewnić bezpieczeństwo typów, pomagać w zapobieganiu typowych problemów z zabezpieczeniami (np. przepełnienie buforu) i Włącz sandboxing za pośrednictwem izolacji procesu podrzędnego [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] zabezpieczeń korzysta z koncepcji weryfikacji.  
  
 Zarządzane aplikacje są kompilowane do firmy Microsoft pośredniego Language (MSIL). Po wykonaniu metody w zarządzanej aplikacji są jego MSIL jest kompilowany do kodu natywnego za pośrednictwem kompilacja just in Time (JIT). Kompilacja JIT obejmuje proces weryfikacji, który dotyczy wiele reguł bezpieczeństwa i niezawodności upewnij się, że nie ma kodu:  
  
-   Naruszenie umowy typu  
  
-   Wprowadzenie przepełnienia buforów  
  
-   Bardzo dostęp do pamięci.  
  
 Zarządzany kod, który nie jest zgodna z reguły weryfikacji jest nie można wykonać operacji, o ile jest on uznawany za zaufany kod.  
  
 Zaletą weryfikowalny kod jest klucza Przyczyna Dlaczego [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] oparty na programie .NET Framework. W zakresie, w jakim weryfikowalny kod jest używana, możliwość wykorzystania luk w zabezpieczeniach możliwe jest znacznie obniżony.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 Komputer kliencki przedstawia szeroką gamę zasobów, że zarządzanej aplikacji może mieć dostęp do, w tym system plików, rejestru, usług drukowania, interfejs użytkownika, odbicia i zmiennych środowiskowych. Przed zarządzanej aplikacji można uzyskać dostęp do zasobów na komputerze klienckim, musi mieć uprawnienia .NET Framework, aby to zrobić. Uprawnienia w [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] jest podklasą <xref:System.Security.CodeAccessPermission>; [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] implementuje jednej podklasy dla każdego zasobu, który zarządzane aplikacje mogą uzyskiwać dostęp do.  
  
 Zestaw uprawnień, które otrzymuje aplikacji zarządzanej przez [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] przy rozpoczęciu wykonywania jest znana jako zestaw uprawnień i jest określany przez dowód udostępniany przez aplikację. Dla [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacji, to dowód, że podano lokalizacji lub strefę, w którym będą uruchamiane aplikacje. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] identyfikuje następujących stref:  
  
-   **Komputer**. Aplikacje uruchomione z komputera klienta (w pełni zaufanych).  
  
-   **Lokalny Intranet**. Aplikacje uruchamiane z sieci intranet. (Nieco zaufane).  
  
-   **Internet**. Aplikacje uruchomione z Internetu. (Najmniej zaufanej).  
  
-   **Zaufane witryny**. Aplikacje określone przez użytkownika jako jest zaufana. (Najmniej zaufanej).  
  
-   **Witryn niezaufanych**. Aplikacje określone przez użytkownika jako jest zaufany. (Niezaufanych).  
  
 Dla każdego z tych stref [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] udostępnia wstępnie zdefiniowane uprawnienia zestaw, który obejmuje uprawnienia odpowiadającego poziom zaufania skojarzone z każdym. Należą do nich następujące elementy:  
  
-   **FullTrust**. Dla aplikacji, uruchamiana z **Mój komputer** strefy. Wszystkie możliwe uprawnienia są przyznawane.  
  
-   **LocalIntranet**. Dla aplikacji, uruchamiana z **lokalny Intranet** strefy. Podzbiór uprawnienia są przyznawane umiarkowane dostęp do zasobów na komputerze klienckim, w tym izolowanych magazynów, nieograniczony dostęp do interfejsu użytkownika, okna dialogowe nieograniczony pliku, ograniczone odbicia, ograniczony dostęp do zmiennych środowiskowych. Uprawnienia do kluczowych zasobów, takich jak rejestru nie są dostarczane.  
  
-   **Internet**. Dla aplikacji, uruchamiana z **Internet** lub **Zaufane witryny** strefy. Podzbiór uprawnienia są udzielane pod warunkiem ograniczony dostęp do zasobów na komputerze klienckim, w tym izolowanych magazynów, plik otwarty tylko, a ograniczony interfejsu użytkownika. Zasadniczo to uprawnienie ustawia izoluje aplikacje z komputera klienta.  
  
 Aplikacje określone jako pochodzącej z **witryn niezaufanych** strefy są przyznawane żadne uprawnienia przez [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] w ogóle. W związku z tym zestawu wstępnie zdefiniowane uprawnienia nie istnieje dla nich.  
  
 Na poniższym rysunku przedstawiono relację między stref, zestawy uprawnień, uprawnień i zasobów.  
  
 ![Zestawy uprawnień CAS](../../../docs/framework/wpf/media/caspermissionsets.png "CASPermissionSets")  
  
 Ograniczenia Internet strefy izolowanym stosowane jednakowo do żadnego kodu, który [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] importuje z biblioteki systemu, w tym [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. To zapewnia, że każdy bit kodu jest zablokowaną, nawet [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Niestety, aby można było wykonać, [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] musi korzystać z funkcji, która wymaga więcej uprawnień niż włączane przez piaskownicy zabezpieczeń strefy Internet.  
  
 Należy wziąć pod uwagę [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] aplikacja, która zawiera następującą stronę:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Do wykonania tej operacji [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], odpowiadającego [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kod musi być wykonywany więcej funkcji niż jest dostępne dla wywołujący [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], takie jak:  
  
-   Tworzenie uchwyt okna (hWnd) do renderowania  
  
-   Podczas wysyłania wiadomości  
  
-   Podczas ładowania czcionki Tahoma  
  
 Z zabezpieczeń punktu widzenia, dzięki czemu bezpośredni dostęp do żadnej z tych operacji w trybie piaskownicy aplikacji będzie krytycznego.  
  
 Na szczęście [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] może w tej sytuacji zezwalając te operacje można wykonać z podwyższonym poziomem uprawnień w imieniu aplikacji piaskownicy. Podczas wszystkich [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] operacji są porównywane z ograniczonymi uprawnieniami zabezpieczeń strefy Internet domeny aplikacji [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (tak jak inne biblioteki systemu) otrzymuje zestaw uprawnień, który zawiera wszystkie możliwe uprawnienia  
  
 Takie rozwiązanie wymaga [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] odbiera podniesione uprawnienia podczas uniemożliwia te uprawnienia są regulowane przez zestaw uprawnień internetowych strefy domeny aplikacji hosta.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] dokonuje tego przy użyciu **Assert** metody uprawnienia. Poniższy kod przedstawia, jak to jest wykonywana.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Assert** zasadniczo uniemożliwia nieograniczone uprawnienia wymagane przez [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] z są ograniczone przez Internet strefę uprawnień [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)].  
  
 Z punktu widzenia platformy [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jest odpowiedzialny za pomocą **Assert** poprawnie; nieprawidłowe użycie **Assert** złośliwego kodu podniesienia uprawnień. W związku z tym, ważne jest następnie wywoływać tylko **Assert** w razie potrzeby i aby upewnić się, że piaskownicy ograniczenia pozostaną nienaruszone. Na przykład kodu w trybie piaskownicy nie może otworzyć losowe pliki, ale może używać czcionek. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Umożliwia aplikacjom piaskownicy funkcja czcionki, wywołując **Assert**oraz [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] odczytu plików zawiera te czcionki w imieniu aplikacji piaskownicy.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Wdrożenie ClickOnce  
 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] to technologia kompleksowe wdrożenia, która znajduje się w programie .NET Framework i integruje się z [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (zobacz [omówienie wdrażania ClickOnce](http://msdn.microsoft.com/library/142dbbz4.aspx) Aby uzyskać szczegółowe informacje). Autonomiczny [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje można wdrażać za pomocą [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)], podczas gdy aplikacje obsługiwane w przeglądarce muszą być wdrażane z [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)].  
  
 Aplikacje wdrożone za pomocą [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] podane są dodatkowe zabezpieczenia warstwy [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]; zasadniczo [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] wdrożonych aplikacji zażądać uprawnień, które są im niezbędne. Otrzymali uprawnienia Jeśli nie przekraczają zestawu uprawnień dla strefy, w którym aplikacja jest wdrażana. Dzięki zmniejszeniu zestaw uprawnień tylko te, które są potrzebne, nawet jeśli są mniejsze niż podana przez zestaw uprawnień strefy uruchamiania, jest liczba zasobów, których aplikacja ma dostęp do zmniejszyć do minimum systemu od zera. W związku z tym jeśli przejęta aplikacji zostanie zmniejszona potencjalnych uszkodzenia komputera klienckiego.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Metodologia krytyczny dla zabezpieczeń  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Kod, który używa uprawnień, aby umożliwić piaskownicy strefy Internetu dla [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] aplikacji musi być przechowywany w najwyższym możliwym stopniu inspekcji zabezpieczeń i kontroli. Ułatwia to wymaganie, .NET Framework zapewnia obsługę nowych Zarządzanie kod, który zostanie uprawnień. W szczególności [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] pozwala na określenie kodu, który zostanie uprawnień i oznacz ją z <xref:System.Security.SecurityCriticalAttribute>; dowolny kod nie jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> staje się *przezroczysty* przy użyciu tej metody. Z drugiej strony, zarządzanego kodu, który nie jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> nie będzie mógł wzrasta uprawnień.  
  
 Metodologia krytyczny dla zabezpieczeń pozwala organizacji [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kod, który zostanie uprawnień do *krytyczny dla zabezpieczeń jądra*, pozostałych jest przezroczysty. Kod krytyczny dla zabezpieczeń izolowanie umożliwia [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] engineering team skupić się dodatkowe zabezpieczenia analizy i źródła formantu o jądrze krytyczny dla zabezpieczeń niż standardowe rozwiązania (zobacz [strategii zabezpieczeń WPF -Engineering zabezpieczeń](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)).  
  
 Należy pamiętać, że .NET Framework pozwala zaufany kod, aby rozszerzyć [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] piaskownicy strefy Internet, zezwalając deweloperom pisanie zarządzanych zestawów, które są oznaczone ikoną z <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) i wdrożone do użytkownika globalne Assembly Cache (GAC). Oznaczenie zestawu z atrybutem APTCA jest operacji zabezpieczeń bardzo ważne, ponieważ umożliwia dowolny kod do wywołania tego zestawu, w tym złośliwego kodu z Internetu. Wyjątkową ostrożność i najlepsze rozwiązania w zakresie muszą być używane w ten sposób, a użytkownicy muszą wybrać opcję zaufania oprogramowania w celu zainstalowania.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Zabezpieczeń programu Microsoft Internet Explorer  
 Poza zmniejszenie problemy dotyczące zabezpieczeń i konfiguracji zabezpieczeń, uproszczenie [!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] zawiera kilka funkcji w tym poprawki zabezpieczeń, które Podnieś poziom zabezpieczeń dla użytkowników [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Kierunek te funkcje próbuje Zezwalaj użytkownikom większą kontrolę nad ich środowisko przeglądania sieci Web.  
  
 Przed [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)], użytkownicy mogą podlegać następujących:  
  
-   Okna podręczne losowych.  
  
-   Przekierowywanie skryptu mylące.  
  
-   Wiele okien dialogowych zabezpieczeń niektórych witryn sieci Web.  
  
 W niektórych przypadkach niezaufanym witryn sieci Web może spróbować wymuszać użytkowników przez fałszowania instalacji [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] lub wielokrotnie Pokazywanie [!INCLUDE[TLA#tla_actx](../../../includes/tlasharptla-actx-md.md)] okno dialogowe instalacji, nawet wtedy, gdy użytkownik może mieć jej anulowaniem. Za pomocą tych metod, jest możliwe, że duża liczba użytkowników ma został zachęceni do podejmowania decyzji niska, które spowodowało instalację aplikacji, programów szpiegujących.  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zawiera kilka funkcji w celu ograniczenia tego rodzaju problemy, które obracać wokół pojęcie inicjowania użytkownika. [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] wykrywa, gdy użytkownik kliknął element link lub strony przed akcji, która nazywa się *inicjowania użytkownika*i traktuje je inaczej niż podczas podobne kroki zamiast tego zostanie wywołany przez skrypt na stronie. Na przykład [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zawiera **blokowanie wyskakujących okienek** wykrywa, gdy użytkownik kliknie przycisk przed strony tworzenia okno podręczne. Dzięki temu [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] najbardziej nieszkodliwe wyskakujące okienka wyskakujące okienka, których użytkownicy nie pytaj o ani mają zapobiegając. Zablokowane wyskakujące okienka są kolor w nowym **paska informacji**, który umożliwia użytkownikowi ręcznie zastąpić bloku i wyświetlić oknie podręcznym.  
  
 Ta sama logika inicjowania użytkownika jest również stosowany do **Otwórz**/**zapisać** monity zabezpieczeń. [!INCLUDE[TLA2#tla_actx](../../../includes/tla2sharptla-actx-md.md)] okna dialogowe instalacji są zawsze kolor poniżej paska informacji, chyba że reprezentują uaktualnienia z wcześniej zainstalowanych kontroli. Połączenie tych środków umożliwić użytkownikom bezpieczniejsze i bardziej kontrolowany przez użytkowników, ponieważ są one chronione przed nękanie je, aby zainstalować oprogramowanie niechcianych ani złośliwych witryn.  
  
 Te funkcje także chronić klientów, którzy korzystają z [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] aby przejść do witryny sieci web, umożliwiające pobranie i zainstalowanie [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacji. W szczególności wynika to z faktu [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zapewnia lepsze środowisko użytkownika, co zmniejsza ryzyko, które użytkownicy mogą zainstalować złośliwego lub devious aplikacji niezależnie od tego, jakie technologii użyte do kompilacji, w tym [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] dodaje do tych środków ochronnych za pomocą [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] ułatwiające pobieranie jego aplikacji za pośrednictwem Internetu. Ponieważ [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] wykonywane w strefie Internet izolowanym, może zostać bezproblemowo uruchomiona. Z drugiej strony, autonomiczny [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje wymagają pełnego zaufania do wykonania. W przypadku tych aplikacji [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] wyświetli okno dialogowe zabezpieczeń podczas procesu uruchamiania powiadomiono korzystanie z aplikacji dodatkowe wymagania dotyczące zabezpieczeń. Jednak to musi być inicjowane przez użytkownika, będą również regulowane przez logikę zainicjowanej przez użytkownika i mogą zostać anulowane.  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)] dołącza i rozszerza możliwości zabezpieczeń [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] jako część stale zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Opis zabezpieczeń w programie Microsoft Internet Explorer 6 w systemie Windows XP z dodatkiem SP2](http://www.microsoft.com/downloads/details.aspx?FamilyId=E550F940-37A0-4541-B5E2-704AB386C3ED&displaylang=en)  
 [Opis i pracy w programie Internet Explorer w trybie chronionym](http://msdn.microsoft.com/library/bb250462.aspx)  
 [Windows XP Service Pack 3](http://www.microsoft.com/windows/products/windowsxp/sp3/default.mspx)  
 [Podręcznik zabezpieczeń systemu Windows Vista](http://www.microsoft.com/downloads/details.aspx?familyid=a3d1bbed-7f35-4e72-bfb5-b84a526c1565&displaylang=en)  
 [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)  
 [Zabezpieczenia](../../../docs/framework/wpf/security-wpf.md)  
 [Zabezpieczenie częściowej relacji zaufania WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [Strategia zabezpieczeń WPF — projekt zabezpieczeń](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
