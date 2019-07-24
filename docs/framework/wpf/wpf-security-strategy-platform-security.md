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
ms.openlocfilehash: 42b1596082fe3e682a6fa806412ab5837b087bf9
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400708"
---
# <a name="wpf-security-strategy---platform-security"></a>Strategia zabezpieczeń WPF - zabezpieczenia platformy
Mimo że Windows Presentation Foundation (WPF) oferuje różne usługi zabezpieczeń, wykorzystuje również funkcje zabezpieczeń podstawowej platformy, w tym system operacyjny, środowisko CLR i [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)]. Te warstwy łączą się [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] , aby zapewnić mocny, kompleksowy model zabezpieczeń, który podejmuje próbę uniknięcia wszelkich Single Point of Failure, jak pokazano na poniższej ilustracji:  
  
 ![Diagram przedstawiający model zabezpieczeń WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 W pozostałej części tego tematu omówiono funkcje w każdej z tych warstw, które [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] odnoszą się do programu.  

<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>Zabezpieczenia systemu operacyjnego  
 Minimalny poziom systemu operacyjnego, który jest wymagany przez [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] program to. [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] Rdzeń programu [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] zapewnia kilka funkcji zabezpieczeń, które tworzą podstawę zabezpieczeń dla wszystkich aplikacji systemu Windows, w tym tych [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]utworzonych za pomocą programu. [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]obejmuje funkcje zabezpieczeń programu i zwiększa ich [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] liczbę. W tym temacie omówiono zakres tych funkcji zabezpieczeń, które są ważne dla [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]programu, a także [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] integrację z nimi w celu zapewnienia dalszej ochrony szczegółowej.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Oprócz ogólnego przeglądu i wzmocnienia systemu Windows, istnieją trzy kluczowe funkcje [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] , które są omawiane w tym temacie:  
  
- Kompilacja/GS  
  
- [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>Kompilacja/GS  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]zapewnia ochronę przez ponowną kompilację wielu podstawowych bibliotek systemowych, w tym [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] wszystkich zależności, takich jak środowisko CLR, aby pomóc w ograniczeniu przekroczenia buforu. Jest to osiągane przy użyciu parametru/GS z kompilatorem wierszaC++ polecenia C/. Mimo że przepełnienia buforów należy jawnie uniknąć, kompilacja/GS oferuje przykład obrony przed potencjalnymi lukami, które są przypadkowo lub złośliwie tworzone przez nie.  
  
 W przeszłości przekroczenia buforu były przyczyną wielu luk w zabezpieczeniach o dużym wpływie. Przepełnienie buforu występuje, gdy osoba atakująca korzysta z luki w zabezpieczeniach kodu, która pozwala na wstrzyknięcie złośliwego kodu, który zapisuje się poza granicami buforu. Dzięki temu osoba atakująca może przejąć proces, w którym wykonywany jest kod, zastępując adres zwrotny funkcji, aby spowodować wykonanie kodu osoby atakującej. Wynikiem jest złośliwy kod, który wykonuje dowolny kod z takimi samymi uprawnieniami co proces przejęty.  
  
 Na wysokim poziomie flaga kompilatora/GS chroni przed niektórymi potencjalnymi przedziałami buforu poprzez wstrzyknięcie specjalnego pliku cookie zabezpieczeń w celu ochrony adresu zwrotnego funkcji, która ma lokalne bufory ciągów. Po powrocie funkcji plik cookie zabezpieczeń jest porównywany z poprzednią wartością. Jeśli wartość została zmieniona, może wystąpić przepełnienie buforu i proces zostanie zatrzymany z warunkiem błędu. Zatrzymanie procesu uniemożliwia wykonanie potencjalnie złośliwego kodu. Aby uzyskać więcej informacji, zobacz [/GS (sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check) .  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]jest kompilowany za pomocą flagi/GS, aby dodać jeszcze inną warstwę obrony do [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Udoskonalenia programu Microsoft Windows Update  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)]Ulepszono również w [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] programie, aby uprościć proces pobierania i instalowania aktualizacji. Te zmiany znacząco zwiększają bezpieczeństwo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] klientów, pomagając w upewnieniu się, że ich systemy są aktualne, szczególnie w odniesieniu do aktualizacji zabezpieczeń.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] użytkownicy mogą korzystać z dodatkowych ulepszeń zabezpieczeń systemu operacyjnego, takich jak "dostęp użytkownika z najwyższymi uprawnieniami", sprawdzanie integralności kodu i izolacja uprawnień.  
  
