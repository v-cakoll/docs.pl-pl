---
title: .NET framework — przewodnik wdrażania dla deweloperów
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d41d1ee2ab5e423ca6a1b28a0e10bac4bc58ad79
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56094012"
---
# <a name="net-framework-deployment-guide-for-developers"></a>.NET framework — przewodnik wdrażania dla deweloperów
Ten temat zawiera informacje dla deweloperów, którzy chcą zainstalować dowolną wersję programu .NET Framework z .NET Framework 4.5 do [!INCLUDE[net_current](../../../includes/net-current-version.md)] wraz ze swoimi aplikacjami.

Łącza pobierania sekcja [pakietów redystrybucyjnych](#redistributable-packages). Możesz również pobrać pakiety do dystrybucji i pakiety językowe z tych stron witryny Microsoft Download Center:

- .NET framework 4.7.2 dla wszystkich systemów operacyjnych ([Instalator sieci web](https://go.microsoft.com/fwlink/?LinkId=863262) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=863265))

- .NET framework 4.7.1 dla wszystkich systemów operacyjnych ([Instalator sieci web](https://go.microsoft.com/fwlink/?LinkId=852095) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=852107))

- .NET framework 4.7 dla wszystkich systemów operacyjnych ([Instalator sieci web](https://go.microsoft.com/fwlink/?LinkId=825299) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=825303))

- [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] dla wszystkich systemów operacyjnych ([Instalator sieci web](https://go.microsoft.com/fwlink/?LinkId=780597) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=780601))

- [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] dla wszystkich systemów operacyjnych ([Instalator sieci web](https://go.microsoft.com/fwlink/?LinkId=671729) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=671744))

- [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] dla wszystkich systemów operacyjnych ([Instalator sieci web](https://go.microsoft.com/fwlink/?LinkId=528222) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=528232))

- .NET framework 4.5.2 dla wszystkich systemów operacyjnych ([Instalator sieci web](https://go.microsoft.com/fwlink/p/?LinkId=397703) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=397706))

- .NET framework 4.5.1 dla wszystkich systemów operacyjnych ([Instalator sieci web](https://go.microsoft.com/fwlink/p/?LinkId=310158) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=310159))

- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)

 Ważne uwagi:

> [!NOTE]
> Wyrażenie " [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i jego wydania punktowe" odnosi się do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i wszystkich nowszych wersji.

- Wersje programu .NET Framework z [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] za pośrednictwem [!INCLUDE[net_current](../../../includes/net-current-version.md)] są aktualizacje w miejscu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], co oznacza, używają tej samej wersji środowiska uruchomieniowego, ale wersje zestawów są aktualizowane i obejmują nowe typy i elementy członkowskie.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i jego wydania punktowe są tworzone przyrostowo na [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Po zainstalowaniu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub jego wydania punktowe w systemie, który ma [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zainstalowany, zestawy wersji 4 są zastępowane nowszymi wersjami.

- Jeśli odwołujesz się do programu Microsoft [pakietu out-of-band](../get-started/the-net-framework-and-out-of-band-releases.md) w swojej aplikacji zestawu zostaną uwzględnione w pakiecie aplikacji.

- Musi mieć uprawnienia administratora, aby zainstalować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i jego wydania punktowe.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Znajduje się w [!INCLUDE[win8](../../../includes/win8-md.md)] i [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], więc nie trzeba go wdrażać wraz z aplikacją w tych systemach operacyjnych. Podobnie [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] znajduje się w [!INCLUDE[win81](../../../includes/win81-md.md)] i Windows Server 2012 R2. .NET Framework 4.5.2 nie jest zawarty w systemy operacyjne. [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] Znajduje się w systemie Windows 10 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] znajduje się w aktualizacji systemu Windows 10 listopada, a [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] znajduje się w Rocznicowej aktualizacji systemu Windows 10.  .NET Framework 4.7 znajduje się w systemie Windows 10 Creators Update, programu .NET Framework 4.7.1 znajduje się w Windows 10 Fall Creators Update i .NET Framework 4.7.2 znajduje się w systemie Windows 10 października 2018 Update i Windows 10 kwietnia 2018 r. Zaktualizuj. Aby uzyskać pełną listę wymagań sprzętowych i programowych, zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).

- Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], użytkownicy mogą wyświetlić listę uruchomionych aplikacji .NET Framework podczas instalacji i łatwo je zamknąć. Może to pomóc uniknąć ponownych uruchomień systemu spowodowanych przez instalacje .NET Framework. Zobacz [zmniejszenie liczby System ponownych uruchomień](../../../docs/framework/deployment/reducing-system-restarts.md).

- Odinstalowywanie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub jeden z jego punktu również zwalnia usuwa istniejące [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] plików. Jeśli chcesz wrócić do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], należy ponownie zainstalować wraz z wszelkimi aktualizacjami do niego. (Zobacz [Instalowanie programu .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).)

- .NET Framework 4.5 redistributable został zaktualizowany na 9 października 2012 r. Aby rozwiązać problem związany z niewłaściwym znacznikiem czasu dla certyfikatu cyfrowego, który spowodował cyfrowego podpisu wygenerowanego i podpisanego przez firmę Microsoft przedwczesne wygaśnięcie. Jeśli wcześniej zainstalowano .NET Framework 4.5, pakiet redystrybucyjny z dnia 16 sierpnia 2012 r., firma Microsoft zaleca aktualizację kopii najnowszym składnikiem redystrybucyjnym z [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=245484). Aby uzyskać więcej informacji na temat tego problemu, zobacz [Microsoft Security Advisory 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

 Aby dowiedzieć się, jak jak administrator systemu może wdrożyć środowiska .NET Framework i jego zależności systemowe przez sieć, zobacz [przewodnik wdrażania dla administratorów](../../../docs/framework/deployment/guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Opcje wdrażania dla aplikacji
 Gdy wszystko będzie gotowe opublikować aplikację na serwerze sieci web lub innej scentralizowanej lokalizacji, tak aby użytkownicy mogą zainstalować ją, możesz z kilku metod wdrażania. Niektóre z nich są dostarczane z programem Visual Studio. Poniższa tabela zawiera listę opcji wdrażania dla aplikacji i określa pakietu redystrybucyjnego .NET Framework, który obsługuje poszczególne z nich. Oprócz wspomnianych można napisać niestandardowy program instalacyjny dla aplikacji; Aby uzyskać więcej informacji, zobacz sekcję [łańcucha instalacji programu .NET Framework do Instalatora aplikacji](#chaining).

|Strategia wdrażania aplikacji|Dostępne metody wdrażania|Pakiet redystrybucyjny .NET framework do użycia|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Instalowanie z sieci web|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Zestaw narzędzi WiX](#wix)<br />- [Instalacja ręczna](#installing_manually)|[Instalator sieci Web](#redistributable-packages)|
|Instalowanie z dysku|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Zestaw narzędzi WiX](#wix)<br />- [Instalacja ręczna](#installing_manually)|[Instalator w trybie offline](#redistributable-packages)|
|Instalowanie z sieci lokalnej (dla aplikacji korporacyjnych)|- [ClickOnce](#clickonce-deployment)|Albo [Instalator sieci web](#redistributable-packages) (zobacz [ClickOnce](#clickonce-deployment) dla ograniczeń) lub [Instalator w trybie offline](#redistributable-packages)|

## <a name="redistributable-packages"></a>Pakiety redystrybucyjne
 .NET Framework jest dostępna w dwóch pakietach redystrybucyjnych: sieci web, pliki Instalatora (program inicjujący) i Instalator w trybie offline (autonomiczny redystrybucyjny). W poniższej tabeli porównano dwa pakiety.

||Instalator sieci Web|Instalator w trybie offline|
|-|-------------------|-----------------------|
|Pobierz plik|.NET Framework 4.7.2: <br/>[NDP472-KB4054531-Web.exe](https://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>.NET Framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](https://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>.NET Framework 4.7: <br />[NDP47-KB3186500-Web.exe](https://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151802-Web.exe](https://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]:<br />[NDP461-KB3102438-Web.exe](https://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]:<br />[NDP46-KB3045560-Web.exe](https://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](https://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2859818-Web.exe](https://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_setup.exe](https://go.microsoft.com/fwlink/?LinkId=225704)|.NET Framework 4.7.2: <br/>[NDP472-KB4054530-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>.NET Framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET Framework 4.7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_x86_x64.exe](https://go.microsoft.com/fwlink/?LinkId=225702)|
|Wymagane połączenie z Internetem?|Tak|Nie|
|Wielkość pliku do pobrania|Mniejsza (zawiera Instalator dla docelowej platformy) *|Większe *|
|Pakiety językowe|Included**|Musi być [zainstalowany oddzielnie](#chain_langpack), chyba że używasz pakietu, który jest przeznaczony dla wszystkich systemów operacyjnych|
|Metoda wdrażania|Obsługuje wszystkie metody:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Instalator Windows XML (WiX)](#wix)<br />- [Instalacja ręczna](#installing_manually)<br />- [Instalacja niestandardowa (łańcuch)](#chaining)|Obsługuje wszystkie metody:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Instalator Windows XML (WiX)](#wix)<br />- [Instalacja ręczna](#installing_manually)<br />- [Instalacja niestandardowa (łańcuch)](#chaining)|
|Lokalizacja pliku do pobrania dla wdrażania ClickOnce|Centrum pobierania Microsoft:<br /><br /> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863262) <br/> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET Framework 4.7](https://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET Framework 4.6](https://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|Twój własny serwer lub Microsoft Download Center:<br /><br /> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863265)<br /> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET Framework 4.7](https://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET Framework 4.6](https://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|

 \* Instalator w trybie offline jest większy, ponieważ zawiera komponenty dla wszystkich platform docelowych. Po zakończeniu działania Instalatora, system operacyjny Windows buforuje tylko Instalatora, który został użyty. Jeśli Instalator w trybie offline jest usuwany po zakończeniu instalacji, miejsce na dysku, używane jest taka sama, który jest używany przez Instalator sieci web. Jeśli używasz narzędzia (na przykład [InstallAware](#installaware-deployment) lub [InstallShield](#installshield-deployment)) do tworzenia programu instalacyjnego aplikacji udostępnia folder pliku instalacyjnego, który jest usuwany po instalacji, Instalator w trybie offline może być automatycznie usuwane przez umieszczenie go w folderze instalacyjnym.

 ** W przypadku korzystania z Instalatora sieci web z konfiguracją niestandardowego, możesz użyć domyślnych ustawień języka na podstawie ustawienia wielojęzycznego interfejsu użytkownika (MUI) użytkownika lub określić inny pakiet językowy przy użyciu `/LCID` opcji w wierszu polecenia. Zobacz sekcję [Instalacja łańcuchowa przy użyciu interfejsu użytkownika domyślne Framework .NET](#chaining_default) przykłady.

## <a name="deployment-methods"></a>Metody wdrażania
 Dostępne są cztery metody wdrażania:

- Możesz ustawić zależność od programu .NET Framework. .NET Framework można określić jako warunek wstępny instalacji danej aplikacji przy użyciu jednej z następujących metod:

    - Użyj [wdrażania ClickOnce](#clickonce-deployment) (dostępne w programie Visual Studio)

    - Tworzenie [projektu InstallAware](#installaware-deployment) (bezpłatną dostępne dla użytkowników programu Visual Studio)

    - Tworzenie [projekt InstallShield](#installshield-deployment) (dostępne w programie Visual Studio)

    - Użyj [zestaw narzędzi XML Instalatora Windows (WiX)](#wix)

- Można Poproś użytkowników o [ręcznie zainstaluj program .NET Framework](#installing_manually).

- Można połączyć w łańcuch (Dołącz) programu .NET Framework procesu w aplikacji ustawienia instalacji i zdecyduj, jak chcesz obsługiwać środowisko instalacji .NET Framework:

    - [Użyj domyślnego interfejsu użytkownika](#chaining_default). Pozwól Instalatora programu .NET Framework zapewnia środowisko instalacji.

    - [Dostosowywanie interfejsu użytkownika](#chaining_custom) przedstawić ujednoliconej instalacji oraz monitorować postępy instalacji na .NET Framework.

 Te metody wdrażania opisano szczegółowo w poniższych sekcjach.

## <a name="setting-a-dependency-on-the-net-framework"></a>Ustawianie zależności dla programu .NET Framework
Użycie technologii ClickOnce, InstallAware, InstallShield lub WiX do wdrożenia aplikacji, możesz dodać zależność od programu .NET Framework, dzięki czemu można zainstalować jako część aplikacji.

### <a name="clickonce-deployment"></a>wdrożenie ClickOnce
 Wdrażanie ClickOnce jest dostępne dla projektów, które są tworzone za pomocą języka Visual Basic i Visual C#, ale nie jest dostępna dla języka Visual C++.

 W programie Visual Studio, aby wybrać wdrażanie ClickOnce i dodać zależność od programu .NET Framework:

1.  Otwórz projekt aplikacji którą chcesz opublikować.

2.  W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.

3.  Wybierz **Publikuj** okienka.

4.  Wybierz **wymagania wstępne** przycisku.

5.  W **wymagania wstępne** okna dialogowego pole, upewnij się, że **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.

6.  Na liście wymagań wstępnych Znajdź i wybierz wersję programu .NET Framework, który został użyty do utworzenia projektu.

7.  Wybierz opcję, aby określić lokalizację źródłową wymagań wstępnych, a następnie wybierz **OK**.

     Jeśli podasz adres URL dla lokalizacji pobierania .NET Framework, można określić witrynę Microsoft Download Center lub własnej witryny. Jeśli umieszczasz pakiet redystrybucyjny na własnym serwerze, musi to być Instalator w trybie offline, a nie Instalator sieci web. Możesz tylko połączyć Instalator sieci web w Microsoft Download Center. Adres URL można także określić dysk, na którym jest rozpowszechniana własną aplikację.

8.  W **stron właściwości** okna dialogowego wybierz **OK**.

<a name="installaware"></a> 
### <a name="installaware-deployment"></a>InstallAware wdrożenia
InstallAware tworzy aplikację Windows (APPX), Instalator Windows (MSI), kodu natywnego (EXE) i pakietów programu App-V (Wirtualizacja aplikacji) z jednego źródła. Łatwo [zawierają żadnej wersji programu .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) w ustawieniach, opcjonalnie dostosowywanie instalacji przez [edycji skryptów domyślne](https://www.installaware.com/msicode.htm). InstallAware instaluje wstępnie certyfikaty na Windows 7, bez których instalacja programu .NET Framework 4.7 kończy się niepowodzeniem. Aby uzyskać więcej informacji na temat InstallAware, zobacz [InstallAware dla Instalatora Windows](https://www.installaware.com/) witryny sieci Web.

### <a name="installshield-deployment"></a>Wdrażanie InstallShield
 W programie Visual Studio, aby wybrać wdrażanie InstallShield i dodać zależność od programu .NET Framework:

1.  Na pasku menu programu Visual Studio, wybierz **pliku**, **New**, **projektu**.

2.  W okienku po lewej stronie **nowy projekt** okna dialogowego wybierz **inne typy projektów**, **instalacja i wdrożenie**, **InstallShield LE**.

3.  W **nazwa** polu, wpisz nazwę dla projektu, a następnie wybierz **OK**.

4.  Jeśli tworzysz projekt instalacji i wdrożenia po raz pierwszy, wybierz opcję **przejdź do programu InstallShield** lub **Włącz InstallShield Limited Edition** pobierania programu InstallShield Limited Edition dla używanej wersji programu Microsoft Visual Studio. Uruchom ponownie program Visual Studio.

5.  Przejdź do **Asystent projektu** kreatora i wybierz polecenie **pliki aplikacji** można dodać danych wyjściowych projektu. Inne atrybuty projektu można skonfigurować za pomocą tego kreatora.

6.  Przejdź do **wymagania dotyczące instalacji** i wybierz systemy operacyjne oraz wersję programu .NET Framework, którą chcesz zainstalować.

7.  Otwórz menu skrótów projektu Instalatora i wybierz polecenie **kompilacji**.
 
<a name="wix"></a> 
### <a name="windows-installer-xml-wix-deployment"></a>Wdrożenie XML Instalatora Windows (WiX)
 Zestaw narzędzi XML Instalatora Windows (WiX) tworzy pakiety instalacyjne Windows z kodu źródłowego XML. WiX obsługuje środowisko wiersza polecenia, które można zintegrować procesom kompilacji do tworzenia pakietów Instalatora MSI i MSM. Za pomocą WiX, możesz [określić .NET Framework jako warunek wstępny](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html), lub [utworzyć moduł łańcucha](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) w pełni kontrolować proces wdrażania .NET Framework. Aby uzyskać więcej informacji na temat Instalatora WiX, zobacz [zestaw narzędzi XML Instalatora Windows (WiX)](http://wixtoolset.org/) witryny sieci Web.

<a name="installing_manually"></a> 
## <a name="installing-the-net-framework-manually"></a>Ręczne instalowanie programu .NET Framework
 W niektórych sytuacjach może być niepraktyczne, aby automatycznie zainstalować program .NET Framework z aplikacją. W takim przypadku można zalecić użytkownikom, instalowanie programu .NET Framework, samodzielnie. Pakiet redystrybucyjny jest dostępny w [dwa pakiety](#redistributable-packages). W trakcie procesu instalacji zawiera instrukcji dotyczących sposobu znajdowania i instalowania programu .NET Framework użytkowników.

<a name="chaining"></a> 
## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Tworzenie łańcuchów instalacji programu .NET Framework do Instalatora aplikacji
 Jeśli tworzysz niestandardowy program instalacyjny dla aplikacji, można połączyć w łańcuch (Dołącz) proces instalacji programu .NET Framework w procesie instalacji aplikacji. Łańcucha są dostępne dwie opcje interfejsu użytkownika dla instalacji programu .NET Framework:

- Użyj domyślnego interfejsu użytkownika z Instalatora programu .NET Framework.

- Tworzenie niestandardowego interfejsu użytkownika dla instalacji programu .NET Framework w celu zachowania spójności z Instalatorem aplikacji.

 Obie metody umożliwiają używanie Instalatora sieci web lub Instalatora w trybie offline. Każdy pakiet ma swoje zalety:

- Jeśli używasz Instalatora sieci web, proces instalacji programu .NET Framework zdecyduj, który pakiet instalacyjny jest wymagany i pobierze i zainstaluje tylko tego pakietu z sieci web.

- Jeśli używasz Instalatora w trybie offline, może zawierać kompletny zestaw pakietów instalacyjnych .NET Framework za pomocą usługi nośniku redystrybucyjnym, aby użytkownicy nie musieli pobierać żadnych dodatkowych plików z sieci web podczas instalacji.

<a name="chaining_default"></a> 
### <a name="chaining-by-using-the-default-net-framework-ui"></a>Instalacja łańcuchowa przy użyciu domyślnego interfejsu użytkownika programu .NET Framework
 Aby dyskretnie połączyć w łańcuch proces instalacji programu .NET Framework i pozwolić Instalatora programu .NET Framework zapewnił UI, Dodaj następujące polecenie do programu instalacyjnego:

```
<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>
```

 Na przykład, jeśli programu wykonywalnego to Contoso.exe i chcesz, aby dyskretnie zainstalować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pakiet redystrybucyjny w trybie offline, użyj polecenia:

```
dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso
```

 Dodatkowe opcje wiersza polecenia można użyć do dostosowania instalacji. Na przykład:

- Udostępniający użytkownicy mogli zamknąć uruchamiania aplikacji .NET Framework w celu zminimalizowania ponownego uruchomienia systemu, ustaw tryb pasywny i użyj `/showrmui` opcji w następujący sposób:

    ```
    dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso
    ```

     To polecenie umożliwia Menedżera ponownego uruchamiania wyświetlić okno komunikatu, które daje użytkownikom możliwość zamknięcia aplikacji .NET Framework przed zainstalowaniem programu .NET Framework.

- Jeśli używasz Instalatora sieci web, możesz użyć `/LCID` opcję, aby określić pakiet językowy. Na przykład do łańcucha [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalator do programu instalacyjnego Contoso sieci web i zainstaluj pakiet języka japońskiego, należy dodać następujące polecenie, aby proces instalacji aplikacji:

    ```
    dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041
    ```

     Jeżeli pominięto `/LCID` opcji, Instalator zainstaluje pakiet językowy, który odpowiada ustawieniu MUI użytkownika.

    > [!NOTE]
    > Różne pakiety językowe mogą mieć różne daty wydania. Jeśli pakiet językowy, który określisz nie jest dostępny w Centrum pobierania, Instalator zainstaluje programu .NET Framework bez pakietu językowego. Jeśli programu .NET Framework jest już zainstalowany na komputerze użytkownika, Instalator zainstaluje tylko pakiet językowy.

 Aby uzyskać pełną listę opcji, zobacz [opcje wiersza polecenia](#command-line-options) sekcji.

 Wspólne kody powrotne, zobacz [kody powrotne](#return-codes) sekcji.

<a name="chaining_custom"></a>
### <a name="chaining-by-using-a-custom-ui"></a>Instalacja łańcuchowa przy użyciu niestandardowego interfejsu użytkownika
 Jeśli masz niestandardowy pakiet Instalatora, możesz dyskretnie uruchomić i śledzić instalację .NET Framework podczas wyświetlania własnego widoku postępu instalacji. Jeśli jest to możliwe, upewnij się, że Twój kod obejmuje następujące czynności:

- Wyszukaj [wymagania dotyczące sprzętu i oprogramowania .NET Framework](../../../docs/framework/get-started/system-requirements.md).

- [Wykrywanie](#detect_net) czy poprawną wersję programu .NET Framework jest już zainstalowana na komputerze użytkownika.

    > [!IMPORTANT]
    > Przy określaniu, czy jest już zainstalowana poprawna wersja programu .NET Framework, należy sprawdzić, czy wersji docelowej *lub* zainstalowana nowsza wersja nie, czy jest zainstalowany w wersji docelowej. Innymi słowy, należy ocenić, czy klucz wersji, możesz pobrać z rejestru jest większa lub równa klucz wydania wersji docelowej, *nie* tego, czy jest równa klucz wydania wersji docelowej.

- [Wykrywanie](#detecting-the-language-packs) tego, czy pakiety językowe są już zainstalowane na komputerze użytkownika.

- Jeśli chcesz kontrolować wdrażanie, dyskretnie Uruchom i Śledź proces instalacji programu .NET Framework (zobacz [jak: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)).

- Jeśli wdrażasz Instalator w trybie offline, [oddzielnie łańcucha pakietów językowych](#chain_langpack).

- Dostosuj wdrażanie za pomocą [opcje wiersza polecenia](#command-line-options). Na przykład, jeśli do łańcucha Instalator sieci web .NET Framework, ale chcesz zastąpić domyślny pakiet językowy, użyj `/LCID` opcji, zgodnie z opisem w poprzedniej sekcji.

- [Rozwiązywanie problemów z](#troubleshooting).

<a name="detect_net"></a>
### <a name="detecting-the-net-framework"></a>Wykrywanie programu .NET Framework
 Instalator .NET Framework zapisuje klucze rejestru, gdy instalacja się powiedzie. Można sprawdzić, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszy jest zainstalowany, sprawdzając `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` folderu w rejestrze `DWORD` wartość o nazwie `Release`. (Zwróć uwagę, że "NET Framework Setup" nie rozpoczyna się kropką). Istnienie tego klucza oznacza, że [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowsza wersja została zainstalowana na tym komputerze. Wartość `Release` wskazuje, która wersja programu .NET Framework jest zainstalowana.

> [!IMPORTANT]
> Należy sprawdzić wartość **większa lub równa** wartość słowa kluczowego wersji podczas próby wykrycia, czy występuje określonej wersji.

|Wersja|Wartość DWORD dotycząca wersji|
|-------------|--------------------------------|
|.NET framework 4.7.2 zainstalowany w systemie Windows 10 kwietnia 2018 r. Zaktualizuj i w systemie Windows Server w wersji 1803|461808|
|.NET framework 4.7.2 zainstalowane we wszystkich wersjach systemów operacyjnych innych niż Windows 10 kwietnia 2018 Update i Windows Server w wersji 1803. W tym Windows 10 października 2018 r. Zaktualizuj. |461814|
|.NET framework 4.7.1 zainstalowane na Windows 10 Fall Creators Update oraz w systemie Windows Server w wersji 1709|461308|
|.NET framework 4.7.1 zainstalowane we wszystkich wersjach systemów operacyjnych innych niż Windows 10 Fall Creators Update i Windows Server w wersji 1709|461310|
|.NET framework 4.7 zainstalowanym systemem Windows 10 Creators Update|460798|
|.NET framework 4.7 zainstalowane we wszystkich wersjach systemów operacyjnych innych niż Windows 10 Creators Update|460805|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] zainstalowane w systemie Windows 10 Anniversary Edition i systemie Windows Server 2016|394802|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] zainstalowane we wszystkich wersjach systemów operacyjnych innych niż Windows 10 Anniversary Edition i Windows Server 2016|394806|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] zainstalowane w aktualizacji systemu Windows 10 listopada|394254|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] zainstalowane we wszystkich wersjach systemu operacyjnego innego niż aktualizacji systemu Windows 10 listopada|394271|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] zainstalowane w systemie Windows 10|393295|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] zainstalowane we wszystkich wersjach systemów operacyjnych innych niż Windows 10|393297|
|.NET Framework 4.5.2|379893|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] zainstalowane z [!INCLUDE[win81](../../../includes/win81-md.md)] lub Windows Server 2012 R2|378675|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] zainstalowana na [!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7|378758|
|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|378389|

### <a name="detecting-the-language-packs"></a>Wykrywanie pakietów językowych
 Możesz sprawdzić, czy dany pakiet językowy jest zainstalowany, sprawdzając HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework setup\ndp\v4\full ma\\*LCID* folderu w rejestrze wartość DWORD o nazwie `Release`. (Zwróć uwagę, że "NET Framework Setup" nie rozpoczyna się kropką). *Identyfikator LCID* Określa identyfikator ustawień regionalnych; zobacz [obsługiwane języki](#supported-languages) Aby uzyskać listę.

 Na przykład, aby wykryć czy pełny pakiet języka japońskiego (LCID = 1041) jest zainstalowany, sprawdź, czy są dostępne następujące wartości w rejestrze:

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041
Name: Release
Type: DWORD
```

 Aby ustalić, czy dla konkretnej wersji programu .NET Framework 4.5, za pośrednictwem 4.7.2 zainstalowano ostateczna wersja pakietu językowego, sprawdź wartość wartości DWORD klucza RELEASE opisanego w poprzedniej sekcji [wykrywanie programu .NET Framework](#detect_net).

<a name="chain_langpack"></a> 
### <a name="chaining-the-language-packs-to-your-app-setup"></a>Tworzenie łańcuchów języka pakietów do ustawień aplikacji
 .NET Framework udostępnia zestaw autonomicznych języka plików wykonywalnych pakietu, które zawierają zlokalizowane zasoby dla określonych kultur. Pakiety językowe są dostępne z Microsoft Download Center:

- [Pakiety językowe .NET framework 4.7.2](https://go.microsoft.com/fwlink/p/?LinkId=863258)

- [Pakiety językowe .NET framework 4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090)

- [Pakiety językowe programu .NET framework 4.7](https://go.microsoft.com/fwlink/p/?LinkId=825306)

- [.NET framework 4.6.2 language Pack](https://go.microsoft.com/fwlink/p/?LinkId=780604)

- [.NET framework 4.6.1 language Pack](https://go.microsoft.com/fwlink/p/?LinkId=671747)

- [Pakiety językowe .NET framework 4.6](https://go.microsoft.com/fwlink/p/?LinkId=528314)

- [Pakiety językowe .NET framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397701)

- [.NET framework 4.5.1 language Pack](https://go.microsoft.com/fwlink/p/?LinkId=322101)

- [Pakiety językowe .NET framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Pakiety językowe nie zawierają składników programu .NET Framework, które są wymagane do uruchamiania aplikacji; za pomocą sieci web lub Instalatora w trybie offline, przed zainstalowaniem pakietu językowego, należy zainstalować .NET Framework.

 Począwszy od [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], nazwy pakietów przyjmują formularza NDP <`version`>-KB <`number`>-x86-x64 - AllOS - <`culture`> .exe, gdzie `version` jest numer wersji programu .NET Framework, `number` jest Numer artykułu bazy wiedzy Microsoft Knowledge Base, i `culture` Określa [kraj/region](#supported-languages). Na przykład jeden z tych pakietów `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Nazwy pakietów są wymienione w [pakietów redystrybucyjnych](#redistributable-packages) sekcji we wcześniejszej części tego artykułu.

 Aby zainstalować pakiet językowy z Instalatora w trybie offline programu .NET Framework, można go połączyć z własnym Instalatorem aplikacji. Na przykład, aby wdrożyć [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] Instalator w trybie offline z pakietem języka japońskiego, należy użyć następującego polecenia:

```
NDP451-KB2858728-x86-x64-AllOS-JPN.exe/q /norestart /ChainingPackage <ProductName>
```

 Nie masz do łańcucha pakietów językowych, jeśli używasz Instalatora sieci web; Instalator zainstaluje pakiet językowy, który odpowiada ustawieniu MUI użytkownika. Jeśli chcesz zainstalować inny język, możesz użyć `/LCID` opcję, aby określić pakiet językowy.

 Aby uzyskać pełną listę opcji wiersza polecenia, zobacz [opcje wiersza polecenia](#command-line-options) sekcji.

### <a name="troubleshooting"></a>Rozwiązywanie problemów

#### <a name="return-codes"></a>Kody powrotne
 W poniższej tabeli wymieniono najbardziej typowe kody powrotne dla Instalatora pakiet redystrybucyjny programu .NET Framework. Kody powrotne są takie same dla wszystkich wersji instalatora. Aby uzyskać łącza do szczegółowych informacji zobacz następną sekcję.

|Kod powrotu|Opis|
|-----------------|-----------------|
|0|Instalacja została zakończona pomyślnie.|
|1602|Użytkownik anulował instalację.|
|1603|Podczas instalacji wystąpił błąd krytyczny.|
|1641|Do ukończenia instalacji wymagane jest ponowne uruchomienie komputera. Ten komunikat oznacza sukces.|
|3010|Do ukończenia instalacji wymagane jest ponowne uruchomienie komputera. Ten komunikat oznacza sukces.|
|5100|Komputer użytkownika nie spełnia wymagań systemowych.|

#### <a name="download-error-codes"></a>Kody błędów pobierania
 Zobacz następującą zawartość:

- [Kody błędów Intelligent Transfer Service (BITS) w tle](https://go.microsoft.com/fwlink/?LinkId=180946)

- [Kody błędu krótkiej nazwy adresu URL](https://go.microsoft.com/fwlink/?LinkId=180947)

- [Kody błędów usługi WinHttp](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Inne kody błędów
 Zobacz następującą zawartość:

- [Kody błędów usługi Instalator Windows](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Kody wyników programu Windows Update Agent](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Odinstalowywanie programu .NET Framework
 Począwszy od [!INCLUDE[win8](../../../includes/win8-md.md)], możesz odinstalować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub jeden z jego punktu zwalnia przy użyciu **Windows Włącz lub wyłącz funkcje** w Panelu sterowania. W starszych wersjach systemu Windows, możesz odinstalować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub jeden z jego punktu zwalnia przy użyciu **apletu Dodaj lub usuń programy** w Panelu sterowania.

> [!IMPORTANT]
> Windows 7 i starszych systemów operacyjnych, odinstalowywanie [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 lub 4.7.2 nie przywraca [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] plików i odinstalowywania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie przywraca [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] plików. Jeśli chcesz wrócić do starszej wersji, należy ponownie zainstalować wraz z wszelkimi aktualizacjami do niego.

## <a name="appendix"></a>Dodatek

### <a name="command-line-options"></a>Opcje wiersza polecenia
 W poniższej tabeli wymieniono opcje, które można uwzględnić podczas tworzenia łańcucha [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pakietu redystrybucyjnego umożliwiającego własnym Instalatorem aplikacji.

|Opcja|Opis|
|------------|-----------------|
|**/CEIPConsent**|Zastępuje domyślne zachowanie i wysyła anonimowe opinie do firmy Microsoft w celu wdrażania w przyszłości. Ta opcja może służyć tylko wtedy, gdy Instalator monituje o zgodę, i jeśli użytkownik udziela uprawnień do wysyłania anonimowych opinii do firmy Microsoft.|
|**chainingpackage** `packageName`|Określa nazwę pliku wykonywalnego, który tworzy łańcuch. Te informacje są wysyłane do firmy Microsoft, jak napotyka anonimowe opinie do ulepszania wdrażania w przyszłości.<br /><br /> Jeśli nazwa pakietu zawiera spacje, należy użyć podwójnego cudzysłowu jako ogranicznika; na przykład: **chainingpackage "Lucerne Publishing"**. Na przykład pakiet łańcuchowy zobacz [uzyskiwanie informacji o postępie z pakietu instalacyjnego](https://go.microsoft.com/fwlink/?LinkId=181926) w bibliotece MSDN.|
|**/LCID**  `LCID`<br /><br /> gdzie `LCID` Określa identyfikator ustawień regionalnych (zobacz [obsługiwane języki](#supported-languages))|Instaluje pakiet językowy określony przez `LCID` i wymusza wyświetlanie interfejsu użytkownika, które mają być wyświetlane w tym języku, o ile nie jest ustawiony tryb cichy.<br /><br /> Aby uzyskać Instalator sieci web ta opcja instaluje łańcuchowo pakiet językowy z sieci web. **Uwaga:**  Użyj tej opcji tylko w przypadku Instalatora sieci web.|
|**/ log** `file`&#124; `folder`|Określa lokalizację pliku dziennika. Wartość domyślna to folder tymczasowy dla procesu, a domyślna nazwa pliku opiera się na pakiet. Jeśli rozszerzenie .txt, generowany jest Dziennik tekstowy. Jeśli określisz dowolne inne rozszerzenie lub Brak rozszerzenia, zostanie utworzony dziennik HTML.|
|**/msioptions**|Określa opcje przekazywane do elementów .msi i .msp; na przykład: `/msioptions "PROPERTY1='Value'"`.|
|**/ norestart /**|Uniemożliwia automatyczne ponowne uruchomienie programu instalacyjnego. Jeśli używasz tej opcji, aplikacja połączona w łańcuch musi przechwytywać kod powrotny i obsługiwać ponowny rozruch (zobacz [uzyskiwanie informacji o postępie z pakietu instalacyjnego](https://go.microsoft.com/fwlink/?LinkId=179606) w bibliotece MSDN).|
|**/ passive**|Ustawia tryb pasywny. Wyświetla pasek postępu, aby wskazać, że instalacja jest w toku, ale nie wyświetla żadnych monitów ani komunikatów o błędzie dla użytkownika. W tym trybie, gdy łańcuchowa program instalacyjny jest, pakiet łańcuchowy musi obsłużyć [kody powrotne](#return-codes).|
|**/pipe**|Tworzy kanał komunikacyjny, aby umożliwić pobieranie danych o postępie przez pakiet łańcuchowy.|
|**promptrestart**|Tylko tryb pasywny, jeśli program instalacyjny wymaga ponownego uruchomienia, użytkownik jest monitowany. Ta opcja wymaga interakcji użytkownika, jeśli wymagane jest ponowne uruchomienie komputera.|
|**/q**|Ustawia tryb cichy.|
|**/ Repair**|Uruchamia funkcję naprawy.|
|**/serialdownload**|Wymusza instalację dopiero, po pobraniu pakietu.|
|**/showfinalerror**|Ustawia tryb pasywny. Wyświetla błędy tylko wtedy, gdy instalacja nie powiodła się. Ta opcja wymaga interakcji użytkownika, jeśli instalacja nie powiodła się.|
|**/showrmui**|Używana tylko z **/passive** opcji. Wyświetla okno komunikatu, który monituje użytkowników o konieczności zamykania aplikacji .NET Framework, które są aktualnie uruchomione. To okno komunikatu zachowuje się takie same, w trybie pasywnym pasywnym i niepasywnym.|
|**/uninstall**|Odinstalowuje pakiet redystrybucyjny programu .NET Framework.|

### <a name="supported-languages"></a>Obsługiwane języki
W poniższej tabeli wymieniono pakiety językowe .NET Framework, które są dostępne dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i jego wydania punktowe.

|LCID|Język — kraj/region|Kultura|
|----------|--------------------------------|-------------|
|1025|Arabski — Arabia Saudyjska|ar|
|1028|Chiński (tradycyjny)|zh-Hant|
|1029|czeski|cs|
|1030|duński|da|
|1031|Niemiecki (Niemcy)|Niemcy|
|1032|grecki|el|
|1035|fiński|fi|
|1036|Francuski (Francja)|fr|
|1037|Hebrajski|ADAM|
|1038|węgierski|hu|
|1040|Włoski (Włochy)|go|
|1041|japoński|ja|
|1042|koreański|ko|
|1043|Holenderski (Holandia)|nl|
|1044|Norwegian (Bokmål)|Brak|
|1045|polski|pl|
|1046|Portugalski (Brazylia)|pt-BR|
|1049|Rosyjski|ru|
|1053|szwedzki|sv|
|1055|turecki|tr|
|2052|Chiński (uproszczony)|zh-Hans|
|2070|Portugalski — Portugalia|pt-PT|
|3082|Hiszpański — Hiszpania (nowoczesny)|es|

## <a name="see-also"></a>Zobacz także
- [Przewodnik wdrażania dla administratorów](../../../docs/framework/deployment/guide-for-administrators.md)
- [Wymagania systemowe](../../../docs/framework/get-started/system-requirements.md)
- [Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md)
- [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
- [Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)
- [Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
