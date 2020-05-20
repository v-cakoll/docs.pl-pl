---
title: Wdrażanie nowoczesnych aplikacji klasycznych
description: Wszystko, czego potrzebujesz, aby dowiedzieć się więcej o wdrażaniu nowoczesnych aplikacji klasycznych.
ms.date: 05/12/2020
ms.openlocfilehash: 4a4d93caf1c2f8f58d48ee3199bbe6983fa939f4
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423258"
---
# <a name="deploying-modern-desktop-applications"></a>Wdrażanie nowoczesnych aplikacji klasycznych

Podczas tworzenia aplikacji klasycznych warto wziąć pod uwagę sposób, w jaki aplikacja ma zostać spakowana i wdrożona na maszynach użytkowników. Problem z pakowaniem, wdrażaniem i instalacją polega na tym, że zwykle znajduje się on w ramach parasola specjalistów IT, którzy zapewnią różne rzeczy niż deweloperzy.

W tych dniach wszyscy znają koncepcje DevOps, w których deweloperzy i specjaliści IT ściśle współpracują nad przenoszeniem aplikacji do ich środowisk produkcyjnych. Ale jeśli jesteś w sprawdzoneje pulpitu przez ponad 10 lat, być może zaobserwowano Poniższy scenariusz. Zespół deweloperów pracuje ze sobą bardzo trudno, aby spełniał terminy projektu. Osoby biznesowe są urządzenia nerwowego, ponieważ potrzebują systemu działającego na wielu maszynach użytkownika w celu uruchomienia firmy. W ciągu "D-Day" Menedżer projektu sprawdza każdego dewelopera, że jego kod działa prawidłowo i że wszystko jest poprawne, dzięki czemu mogą być dostarczane. Następnie zespół pakietu jest w stanie generować Instalatora dla aplikacji, rozpowszechniać go na każdym komputerze użytkownika, a zestaw użytkowników testowych uruchamia aplikację. Ponadto spróbują, że przed wyświetleniem dowolnego interfejsu użytkownika aplikacja zgłasza wyjątek mówiący, że metoda ~ obiektu ~ nie powiodła się. Awaryjnego zaczyna przepływać przez powietrze i krótkie punkty dochodzenia do młodych i nieaktualnych deweloperów, którzy wprowadziły kontrolę innej firmy, która wykazała "prace na komputerze deweloperskim".

Instalowanie aplikacji klasycznych było tradycyjnie okropnej z dwóch głównych przyczyn:

- Brak bliskiej kultury współpracy między zespołami deweloperów i działów IT.
- Brak stałego pakowania i technologii wdrażania, które możemy skompilować.

W rzeczywistości mieszkamy z faktem, że czasami zrezygnujesz z zainstalowania aplikacji, ponieważ:

- Zakończyło się nieoczekiwanym efektem ubocznym na maszynie.
- Niektóre aplikacje, które zostały wcześniej zainstalowane, przestają działać.

Ponadto nie można przywrócić oryginalnego stanu systemu przez odinstalowanie aplikacji. Używamy tej sytuacji, aby na bieżąco korzystać z takich warunków, jak "DLL Hell" lub "Winrot".

W tym rozdziale porozmawiamy o MSIX. MSIX to nowa technologia marki firmy Microsoft, która próbuje przechwycić najlepsze z powyższych technologii, aby zapewnić solidną podstawę dla technologii tworzenia pakietów w przyszłości.

Co robi technologia tworzenia pakietów z modernizacją? Ponadto wychodzi to, że opakowanie jest podstawą dla przedsiębiorstwa IT z dużą ilością pieniędzy. Modernizacja nie dotyczy tylko najnowszych technologii. Jest on także związany z skróceniem czasu wprowadzenia na rynek od momentu, w którym jest zdefiniowane wymaganie biznesowe, do momentu, gdy firma dostarczy tę funkcję klientowi.

## <a name="the-modern-application-lifecycle"></a>Cykl życia nowoczesnej aplikacji

