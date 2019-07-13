---
title: Strategia zabezpieczeń WPF - zabezpieczenia platformy
ms.date: 03/30/2017
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
ms.openlocfilehash: 5d7b76365178c78d2b20b9541d5e52a605158a77
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859825"
---
# <a name="wpf-security-strategy---platform-security"></a>Strategia zabezpieczeń WPF - zabezpieczenia platformy
Windows Presentation Foundation (WPF) zapewnia szereg usług zabezpieczeń, jednocześnie również wykorzystuje funkcje zabezpieczeń, możliwości platformy, która zawiera system operacyjny, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], i [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)]. Te warstwy są łączone w celu zapewnienia [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] model zabezpieczeń silne, ochronę w głębi, który próbuje uniknąć dowolnego pojedynczego punktu awarii, jak pokazano na poniższej ilustracji:  
  
 ![Diagram pokazujący model zabezpieczeń WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 W pozostałej części tego tematu opisano funkcje, w każdym z tych warstw, które odnoszą się do [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] specjalnie.  

<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>Zabezpieczeń systemu operacyjnego  
 Minimalny poziom systemu operacyjnego, która jest wymagana przez [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jest [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]. Rdzeń [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] udostępnia kilka funkcji zabezpieczeń, które stanowią podstawę zabezpieczeń dla wszystkich aplikacji Windows, łącznie z tymi utworzonych za pomocą [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] zawiera funkcje zabezpieczeń [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] i rozszerza je dalej. W tym temacie omówiono szerokość te funkcje zabezpieczeń, które są istotne dla [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], a także [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] integruje się z nimi, aby zapewnić dalsze ochronę w głębi.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Oprócz ogólnego przeglądu i wzmocnienie Windows, istnieją trzy najważniejsze funkcje z [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] , omówimy w tym temacie:  
  
- Kompilacji/GS  
  
- [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>/GS Compilation  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] zapewnia ochronę przez kompilację wiele bibliotek systemu core, wraz ze wszystkimi [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zależności, takie jak [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], aby ułatwić uniknięcie przepełnienia buforu. Jest to osiągane przy użyciu parametru/GS za pomocą kompilatora wiersza polecenia języka C/C++. Chociaż należy jawnie unikać przepełnienia buforu, kompilacji/GS zawiera przykład obrony głębokiej względem potencjalnych luk w zabezpieczeniach, które nieodwracalnie lub celowego tworzonych przez nich.  
  
 W przeszłości przepełnienia buforu zostały Przyczyna wielu lukami w zabezpieczeniach o dużym znaczeniu. Przepełnienie buforu występuje, gdy osoba atakująca wykorzystuje kodu, który umożliwia uruchomienie złośliwego kodu, który zapisuje poza granice buforu. Pozwala to następnie osobie atakującej przejąć kontrolę nad proces, w której kod jest wykonywany przez zastąpienie adres zwrotny funkcji, aby spowodować, że wykonywanie kodu osoby atakującej. Wynik jest złośliwy kod, który jest wykonywany dowolnego kodu z takie same uprawnienia jak proces przejętego.  
  
 Na wysokim poziomie flagi kompilatora/GS chroni przed niektóre potencjalne przepełnienia buforów przez iniekcję specjalnych zabezpieczeniach plik cookie, aby chronić adres zwrotny funkcji, która ma buforów lokalnego ciągu. Po powrocie funkcji, pliku cookie zabezpieczeń jest porównywana z poprzedniej wartości. Jeśli wartość została zmieniona, może wystąpić przepełnienie buforu, a proces zostanie zatrzymany warunek błędu. Trwa zatrzymywanie procesu uniemożliwia wykonywanie potencjalnie złośliwego kodu. Zobacz [/GS (Sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check) Aby uzyskać więcej informacji.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jest kompilowany za pomocą flagi/GS, aby dodać kolejną warstwę ochrony do [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Program Microsoft Windows aktualizacji rozszerzenia  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] poprawiła się również w [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] w celu uproszczenia procesu pobierania i instalowania aktualizacji. Te zmiany znacznie poprawić zabezpieczenia [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] klientów dzięki zapewnieniu, że ich systemy są aktualne, szczególnie w odniesieniu do aktualizacji zabezpieczeń.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Użytkownicy na [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] będzie korzystać z rozszerzeń zabezpieczeń systemu operacyjnego, "Najniższych dostęp użytkownika", sprawdzania integralności kodu, w tym i uprawnieniami izolacji.  
  
#### <a name="user-account-control-uac"></a>Kontrola konta użytkownika (UAC)  
 Obecnie użytkownicy Windows zwykle uruchomione z uprawnieniami administratora, ponieważ wiele aplikacji wymaga ich do instalacji lub wykonania lub obu. Przykładem jest możliwość zapisu domyślne ustawienia aplikacji w rejestrze.  
  
 Uruchomione z uprawnieniami administratora tak naprawdę oznacza, że aplikacje są wykonywane z procesów, które są przyznawane uprawnienia administratora. Wpływ zabezpieczeń jest złośliwy kod, który przejęcia proces uruchomiony z uprawnieniami administratora będą automatycznie dziedziczone tych uprawnień, łącznie z dostępem do krytyczne zasoby systemu.  
  
 Jednym ze sposobów, aby chronić przed zagrożeniem bezpieczeństwa jest uruchomienie aplikacji z najmniejszą ilością uprawnień, które są wymagane. To jest znany jako zasadę najmniejszych uprawnień, a to funkcja core [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] systemu operacyjnego. Ta funkcja jest wywoływana kontroli konta użytkownika (UAC) i jest używany przez [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] funkcji Kontrola konta użytkownika na dwa sposoby klucza:  
  
- Aby uruchamiać większość aplikacji przy użyciu uprawnień funkcji kontroli konta użytkownika domyślnie, nawet jeśli użytkownik jest administratorem; tylko te aplikacje, które są wymagane uprawnienia administratora zostanie uruchomione z uprawnieniami administratora. Aby uruchomić z uprawnieniami administracyjnymi, aplikacje muszą być jawnie oznaczone albo swoich aplikacji manifestu lub jako wpis w zasadach zabezpieczeń.  
  
- Aby zapewnić zgodność z rozwiązaniami, takimi jak wirtualizacji. Na przykład wiele aplikacji próby zapisu ograniczeniami trafić C:\Program Files. W przypadku aplikacji wykonywanie w ramach kontroli konta użytkownika z lokalizacją użytkownika alternatywnych istnieje nie wymaga uprawnień administratora do zapisu. Dla aplikacji działających w ramach kontroli konta użytkownika C:\Program Files Wirtualizuje funkcji Kontrola konta użytkownika, tak, aby aplikacje, którzy wydaje się, że pisania do niego są faktycznie zapisu do lokalizacji alternatywnej, na użytkownika. Tego rodzaju pracy zgodności umożliwia uruchamianie wielu aplikacji, które wcześniej nie można uruchomić w funkcji kontroli konta użytkownika systemu operacyjnego.  
  
#### <a name="code-integrity-checks"></a>Sprawdzanie integralności kodu  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] łączy w sobie lepiej sprawdzania integralności kodu w celu uniemożliwienia złośliwym kodem są wstrzykiwane do plików systemowych lub jądra w momencie uruchomienia/obciążenia. To wykracza poza ochrony plików systemowych.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Proces ograniczonych uprawnień dla aplikacji hostowanych w przeglądarce  
 Hostowana w przeglądarce [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje są wykonywane w piaskownicy strefy Internet. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Integracja z usługą [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] rozszerza tę ochronę za pomocą dodatkowej pomocy technicznej.  
  
#### <a name="internet-explorer-6-service-pack-2-and-internet-explorer-7-for-xp"></a>Dodatek Service Pack 2 dla Internet Explorer 6 i Internet Explorer 7 XP  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] wykorzystuje zabezpieczeń systemu operacyjnego przez ograniczenie uprawnień procesów dla [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] do dalszej ochrony. Przed obsługiwane w przeglądarce [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacja jest uruchamiana, system operacyjny tworzy proces hosta, która usuwa niepotrzebnych uprawnień z tokenu procesu. Przykłady uprawnień, które są usuwane: możliwość zamknięcia komputera użytkownika, obciążenia sterowniki i dostęp do odczytu do wszystkich plików na komputerze.  
  
#### <a name="internet-explorer-7-for-vista"></a>Internet Explorer 7 for Vista  
 W [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje są uruchamiane w trybie chronionym. W szczególności [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] Uruchom o poziomie średnim integralności.  
  
#### <a name="defense-in-depth-layer"></a>Warstwa ochronę w głębi  
 Ponieważ [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] są zazwyczaj piaskownicy za pośrednictwem Internetu, zestaw uprawnień strefy, usuwając te uprawnienia nie uszkodzić [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] z punktu widzenia zgodności. Zamiast tego tworzony jest dodatkową warstwę ochronę w głębi; Jeśli aplikacja w trybie piaskownicy jest w stanie wykorzystać innych warstw i przejęcia proces, proces będzie nadal tylko ma ograniczone uprawnienia.  
  
 Zobacz [przy użyciu konta użytkownika najmniej uprzywilejowane](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Zabezpieczenia usługi Common Language Runtime  
 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] Oferuje szereg korzyści klucza zabezpieczeń, które obejmują sprawdzanie poprawności i weryfikacji, [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]i metodologia krytyczne zabezpieczeń.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Sprawdzanie poprawności i weryfikacja  
 Zapewnienie izolacji zestawu oraz integralności, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] używa procesu sprawdzania poprawności. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] Sprawdzanie poprawności zapewnia, że zestawy są izolowane, sprawdzając poprawność format pliku przenośny plik wykonywalny (PE) ich adresy, które wskazują spoza zestawu. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] Sprawdzanie poprawności także weryfikuje integralność metadanych, który jest osadzony w zestawie.  
  
 Aby zapewnić bezpieczeństwo typów, zapobiec typowych problemów z zabezpieczeniami (np. przepełnienie buforu) i Włącz tryb piaskownicy za pośrednictwem procesów podrzędnych izolacji [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] zabezpieczeń korzysta z koncepcji weryfikacji.  
  
 Zarządzane aplikacje są kompilowane do firmy Microsoft Intermediate Language (MSIL). Gdy są wykonywane w aplikacji zarządzanej metody, jego MSIL jest kompilowane do kodu natywnego za pośrednictwem kompilacji just in Time (JIT). Kompilacja JIT obejmuje proces weryfikacji, który ma zastosowanie wielu reguł bezpieczeństwa i niezawodności, które upewnij się, że nie ma kodu:  
  
- Naruszać kontraktów typu  
  
- Wprowadzenie przepełnienia buforów  
  
- Bardzo popularny mają dostęp do pamięci.  
  
 Kod zarządzany, który nie jest zgodny z regułami weryfikacji jest niedozwolone są wykonywane, chyba że jest on uznawany za zaufany kod.  
  
 Zaletą weryfikowalny kod jest klucza przyczyny, dlaczego [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] opiera się na programie .NET Framework. W zakresie, w jakim weryfikowalny kod jest używany, możliwość wykorzystania możliwe luki w zabezpieczeniach jest znacząco obniżona.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 Komputer kliencki udostępnia szeroką gamę zasobów, że aplikacji zarządzanej może mieć dostęp do, w tym system plików, rejestru, usług drukowania, interfejs użytkownika, odbicia i zmiennych środowiskowych. Zanim zarządzanej aplikacji dostęp do zasobów na komputerze klienckim, musi mieć uprawnienia systemu .NET Framework, aby to zrobić. Dla uprawnienia w [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] jest podklasą <xref:System.Security.CodeAccessPermission>; [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] implementuje jedną podklasę dla poszczególnych zasobów, które zarządzane aplikacje mogą uzyskiwać dostęp do.  
  
 Zestaw uprawnień aplikacji zarządzanej jest udzielany przez [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] przy rozpoczęciu wykonywania jest znany jako zestaw uprawnień i jest określana przez dowody dostarczone przez aplikację. Aby uzyskać [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jest dowód, który jest dostarczany aplikacji, lokalizacji lub strefy, z którego będą uruchamiane aplikacje. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] identyfikuje następujących stref:  
  
- **Mój komputer**. Aplikacje uruchomione na komputerze klienta (w pełni zaufane).  
  
- **Lokalny Intranet**. Aplikacje uruchamiane w sieci intranet. (W pewnym stopniu zaufany).  
  
- **Internet**. Aplikacje uruchomione z Internetu. (Najmniej zaufanej).  
  
- **Zaufane witryny**. Aplikacje identyfikowane przez użytkownika jako jest zaufana. (Najmniej zaufanej).  
  
- **Niezaufanych witryn**. Aplikacje, zidentyfikowane przez użytkownika jako jest niezaufany. (Niezaufanych).  
  
 Dla każdego z tych stref [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] udostępnia wstępnie zdefiniowanego zestawu uprawnień, który obejmuje uprawnienia odpowiadającego poziom zaufania związany z każdą. Należą do nich następujące elementy:  
  
- **FullTrust**. W przypadku aplikacji, uruchomione z **Mój komputer** strefy. Wszystkie możliwe uprawnienia są przyznawane.  
  
- **LocalIntranet**. W przypadku aplikacji, uruchomione z **lokalny Intranet** strefy. Podzbiór uprawnienia są przyznawane zapewniają umiarkowane dostęp do zasobów komputera klienta, w tym wydzielonej pamięci masowej, nieograniczony dostęp do interfejsu użytkownika, okna dialogowe pliku bez ograniczeń, ograniczone odbicia, ograniczony dostęp do zmiennych środowiskowych. Uprawnienia dla krytycznych zasobów, takich jak rejestru nie są dostarczane.  
  
- **Internet**. W przypadku aplikacji, uruchomione z **Internet** lub **Zaufane witryny** strefy. Podzbiór uprawnienia udzielane pod warunkiem ograniczony dostęp do zasobów komputera klienta, w tym wydzielonej pamięci masowej, można otworzyć pliku tylko i ograniczenia interfejsu użytkownika. Zasadniczo to uprawnienie Ustaw izoluje aplikacje z komputera klienckiego.  
  
 Aplikacje określone jako pochodzącej z **niezaufanych witryn** strefy są przyznawane żadne uprawnienia przez [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] wcale. W związku z tym zestawu wstępnie zdefiniowanych uprawnień nie istnieje dla nich.  
  
 Na poniższym rysunku przedstawiono relację między strefami, zestawy uprawnień, uprawnienia i zasoby:  
  
 ![Diagram pokazujący zestawy uprawnień CAS.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Ograniczenia strefy Internet izolowanym stosuje się jednakowo do wszelki kod, który XBAP importuje z biblioteki systemu, w tym [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Gwarantuje to, że każdy bit kod jest zablokowane, nawet [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Niestety Aby móc wykonać XBAP musi korzystać z funkcji, która wymaga więcej uprawnień niż te, wynikające z piaskownicy zabezpieczeń strefy Internet.  
  
 Należy wziąć pod uwagę aplikacji XBAP, który zawiera następująca strona:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Do wykonania tego XBAP bazowego [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kod musi być wykonany więcej funkcji niż jest dostępne do wywoływania XBAP, w tym:  
  
- Tworzenie uchwyt okna (HWND) do renderowania  
  
- Podczas wysyłania wiadomości  
  
- Trwa ładowanie czcionki Tahoma  
  
 Z zabezpieczeń będzie krytycznego punktu widzenia, dzięki czemu bezpośredni dostęp do dowolnego z tych operacji z aplikacji w trybie piaskownicy.  
  
 Na szczęście [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] przeznaczony dla tej sytuacji, umożliwiając te operacje do wykonania z podwyższonym poziomem uprawnień w imieniu aplikacji w trybie piaskownicy. Podczas wszystkich [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] operacje są porównywane z ograniczonymi uprawnieniami zabezpieczeń strefy Internet domeny aplikacji XBAP [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (tak jak inne biblioteki systemu) otrzymuje zestawu uprawnień, który zawiera wszystkie możliwe uprawnienia.
  
 Takie rozwiązanie wymaga [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] odbiera podwyższonego poziomu uprawnień podczas uniemożliwia tych uprawnień jest regulowane przez zestaw uprawnień strefy Internet domeny aplikacji hosta.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] robi to przy użyciu **Asercja** metoda uprawnienia. Poniższy kod pokazuje, jak to się dzieje.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Asercja** zasadniczo zapobiega nieograniczone uprawnienia wymagane przez [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] z są ograniczone przez Internet strefa uprawnienia XBAP.  
  
 Z punktu widzenia platformy [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jest odpowiedzialny za pomocą **Asercja** poprawnie; niepoprawnego użycia **Asercja** można włączyć złośliwego kodu do podniesienia uprawnień. W związku z tym, należy następnie wywoływać tylko **Asercja** w razie potrzeby, oraz aby upewnić się, że piaskownicy ograniczenia pozostają bez zmian. Na przykład kodu w trybie piaskownicy nie może otworzyć plików losowych, ale może on być używać czcionek. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Umożliwia piaskownicy aplikacji przy użyciu funkcji czcionek, wywołując **Asercja**oraz [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] odczytu plików zawiera te czcionki w imieniu aplikacji w trybie piaskownicy.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Wdrożenie ClickOnce  
 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] to technologia wdrażania kompleksowe, jest dołączana do .NET Framework, która integruje się z [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (zobacz [ClickOnce zabezpieczeń i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment) Aby uzyskać szczegółowe informacje). Autonomiczny [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacje można wdrożyć przy użyciu [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)], natomiast aplikacje hostowane w przeglądarce musi zostać wdrożony za pomocą [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)].  
  
 Aplikacje wdrożone za pomocą [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] są podane jako dodatkowa warstwa zabezpieczeń za pośrednictwem [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]; zasadniczo [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] wdrożone aplikacje zażądać uprawnień, które są im niezbędne. Otrzymują uprawnienia Jeśli nie przekraczają zestaw uprawnień strefy, w którym aplikacja jest wdrażana. Dzięki zmniejszeniu zestaw uprawnień tylko do tych, które są potrzebne, nawet jeśli są mniejsze niż te dostarczone przez uprawnień strefy uruchamiania Ustaw, liczby zasobów, czy aplikacja ma dostęp do jest ograniczone do minimum systemu od zera. W związku z tym jeśli przejęta aplikacji jest mniejsze ryzyko uszkodzenia komputer kliencki.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Metodologia zabezpieczenia krytyczny  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Kodu, które używa uprawnień, aby włączyć piaskownicy strefy Internet, dla aplikacji XBAP musi być przechowywany na najwyższym możliwym stopniu inspekcji zabezpieczeń i kontroli. Aby ułatwić to wymaganie, .NET Framework zawiera nową obsługę zarządzania kod, który podnosi poziom uprawnień uprawnień. W szczególności [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] umożliwia Zidentyfikuj kod, który podnosi poziom uprawnień uprawnień i oznacz go za pomocą <xref:System.Security.SecurityCriticalAttribute>; każdy kod nie jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> staje się *przezroczyste* przy użyciu tej metody. Z drugiej strony, zarządzanego kodu, który nie jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> nie będzie mógł wzrasta uprawnień.  
  
 Zabezpieczenia-krytyczny metodologii umożliwia organizacji [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kod, który podnosi poziom uprawnień uprawnień do *zabezpieczenia krytyczny jądra*, za pomocą reszta jest przezroczysty. Izolując kod zabezpieczenia krytyczny umożliwia [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zespół inżynierów skupić się na dodatkowe analizy i źródła kontrole bezpieczeństwa na zabezpieczenia krytyczny jądra niż wskazówki dotyczące standardowych zabezpieczeń (zobacz [strategia zabezpieczeń WPF -Projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)).  
  
 Należy pamiętać, że .NET Framework pozwala zaufany kod, aby rozszerzyć piaskownicy strefy XBAP Internet, umożliwiając programistom pisanie zestawów zarządzanych, które są oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) i wdrażana do użytkownika pamięci podręcznej (globalnej). Oznaczenia zestawu za pomocą APTCA jest operacją zabezpieczeń bardzo ważne, ponieważ pozwala ono żadnego kodu do wywoływania tego zestawu, w tym złośliwy kod z Internetu. Należy zachować wyjątkową ostrożność i najlepsze rozwiązania muszą być używane w ten sposób, a użytkownicy muszą dokonać wyboru zaufać oprogramowanie w celu zainstalowania.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer Security  
 Poza zmniejszenie problemy dotyczące zabezpieczeń i konfiguracji zabezpieczeń, uproszczenie [!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] zawiera kilka funkcji, w tym poprawki zabezpieczeń, zwiększających bezpieczeństwo dla użytkowników [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Kierunek te funkcje próbuje umożliwić użytkownikom większą kontrolę nad przeglądania.  
  
 Przed [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)], użytkownicy mogą podlegać dowolne z następujących czynności:  
  
- Losowe menu podręczne dla systemu windows.  
  
- Mylenie przekierowania skryptu.  
  
- Wiele okien dialogowych zabezpieczeń w niektórych witrynach sieci Web.  
  
 W niektórych przypadkach niezaufana witryn sieci Web może spróbować nakłonienia użytkowników fałszując instalacji [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] lub wielokrotnie przedstawiający okno dialogowe instalacji ActiveX firmy Microsoft, nawet jeśli użytkownik mógł anulować go. Korzystając z tych metod, jest możliwe, że znaczna liczba użytkowników zostały zwiódł już, że niską decyzje, które spowodowały instalację aplikacji programów szpiegujących.  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zawiera kilka funkcji, aby uniknąć tego rodzaju problemów, które koncentrują się wokół koncepcji inicjowania użytkownika. [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] wykrywa, gdy użytkownik kliknął element link lub strony przed akcji, który jest znany jako *inicjowania użytkownika*i traktuje to inaczej niż kiedy podobne kroki zamiast tego jest wyzwalany przy użyciu skryptu na stronie. Na przykład [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zawiera **blokowanie wyskakujących okienek** wykrywa, gdy użytkownik kliknie przycisk przed strony tworzenia okno podręczne. Dzięki temu [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] wyskakujące najbardziej nieszkodliwe uniemożliwiając wyskakujących okienek, które użytkownicy, poproś o ani ma. Zablokowane wyskakujące okienka są zablokował w nowym **pasek informacji**, który umożliwia użytkownikowi ręczne przesłonięcie blokady i wyświetlić w oknie podręcznym.  
  
 Ta sama logika inicjowania użytkownika jest również zastosowane do **Otwórz**/**Zapisz** monity dotyczące zabezpieczeń. Instalacji ActiveX — okno dialogowe są zawsze zablokował poniżej paska informacji, o ile nie reprezentują one uaktualnienie z uprzednio zainstalowanych kontroli. Te miary są łączone w celu użytkownikom bezpieczniejszego, bardziej kontrolowanego interfejs użytkownika, ponieważ są one chronione przed witryn, które prześladowania je do zainstalowania złośliwego lub niechcianego oprogramowania.  
  
 Te funkcje także chronić klientów, którzy korzystają z [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] aby przejść do witryny sieci web, umożliwiające pobranie i zainstalowanie [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacji. W szczególności, jest to spowodowane [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] oferuje lepsze środowisko użytkownika, która zmniejsza ryzyko, które użytkownicy mogą zainstalować złośliwych lub devious aplikacji, niezależnie od tego, jakich technologii został użyty do kompilacji, w tym [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] dodaje do tych środków ochronnych za pomocą [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] ułatwiające pobieranie aplikacji niezbędnych do prowadzenia za pośrednictwem Internetu. Ponieważ [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] wykonywane w strefie Internet izolowanym, może zostać bezproblemowo uruchomione. Z drugiej strony, autonomiczny [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacji wymaga pełnego zaufania do wykonania. W przypadku tych aplikacji [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] wyświetli okno dialogowe zabezpieczeń podczas procesu uruchamiania, aby powiadomić użytkowania aplikacji dodatkowe wymagania dotyczące zabezpieczeń. Jednak to musi być inicjowane przez użytkownika, również podlega logiki zainicjowanej przez użytkownika i może być anulowany.  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)] dołącza i rozszerza możliwości zabezpieczeń [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] jako część nieustannie zobowiązuje się do zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia dostępu kodu](../misc/code-access-security.md)
- [Zabezpieczenia](security-wpf.md)
- [Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