#### <a name="user-account-control-uac"></a>Kontrola konta użytkownika (UAC)  
 Obecnie użytkownicy systemu Windows mogą uruchamiać się z uprawnieniami administratora, ponieważ wiele aplikacji wymaga ich do instalacji lub wykonania albo obu tych metod. Przykładem może być zapisanie domyślnych ustawień aplikacji do rejestru.  
  
 Uruchamianie z uprawnieniami administratora naprawdę oznacza, że aplikacje są wykonywane z procesów, które mają uprawnienia administratora. Wpływem bezpieczeństwa tego jest to, że dowolny złośliwy kod, który przejmuje proces z uprawnieniami administratora, będzie automatycznie dziedziczyć te uprawnienia, w tym dostęp do krytycznych zasobów systemu.  
  
 Jednym ze sposobów ochrony przed tym zagrożeniem bezpieczeństwa jest uruchomienie aplikacji z najmniejszą ilością wymaganych uprawnień. Jest to nazywane zasadą najniższych uprawnień i jest podstawową funkcją [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] systemu operacyjnego. Ta funkcja jest nazywana kontrolą konta użytkownika (UAC) i jest używana przez [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] funkcję UAC na dwa kluczowe sposoby:  
  
- Aby domyślnie uruchamiać większość aplikacji z uprawnieniami funkcji Kontrola konta użytkownika, nawet jeśli użytkownik jest administratorem. tylko aplikacje, które wymagają uprawnień administratora, będą uruchamiane z uprawnieniami administratora. Aby można było uruchamiać z uprawnieniami administracyjnymi, aplikacje muszą być jawnie oznaczone w manifeście aplikacji lub jako wpis w zasadach zabezpieczeń.  
  
- Zapewnianie rozwiązań zgodności, takich jak wirtualizacja. Przykładowo wiele aplikacji próbuje zapisywać w lokalizacjach z ograniczeniami, takimi jak C:\Program Files. W przypadku aplikacji uruchamianych w ramach funkcji Kontrola konta użytkownika istnieje alternatywna lokalizacja dla poszczególnych użytkowników, która nie wymaga uprawnień administratora do zapisu w usłudze. W przypadku aplikacji uruchamianych w ramach funkcji UAC funkcja Kontrola konta użytkownika umożliwia wirtualizację C:\Program Files w taki sposób, że aplikacje, które zauważają, że zapisu są w rzeczywistości zapisywane do alternatywnej lokalizacji na użytkownika. Ten rodzaj pracy zgodności umożliwia systemowi operacyjnemu uruchamianie wielu aplikacji, które nie mogły wcześniej działać w funkcji Kontrola konta użytkownika.  
  
#### <a name="code-integrity-checks"></a>Sprawdzanie integralności kodu  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]zapewnia lepszą kontrolę integralności kodu, aby zapobiec wprowadzaniu złośliwego kodu do plików systemowych lub jądra w czasie ładowania/uruchamiania. Powoduje to przekroczenie ochrony plików systemowych.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Ograniczony proces uprawnień dla aplikacji hostowanych w przeglądarce  
 Aplikacje hostowane [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] w przeglądarce są wykonywane w piaskownicy strefy internetowej. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]Integracja z [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] programem rozszerza tę ochronę dzięki dodatkowej obsłudze.  
  
#### <a name="internet-explorer-6-service-pack-2-and-internet-explorer-7-for-xp"></a>Internet Explorer 6 z dodatkiem Service Pack 2 i Internet Explorer 7 dla systemu XP  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]wykorzystuje zabezpieczenia systemu operacyjnego przez ograniczenie uprawnień procesu do [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] dalszej ochrony. Przed uruchomieniem aplikacji hostowanej [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] w przeglądarce system operacyjny tworzy proces hosta, który usuwa zbędne uprawnienia z tokenu procesu. Niektóre przykłady uprawnień, które zostały usunięte, obejmują możliwość zamykania komputera użytkownika, ładowania sterowników i dostępu do odczytu do wszystkich plików na komputerze.  
  
