---
title: Strategia bezpieczeństwa platformy
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
ms.openlocfilehash: 258fcd7c51ea59de03fe60a4eeb9a82dd1c7efca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174605"
---
# <a name="wpf-security-strategy---platform-security"></a>Strategia zabezpieczeń WPF - zabezpieczenia platformy
Podczas gdy Windows Presentation Foundation (WPF) udostępnia wiele usług zabezpieczeń, wykorzystuje również funkcje zabezpieczeń podstawowej platformy, która obejmuje system operacyjny, ŚRODOWISKO CLR i program Internet Explorer. Warstwy te łączą się, aby zapewnić WPF silny, obrony w głębi modelu zabezpieczeń, który próbuje uniknąć pojedynczego punktu awarii, jak pokazano na poniższym rysunku:  
  
 ![Diagram, który pokazuje model zabezpieczeń WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 W dalszej części tego tematu omówiono funkcje w każdej z tych warstw, które odnoszą się do WPF WPF w szczególności.  

## <a name="operating-system-security"></a>Bezpieczeństwo systemu operacyjnego  
Rdzeń systemu Windows zawiera kilka funkcji zabezpieczeń, które tworzą podstawę zabezpieczeń dla wszystkich aplikacji systemu Windows, w tym tych zbudowanych za pomocą WPF. W tym temacie omówiono szerokość tych funkcji zabezpieczeń, które są ważne dla WPF, a także jak WPF integruje się z nimi, aby zapewnić dalsze obrony w głębi.  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Oprócz ogólnego przeglądu i wzmocnienia systemu Windows, istnieją trzy kluczowe funkcje z dodatku SP2 systemu Windows XP, które omówimy w tym temacie:  
  
- Kompilacja /GS  
  
- Microsoft Windows Update.  
  
#### <a name="gs-compilation"></a>Kompilacja /GS  
 Dodatek SP2 dla systemu Windows XP zapewnia ochronę, ponownie komponując wiele podstawowych bibliotek systemowych, w tym wszystkie zależności WPF, takie jak CLR, aby zmniejszyć przepełnienie buforu. Jest to osiągane przy użyciu parametru /GS z kompilatorem wiersza polecenia C/C++. Chociaż należy jawnie unikać przekroczenia buforu, kompilacja /GS zawiera przykład obrony w głębi przed potencjalnymi lukami, które są przypadkowo lub złośliwie przez nie utworzone.  
  
 Historycznie przekroczenia buforów były przyczyną wielu luk w zabezpieczeniach o dużym wpływie. Przepełnienie buforu występuje, gdy osoba atakująca korzysta z luki w zabezpieczeniach kodu, która umożliwia wstrzyknięcie złośliwego kodu, który zapisuje poza granicami buforu. Następnie umożliwia osobie atakującej przejęcie kontroli nad procesem, w którym kod jest wykonywany przez zastąpienie adresu zwrotnego funkcji w celu spowodowania wykonania kodu osoby atakującej. Wynikiem jest złośliwy kod, który wykonuje dowolny kod z tymi samymi uprawnieniami, co proces porwany.  
  
 Na wysokim poziomie flaga kompilatora -GS chroni przed niektórymi potencjalnymi przekroczeniami buforu przez wstrzyknięcie specjalnego pliku cookie zabezpieczeń w celu ochrony adresu zwrotnego funkcji, która ma lokalne bufory ciągów. Po powrocie funkcji plik cookie zabezpieczeń jest porównywany z jego poprzednią wartością. Jeśli wartość uległa zmianie, mogło wystąpić przepełnienie buforu i proces zostanie zatrzymany z warunkiem błędu. Zatrzymanie procesu uniemożliwia wykonanie potencjalnie złośliwego kodu. Aby uzyskać więcej informacji, zobacz [-GS (Kontrola zabezpieczeń bufora).](/cpp/build/reference/gs-buffer-security-check)  
  
 WPF WPF jest skompilowany z /GS flagi, aby dodać jeszcze kolejną warstwę obrony do aplikacji WPF.  
  
### <a name="windows-vista"></a>Windows Vista  
Użytkownicy WPF w systemie Windows Vista będą korzystać z dodatkowych ulepszeń zabezpieczeń systemu operacyjnego, w tym "Dostęp użytkownika o najniższych uprawnieniach", sprawdzanie integralności kodu i izolacji uprawnień.  
  
#### <a name="user-account-control-uac"></a>Kontrola konta użytkownika  
 Obecnie użytkownicy systemu Windows mają tendencję do uruchamiania z uprawnieniami administratora, ponieważ wiele aplikacji wymaga ich do instalacji lub wykonania lub obu. Możliwość zapisu domyślnych ustawień aplikacji do rejestru jest jednym z przykładów.  
  
 Uruchamianie z uprawnieniami administratora naprawdę oznacza, że aplikacje są wykonywane z procesów, którym przyznano uprawnienia administratora. Wpływ na bezpieczeństwo jest to, że każdy złośliwy kod, który przechwytuje proces uruchomiony z uprawnieniami administratora automatycznie dziedziczy te uprawnienia, w tym dostęp do krytycznych zasobów systemowych.  
  
 Jednym ze sposobów ochrony przed tym zagrożeniem bezpieczeństwa jest uruchamianie aplikacji z najmniejszą ilością wymaganych uprawnień. Jest to znane jako zasada najmniejszych uprawnień i jest podstawową cechą systemu operacyjnego Windows. Ta funkcja jest nazywana kontrolą konta użytkownika (UAC) i jest używana przez system Kontrola konta użytkownika systemu Windows na dwa kluczowe sposoby:  
  
- Aby domyślnie uruchamiać większość aplikacji z uprawnieniami kontrola konta użytkownika, nawet jeśli użytkownik jest administratorem; tylko aplikacje, które wymagają uprawnień administratora będą uruchamiane z uprawnieniami administratora. Aby można było uruchomić z uprawnieniami administracyjnymi, aplikacje muszą być jawnie oznaczone w manifeście aplikacji lub jako wpis w zasadach zabezpieczeń.  
  
- Aby zapewnić rozwiązania zgodności, takie jak wirtualizacja. Na przykład wiele aplikacji próbuje zapisywać w ograniczonych lokalizacjach, takich jak Pliki C:\Program. W przypadku aplikacji wykonywanych w ramach kontrola konta użytkownika istnieje alternatywna lokalizacja dla użytkownika, która nie wymaga uprawnień administratora do zapisu. W przypadku aplikacji działających w ramach funkcji Kontrola konta użytkownika funkcja Kontrola konta użytkownika wirtualizuje pliki C:\Program, dzięki czemu aplikacje, które myślą, że zapisują do niego, faktycznie zapisują się do alternatywnej lokalizacji na użytkownika. Ten rodzaj pracy zgodności umożliwia systemowi operacyjnemu uruchamianie wielu aplikacji, które nie mogły wcześniej działać w uat.  
  
#### <a name="code-integrity-checks"></a>Sprawdzanie integralności kodu  
 System Windows Vista zawiera głębsze sprawdzanie integralności kodu, aby zapobiec wstrzyknięciu złośliwego kodu do plików systemowych lub do jądra w czasie ładowania/wykonywania. Wykracza to poza ochronę plików systemowych.  

### <a name="limited-rights-process-for-browser-hosted-applications"></a>Proces ograniczonych praw dla aplikacji hostowanych przez przeglądarkę  
 Aplikacje WPF hostowane przez przeglądarkę są wykonywane w strefie internetowej izolowane. Integracja WPF z programem Microsoft Internet Explorer rozszerza tę ochronę o dodatkową pomoc techniczną.  
  
 Ponieważ aplikacje przeglądarki XAML (XBAPs) są zazwyczaj w trybie piaskownicy przez zestaw uprawnień strefy internetowej, usunięcie tych uprawnień nie szkodzi aplikacjom przeglądarki XAML (XBAPs) z punktu widzenia zgodności. Zamiast tego tworzona jest dodatkowa warstwa obrony w głębi; Jeśli aplikacja w trybie piaskownicy jest w stanie wykorzystać inne warstwy i przejąć kontrolę nad procesem, proces nadal będzie miał tylko ograniczone uprawnienia.  
  
 Zobacz [Korzystanie z konta użytkownika o najniższych uprawnieniach](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
## <a name="common-language-runtime-security"></a>Zabezpieczenia środowiska wykonawczego języka wspólnego  
 Środowisko wykonawcze języka wspólnego (CLR) oferuje szereg kluczowych korzyści bezpieczeństwa, które obejmują sprawdzanie poprawności i weryfikacji, Zabezpieczenia dostępu do kodu (CAS) i metodologii krytyczne dla zabezpieczeń.  

### <a name="validation-and-verification"></a>Walidacja i weryfikacja  
 Aby zapewnić izolację i integralność zestawu, CLR używa procesu sprawdzania poprawności. Sprawdzanie poprawności clr zapewnia, że zestawy są izolowane przez sprawdzanie poprawności ich przenośny plik wykonywalny (PE) format dla adresów, które wskazują poza zestawem. Sprawdzanie poprawności programu CLR sprawdza również integralność metadanych, które są osadzone w zestawie.  
  
 Aby zapewnić bezpieczeństwo typu, należy zapobiegać typowym problemom z zabezpieczeniami (np. przekroczenia buforu) i włączyć piaskownicę poprzez izolację podprocesową, zabezpieczenia CLR używają koncepcji weryfikacji.  
  
 Aplikacje zarządzane są kompilowane w języku pośrednim firmy Microsoft (MSIL). Gdy metody w aplikacji zarządzanej są wykonywane, jego MSIL jest kompilowany do kodu macierzystego za pośrednictwem kompilacji Just-In-Time (JIT). Kompilacja JIT zawiera proces weryfikacji, który stosuje wiele zasad bezpieczeństwa i niezawodności, które zapewniają, że kod nie:  
  
- Naruszanie umów typu  
  
- Wprowadzenie przekroczenia buforu  
  
- Szalenie dostęp do pamięci.  
  
 Kod zarządzany, który nie jest zgodny z regułami weryfikacji, nie może być wykonywany, chyba że jest uważany za kod zaufany.  
  
 Zaletą weryfikowalny kod jest kluczowym powodem, dla którego WPF WPF tworzy na .NET Framework. W zakresie, w jakim używany jest możliwy do zweryfikowanie kod, możliwość wykorzystania ewentualnych luk w zabezpieczeniach jest znacznie obniżona.  
  
### <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 Komputer kliencki udostępnia szeroką gamę zasobów, które aplikacja zarządzana może mieć dostęp do, w tym system plików, rejestr, usługi drukowania, interfejs użytkownika, odbicie i zmienne środowiskowe. Aby aplikacja zarządzana mogła uzyskać dostęp do dowolnego zasobu na komputerze klienckim, musi mieć uprawnienie .NET Framework, aby to zrobić. Uprawnienie w CAS jest podklasą <xref:System.Security.CodeAccessPermission>; Cas implementuje jedną podklasę dla każdego zasobu, do który mogą uzyskiwać dostęp aplikacje zarządzane.  
  
 Zestaw uprawnień, które aplikacja zarządzana jest przyznawana przez cas po uruchomieniu wykonywania jest znany jako zestaw uprawnień i jest określana przez dowody dostarczone przez aplikację. W przypadku aplikacji WPF, dowody, które są dostarczane jest lokalizacja lub strefa, z której są uruchamiane aplikacje. CAS identyfikuje następujące strefy:  
  
- **Mój komputer**. Aplikacje uruchamiane z komputera klienckiego (w pełni zaufane).  
  
- **Lokalny intranet**. Aplikacje uruchomione z intranetu. (Nieco zaufany).  
  
- **Internet**. Aplikacje uruchomione z Internetu. (Najmniej zaufany).  
  
- **Zaufane witryny**. Aplikacje zidentyfikowane przez użytkownika jako zaufane. (Najmniej zaufany).  
  
- **Niezaufane witryny**. Aplikacje zidentyfikowane przez użytkownika jako niezaufane. (Niezaufane).  
  
 Dla każdej z tych stref cas zawiera wstępnie zdefiniowany zestaw uprawnień, który zawiera uprawnienia, które odpowiada poziom zaufania skojarzony z każdym. Należą do nich:  
  
- **FullTrust**. Dla aplikacji uruchomionych ze strefy **Mój komputer.** Wszystkie możliwe uprawnienia są przyznawane.  
  
- **LocalIntranet**. Dla aplikacji uruchamianych ze strefy **Lokalny intranet.** Podzbiór uprawnień są przyznawane w celu zapewnienia umiarkowanego dostępu do zasobów komputera klienckiego, w tym izolowanego magazynu, nieograniczony dostęp interfejsu użytkownika, nieograniczone okna dialogowe plików, ograniczone odbicie, ograniczony dostęp do zmiennych środowiskowych. Uprawnienia do zasobów krytycznych, takich jak rejestr nie są dostarczane.  
  
- **Internet**. W przypadku aplikacji uruchamianych ze strefy **Internet** lub **Zaufane witryny.** Podzbiór uprawnień są przyznawane pod warunkiem ograniczony dostęp do zasobów komputera klienckiego, w tym izolowanego magazynu, tylko plik otwarty i ograniczony interfejs użytkownika. Zasadniczo ten zestaw uprawnień izoluje aplikacje z komputera klienckiego.  
  
 Aplikacjom zidentyfikowanym jako pochodzące ze strefy **Niezaufane witryny** nie są w ogóle przyznawane żadne uprawnienia przez cas. W związku z tym wstępnie zdefiniowany zestaw uprawnień nie istnieje dla nich.  
  
 Na poniższym rysunku przedstawiono relację między strefami, zestawami uprawnień, uprawnieniami i zasobami:  
  
 ![Diagram przedstawiający zestawy uprawnień CAS.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Ograniczenia piaskownicy zabezpieczeń strefy internetowej mają zastosowanie w równym stopniu do dowolnego kodu importowanego przez narzędzie XBAP z biblioteki systemowej, w tym w pulę WPF. Gwarantuje to, że każdy bit kodu jest zablokowany, nawet WPF. Niestety, aby móc wykonać, XBAP musi wykonać funkcje, które wymaga więcej uprawnień niż te włączone przez izolat bezpieczeństwa strefy internetowej.  
  
 Należy wziąć pod uwagę aplikację XBAP, która zawiera następującą stronę:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Aby wykonać ten XBAP, podstawowy kod WPF musi wykonać więcej funkcji niż jest dostępna dla wywołującego XBAP, w tym:  
  
- Tworzenie uchwytu okna (HWND) do renderowania  
  
- Wysyłanie wiadomości  
  
- Ładowanie czcionki Tahoma  
  
 Z punktu widzenia zabezpieczeń umożliwienie bezpośredniego dostępu do dowolnej z tych operacji z aplikacji w trybie piaskownicy byłoby katastrofalne.  
  
 Na szczęście WPF WPF obsługuje tę sytuację, zezwalając na te operacje do wykonania z podwyższonymi uprawnieniami w imieniu aplikacji piaskownicy. Podczas gdy wszystkie operacje WPF są sprawdzane względem ograniczonych uprawnień zabezpieczeń strefy internetowej domeny aplikacji XBAP, WPF WPF (podobnie jak w przypadku innych bibliotek systemowych) otrzymuje zestaw uprawnień, który zawiera wszystkie możliwe uprawnienia.
  
 Wymaga to, aby WPF otrzymuje podwyższone uprawnienia, jednocześnie uniemożliwiając te uprawnienia są regulowane przez zestaw uprawnień strefy internetowej domeny aplikacji hosta.  
  
 WPF WPF robi to przy użyciu **Assert** metody uprawnienia. Poniższy kod pokazuje, jak to się dzieje.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Assert** zasadniczo uniemożliwia nieograniczone uprawnienia wymagane przez WPF jest ograniczona przez uprawnienia strefy internet XBAP.  
  
 Z punktu widzenia platformy WPF WPF jest odpowiedzialny za przy użyciu **Assert** poprawnie; niepoprawne użycie **Assert** może włączyć złośliwy kod do podniesienia uprawnień. W związku z tym ważne jest, aby następnie wywołać **Assert** tylko wtedy, gdy jest to potrzebne i zapewnić, że ograniczenia piaskownicy pozostają nienaruszone. Na przykład kod w trybie piaskownicy nie może otwierać losowych plików, ale może używać czcionek. WPF WPF umożliwia piaskownicy aplikacji do korzystania z funkcji czcionki przez wywołanie **Assert**, i WPF do odczytu plików, o których wiadomo, że zawierają te czcionki w imieniu aplikacji piaskownicy.  
  
### <a name="clickonce-deployment"></a>Wdrożenie clickonce  
 ClickOnce to kompleksowa technologia wdrażania, która jest dołączona do programu .NET Framework i integruje się z programem Visual Studio (zobacz [ClickOnce zabezpieczeń i wdrażania,](/visualstudio/deployment/clickonce-security-and-deployment) aby uzyskać szczegółowe informacje). Autonomiczne aplikacje WPF można wdrożyć za pomocą ClickOnce, podczas gdy aplikacje hostowane w przeglądarce muszą być wdrażane za pomocą ClickOnce.  
  
 Aplikacje wdrożone przy użyciu ClickOnce otrzymują dodatkową warstwę zabezpieczeń nad zabezpieczeniami dostępu do kodu (CAS); zasadniczo ClickOnce wdrożone aplikacje żądają uprawnień, które są potrzebne. Są one przyznawane tylko te uprawnienia, jeśli nie przekraczają zestawu uprawnień dla strefy, z której aplikacja jest wdrażana. Zmniejszając zestaw uprawnień tylko do tych, które są potrzebne, nawet jeśli są one mniejsze niż te dostarczone przez zestaw uprawnień strefy uruchamiania, liczba zasobów, do których aplikacja ma dostęp, jest ograniczona do minimum. W związku z tym jeśli aplikacja zostanie przejęta, zmniejsza się możliwość uszkodzenia komputera klienckiego.  
  
### <a name="security-critical-methodology"></a>Metodologia o krytycznym znaczeniu dla bezpieczeństwa  
 Kod WPF, który używa uprawnień, aby włączyć strefę internetową izolowane dla aplikacji XBAP musi być utrzymywany w najwyższym możliwym stopniu inspekcji zabezpieczeń i kontroli. Aby ułatwić to wymaganie, .NET Framework zapewnia nową obsługę zarządzania kodem, który podnosi uprawnienia. W szczególności CLR umożliwia identyfikację kodu, który podnosi uprawnienia <xref:System.Security.SecurityCriticalAttribute>i oznaczyć go za pomocą ; każdy kod, <xref:System.Security.SecurityCriticalAttribute> który nie został oznaczony, staje się *przejrzysty* przy użyciu tej metodologii. Z drugiej strony kod zarządzany, <xref:System.Security.SecurityCriticalAttribute> który nie jest oznaczony za pomocą nie jest uniemożliwiony podniesienie uprawnień.  
  
 Metodologia security-critical umożliwia organizację kodu WPF, który podnosi uprawnienia do *jądra o znaczeniu krytycznym dla zabezpieczeń,* a pozostała część jest przezroczysta. Izolowanie kodu krytycznego dla zabezpieczeń umożliwia zespołowi inżynierów WPF skupienie się na dodatkowej analizie zabezpieczeń i kontroli źródła na jądrze o krytycznym znaczeniu dla zabezpieczeń, wykraczające poza standardowe praktyki bezpieczeństwa (patrz [WPF Security Strategy - Security Engineering](wpf-security-strategy-security-engineering.md)).  
  
 Należy zauważyć, że program .NET Framework zezwala zaufanemu kodowi na rozszerzenie piaskownicy strefy <xref:System.Security.AllowPartiallyTrustedCallersAttribute> internetowej XBAP, umożliwiając deweloperom pisanie zarządzanych zestawów oznaczonych (APTCA) i wdrożonych w globalnej pamięci podręcznej zestawu użytkownika (GAC). Oznaczanie zestawu za pomocą APTCA jest bardzo wrażliwą operacją zabezpieczeń, ponieważ umożliwia każdemu kodowi wywołanie tego zestawu, w tym złośliwy kod z Internetu. Aby można było je zainstalować, należy zachować szczególną ostrożność i najlepsze rozwiązania, a użytkownicy muszą zdecydować się na zaufanie do tego oprogramowania.  
  
## <a name="microsoft-internet-explorer-security"></a>Zabezpieczenia programu Microsoft Internet Explorer  
 Oprócz ograniczenia problemów z zabezpieczeniami i uproszczenia konfiguracji zabezpieczeń, program Microsoft Internet Explorer 6 (SP2) zawiera kilka funkcji, które zwiększają bezpieczeństwo użytkowników aplikacji przeglądarki XAML (XBAPs). Ciąg tych funkcji próbuje umożliwić użytkownikom większą kontrolę nad ich przeglądania.  
  
 Przed ie6 SP2, użytkownicy mogą podlegać każdej z następujących czynności:  
  
- Losowe okna podręczne.  
  
- Mylące przekierowanie skryptu.  
  
- Liczne okna dialogowe zabezpieczeń w niektórych witrynach sieci Web.  
  
 W niektórych przypadkach nierzetelne witryny sieci Web próbowały oszukać użytkowników, podszywając się pod instalację [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] lub wielokrotnie wyświetlając okno dialogowe instalacji programu Microsoft ActiveX, nawet jeśli użytkownik mógł go anulować. Za pomocą tych technik, jest możliwe, że znaczna liczba użytkowników zostały oszukane do podejmowania złych decyzji, które doprowadziły do instalacji aplikacji szpiegujących.  
  
 Dodatek SP2 dla systemu IE6 zawiera kilka funkcji w celu złagodzenia tego typu problemów, które koncentrują się wokół koncepcji inicjacji użytkownika. Dodatek SP2 dla aplikacji IE6 wykrywa, gdy użytkownik kliknął łącze lub element strony przed akcją, która jest nazywana *inicjacją użytkownika,* i traktuje ją inaczej niż wtedy, gdy podobna akcja jest wyzwalana przez skrypt na stronie. Na przykład dodatek SP2 IE6 zawiera **blokowanie wyskakujących wyskakujących** wyskakujących po sobie, które wykrywa, gdy użytkownik kliknie przycisk przed utworzeniem strony wyskakującego okienka. Dzięki temu IE6 SP2 pozwala na większość nieszkodliwych wyskakujących okienków, jednocześnie zapobiegając wyskakującym okienkom, o które użytkownicy nie proszą ani nie chcą. Zablokowane wyskakujące okienka są zalewkowane pod nowym **pasem informacji,** co pozwala użytkownikowi ręcznie zastąpić blok i wyświetlić okno podręczne.  
  
 Ta sama logika inicjowania użytkownika jest również stosowana do monitów zabezpieczeń **Otwórz**/**zapisz.** Okna dialogowe instalacji ActiveX są zawsze zalewkowane pod paskiem informacji, chyba że reprezentują uaktualnienie z wcześniej zainstalowanego formantu. Środki te łączą się, aby zapewnić użytkownikom bezpieczniejsze, bardziej kontrolowane środowisko użytkownika, ponieważ są one chronione przed witrynami, które nękają ich, aby zainstalować niechciane lub złośliwe oprogramowanie.  
  
 Te funkcje chronią również klientów korzystających z dodatku SP2 iE6 do przeglądania witryn sieci Web, które umożliwiają pobieranie i instalowanie aplikacji WPF. W szczególności jest to spowodowane tym, że IE6 SP2 oferuje lepsze środowisko użytkownika, które zmniejsza szansę dla użytkowników na instalowanie złośliwych lub przebiegłych aplikacji, niezależnie od tego, jaka technologia została użyta do jego zbudowania, w tym WPF. WPF WPF dodaje do tych zabezpieczeń za pomocą ClickOnce w celu ułatwienia pobierania swoich aplikacji przez Internet. Ponieważ aplikacje przeglądarki XAML (XBAPs) są wykonywane w strefie internetowej, można je bezproblemowo uruchamiać. Z drugiej strony autonomiczne aplikacje WPF wymagają pełnego zaufania do wykonania. W przypadku tych aplikacji ClickOnce wyświetli okno dialogowe zabezpieczeń podczas procesu uruchamiania, aby powiadomić o użyciu dodatkowych wymagań dotyczących zabezpieczeń aplikacji. Jednak to musi być inicjowane przez użytkownika, będzie również regulowane przez logikę inicjowane przez użytkownika i może zostać anulowane.  
  
 Program Internet Explorer 7 zawiera i rozszerza możliwości zabezpieczeń dodatku SP2 iE6 w ramach stałego zaangażowania w bezpieczeństwo.  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia dostępu kodu](../misc/code-access-security.md)
- [Zabezpieczenia](security-wpf.md)
- [Częściowe zabezpieczenia zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
