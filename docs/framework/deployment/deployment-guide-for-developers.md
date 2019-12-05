---
title: .NET Framework Przewodnik wdrażania dla deweloperów
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
ms.openlocfilehash: 62777356dae6e2dce9753b832f08ab2fa2cb5881
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801876"
---
# <a name="net-framework-deployment-guide-for-developers"></a>.NET Framework Przewodnik wdrażania dla deweloperów
Ten temat zawiera informacje dla deweloperów, którzy chcą zainstalować dowolną wersję .NET Framework z .NET Framework 4,5, aby [!INCLUDE[net_current](../../../includes/net-current-version.md)] z ich aplikacjami.

Linki do pobrania znajdują się w sekcji [pakiety redystrybucyjne](#redistributable-packages). Pakiety i pakiety językowe pakietu redystrybucyjnego można także pobrać z tych stron centrum pobierania Microsoft:

- .NET Framework 4,8 dla wszystkich systemów operacyjnych ([Instalator sieci Web](https://go.microsoft.com/fwlink/?LinkId=2085155) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/?linkid=2088631))

- .NET Framework 4.7.2 dla wszystkich systemów operacyjnych ([Instalator sieci Web](https://go.microsoft.com/fwlink/?LinkId=863262) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=863265))

- .NET Framework 4.7.1 dla wszystkich systemów operacyjnych ([Instalator sieci Web](https://go.microsoft.com/fwlink/?LinkId=852095) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=852107))

- .NET Framework 4,7 dla wszystkich systemów operacyjnych ([Instalator sieci Web](https://go.microsoft.com/fwlink/?LinkId=825299) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=825303))

- .NET Framework 4.6.2 dla wszystkich systemów operacyjnych ([Instalator sieci Web](https://go.microsoft.com/fwlink/?LinkId=780597) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=780601))

- .NET Framework 4.6.1 dla wszystkich systemów operacyjnych ([Instalator sieci Web](https://go.microsoft.com/fwlink/?LinkId=671729) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=671744))

- .NET Framework 4,6 dla wszystkich systemów operacyjnych ([Instalator sieci Web](https://go.microsoft.com/fwlink/?LinkId=528222) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=528232))

- .NET Framework 4.5.2 dla wszystkich systemów operacyjnych ([Instalator sieci Web](https://go.microsoft.com/fwlink/p/?LinkId=397703) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=397706))

- .NET Framework 4.5.1 dla wszystkich systemów operacyjnych ([Instalator sieci Web](https://go.microsoft.com/fwlink/p/?LinkId=310158) lub [Instalator w trybie offline](https://go.microsoft.com/fwlink/p/?LinkId=310159))

- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)

 Ważne uwagi:

> [!NOTE]
> Fraza ".NET Framework 4,5 i jej wydania punktowe" odnosi się do .NET Framework 4,5 i wszystkich nowszych wersji.

- Wersje .NET Framework z .NET Framework 4.5.1 przez [!INCLUDE[net_current](../../../includes/net-current-version.md)] to aktualizacje w miejscu do .NET Framework 4,5, co oznacza, że korzystają z tej samej wersji środowiska uruchomieniowego, ale wersje zestawu są aktualizowane i zawierają nowe typy i elementy członkowskie.

- .NET Framework 4,5 i jego wydania punktowe są kompilowane przyrostowo na .NET Framework 4. W przypadku zainstalowania .NET Framework 4,5 lub jego wydań w systemie, w którym zainstalowano .NET Framework 4, zestawy w wersji 4 są zastępowane nowszymi wersjami.

- Jeśli odwołujesz się do [pakietu oprogramowania poza pasmem](../get-started/the-net-framework-and-out-of-band-releases.md) w aplikacji, zestaw zostanie uwzględniony w pakiecie aplikacji.

- Musisz mieć uprawnienia administratora, aby zainstalować .NET Framework 4,5 i jego wydania punktowe.

- .NET Framework 4,5 jest dołączony do systemu Windows 8 i [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], dlatego nie trzeba wdrażać go w aplikacji w tych systemach operacyjnych. Podobnie .NET Framework 4.5.1 znajduje się w Windows 8.1 i Windows Server 2012 R2. .NET Framework 4.5.2 nie jest uwzględniony w żadnym systemie operacyjnym. .NET Framework 4,6 jest zawarty w systemie Windows 10, .NET Framework 4.6.1 jest zawarty w aktualizacji systemu Windows 10 listopad i .NET Framework 4.6.2 jest uwzględniony w rocznicowej aktualizacji systemu Windows 10.  .NET Framework 4,7 jest zawarta w aktualizacji systemu Windows 10 dla twórców, .NET Framework 4.7.1 jest dołączany do aktualizacji systemu Windows 10 dla twórców, a aktualizacja .NET Framework 4.7.2 została uwzględniona w aktualizacji systemu Windows 10 z października 2018 i Windows 10 kwietnia 2018. .NET Framework 4,8 jest dołączony do aktualizacji systemu Windows 10 maja 2019. Aby zapoznać się z pełną listą wymagań sprzętowych i programowych, zobacz [wymagania systemowe](../get-started/system-requirements.md).

- Począwszy od .NET Framework 4,5, użytkownicy mogą wyświetlić listę uruchomionych .NET Framework aplikacji podczas instalacji i łatwo je zamknąć. Może to pomóc uniknąć ponownych uruchomień systemu spowodowanych przez instalacje .NET Framework. Zobacz [redukowanie ponownych uruchomień systemu](reducing-system-restarts.md).

- Odinstalowanie .NET Framework 4,5 lub jednej z jego wydań w punkcie spowoduje również usunięcie istniejących wcześniej plików .NET Framework 4. Jeśli chcesz wrócić do .NET Framework 4, musisz zainstalować ją ponownie i wszystkie jej aktualizacje. Zobacz [instalowanie .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).

- .NET Framework 4.5 Redistributable został zaktualizowany w dniu 9 października 2012 r., aby rozwiązać problem związany z niewłaściwym znacznikiem czasu dla certyfikatu cyfrowego, który spowodował przedwczesne wygaśnięcie cyfrowego podpisu wygenerowanego i podpisanego przez firmę Microsoft. Jeśli wcześniej zainstalowano pakiet redystrybucyjny .NET Framework 4,5 z 16 sierpnia 2012, Zalecamy zaktualizowanie kopii przy użyciu najnowszego pakietu redystrybucyjnego z [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=245484). Aby uzyskać więcej informacji o tym problemie, zobacz [Poradnik zabezpieczeń firmy Microsoft 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

Aby uzyskać informacje o tym, jak administrator systemu może wdrożyć .NET Framework i zależności systemu w sieci, zobacz [Przewodnik wdrażania dla administratorów](guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Opcje wdrażania dla aplikacji

Kiedy chcesz opublikować aplikację na serwerze sieci Web lub w innej scentralizowanej lokalizacji, aby użytkownicy mogli ją instalować, możesz wybrać jedną z kilku metod wdrażania. Niektóre z nich są dostarczane z programem Visual Studio. W poniższej tabeli wymieniono opcje wdrażania aplikacji i określono .NET Framework pakiet redystrybucyjny obsługujący każdą opcję. Oprócz tych można napisać niestandardowy program instalacyjny dla swojej aplikacji. Aby uzyskać więcej informacji, zapoznaj się z sekcją Tworzenie [łańcucha .NET Framework instalacji aplikacji](#chaining).

|Strategia wdrażania aplikacji|Dostępne metody wdrażania|Pakiet redystrybucyjny .NET Framework|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Instalowanie z sieci Web|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />zestaw [narzędzi - WIX](#wix)<br />- [instalacji ręcznej](#installing_manually)|[Instalator sieci Web](#redistributable-packages)|
|Instalowanie z dysku|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />zestaw [narzędzi - WIX](#wix)<br />- [instalacji ręcznej](#installing_manually)|[Instalator w trybie offline](#redistributable-packages)|
|Instalowanie z sieci lokalnej (w przypadku aplikacji dla przedsiębiorstw)|- [ClickOnce](#clickonce-deployment)|[Instalator sieci Web](#redistributable-packages) (zobacz [ClickOnce](#clickonce-deployment) for ograniczenia) lub [Instalator w trybie offline](#redistributable-packages)|

## <a name="redistributable-packages"></a>Pakiety redystrybucyjne

.NET Framework jest dostępny w dwóch pakietach redystrybucyjnych: jako instalator sieci Web (program inicjujący sieci Web) i instalator w trybie offline (autonomiczny pakiet redystrybucyjny). W poniższej tabeli porównano dwa pakiety.

||Instalator sieci Web|Instalator w trybie offline|
|-|-------------------|-----------------------|
|Plik do pobrania|.NET Framework 4,8: <br/>[ndp48-web.exe](https://go.microsoft.com/fwlink/?LinkId=2085155)<br/><br/>.NET Framework 4.7.2: <br/>[NDP472-KB4054531-Web.exe](https://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>.NET Framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](https://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>.NET Framework 4,7: <br />[NDP47-KB3186500-Web.exe](https://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />.NET Framework 4.6.2: <br />[NDP462-KB3151802-Web.exe](https://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> .NET Framework 4.6.1:<br />[NDP461-KB3102438-Web.exe](https://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> .NET Framework 4.6:<br />[NDP46-KB3045560-Web.exe](https://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](https://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> .NET Framework 4.5.1: <br />[NDP451-KB2859818-Web.exe](https://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> .NET Framework 4.5: <br />[dotNetFx45_Full_setup.exe](https://go.microsoft.com/fwlink/?LinkId=225704)|.NET Framework 4,8: <br/>[NDP48-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?linkid=2088631)<br/><br/>.NET Framework 4.7.2: <br/>[NDP472-KB4054530-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>.NET Framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET Framework 4,7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />.NET Framework 4.6.2: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> .NET Framework 4.6.1: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> .NET Framework 4.6: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> .NET Framework 4.5.1: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> .NET Framework 4.5: <br />[dotNetFx45_Full_x86_x64.exe](https://go.microsoft.com/fwlink/?LinkId=225702)|
|Wymagane połączenie z Internetem?|Tak|Nie|
|Wielkość pliku do pobrania|Mniejsza (zawiera tylko instalator dla docelowej platformy)*|Większe*|
|Pakiety językowe|Included**|Należy [zainstalować oddzielnie](#chain_langpack), chyba że jest używany pakiet przeznaczony dla wszystkich systemów operacyjnych|
|Metoda wdrażania|Obsługuje wszystkie metody:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Instalator Windows XML (WiX)](#wix)<br />- [instalacji ręcznej](#installing_manually)<br />[Konfiguracja Niestandardowa - (tworzenie łańcuchów)](#chaining)|Obsługuje wszystkie metody:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Instalator Windows XML (WiX)](#wix)<br />- [instalacji ręcznej](#installing_manually)<br />[Konfiguracja Niestandardowa - (tworzenie łańcuchów)](#chaining)|
|Lokalizacja pliku do pobrania dla wdrażania ClickOnce|Centrum pobierania firmy Microsoft:<br /><br /> - [.NET Framework 4,8](https://go.microsoft.com/fwlink/?LinkId=2085155) <br/> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863262) <br/> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET Framework 4,7](https://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET Framework 4,6](https://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [.NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|Twój własny serwer lub Microsoft Download Center:<br /><br /> - [.NET Framework 4,8](https://go.microsoft.com/fwlink/?linkid=2088631)<br /> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863265)<br /> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET Framework 4,7](https://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET Framework 4,6](https://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [.NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|

\* Instalator w trybie offline jest większy, ponieważ zawiera składniki dla wszystkich platform docelowych. Po zakończeniu działania instalatora system operacyjny Windows buforuje tylko instalatora, który został użyty. Jeśli instalator w trybie offline jest usuwany po zakończeniu instalacji, zużywana jest tyle samo miejsca na dysku co w przypadku użycia instalatora sieci Web. Jeśli używane narzędzie (na przykład [InstallAware](#installaware-deployment) lub [InstallShield](#installshield-deployment)) do tworzenia programu instalacyjnego aplikacji udostępnia folder plików instalacyjnych, który jest usuwany po zakończeniu instalacji, można automatycznie usunąć instalatora w trybie offline, umieszczając go w folderze instalacyjnym.

\*\* Jeśli używasz Instalatora sieci Web z konfiguracją niestandardową, możesz użyć domyślnych ustawień języka na podstawie ustawienia wielojęzycznego interfejsu użytkownika (MUI) użytkownika lub określić inny pakiet językowy przy użyciu opcji `/LCID` w wierszu polecenia. Zapoznaj się z sekcją Tworzenie [łańcucha przy użyciu domyślnego interfejsu użytkownika .NET Framework](#chaining_default) .

## <a name="deployment-methods"></a>Metody wdrażania

 Dostępne są cztery metody wdrażania:

- Możesz ustawić zależność dla programu .NET Framework. Program .NET Framework można określić jako warunek wstępny instalacji danej aplikacji, za pomocą jednej z następujących metod:

  - Korzystanie z [wdrażania ClickOnce](#clickonce-deployment) (dostępnego w programie Visual Studio)

  - Tworzenie [projektu InstallAware](#installaware-deployment) (wersja bezpłatna dostępna dla użytkowników programu Visual Studio)

  - Utwórz [projekt InstallShield](#installshield-deployment) (dostępny w programie Visual Studio)

  - Korzystanie z zestawu [narzędzi Instalator Windows XML (WiX)](#wix)

- Możesz polecić użytkownikom [Ręczne instalowanie .NET Framework](#installing_manually).

- Możesz połączyć (dołącz) proces instalowania programu .NET Framework w instalacji aplikacji i określić, jak będzie realizowana instalacja programu .NET Framework:

  - [Użyj domyślnego interfejsu użytkownika](#chaining_default). Obsługa instalacji przez instalatora programu .NET Framework.

  - [Dostosuj interfejs użytkownika](#chaining_custom) w celu zaprezentowania ujednoliconego środowiska instalacji i monitorowania .NET Framework postęp instalacji.

Te metody wdrażania opisano szczegółowo w poniższych sekcjach.

## <a name="setting-a-dependency-on-the-net-framework"></a>Ustawianie zależności w .NET Framework

Jeśli do wdrożenia aplikacji używasz technologii ClickOnce, InstallAware, InstallShield lub WiX, możesz dodać zależność od .NET Framework, aby można ją było zainstalować w ramach aplikacji.

### <a name="clickonce-deployment"></a>wdrożenie ClickOnce

Wdrażanie ClickOnce jest dostępne w projektach, które są tworzone za pomocą języków Visual Basic i Visual C#, ale nie jest dostępne w przypadku języka Visual C++.

W programie Visual Studio, aby wybrać wdrażanie ClickOnce i dodać zależność od programu .NET Framework:

1. Otwórz projekt aplikacji, którą chcesz opublikować.

2. W Eksplorator rozwiązań otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.

3. Wybierz okienko **Publikowanie** .

4. Wybierz przycisk **wymagania wstępne** .

5. W oknie dialogowym **wymagania wstępne** upewnij się, że jest zaznaczone pole wyboru **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** .

6. Na liście wymagania wstępne Znajdź i wybierz wersję .NET Framework, która została użyta do skompilowania projektu.

7. Wybierz opcję, aby określić lokalizację źródłową dla wymagań wstępnych, a następnie wybierz przycisk **OK**.

     Jeśli podasz adres URL dla lokalizacji pobierania .NET Framework, możesz określić witrynę Centrum pobierania Microsoft lub własną witrynę. Jeśli umieszczasz pakiet redystrybucyjny na własnym serwerze, musi to być instalator w trybie offline, a nie instalator sieci Web. Możesz dodać tylko łącze do instalatora sieci Web w witrynie Centrum pobierania firmy Microsoft. Adres URL może również określać dysk, na którym jest rozpowszechniana własna aplikacja.

8. W oknie dialogowym **strony właściwości** wybierz **przycisk OK**.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>Wdrożenie InstallAware

InstallAware kompiluje aplikacje systemu Windows (APPX), Instalator Windows (MSI), kod natywny (EXE) i App-V (Application Virtualization) z jednego źródła. Łatwo [Dołączaj wszystkie wersje .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) w konfiguracji, opcjonalnie dostosowując instalację, [edytując domyślne skrypty](https://www.installaware.com/msicode.htm). Na przykład InstallAware wstępnie instaluje certyfikaty w systemie Windows 7, bez którego instalacja .NET Framework 4,7 kończy się niepowodzeniem. Aby uzyskać więcej informacji na temat InstallAware, zobacz witrynę sieci Web [InstallAware dla Instalator Windows](https://www.installaware.com/) .

### <a name="installshield-deployment"></a>Wdrożenie InstallShield

W programie Visual Studio, aby wybrać wdrażanie InstallShield i dodać zależność od programu .NET Framework:

1. Na pasku menu programu Visual Studio wybierz kolejno opcje **plik**, **Nowy**, **projekt**.

2. W lewym okienku okna dialogowego **Nowy projekt** wybierz kolejno pozycje **Inne typy projektów**, **Instalacja i wdrożenie**, **InstallShield Le**.

3. W polu **Nazwa** wpisz nazwę projektu, a następnie wybierz przycisk **OK**.

4. Jeśli tworzysz projekt instalacji i wdrożenia po raz pierwszy, wybierz opcję **Przejdź do InstallShield** lub **Włącz InstallShield Limited Edition** , aby pobrać InstallShield Limited Edition dla używanej wersji programu Microsoft Visual Studio. Uruchom ponownie program Visual Studio.

5. Przejdź do kreatora **Asystenta projektu** i wybierz pozycję **pliki aplikacji** , aby dodać dane wyjściowe projektu. Inne atrybuty projektu możesz skonfigurować za pomocą tego kreatora.

6. Przejdź do pozycji **wymagania dotyczące instalacji** i wybierz systemy operacyjne oraz wersję .NET Framework chcesz zainstalować.

7. Otwórz menu skrótów dla projektu Instalatora i wybierz polecenie **Kompiluj**.

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Wdrożenie Instalator Windows XML (WiX)

Zestaw narzędzi XML Instalatora Windows (WiX) tworzy pakiety instalacyjne systemu Windows z kodu źródłowego XML. WiX obsługuje środowisko wiersza polecenia, które można zintegrować z procesami kompilacji w celu tworzenia pakietów instalatora MSI i MSM. Korzystając z WiX, można [określić .NET Framework jako warunek wstępny](https://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html)lub [utworzyć łańcuch](https://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) , aby w pełni kontrolować środowisko wdrażania .NET Framework. Aby uzyskać więcej informacji na temat WiX, zobacz witrynę sieci Web zestawu [narzędzi Instalator Windows XML (WiX)](https://wixtoolset.org/) .

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>Ręczne instalowanie .NET Framework

W niektórych sytuacjach automatyczne instalowanie programu .NET Framework z aplikacją może być niepraktyczne. W takim przypadku można zalecić użytkownikom, aby sami instalowali program .NET Framework. Pakiet redystrybucyjny jest dostępny w [dwóch pakietach](#redistributable-packages). W trakcie procesu instalacji podaj użytkownikom instrukcje znajdowania i instalowania programu .NET Framework.

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Łączenie .NET Framework instalacji z instalacją aplikacji

W przypadku tworzenia niestandardowego instalatora aplikacji możesz połączyć w łańcuch (dodać) proces instalacji programu .NET Framework z procesem instalowania tej aplikacji. W przypadku łańcucha są dostępne dwie opcje interfejsu użytkownika dotyczące instalacji programu .NET Framework:

- Użyj domyślnego interfejsu użytkownika z instalatora programu .NET Framework.

- Utwórz niestandardowy interfejs użytkownika instalacji programu .NET Framework w celu ujednolicenia z programem instalacyjnym aplikacji.

Obie metody pozwalają na korzystanie z instalatora sieci Web lub instalatora w trybie offline. Każdy pakiet ma swoje zalety:

- Jeśli używasz instalatora sieci Web, proces instalacji programu .NET Framework decyduje, który pakiet instalacyjny jest wymagany, oraz pobiera z sieci Web i instaluje tylko ten pakiet.

- Jeśli używasz instalatora w trybie offline, możesz zamieścić kompletny zestaw pakietów instalacyjnych programu .NET Framework na nośniku redystrybucyjnym, aby użytkownicy nie musieli pobierać żadnych dodatkowych plików z sieci Web podczas instalacji.

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>Tworzenie łańcucha przy użyciu domyślnego interfejsu użytkownika .NET Framework

Aby dyskretnie połączyć w łańcuch proces instalacji programu .NET Framework i pozwolić, aby instalator programu .NET Framework zapewnił UI, dodaj następujące polecenie do programu instalacyjnego:

`<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>`

Na przykład jeśli program wykonywalny jest contoso. exe i chcesz w trybie dyskretnym zainstalować pakiet redystrybucyjny offline w trybie .NET Framework 4,5, użyj polecenia:

`dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso`

Dodatkowe opcje wiersza polecenia mogą służyć do dostosowania instalacji. Na przykład:

- Aby użytkownicy mogli zamknąć działające aplikacje programu .NET Framework, aby system mniej razy wymagał ponownego uruchamiania, ustaw tryb pasywny i użyj opcji `/showrmui` następująco:

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     To polecenie umożliwia menedżerowi ponownego uruchamiania wyświetlenie okna komunikatu, które umożliwia użytkownikom zamknięcie .NET Framework aplikacji przed zainstalowaniem .NET Framework.

- Jeśli korzystasz z instalatora sieci Web, możesz użyć opcji `/LCID`, aby określić pakiet językowy. Na przykład, aby połączyć Instalatora sieci Web .NET Framework 4,5 z programem instalacyjnym firmy Contoso i zainstalować pakiet języka japońskiego, Dodaj następujące polecenie do procesu instalacji aplikacji:

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     Jeżeli pominięto opcję `/LCID`, instalator zainstaluje pakiet językowy, który odpowiada ustawieniu MUI użytkownika.

    > [!NOTE]
    > Różne pakiety językowe mogą mieć różne daty wydania. Jeśli pakiet językowy, który określisz, nie jest dostępny w centrum pobierania, instalator zainstaluje program .NET Framework bez pakietu językowego. Jeśli program .NET Framework jest już zainstalowany na komputerze, instalator zainstaluje tylko pakiet językowy.

Aby uzyskać pełną listę opcji, zobacz sekcję [Opcje wiersza polecenia](#command-line-options) .

Aby poznać typowe kody powrotne, zobacz sekcję [kody powrotne](#return-codes) .

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Instalacja łańcuchowa przy użyciu niestandardowego interfejsu użytkownika

Jeśli masz niestandardowy pakiet instalatora, możesz dyskretnie uruchomić i śledzić instalację .NET Framework podczas wyświetlania własnego widoku postępu instalacji. W tym przypadku należy się upewnić, że w kodzie są wykonywane następujące działania:

- Sprawdź [, czy .NET Framework wymagania dotyczące sprzętu i oprogramowania](../get-started/system-requirements.md).

- [Wykryj](#detect_net) , czy poprawna wersja .NET Framework jest już zainstalowana na komputerze użytkownika.

    > [!IMPORTANT]
    > W przypadku określenia, czy poprawna wersja .NET Framework jest już zainstalowana, należy sprawdzić, czy zainstalowano wersję docelową *, czy nowszą, a nie* bez względu na to, czy wersja docelowa jest zainstalowana. Innymi słowy, należy sprawdzić, czy klucz wydania pobierany z rejestru jest większy niż lub równy kluczowi wydania wersji docelowej, *bez* względu na to, czy jest to klucz zwolnienia wersji docelowej.

- [Wykryj](#detecting-the-language-packs) , czy pakiety językowe są już zainstalowane na komputerze użytkownika.

- Jeśli chcesz kontrolować wdrożenie, uruchom je w trybie dyskretnym i śledź proces instalacji .NET Framework (zobacz [How to: Get Progress in the .NET Framework 4,5 Installer](how-to-get-progress-from-the-dotnet-installer.md)).

- W przypadku wdrażania Instalatora w trybie offline należy [osobno utworzyć łańcuch pakietów językowych](#chain_langpack).

- Dostosowywanie wdrożenia przy użyciu [opcji wiersza polecenia](#command-line-options). Jeśli na przykład dołączasz do łańcucha instalator sieci Web, ale chcesz zastąpić domyślny pakiet językowy, użyj opcji `/LCID`, jak opisano w poprzedniej sekcji.

- [Rozwiązywanie problemów](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>Wykrywanie programu .NET Framework

Instalator .NET Framework zapisuje klucze rejestru, gdy instalacja się powiedzie. Możesz sprawdzić, czy .NET Framework 4,5 lub nowsza jest zainstalowana, sprawdzając folder `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` w rejestrze dla wartości `DWORD` o nazwie `Release`. (Należy zauważyć, że polecenie "NET Framework Setup" nie zaczyna się od kropki). Istnienie tego klucza wskazuje, że na tym komputerze zainstalowano .NET Framework 4,5 lub nowszą wersję. Wartość `Release` wskazuje, która wersja programu .NET Framework jest zainstalowana.

> [!IMPORTANT]
> Podczas próby wykrycia, czy określona wersja jest obecna, należy sprawdzić wartość **większą lub równą** wartości słowa kluczowego Release.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Wersja|Wartość DWORD dotycząca wersji|
|-------------|--------------------------------|
|.NET Framework 4,8 zainstalowany w systemie Windows 10 maja 2019 Update|528040|
|.NET Framework 4,8 zainstalowany we wszystkich wersjach systemów operacyjnych innych niż Windows 10 maja 2019 Update|528049|
|.NET Framework 4.7.2 zainstalowany w aktualizacji systemu Windows 10 z kwietnia 2018 i w systemie Windows Server w wersji 1803|461808|
|.NET Framework 4.7.2 zainstalowany na wszystkich wersjach systemu operacyjnego innych niż Windows 10 kwiecień 2018 Update i Windows Server, wersja 1803. Obejmuje to aktualizację systemu Windows 10 z października 2018. |461814|
|.NET Framework 4.7.1 zainstalowana w systemie Windows 10 — Aktualizacja dla twórców i w systemie Windows Server w wersji 1709|461308|
|.NET Framework 4.7.1 zainstalowany na wszystkich wersjach systemu operacyjnego innych niż aktualizacja systemu Windows 10 dla twórców i system Windows Server w wersji 1709|461310|
|.NET Framework 4,7 zainstalowany w aktualizacji systemu Windows 10 dla twórców|460798|
|.NET Framework 4,7 zainstalowany na wszystkich wersjach systemu operacyjnego innych niż aktualizacja systemu Windows 10 dla twórców|460805|
|.NET Framework 4.6.2 zainstalowany w systemie Windows 10 w wersji rocznicowej i w systemie Windows Server 2016|394802|
|.NET Framework 4.6.2 zainstalowane na wszystkich wersjach systemu operacyjnego innych niż Windows 10 w wersji rocznicowej i Windows Server 2016|394806|
|.NET Framework 4.6.1 zainstalowany w aktualizacji systemu Windows 10 listopad|394254|
|.NET Framework 4.6.1 zainstalowany we wszystkich wersjach systemu operacyjnego innych niż aktualizacja systemu Windows 10 listopad|394271|
|.NET Framework 4,6 zainstalowany w systemie Windows 10|393295|
|.NET Framework 4,6 zainstalowany we wszystkich wersjach systemów operacyjnych innych niż Windows 10|393297|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.5.1 zainstalowany z Windows 8.1 lub Windows Server 2012 R2|378675|
|.NET Framework 4.5.1 zainstalowany w systemie Windows 8, Windows 7|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>Wykrywanie pakietów językowych

Można sprawdzić, czy określony pakiet językowy jest instalowany, sprawdzając folder HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* w rejestrze dla wartości DWORD o nazwie `Release`. (Należy zauważyć, że polecenie "NET Framework Setup" nie zaczyna się od kropki). *LCID* określa identyfikator ustawień regionalnych; listę tych elementów można znaleźć w sekcji [obsługiwane języki](#supported-languages) .

Na przykład w celu wykrycia, czy pełny japoński pakiet językowy (LCID = 1041) jest zainstalowany, Pobierz następującą nazwaną wartość z rejestru:

| | |
|-|-|
| Key | HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041 |
| Nazwa | Wydanie |
| Typ | DWORD |

Aby określić, czy końcowa wersja pakietu językowego jest zainstalowana dla określonej wersji .NET Framework od 4,5 do 4.7.2, sprawdź wartość DWORD klucza wydania opisanej w poprzedniej sekcji, co [wykrywa .NET Framework](#detect_net).

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Łączenie pakietów językowych z konfiguracją aplikacji

Program .NET Framework udostępnia zestaw autonomicznych plików wykonywalnych pakietu językowego, które zawierają zlokalizowane zasoby dla określonych kultur. Pakiety językowe są dostępne w Centrum pobierania Microsoft:

- [Pakiety językowe .NET Framework 4,8](https://go.microsoft.com/fwlink/p/?LinkId=2086170)

- [Pakiety językowe .NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863275)

- [Pakiety językowe .NET Framework 4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090)

- [Pakiety językowe .NET Framework 4,7](https://go.microsoft.com/fwlink/p/?LinkId=825306)

- [Pakiety językowe .NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604)

- [.NET Framework 4.6.1 — pakiety językowe](https://go.microsoft.com/fwlink/p/?LinkId=671747)

- [Pakiety językowe .NET Framework 4,6](https://go.microsoft.com/fwlink/p/?LinkId=528314)

- [.NET Framework 4.5.2 — pakiety językowe](https://go.microsoft.com/fwlink/p/?LinkId=397701)

- [.NET Framework 4.5.1 — pakiety językowe](https://go.microsoft.com/fwlink/p/?LinkId=322101)

- [Pakiety językowe .NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Pakiety językowe nie zawierają składników programu .NET Framework, które są wymagane do uruchamiania aplikacji; przed zainstalowaniem pakietów językowych należy zainstalować program .NET Framework za pomocą instalatora w trybie sieci web lub offline.

Począwszy od .NET Framework 4.5.1 nazwy pakietów przyjmują postać NDP <`version`>-KB <`number`>-x86-x64-zezwalają-<`culture`>. exe, gdzie `version` jest numerem wersji .NET Framework, `number` jest numerem artykułu bazy wiedzy Microsoft Knowledge Base, a `culture` określa [kraj/region](#supported-languages). Na przykład jeden z tych pakietów to `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Nazwy pakietów są wymienione w sekcji [pakiety redystrybucyjne](#redistributable-packages) we wcześniejszej części tego artykułu.

Aby zainstalować pakiet językowy z instalatorem .NET Framework w trybie offline, należy go połączyć z własnym instalatorem aplikacji. Na przykład w celu wdrożenia Instalatora programu .NET Framework 4.5.1 w trybie offline za pomocą japońskiego pakietu językowego należy użyć następującego polecenia:

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

W przypadku korzystania z instalatora sieci Web nie trzeba dodawać do łańcucha pakietów językowych; instalator zainstaluje pakiet językowy zgodny z ustawieniem MUI użytkownika. Jeśli chcesz zainstalować inny język, możesz użyć opcji `/LCID`, aby określić pakiet językowy.

Aby uzyskać pełną listę opcji wiersza polecenia, zobacz sekcję [Opcje wiersza polecenia](#command-line-options) .

### <a name="troubleshooting"></a>Rozwiązywanie problemów

#### <a name="return-codes"></a>Kody powrotne

W poniższej tabeli wymieniono najbardziej typowe kody powrotne dla programu instalacyjnego pakietu redystrybucyjnego programu .NET Framework. Kody powrotne są takie same dla wszystkich wersji instalatora. Łącza do szczegółowych informacji zawiera następna sekcja.

|Kod powrotu|Opis|
|-----------------|-----------------|
|0|Instalacja została zakończona pomyślnie.|
|1602|Użytkownik anulował instalację.|
|1603|Podczas instalacji wystąpił błąd krytyczny.|
|1641|Do ukończenia instalacji wymagane jest ponowne uruchomienie komputera. Ten komunikat oznacza sukces.|
|3010|Do ukończenia instalacji wymagane jest ponowne uruchomienie komputera. Ten komunikat oznacza sukces.|
|5100|Komputer użytkownika nie spełnia wymagań systemowych.|

#### <a name="download-error-codes"></a>Kody błędów pobierania

Zapoznaj się z następującą zawartością:

- [Kody błędów Usługa inteligentnego transferu w tle (bity)](https://go.microsoft.com/fwlink/?LinkId=180946)

- [Kody błędów monikera adresu URL](https://go.microsoft.com/fwlink/?LinkId=180947)

- [Kody błędów usługi WinHttp](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Inne kody błędów

Zapoznaj się z następującą zawartością:

- [Instalator Windows kody błędów](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Kody wyników agenta Windows Update](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Odinstalowywanie programu .NET Framework

Począwszy od systemu Windows 8, można odinstalować .NET Framework 4,5 lub jeden z jego wydań punktów, korzystając z **opcji Włącz lub wyłącz funkcje systemu Windows** w panelu sterowania. W starszych wersjach systemu Windows można odinstalować .NET Framework 4,5 lub jeden z jego wydań punktów za pomocą apletu **Dodaj lub usuń programy** w panelu sterowania.

> [!IMPORTANT]
> W przypadku systemów operacyjnych Windows 7 i starszych Odinstalowywanie .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 lub 4,8 nie przywraca .NET Framework plików 4,5 i odinstalowywanie .NET Framework 4,5 nie powoduje przywrócenia .NET Framework 4 plików. Jeśli chcesz wrócić do starszej wersji, należy ponownie zainstalować ją i jej wszelkie aktualizacje.

## <a name="appendix"></a>Dodatek

### <a name="command-line-options"></a>Opcje wiersza polecenia

W poniższej tabeli wymieniono opcje, które można uwzględnić podczas tworzenia łańcucha pakietu redystrybucyjnego .NET Framework 4,5 do konfiguracji aplikacji.

|Opcja|Opis|
|------------|-----------------|
|**/CEIPConsent**|Zastępuje domyślne zachowanie i wysyła anonimowe opinie do firmy Microsoft, aby poprawić przebieg wdrażania w przyszłości. Tej opcji można użyć tylko wtedy, gdy instalator monituje o zgodę, i jeśli użytkownik udziela uprawnień do wysyłania anonimowych opinii do firmy Microsoft.|
|**/chainingpackage** `packageName`|Określa nazwę pliku wykonywalnego, który wykonuje łańcuch. Informacja ta jest wysyłana do firmy Microsoft jako anonimowa, w celu poprawy przebiegu wdrażania w przyszłości.<br /><br /> Jeśli nazwa pakietu zawiera spacje, użyj podwójnych cudzysłowów jako ograniczników; na przykład: **/chainingpackage "Publishing"** . Aby zapoznać się z przykładem pakietu łańcucha, zobacz [pobieranie informacji o postępie z pakietu instalacyjnego](https://go.microsoft.com/fwlink/?LinkId=181926) w bibliotece MSDN.|
|**/LCID**  `LCID`<br /><br /> gdzie `LCID` określa identyfikator ustawień regionalnych (zobacz [obsługiwane języki](#supported-languages))|Instaluje pakiet językowy określony przez `LCID` i wymusza wyświetlanie interfejsu użytkownika w tym języku, jeżeli nie jest ustawiony tryb cichy.<br /><br /> W przypadku instalatora sieci Web ta opcja instaluje łańcuchowo pakiet językowy z sieci Web. **Uwaga:**  Tej opcji należy użyć tylko w przypadku Instalatora sieci Web.|
|`file` &#124; /log `folder`|Określa lokalizację pliku dziennika. Wartość domyślna to folder tymczasowy dla procesu, a domyślna nazwa pliku jest zgodna z pakietem. Jeśli plik ma rozszerzenie .txt, generowany jest dziennik tekstowy. Jeśli określisz dowolne inne rozszerzenie lub brak rozszerzenia, zostanie utworzony dziennik HTML.|
|**/msioptions**|Określa opcje przekazywane do elementów .msi i .msp; na przykład: `/msioptions "PROPERTY1='Value'"`.|
|**/ norestart /**|Uniemożliwia automatyczne ponowne uruchomienie programu instalacyjnego. Jeśli używasz tej opcji, aplikacja łańcucha musi przechwycić Kod powrotu i obsłużyć ponowny rozruch (zobacz [pobieranie informacji o postępie z pakietu instalacyjnego](https://go.microsoft.com/fwlink/?LinkId=179606) w bibliotece MSDN).|
|**/ passive**|Ustawia tryb pasywny. Wyświetla pasek postępu, aby wskazać, że instalacja jest w toku, ale nie wyświetla użytkownikowi żadnych monitów ani komunikatów o błędzie. W tym trybie, w przypadku łańcucha przez program instalacyjny, pakiet łańcucha musi obsługiwać [kody powrotne](#return-codes).|
|**/pipe**|Tworzy kanał komunikacyjny, aby umożliwić uzyskanie postępu przez pakiet łańcuchowy.|
|**/promptrestart**|Tylko tryb pasywny, jeśli program instalacyjny wymaga ponownego uruchomienia komputera, monituje o tym użytkownika. Ta opcja wymaga interakcji użytkownika, jeśli jest konieczne ponowne uruchomienie.|
|**/q**|Ustawia tryb cichy.|
|**/ Repair**|Uruchamia funkcję naprawy.|
|**/serialdownload**|Wymusza instalację dopiero po pobraniu pakietu.|
|**/showfinalerror**|Ustawia tryb pasywny. Wyświetla błędy tylko wtedy, gdy instalacja nie powiedzie się. Ta opcja wymaga interakcji użytkownika, jeśli instalacja nie powiedzie się.|
|**/showrmui**|Używane tylko z opcją **/Passive** . Wyświetla okno komunikatu, który monituje użytkowników, aby zamknąć aplikacje .NET Framework, które są uruchomione. To okno komunikatu zachowuje się tak samo w trybie pasywnym i niepasywnym.|
|**/uninstall**|Odinstalowuje pakiet redystrybucyjny programu .NET Framework.|

### <a name="supported-languages"></a>Obsługiwane języki

W poniższej tabeli wymieniono pakiety językowe .NET Framework dostępne dla .NET Framework 4,5 i jego wersji punktów.

|LCID|Język — kraj/region|Kultura|
|----------|--------------------------------|-------------|
|1025|Arabski — Arabia Saudyjska|ty|
|1028|Chiński (tradycyjny)|zh-Hant|
|1029|czeski|cs|
|1030|duński|da|
|1031|Niemiecki — Niemcy|de|
|1032|grecki|el|
|1035|fiński|fi|
|1036|Francuski — Francja|fr|
|1037|hebrajski|Przewodniczący|
|1038|węgierski|hu|
|1040|Włoski — Włochy|it|
|1041|japoński|ja|
|1042|koreański|ko|
|1043|Holenderski — Holandia|nl|
|1044|Norweski (Bokmål)|nie|
|1045|polski|pl|
|1046|Portugalski – Brazylia|pt-BR|
|1049|rosyjski|ru|
|1053|szwedzki|sv|
|1055|turecki|tr|
|2052|Chiński (uproszczony)|zh-Hans|
|2070|Portugalski – Portugalia|pt-PT|
|3082|Hiszpański — Hiszpania (nowoczesny)|Tak|

## <a name="see-also"></a>Zobacz także

- [Przewodnik wdrażania dla administratorów](guide-for-administrators.md)
- [Wymagania systemowe](../get-started/system-requirements.md)
- [Zainstaluj .NET Framework dla deweloperów](../install/guide-for-developers.md)
- [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
- [Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5](reducing-system-restarts.md)
- [Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)