#### <a name="internet-explorer-7-for-vista"></a>Internet Explorer 7 dla systemu Vista  
 W programie [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)]aplikacjedziałająwtrybie chronionym.[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] W tym [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] celu należy uruchomić polecenie z integralnością średniego poziomu.  
  
#### <a name="defense-in-depth-layer"></a>Warstwa obrony szczegółowej  
 Ponieważ [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] zwykle są w trybie piaskownicy przez zestaw uprawnień strefy Internet, Usunięcie tych uprawnień nie jest [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] szkodliwe dla perspektywy zgodności. Zamiast tego zostanie utworzona dodatkowa warstwa zabezpieczeń. Jeśli aplikacja w trybie piaskownicy może wykorzystywać inne warstwy i przejmowanie tego procesu, proces nadal będzie miał tylko ograniczone uprawnienia.  
  
 Zobacz [Używanie konta użytkownika z najniższymi uprawnieniami](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Zabezpieczenia środowiska uruchomieniowego języka wspólnego  
 Środowisko uruchomieniowe języka wspólnego (CLR) oferuje szereg najważniejszych korzyści z zabezpieczeń, które obejmują sprawdzanie poprawności i weryfikację, zabezpieczenia dostępu kodu (CAS) oraz krytyczną metodologię zabezpieczeń.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Weryfikacja i weryfikacja  
 Aby zapewnić izolację i integralność zestawu, środowisko CLR używa procesu weryfikacji. Sprawdzanie poprawności środowiska CLR zapewnia odizolowanie zestawów przez zweryfikowanie ich przenośnego formatu pliku wykonywalnego (PE) dla adresów, które wskazują poza zestawem. Sprawdzanie poprawności środowiska CLR sprawdza również integralność metadanych osadzonych w zestawie.  
  
 Aby zapewnić bezpieczeństwo typów, należy zapobiec typowym problemom z zabezpieczeniami (na przykład przekroczenia buforu) i włączyć obsługę piaskownicy przez izolację podprocesów, a zabezpieczenia CLR wykorzystują koncepcję weryfikacji.  
  
 Aplikacje zarządzane są kompilowane do języka pośredniego firmy Microsoft (MSIL). Gdy są wykonywane metody w aplikacji zarządzanej, jej MSIL jest kompilowany do kodu natywnego za pomocą kompilacji just-in-Time (JIT). Kompilacja JIT obejmuje proces weryfikacji, który stosuje wiele reguł bezpieczeństwa i niezawodności, które gwarantują, że kod nie:  
  
- Narusza kontrakty typu  
  
- Wprowadź przekroczenia buforu  
  
- Bezznaczne dostęp do pamięci.  
  
 Nie można wykonać kodu zarządzanego, który jest niezgodny z regułami weryfikacji, chyba że jest uznawany za zaufany kod.  
  
 Zaletą kodu możliwego do zweryfikowania jest powód [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] , dla którego kompilacje na .NET Framework. W zakresie, w jakim jest używany kod możliwy do zweryfikowania, możliwość wykorzystania możliwych luk w zabezpieczeniach jest znacznie niższa.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 Komputer kliencki uwidacznia szeroką gamę zasobów, do których może mieć dostęp aplikacja zarządzana, w tym system plików, rejestr, usługi drukowania, interfejs użytkownika, odbicie i zmienne środowiskowe. Aby aplikacja zarządzana mogła uzyskać dostęp do dowolnych zasobów na komputerze klienckim, musi mieć odpowiednie uprawnienia .NET Framework. Uprawnienie w urzędach certyfikacji jest podklasą <xref:System.Security.CodeAccessPermission>klasy; Urzędy certyfikacji implementują jedną podklasę dla każdego zasobu, do którego mogą uzyskać dostęp aplikacje zarządzane.  
  
 Zestaw uprawnień, które są przydzielane przez urzędy certyfikacji podczas uruchamiania, jest znany jako zestaw uprawnień i jest określany przez dowody dostarczone przez aplikację. W [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] przypadku aplikacji dostarczane dowody są lokalizacją lub strefą, z której są uruchamiane aplikacje. Urzędy certyfikacji identyfikują następujące strefy:  
  
- **Mój komputer**. Aplikacje uruchomione z komputera klienckiego (w pełni zaufane).  
  
- **Lokalny intranet**. Aplikacje uruchamiane z intranetu. (Nieco zaufane).  
  
- **Internet**. Aplikacje uruchomione z Internetu. (Najmniej zaufany).  
  
- **Zaufane witryny**. Aplikacje identyfikowane przez użytkownika jako zaufane. (Najmniej zaufany).  
  
- **Niezaufane witryny**. Aplikacje zidentyfikowane przez użytkownika jako niezaufanego. (Niezaufane).  
  
 W przypadku każdej z tych stref urzędy certyfikacji udostępniają wstępnie zdefiniowany zestaw uprawnień, który obejmuje uprawnienia zgodne z poziomem zaufania skojarzonym z każdym z nich. Należą do nich następujące elementy:  
  
- **FullTrust**. W przypadku aplikacji uruchamianych z strefy **My Computer** . Przyznano wszystkie możliwe uprawnienia.  
  
- **LocalIntranet**. W przypadku aplikacji uruchomionych ze strefy **Lokalny intranet** . Podzbiór uprawnień zapewnia średni dostęp do zasobów komputera klienckiego, w tym izolowany magazyn, nieograniczony dostęp do interfejsu użytkownika, nieograniczone okna dialogowe plików, ograniczone odbicie i ograniczony dostęp do zmiennych środowiskowych. Nie podano uprawnień do zasobów krytycznych, takich jak rejestr.  
  
- **Internet**. W przypadku aplikacji uruchamianych z strefy **Internet** lub **Zaufane witryny** . Podzbiór uprawnień zapewnia ograniczony dostęp do zasobów komputera klienckiego, w tym do magazynu izolowanego, tylko do otwierania plików i ograniczonych interfejsów użytkownika. Zasadniczo ten zestaw uprawnień izoluje aplikacje z komputera klienckiego.  
  
 Aplikacje zidentyfikowane jako pochodzące z strefy **niezaufane witryny** nie mają żadnych uprawnień przez urzędy certyfikacji. W związku z tym wstępnie zdefiniowany zestaw uprawnień nie istnieje.  
  
 Na poniższej ilustracji przedstawiono relacje między strefami, zestawami uprawnień, uprawnieniami i zasobami:  
  
 ![Diagram przedstawiający zestawy uprawnień urzędów certyfikacji.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Ograniczenia trybu piaskownicy zabezpieczeń strefy internetowej są stosowane jednocześnie do dowolnego kodu, który jest importowany przez XBAP z biblioteki systemowej [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], włącznie z. Pozwala to zagwarantować, że każdy bit kodu jest zablokowany, nawet [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Niestety, aby można było wykonać, aplikacja XBAP musi wykonać funkcjonalność, która wymaga więcej uprawnień niż te włączone przez piaskownicę zabezpieczenia strefy internetowej.  
  
 Rozważ użycie aplikacji XBAP zawierającej następującą stronę:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Aby wykonać tę operację XBAP, kod [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] źródłowy musi wykonywać więcej funkcji niż jest dostępny dla wywołującego programu XBAP, w tym:  
  
- Tworzenie uchwytu okna (HWND) do renderowania  
  
- Wysyłanie komunikatów  
  
- Ładowanie czcionki Tahoma  
  
 Z punktu widzenia zabezpieczeń, umożliwienie bezpośredniego dostępu do którejkolwiek z tych operacji w aplikacji w trybie piaskownicy będzie katastrofalne.  
  
 Na szczęście zawarto tę sytuację, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] umożliwiając wykonywanie tych operacji z podwyższonym poziomem uprawnień w imieniu aplikacji w trybie piaskownicy. Wszystkie [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] operacje są sprawdzane względem ograniczonych uprawnień do zabezpieczeń strefy internetowej domeny aplikacji XBAP, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (podobnie jak w przypadku innych bibliotek systemowych) przyznany zestaw uprawnień, który obejmuje wszystkie możliwe uprawnienia.
  
 Wymaga to, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aby otrzymywać podwyższone uprawnienia, jednocześnie zapobiegając tym, aby te uprawnienia były regulowane przez zestaw uprawnień strefy internetowej domeny aplikacji hosta.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]w tym celu należy użyć metody **Assert** uprawnienia. Poniższy kod pokazuje, jak to się dzieje.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Potwierdzenie** zasadniczo uniemożliwia nieograniczone uprawnienia wymagane przez [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] program przed ograniczeniem uprawnień strefy Internetu aplikacji XBAP.  
  
 Z perspektywy platformy program [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jest odpowiedzialny za używanie potwierdzeń prawidłowo; nieprawidłowe użycie **potwierdzenia** może umożliwić złośliwemu kodowi podwyższenie poziomu uprawnień. W związku z tym ważne jest, aby w razie potrzeby wywołać tylko **potwierdzenie** , i upewnić się, że ograniczenia piaskownicy pozostają nienaruszone. Na przykład kod w trybie piaskownicy nie może otwierać plików losowych, ale może korzystać z czcionek. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]umożliwia aplikacjom w trybie piaskownicy używanie funkcji czcionki przez wywoływanie metody [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Assert, a w celu odczytu plików, które są znane, zawierają te czcionki w imieniu aplikacji w trybie piaskownicy.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Wdrożenie ClickOnce  
 ClickOnce to kompleksowa technologia wdrażania dołączona do .NET Framework i integruje się z programem [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) , aby uzyskać szczegółowe informacje). Aplikacje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] autonomiczne można wdrażać przy użyciu technologii ClickOnce, natomiast aplikacje hostowane w przeglądarce muszą być wdrażane za pomocą technologii ClickOnce.  
  
 Aplikacje wdrożone przy użyciu technologii ClickOnce mają dodatkową warstwę zabezpieczeń w porównaniu z zabezpieczeniami dostępu kodu (CAS); zasadniczo aplikacje wdrożone ClickOnce żądają wymaganych uprawnień. Te uprawnienia są udzielane tylko wtedy, gdy nie przekraczają zestawu uprawnień dla strefy, z której aplikacja jest wdrażana. Zmniejszając zestaw uprawnień tylko do tych, które są niezbędne, nawet jeśli są one mniejsze niż te podane przez zestaw uprawnień strefy uruchamiania, liczba zasobów, do których aplikacja ma dostęp, jest ograniczona do minimum od zera. W związku z tym, jeśli aplikacja zostanie przejęta, potencjalne uszkodzenie komputera klienckiego jest ograniczone.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Metodologia krytyczna dla zabezpieczeń  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Kod, który używa uprawnień do włączania piaskownicy strefy internetowej dla aplikacji XBAP, musi być utrzymywany do największego możliwego stopnia inspekcji i kontroli zabezpieczeń. Aby ułatwić to wymaganie, .NET Framework zapewnia nową obsługę zarządzania kodem, który podnosi uprawnienia. Środowisko CLR umożliwia zidentyfikowanie kodu, który podnosi poziom uprawnień i oznaczenie go z; dowolny kod <xref:System.Security.SecurityCriticalAttribute>, który nie jest <xref:System.Security.SecurityCriticalAttribute> oznaczony jako jest *przezroczysty* przy użyciu tej metodologii. Z drugiej strony kod zarządzany, który nie jest <xref:System.Security.SecurityCriticalAttribute> oznaczony za pomocą, nie jest zablokowany do podniesienia uprawnień.  
  
 Metodologia krytyczna dla zabezpieczeń umożliwia organizacjom kodu [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] podnoszącym uprawnienia do *jądra o krytycznym znaczeniu dla bezpieczeństwa*, gdy pozostała część jest przejrzysta. Izolowanie kodu krytycznego dla zabezpieczeń umożliwia [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zespołowi inżynieryjnemu skoncentrowanie się na dodatkowej analizie zabezpieczeń i kontroli źródła na jądrze o krytycznym znaczeniu dla bezpieczeństwa powyżej i poza standardowymi praktykami w zakresie zabezpieczeń (zobacz temat [strategia zabezpieczeń WPF — zabezpieczenia Inżynieria](wpf-security-strategy-security-engineering.md)).  
  
 Należy pamiętać, że .NET Framework pozwala na rozbudowanie obszaru izolowanego strefy internetowej programu XBAP przez deweloperów, dzięki czemu deweloperzy mogą <xref:System.Security.AllowPartiallyTrustedCallersAttribute> pisać zarządzane zestawy oznaczone za pomocą (APTCA) i wdrożone w globalnej pamięci podręcznej zestawów (GAC) użytkownika. Oznaczanie zestawu za pomocą APTCA jest wysoce poufną operacją zabezpieczeń, ponieważ umożliwia każdemu kodowi wywoływanie tego zestawu, w tym złośliwy kod z Internetu. Należy zachować szczególną ostrożność i korzystać z najlepszych rozwiązań, aby użytkownicy mogli je zaufać.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Zabezpieczenia programu Microsoft Internet Explorer  
 Poza zmniejszeniem problemów z zabezpieczeniami i uproszczenie konfiguracji zabezpieczeń [!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] program zawiera kilka funkcji, które zwiększają bezpieczeństwo użytkowników programu. [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] Nacisk tych funkcji próbuje umożliwić użytkownikom większą kontrolę nad ich doświadczeniem w przeglądaniu.  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)]W systemach wcześniejszych niż użytkownicy mogą podlegać dowolnym z następujących czynności:  
  