Obecnie deweloperzy zapisują i tworzą kod dla aplikacji, a następnie przekazują wygenerowane zasoby do specjalistów IT. Następnie specjaliści IT ponownie konfigurują aplikację i pakują ją, zwykle w pliku MSI lub później w formacie pakietu App-V. Aplikacja jest wdrażana za pomocą różnych kanałów i narzędzi. Jednym z głównych problemów z tym podejściem jest często znana jako "pakowanie Paralysis". Problem polega na tym, że cykl jest powtarzany za każdym razem, gdy istnieje aktualizacja aplikacji lub Aktualizacja systemu operacyjnego.

Proces ten można zobaczyć na poniższej ilustracji:

![Diagram przedstawiający nowoczesny cykl życia IT](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

Firmy muszą mieć możliwość przerwania tego cyklu pakowania na trzy niezależne cykle:

- Aktualizacje systemu operacyjnego
- Aktualizacje aplikacji
- Dostosowywanie

![Diagram przedstawiający nowoczesny cykl IT składa](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

Na poprzednim diagramie przedstawiono następujące możliwości:

- Aktualizowanie podstawowego systemu operacyjnego bez konieczności ponownego pakowania aplikacji.
- Włącz ich dostosowania bez konieczności ponownej pakowania oryginalnego pakietu dewelopera.

Ten pierwiastek zmiany prowadzi do nowego i nowoczesnego cyklu życia IT, jak pokazano na poniższej ilustracji:

![Diagram przedstawiający cykl życia aplikacji przy użyciu narzędzi firmy Microsoft](./media/deploy-modern-applications/microsoft-it-tools.png)

Deweloperzy tworzą aplikację i generują pakiet MSIX, który specjaliści IT mogą wykorzystać i skonfigurować bez konieczności ponownego pakowania. Podobnie jak w przypadku technologii MSIX, firma Microsoft stworzyła narzędzia umożliwiające dostosowywanie i Konfigurowanie pakietów bez konieczności ponownego pakowania.

## <a name="msix-the-next-generation-of-deployment"></a>MSIX: Kolejna generacja wdrożenia

Przed MSIX można korzystać z kilku technologii pakowania, takich jak Kreatory instalacji, MSI, ClickOnce, App-V i skrypty. Każda z tych technologii ma swoje własne siły, a firma Microsoft zdecydowała się wybrać najlepsze z nich, aby MSIX kompilację. MSIX jest oparty na wykorzystaniu istniejących technologii, które wybierają najlepszą z nich:

- App-V = \> kontenerach
- ClickOnce = \> autoaktualizowanie
- MSI = \> prosta dystrybucja

Dzięki programowi MSIX uzyskasz jedną technologię Instalatora ze wszystkimi tymi funkcjami.

![Diagram przedstawiający różne technologie, które miały wpływ na tworzenie MSIX](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a>Zalety MSIX

#### <a name="never-regret-installing-an-app"></a>Nigdy nie należy instalować aplikacji

MSIX zapewnia przewidywalne, niezawodne i bezpieczne wdrażanie. Metoda deklaracyjne zawarte w manifeście pakietu umożliwia systemowi operacyjnemu śledzenie każdego zasobu, którego potrzebuje aplikacja. Zapewnia również prawdziwą czystą dezinstalację bez efektów ubocznych.

#### <a name="disk-space-optimization"></a>Optymalizacja miejsca na dysku

MSIX jest zoptymalizowany pod kątem zmniejszenia wpływu aplikacji na miejsce na dysku komputera użytkownika. Tworzy magazyn jednego wystąpienia plików. Oznacza to, że jeśli masz dwa różne pakiety z tą samą biblioteką DLL, biblioteka DLL nie jest zainstalowana dwukrotnie. Platforma zajmie się tym problemem, ponieważ wie, że wszystkie pliki, które zostały zainstalowane w danej aplikacji, z powodu deklaracyjnego charakteru. Pozwala również mieć różne wersje bibliotek DLL, które działają obok siebie.

Korzystając z pakietów zasobów, można łatwo tworzyć aplikacje wielojęzyczne, a system operacyjny zajmuje się instalowaniem tych, które są używane.

#### <a name="network-optimization"></a>Optymalizacja sieci

MSIX wykrywa różnice w plikach na poziomie bloku bajtów, włączając funkcję o nazwie aktualizacje różnicowe. Oznacza to, że tylko zaktualizowane bloki bajtów są pobierane na aktualizacje aplikacji.

![Diagram przedstawiający sposób, w jaki MSIX zarządza aktualizacjami różnicowymi.](./media/deploy-modern-applications/msix-managing-updates.png)

Za pomocą instalacji przesyłania strumieniowego użytkownik może szybko rozpocząć pracę nad aplikacją, podczas gdy inne części aplikacji są pobierane w tle. Ta funkcja przyczynia się do zaangażowania użytkowników.

Dzięki funkcji opcjonalne pakiety można osiągnąć componentization w ramach wdrożenia aplikacji, dzięki czemu można je pobrać w razie potrzeby.

#### <a name="simple-packaging-and-deployment"></a>Proste pakowanie i wdrażanie

AppManifest deklaruje przechowywanie wersji, kierowanie urządzeń i identyfikuje w standardowy sposób dla każdej aplikacji. Umożliwia również podpisywanie zasobów zapewniających pełną podstawę zabezpieczeń.

#### <a name="os-managed"></a>Zarządzane przez system operacyjny

System operacyjny obsługuje wszystkie procesy instalacji, aktualizowania i usuwania aplikacji. Aplikacje są instalowane na użytkownika, ale pobierane tylko raz, co minimalizuje miejsce na dysku. Firma Microsoft pracuje nad udostępnieniem środowiska MSIX w systemie Windows 7.

#### <a name="windows-provides-integrity-for-the-app"></a>System Windows zapewnia integralność aplikacji

Za pomocą podpisów cyfrowych można zagwarantować, że aplikacja nie zostanie zainstalowana z niezaufanych źródeł. MSIX uniemożliwia również manipulowanie, ponieważ:

- Zachowuje rejestr skrótów plików.
- Wykrywa, czy plik został zmodyfikowany po zakończeniu instalacji.

#### <a name="works-for-the-entire-app-catalog"></a>Działa dla całego wykazu aplikacji

Jednym z najMSIXch jest to, że działa ona dla całego katalogu aplikacji, Windows Forms, WPF, MFC/ATL, Delphi, nawet jeśli chcesz zrobić polecenie xCopy, ClickOnce lub przechodzenie do magazynu, możesz użyć tego samego pakietu MSIX.

### <a name="tools"></a>narzędzia

#### <a name="windows-application-packaging-project"></a>Projekt pakietu aplikacji systemu Windows

Możesz użyć projektu pakietu **aplikacji systemu Windows**   w programie Visual Studio, aby wygenerować pakiet dla aplikacji klasycznej. Następnie można opublikować ten pakiet w Microsoft Store lub ładowanie bezpośrednie go na co najmniej jeden komputer.

#### <a name="msix-packaging-tool"></a>Narzędzie MSIX pakowanie

Narzędzie do pakowania MSIX umożliwia ponowne spakowanie istniejących aplikacji Win32 w formacie MSIX. Oferuje interaktywny interfejs użytkownika i wiersz polecenia dla konwersji i daje możliwość konwersji aplikacji bez kodu źródłowego.

![Narzędzie MSIX pakowanie](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a>Struktura obsługi pakietów

Platforma wsparcia pakietu jest zestawem Open Source, który ułatwia stosowanie poprawek do istniejącej aplikacji Win32, gdy nie masz dostępu do kodu źródłowego, tak aby można go było uruchomić w kontenerze MSIX. Struktura obsługi pakietów ułatwia aplikacji stosowanie najlepszych rozwiązań w zakresie nowoczesnego środowiska uruchomieniowego.

#### <a name="app-installer"></a>Instalator aplikacji

Instalator aplikacji umożliwia instalowanie aplikacji systemu Windows 10 przez dwukrotne kliknięcie pakietu aplikacji. Oznacza to, że użytkownicy nie muszą używać programu PowerShell ani innych narzędzi programistycznych do wdrażania aplikacji systemu Windows 10. Instalator aplikacji może również zainstalować aplikację z sieci Web, opcjonalnych pakietów i zestawów pokrewnych.

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a>Jak utworzyć pakiet MSIX z istniejącej aplikacji klasycznej Win32

Przejdźmy przez proces, aby utworzyć pakiet MSIX z istniejącej aplikacji Win32. W tym przykładzie użyjemy aplikacji Windows Forms.

Aby rozpocząć, Dodaj nowy projekt do rozwiązania, wybierz projekt pakiet aplikacji systemu Windows i nadaj mu nazwę.

![Dodawanie nowego projektu pakietu aplikacji systemu Windows](./media/deploy-modern-applications/add-packaging-project.png)

Zostanie wyświetlona struktura projektu pakietu i zanotuj specjalny folder o nazwie *aplikacje*. Wewnątrz tego folderu możesz określić, które aplikacje mają być uwzględnione w pakiecie. Może być więcej niż jeden.

![Struktura projektu pakietu](./media/deploy-modern-applications/packaging-project.png)

Kliknij prawym przyciskiem myszy folder *aplikacje* i wybierz projekt Windows Forms, który chcesz spakować z rozwiązania programu Visual Studio.

![Dodawanie Windows Forms projektu do projektu pakietu](./media/deploy-modern-applications/add-winforms-project.png)

W tym momencie można skompilować i wygenerować pakiet, ale przeanalizować kilka rzeczy. Aby zapewnić lepsze środowisko użytkownika, program Visual Studio może automatycznie generować wszystkie elementy wizualne, a nowoczesne aplikacje muszą obsługiwać ikony i elementy zawartości kafelka dla paska kafelków i menu Start. Otwórz plik *Package. appxmanifest* , aby uzyskać dostęp do projektanta manifestu. Następnie można wygenerować wszystkie elementy wizualne z danego obrazu znajdującego się w projekcie, klikając pozycję **Utwórz**.

![Zrzut ekranu przedstawiający projektanta manifestów w programie Visual Studio](./media/deploy-modern-applications/manifest-designer.png)

Jeśli otworzysz kod pliku *Package. appxmanifest* , możesz zobaczyć kilka interesujących rzeczy.

Z prawej strony `<Package>` znajduje się `<Identity>` węzeł. Jest to miejsce, w którym spakowane aplikacje uzyskują swoją tożsamość, która będzie zarządzana przez system operacyjny.

![Węzeł tożsamości](./media/deploy-modern-applications/identity-node.png)

W `<Capabilities>` węźle można znaleźć wszystkie wymagania wymagane przez aplikację, zwracając szczególną uwagę na to `<rescap:Capability Name="runFullTrust" \>` , że system operacyjny ma uruchamiać aplikację w trybie pełnego zaufania, ponieważ jest to aplikacja Win32.

![Węzeł możliwości](./media/deploy-modern-applications/capabilities-node.png)

Ustaw projekt pakietu jako projekt startowy rozwiązania i wybierz polecenie *Uruchom*. Ma to na celu:

- Kompiluj aplikację Windows Forms.
- Utwórz pakiet MSIX z wyników kompilacji.
- Wdróż pakiety.
- Zainstaluj ją lokalnie na komputerze deweloperskim.
- Uruchomić aplikację.

![Nasza zainstalowana aplikacja](./media/deploy-modern-applications/our-installed-application.png)

Dzięki temu masz czyste środowisko instalacji i dezinstalacji, które MSIX zapewnia pełną integrację z systemem Windows 10.

Ostatnim etapem jest to, jak wdrożyć pakiet MSIX na innym komputerze.

Kliknij prawym przyciskiem myszy projekt pakiet, wybierz menu **Magazyn** , a następnie wybierz opcję **Utwórz pakiety aplikacji** .

Następnie można wybrać opcję tworzenia pakietu do przekazania do sklepu lub tworzenia pakietów na potrzeby pobierania lokalnego. W większości scenariuszy modernizacji wybierz opcję **Chcę utworzyć pakiety do pobierania lokalnego**.

![Konfigurowanie pakietów](./media/deploy-modern-applications/configuring-packages.png)

Można wybrać różne architektury, które mają być przeznaczone do obiektów docelowych, tak jak w przypadku tego samego pakietu MSIX.

Ostatnim krokiem jest zadeklarowanie miejsca, w którym chcesz wdrożyć końcowe zasoby instalacji.

![Konfiguruj ustawienia aktualizacji](./media/deploy-modern-applications/configure-update-settings.png)

Na serwerach plików przedsiębiorstwa można wybrać używanie serwera sieci Web ze współdzieloną ścieżką UNC. Zwróć uwagę na ustawienia, aby określić, w jaki sposób chcesz zaktualizować aplikację. Będziemy omawiać aktualizacje aplikacji w następnej sekcji.

Aby uzyskać szczegółowe instrukcje krok po kroku, zobacz [pakowanie aplikacji klasycznej z kodu źródłowego przy użyciu programu Visual Studio](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).

## <a name="auto-updates-in-msix"></a>Aktualizacje autoMSIX

Sklep Windows ma doskonały mechanizm aktualizacji przy użyciu Windows Update. W większości scenariuszy przedsiębiorstwa nie będziesz używać sklepu do dystrybuowania aplikacji klasycznych. W związku z tym musisz mieć podobny sposób konfigurowania aktualizacji aplikacji i ściągania ich do użytkowników.

Korzystając z kombinacji funkcji systemu Windows 10 i pakietów MSIX, możesz zapewnić użytkownikom doskonałe środowisko aktualizacji. W rzeczywistości użytkownik nie musi być w ogóle techniczny, ale nadal może korzystać z bezproblemowego środowiska aktualizacji aplikacji.

Aktualizacje można skonfigurować tak, aby współpracują z użytkownikiem na dwa różne sposoby:

- Aktualizacje monitu użytkownika: system operacyjny pokazuje jakiś automatycznie wygenerowany interfejs użytkownika z informacją o tym, że aplikacja zostanie zainstalowana. Kompiluje ten interfejs użytkownika na podstawie właściwości określonych w plikach instalacyjnych.

- Aktualizacje dyskretne w tle. W przypadku tej opcji użytkownicy nie muszą znać aktualizacji.

Można również skonfigurować, kiedy mają być przeprowadzane aktualizacje, gdy aplikacja jest uruchamiana lub regularnie. Dzięki funkcjom ładowania bezpośredniego można nawet uzyskać te aktualizacje, gdy aplikacja jest uruchomiona.

W przypadku korzystania z tego typu wdrożenia tworzony jest specjalny plik o nazwie *. Instalatora aplikacji*. Ten prosty plik zawiera następujące sekcje:

- Lokalizacja pliku *. Instalatora aplikacji*
- Główne właściwości pakietu MSIX aplikacji
- Zachowanie aktualizacji

![plik. Instalatora aplikacji](./media/deploy-modern-applications/appinstaller-file.png)

W połączeniu z tym plikiem firma Microsoft zaprojektował specjalny protokół URL do uruchamiania procesu instalacji z linku:

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

Ten protokół działa we wszystkich przeglądarkach i uruchamia proces instalacji przy użyciu doskonałego środowiska użytkownika w systemie Windows 10. Ponieważ system operacyjny zarządza procesem instalacji, jest on świadomy lokalizacji, z której aplikacja została zainstalowana, i śledzi wszystkie pliki, których dotyczy ten proces.

MSIX tworzy interfejs użytkownika na potrzeby instalacji automatycznie pokazujący pewne właściwości pakietu. Pozwala to na typowe środowisko instalacji dla każdej aplikacji.

Po wygenerowaniu nowego pakietu MSIX i przeniesieniu go na serwer wdrażania wystarczy edytować plik *. Instalatora aplikacji* , aby odzwierciedlić te zmiany, głównie wersję i ścieżkę do nowego pliku MSIX. Gdy następnym razem użytkownik uruchomi aplikację, system będzie wykryć zmianę i pobrać pliki dla nowej wersji w tle. Gdy to zrobisz, instalacja zostanie wykonana w przypadku uruchamiania nowej aplikacji w sposób niewidoczny dla użytkownika.

>[!div class="step-by-step"]
>[Poprzednie](example-migration-core.md)