- Losowe okna podręczne.  
  
- Mylące przekierowanie skryptów.  
  
- Wiele okien dialogowych zabezpieczeń w niektórych witrynach sieci Web.  
  
 W niektórych przypadkach niezaufane witryny sieci Web próbują nakłonić użytkowników przez sfałszowanie instalacji [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] lub wielokrotne wyświetlanie okna dialogowego instalacji Microsoft ActiveX, mimo że użytkownik mógł go anulować. Korzystając z tych technik, istnieje możliwość, że znacząca liczba użytkowników została podzielona w celu podejmowania słabych decyzji, które spowodowały zainstalowanie aplikacji szpiegujących.  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)]zawiera kilka funkcji, które ograniczają te rodzaje problemów, które koncentrują się na koncepcji inicjacji użytkownika. [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)]wykrywa, kiedy użytkownik kliknął link lub element strony przed akcją, która jest znana jako *Inicjowanie użytkownika*i traktuje ją inaczej niż w przypadku wyzwolenia podobnej akcji przez skrypt na stronie. Na przykład [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] w programie znajduje się **blok wyskakujących okienek** , który wykrywa, kiedy użytkownik klika przycisk przed stroną tworzenia okna podręcznego. Dzięki [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] temu można zezwolić na większość wyskakujących okienek niewielkiej ilości, jednocześnie uniemożliwiając wyskakujące okienka, których użytkownicy nie proszą ani nie chcą. Zablokowane wyskakujące okienka są zalewkowane na nowym **pasku informacji**, co umożliwia użytkownikowi ręczne przesłonięcie bloku i wyświetlenie okienka wyskakującego.  
  
 Ta sama logika inicjowania użytkownika jest również stosowana do **otwierania**/zapisywanych wskazówek zabezpieczeń. Okna dialogowe instalacji ActiveX są zawsze zalewkowane na pasku informacji, chyba że reprezentuje uaktualnienie z wcześniej zainstalowanej kontrolki. Te miary łączą się, aby zapewnić użytkownikom bezpieczniejsze i bardziej kontrolowane środowisko użytkownika, ponieważ są one chronione przed lokacjami, które nękaniy w celu zainstalowania niechcianych lub złośliwych oprogramowania.  
  
 Te funkcje umożliwiają również ochronę klientów, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] którzy korzystają z programu w celu przeglądania witryn sieci Web, dzięki [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] którym mogą oni pobierać i instalować aplikacje. W szczególności jest to spowodowane [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] tym, że oferuje lepsze środowisko użytkownika, co pozwala użytkownikom na instalowanie złośliwych lub deviousych aplikacji niezależnie od tego, jaka technologia została użyta w celu jej skompilowania, w tym. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]dodaje do tych ochrony przy użyciu technologii ClickOnce, aby ułatwić pobieranie aplikacji przez Internet. Od [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] momentu wykonania w piaskownicy zabezpieczenia strefy internetowej można uruchomić je bezproblemowo. Z drugiej strony Aplikacje autonomiczne [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] wymagają pełnego zaufania do wykonania. W przypadku tych aplikacji Technologia ClickOnce wyświetli okno dialogowe zabezpieczenia podczas procesu uruchamiania, aby powiadomić o użyciu dodatkowych wymagań w zakresie zabezpieczeń aplikacji. Jednak to musi być inicjowane przez użytkownika, a także będzie podlegać logiki zainicjowane przez użytkownika i może być anulowane.  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)]obejmuje i rozszerza możliwości [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zabezpieczeń w ramach ciągłego zaangażowania w zabezpieczenia.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia dostępu kodu](../misc/code-access-security.md)
- [Zabezpieczenia](security-wpf.md)
- [Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
