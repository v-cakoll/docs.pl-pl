---
title: Przewodnik po wdrażaniu programu .NET Framework dla deweloperów
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
ms.openlocfilehash: 26c168040b0fa5e975e64a7518b0d0bf250c4711
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628127"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Przewodnik po wdrażaniu programu .NET Framework dla deweloperów
Ten temat zawiera informacje dla deweloperów, którzy chcą zainstalować dowolną wersję programu .NET Framework z programu .NET Framework 4.5 do [!INCLUDE[net_current](../../../includes/net-current-version.md)] ich aplikacji.

Pakiety redystrybucyjne i pakiety językowe dla programu .NET Framework można pobrać ze stron pobierania:

- [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Framework 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [Program .NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

 Ważne uwagi:

- Wersje programu .NET Framework z platformy .NET Framework 4.5.1 za pośrednictwem [!INCLUDE[net_current](../../../includes/net-current-version.md)] są aktualizacje w miejscu do .NET Framework 4.5, co oznacza, że używają tej samej wersji środowiska wykonawczego, ale wersje zestawu są aktualizowane i zawierają nowe typy i elementy członkowskie.

- .NET Framework 4.5 i nowsze wersje są tworzone przyrostowo na .NET Framework 4. Po zainstalowaniu wersji .NET Framework 4.5 lub nowszych w systemie z zainstalowanym programem .NET Framework 4 zestawy w wersji 4 zostaną zastąpione nowszymi wersjami.

- Jeśli odwołujesz się do [pakietu pozapasmowego](../get-started/the-net-framework-and-out-of-band-releases.md) firmy Microsoft w aplikacji, zestaw zostanie uwzględniony w pakiecie aplikacji.

- Aby zainstalować program .NET Framework 4.5 lub nowszych, musisz mieć uprawnienia administratora.

- Program .NET Framework 4.5 znajduje się w systemach Windows 8 i Windows Server 2012, więc nie trzeba go wdrażać w aplikacji w tych systemach operacyjnych. Podobnie program .NET Framework 4.5.1 znajduje się w systemach Windows 8.1 i Windows Server 2012 R2. .NET Framework 4.5.2 nie jest uwzględniony w żadnych systemach operacyjnych. Program .NET Framework 4.6 jest uwzględniony w systemie Windows 10, program .NET Framework 4.6.1 jest zawarty w systemie Windows 10 November Update, a program .NET Framework 4.6.2 jest zawarty w rocznicowej aktualizacji systemu Windows 10.  Program .NET Framework 4.7 jest zawarty w aktualizacji Windows 10 Creators Update, .NET Framework 4.7.1 jest zawarty w aktualizacji Windows 10 Fall Creators Update, a program .NET Framework 4.7.2 jest zawarty w systemie Windows 10 October 2018 Update i Windows 10 April 2018 Update. Program .NET Framework 4.8 jest uwzględniony w aktualizacji systemu Windows 10 may 2019. Aby uzyskać pełną listę wymagań dotyczących sprzętu i oprogramowania, zobacz [Wymagania systemowe](../get-started/system-requirements.md).

- Począwszy od programu .NET Framework 4.5, użytkownicy mogą wyświetlać listę uruchomionych aplikacji platformy .NET Framework podczas instalacji i łatwo je zamykać. Może to pomóc uniknąć ponownego uruchamiania systemu spowodowane przez instalacje platformy .NET Framework. Zobacz [Ograniczanie liczby ponownych uruchomień systemu](reducing-system-restarts.md).

- Odinstalowanie wersji programu .NET Framework 4.5 lub nowszych powoduje również usunięcie wcześniej istniejących plików programu .NET Framework 4. Jeśli chcesz wrócić do programu .NET Framework 4, należy ponownie zainstalować go i wszelkie aktualizacje do niego. Zobacz [Instalowanie programu .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).

- Redystrybucyjne programu .NET Framework 4.5 zostało zaktualizowane 9 października 2012 r., aby rozwiązać problem związany z niewłaściwą sygnaturą czasową certyfikatu cyfrowego, która spowodowała przedwczesne wygaśnięcie podpisu cyfrowego na plikach wyprodukowanych i podpisanych przez firmę Microsoft. Jeśli wcześniej zainstalowano redystrybucyjny pakiet .NET Framework 4.5 z dnia 16 sierpnia 2012 r., zalecamy zaktualizowanie kopii najnowszą redystrybucjową [ze strony pobierania programu .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/net45). Aby uzyskać więcej informacji na temat tego problemu, zobacz [Poradnik zabezpieczeń firmy Microsoft 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

Aby uzyskać informacje o tym, jak administrator systemu może wdrażać program .NET Framework i jego zależności systemowe w sieci, zobacz [Przewodnik wdrażania dla administratorów](guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Opcje wdrażania aplikacji

Gdy wszystko będzie gotowe do opublikowania aplikacji na serwerze sieci web lub w innej scentralizowanej lokalizacji, aby użytkownicy mogli ją zainstalować, można wybrać jedną z kilku metod wdrażania. Niektóre z nich są dostarczane z programem Visual Studio. W poniższej tabeli wymieniono opcje wdrażania aplikacji i określono pakiet redystrybucyjny platformy .NET Framework obsługujący każdą opcję. Oprócz nich można napisać niestandardowy program instalacyjny dla aplikacji; Aby uzyskać więcej informacji, zobacz sekcję [Tworzenie łańcucha instalacji programu .NET Framework do instalatora aplikacji](#chaining).

|Strategia wdrażania aplikacji|Dostępne metody wdrażania|.NET Framework redystrybucyjny do użycia|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Instalacja z internetu|- [Instalacjaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Zestaw narzędzi WiX](#wix)<br />- [Instalacja ręczna](#installing_manually)|[Instalator sieci Web](#redistributable-packages)|
|Instalacja z płyty|- [Instalacjaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Zestaw narzędzi WiX](#wix)<br />- [Instalacja ręczna](#installing_manually)|[Instalator w trybie offline](#redistributable-packages)|
|Instalowanie z sieci lokalnej (dla aplikacji dla przedsiębiorstw)|- [Clickonce](#clickonce-deployment)|Instalator [internetowy](#redistributable-packages) (zobacz [ClickOnce](#clickonce-deployment) for restrictions) lub [instalator offline](#redistributable-packages)|

## <a name="redistributable-packages"></a>Pakiety redystrybucyjne

Program .NET Framework jest dostępny w dwóch pakietach redystrybucyjnych: instalatorze internetowym (boottrapper) i instalatorze offline (samodzielny redystrybucyjny). Wszystkie pliki do pobrania programu .NET Framework są hostowane na [stronie Pobierz program .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/). W poniższej tabeli porównano dwa pakiety:

||Instalator sieci Web|Instalator w trybie offline|
|-|-------------------|-----------------------|
|Wymagane jest połączenie z Internetem?|Tak|Nie|
|Rozmiar pobierania|Mniejszy (zawiera tylko instalator dla platformy docelowej)*|Większe*|
|Pakiety językowe|W zestawie**|Musi być [zainstalowany oddzielnie](#chain_langpack), chyba że używasz pakietu przeznaczonego dla wszystkich systemów operacyjnych|
|Metoda wdrażania|Obsługuje wszystkie metody:<br /><br />- [Clickonce](#clickonce-deployment)<br />- [Instalacjaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Instalator Windows XML (WiX)](#wix)<br />- [Instalacja ręczna](#installing_manually)<br />- [Konfiguracja niestandardowa (tworzenie łańcucha)](#chaining)|Obsługuje wszystkie metody:<br /><br /> - [Clickonce](#clickonce-deployment)<br />- [Instalacjaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Instalator Windows XML (WiX)](#wix)<br />- [Instalacja ręczna](#installing_manually)<br />- [Konfiguracja niestandardowa (tworzenie łańcucha)](#chaining)|

\*Instalator w trybie offline jest większy, ponieważ zawiera składniki dla wszystkich platform docelowych. Po zakończeniu instalacji z systemem system operacyjny Windows buforuje tylko instalator, który był używany. Jeśli instalator w trybie offline zostanie usunięty po instalacji, użyte miejsce na dysku jest takie samo, jak używane przez instalatora sieci web. Jeśli narzędzie używane (na przykład [InstallAware](#installaware-deployment) lub [InstallShield)](#installshield-deployment)do utworzenia programu instalacyjnego aplikacji udostępnia folder plików instalacyjnych, który zostanie usunięty po instalacji, instalator trybu offline może zostać automatycznie usunięty, umieszczając go w folderze instalacyjnym.

\*\*Jeśli używasz instalatora sieci web z konfiguracją niestandardową, możesz użyć domyślnych ustawień języka opartych na ustawieniu wielojęzycznego `/LCID` interfejsu użytkownika użytkownika (MUI) lub określić inny pakiet językowy za pomocą tej opcji w wierszu polecenia. Zobacz sekcję [Tworzenie łańcucha przy użyciu domyślnego interfejsu użytkownika programu .NET Framework](#chaining_default) dla przykładów.

## <a name="deployment-methods"></a>Metody wdrażania

 Dostępne są cztery metody wdrażania:

- Można ustawić zależność na .NET Framework. Program .NET Framework można określić jako warunek wstępny instalacji aplikacji przy użyciu jednej z następujących metod:

  - Użyj [wdrożenia ClickOnce](#clickonce-deployment) (dostępnego w programie Visual Studio)

  - Tworzenie [projektu InstallAware](#installaware-deployment) (bezpłatna wersja dostępna dla użytkowników programu Visual Studio)

  - Tworzenie [projektu InstallShield](#installshield-deployment) (dostępnego w programie Visual Studio)

  - Korzystanie z zestawu [narzędzi XML (WiX) Instalatora Windows](#wix)

- Możesz poprosić użytkowników o [ręczne zainstalowanie programu .NET Framework](#installing_manually).

- Proces instalacji programu .NET Framework można w konfiguracji programu .NET Framework wiązać z łańcuchem i zdecydować, w jaki sposób chcesz obsługiwać środowisko instalacji programu .NET Framework:

  - [Użyj domyślnego interfejsu użytkownika](#chaining_default). Pozwól instalatorowi .NET Framework zapewnić środowisko instalacji.

  - [Dostosuj interfejs użytkownika,](#chaining_custom) aby przedstawić ujednolicone środowisko instalacji i monitorować postęp instalacji programu .NET Framework.

Te metody wdrażania są szczegółowo omówione w poniższych sekcjach.

## <a name="setting-a-dependency-on-the-net-framework"></a>Ustawianie zależności od programu .NET Framework

Jeśli używasz ClickOnce, InstallAware, InstallShield lub WiX do wdrażania aplikacji, można dodać zależność od programu .NET Framework, aby można było zainstalować jako część aplikacji.

### <a name="clickonce-deployment"></a>wdrożenie ClickOnce

ClickOnce wdrożenia jest dostępna dla projektów, które są tworzone za pomocą języka Visual Basic i Visual C#, ale nie jest dostępna dla języka Visual C++.

W programie Visual Studio, aby wybrać clickonce wdrożenia i dodać zależność na .NET Framework:

1. Otwórz projekt aplikacji, który chcesz opublikować.

2. W Eksploratorze rozwiązań otwórz menu **skrótów**dla projektu, a następnie wybierz polecenie Właściwości .

3. Wybierz okienko **Publikowania.**

4. Wybierz przycisk **Wymagania wstępne.**

5. W oknie dialogowym **Wymagania wstępne** upewnij się, że jest zaznaczone pole wyboru **Utwórz program instalacyjny do zainstalowania składników wymagań wstępnych.**

6. Na liście wymagań wstępnych znajdź i wybierz wersję programu .NET Framework, która została użyta do utworzenia projektu.

7. Wybierz opcję, aby określić lokalizację źródłową dla wymagań wstępnych, a następnie wybierz przycisk **OK**.

     Jeśli podasz adres URL dla lokalizacji pobierania programu .NET Framework, możesz określić stronę pobierania programu .NET Framework lub własną witrynę. Jeśli pakiet redystrybucyjny jest umieszczany na własnym serwerze, musi on być instalatorem w trybie offline, a nie instalatorem sieci Web. Łącze do instalatora sieci Web można utworzyć tylko na stronie pobierania programu .NET Framework. Adres URL może również określić dysk, na którym jest dystrybuowana własna aplikacja.

8. W oknie dialogowym **Strony właściwości** wybierz pozycję **OK**.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>Wdrożenie instalacjiware

InstallAware tworzy pakiety aplikacji systemu Windows (APPX), Instalatora Windows (MSI), kodu macierzystego (EXE) i app-v (wirtualizacja aplikacji) z jednego źródła. Łatwo [dołącz dowolną wersję programu .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) w konfiguracji, opcjonalnie dostosowując instalację, [edytując skrypty domyślne.](https://www.installaware.com/msicode.htm) Na przykład installAware preinstaluje certyfikaty w systemie Windows 7, bez których instalator programu .NET Framework 4.7 kończy się niepowodzeniem. Aby uzyskać więcej informacji na temat installaware, zobacz [InstallAware dla Instalatora Windows](https://www.installaware.com/) w sieci Web.

### <a name="installshield-deployment"></a>Wdrożenie InstallShield

InstallShield tworzy pakiety aplikacji systemu Windows (MSIX, APPX), instalatory pakietów Instalatora Windows (MSI) i kod macierzysty (EXE). InstallShield zapewnia również integrację programu Visual Studio. Aby uzyskać więcej informacji, zobacz witrynę [installshield.](https://www.flexerasoftware.com/install/products/installshield.html)

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Wdrożenie XML Instalatora Windows (WiX)

Zestaw narzędzi XML Instalatora Windows (WiX) tworzy pakiety instalacyjne systemu Windows z kodu źródłowego XML. WiX obsługuje środowisko wiersza polecenia, które można zintegrować z procesami kompilacji w celu tworzenia pakietów instalacyjnych MSI i MSM. Za pomocą WiX, można [określić .NET Framework jako warunek wstępny](https://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html)lub [utworzyć chainer](https://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) w pełni kontrolować środowisko wdrażania .NET Framework. Aby uzyskać więcej informacji na temat programu WiX, zobacz witrynę [sieci Web zestawu narzędzi Windows Installer XML (WiX).](https://wixtoolset.org/)

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>Ręczne instalowanie programu .NET Framework

W niektórych sytuacjach może być niepraktyczne, aby automatycznie zainstalować .NET Framework z aplikacją. W takim przypadku użytkownicy mogą samodzielnie zainstalować program .NET Framework. Pakiet redystrybucyjny jest dostępny w [dwóch pakietach.](#redistributable-packages) W procesie instalacji należy podać instrukcje dotyczące sposobu, w jaki użytkownicy powinni zlokalizować i zainstalować program .NET Framework.

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Tworzenie łańcucha instalacji programu .NET Framework z konfiguracją aplikacji

Jeśli tworzysz niestandardowy program instalacyjny dla aplikacji, możesz utworzyć łańcuch (uwzględnić) proces konfiguracji programu .NET Framework w procesie instalacji aplikacji. Tworzenie łańcucha zapewnia dwie opcje interfejsu użytkownika dla instalacji .NET Framework:

- Użyj domyślnego interfejsu użytkownika dostarczonego przez instalatora programu .NET Framework.

- Utwórz niestandardowy interfejs użytkownika dla instalacji platformy .NET Framework w celu zapewnienia spójności z programem instalacyjnym aplikacji.

Obie metody umożliwiają użycie instalatora sieci web lub instalatora w trybie offline. Każdy pakiet ma swoje zalety:

- Jeśli używasz instalatora sieci web, proces instalacji programu .NET Framework zdecyduje, który pakiet instalacyjny jest wymagany, a następnie pobierz i zainstaluj tylko ten pakiet z sieci Web.

- Jeśli używasz instalatora w trybie offline, możesz dołączyć kompletny zestaw pakietów instalacyjnych platformy .NET Framework z nośnikiem redystrybucji, aby użytkownicy nie musieli pobierać żadnych dodatkowych plików z sieci Web podczas instalacji.

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>Tworzenie łańcucha przy użyciu domyślnego interfejsu użytkownika programu .NET Framework

Aby po cichu posyłać proces instalacji programu .NET Framework i pozwolić instalatorowi .NET Framework podać interfejs użytkownika, dodaj następujące polecenie do programu instalacyjnego:

`<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>`

Jeśli na przykład program wykonywalny to Contoso.exe i chcesz dyskretnie zainstalować pakiet redystrybucyjny w trybie offline .NET Framework 4.5, użyj polecenia:

`dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso`

Aby dostosować instalację, można użyć dodatkowych opcji wiersza polecenia. Przykład:

- Aby zapewnić użytkownikom możliwość zamykania uruchomionych aplikacji platformy .NET Framework w celu `/showrmui` zminimalizowania ponownego uruchamiania systemu, ustaw tryb pasywny i użyj następującej opcji:

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     To polecenie umożliwia Menedżerowi ponownego uruchamiania wyświetlanie okna komunikatu, które daje użytkownikom możliwość zamknięcia aplikacji .NET Framework przed zainstalowaniem programu .NET Framework.

- Jeśli używasz instalatora sieci Web, możesz `/LCID` użyć tej opcji, aby określić pakiet językowy. Na przykład, aby spakować instalatora sieci web .NET Framework 4.5 do programu instalacyjnego contoso i zainstalować pakiet języka japońskiego, dodaj następujące polecenie do procesu konfiguracji aplikacji:

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     Jeśli ta opcja `/LCID` zostanie pominięta, instalator zainstaluje pakiet językowy zgodny z ustawieniem mui użytkownika.

    > [!NOTE]
    > Różne pakiety językowe mogą mieć różne daty wydania. Jeśli określony pakiet językowy nie jest dostępny w centrum pobierania, instalator zainstaluje program .NET Framework bez pakietu językowego. Jeśli program .NET Framework jest już zainstalowany na komputerze użytkownika, instalator zainstaluje tylko pakiet językowy.

Aby uzyskać pełną listę opcji, zobacz sekcję [Opcje wiersza polecenia.](#command-line-options)

Typowe kody zwrotne można znaleźć w sekcji [Kody zwrotów.](#return-codes)

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Tworzenie łańcucha przy użyciu niestandardowego interfejsu użytkownika

Jeśli masz niestandardowy pakiet instalacyjny, możesz po cichu uruchomić i śledzić konfigurację programu .NET Framework, wyświetlając własny widok postępu instalacji. W takim przypadku upewnij się, że kod obejmuje następujące elementy:

- Sprawdź [wymagania sprzętowe i programowe platformy .NET Framework](../get-started/system-requirements.md).

- [Wykryj,](#detect_net) czy na komputerze użytkownika jest już zainstalowana poprawna wersja programu .NET Framework.

    > [!IMPORTANT]
    > Przy określaniu, czy poprawna wersja programu .NET Framework jest już zainstalowana, należy sprawdzić, czy zainstalowana jest wersja docelowa *lub* nowsza, a nie czy jest zainstalowana wersja docelowa. Innymi słowy należy ocenić, czy klucz wydania pobrany z rejestru jest większy lub równy kluczowi wydania wersji docelowej, *a nie,* czy jest on równy kluczowi wydania wersji docelowej.

- [Wykryj,](#detecting-the-language-packs) czy pakiety językowe są już zainstalowane na komputerze użytkownika.

- Jeśli chcesz kontrolować wdrożenie, po cichu uruchom i śledź proces instalacji programu .NET Framework (zobacz [Jak: Uzyskaj postęp z instalatora .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)).

- Jeśli wdrażasz instalator w trybie offline, [należy je łańcucucucieć oddzielnie.](#chain_langpack)

- Dostosuj wdrożenie przy użyciu [opcji wiersza polecenia](#command-line-options). Na przykład jeśli dajesz łańcuch instalatorowi sieci web .NET Framework, ale chcesz zastąpić domyślny pakiet językowy, użyj `/LCID` tej opcji, zgodnie z opisem w poprzedniej sekcji.

- [Rozwiązywanie problemów](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>Wykrywanie programu .NET Framework

Instalator programu .NET Framework zapisuje klucze rejestru po pomyślnym zakończeniu instalacji. Można sprawdzić, czy program .NET Framework 4.5 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` lub nowszy `DWORD` jest `Release`zainstalowany, sprawdzając folder w rejestrze pod kątem wartości o nazwie . (Należy zauważyć, że "Net Framework Setup" nie zaczyna się od okresu.) Istnienie tego klucza wskazuje, że program .NET Framework 4.5 lub nowsza wersja została zainstalowana na tym komputerze. Wartość wskazuje, `Release` która wersja programu .NET Framework jest zainstalowana.

> [!IMPORTANT]
> Podczas próby wykrycia, czy istnieje określona wersja, należy sprawdzić wartość **większą lub równą** wartości słowa kluczowego wydania.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Wersja|Wartość DWORD dotycząca wersji|
|-------------|--------------------------------|
|.NET Framework 4.8 zainstalowany w systemie Windows 10 May 2019 Update|528040|
|.NET Framework 4.8 zainstalowany we wszystkich wersjach systemu operacyjnego innych niż Windows 10 May 2019 Update|528049|
|Program .NET Framework 4.7.2 zainstalowany w systemie Windows 10 April 2018 Update i Windows Server w wersji 1803|461808|
|Program .NET Framework 4.7.2 jest zainstalowany we wszystkich wersjach systemu operacyjnego innych niż Windows 10 April 2018 Update i Windows Server w wersji 1803. Obejmuje to aktualizację systemu Windows 10 z października 2018 r. |461814|
|.NET Framework 4.7.1 zainstalowany w systemie Windows 10 Fall Creators Update i windows server, wersja 1709|461308|
|.NET Framework 4.7.1 zainstalowany we wszystkich wersjach systemu operacyjnego innych niż Windows 10 Fall Creators Update i Windows Server, wersja 1709|461310|
|.NET Framework 4.7 zainstalowany w systemie Windows 10 Creators Update|460798|
|.NET Framework 4.7 zainstalowany we wszystkich wersjach systemu operacyjnego innych niż Windows 10 Creators Update|460805|
|Program .NET Framework 4.6.2 zainstalowany w systemie Windows 10 Anniversary Edition i windows Server 2016|394802|
|Program .NET Framework 4.6.2 zainstalowany we wszystkich wersjach systemu operacyjnego innych niż Windows 10 Anniversary Edition i Windows Server 2016|394806|
|.NET Framework 4.6.1 zainstalowany w systemie Windows 10 November Update|394254|
|.NET Framework 4.6.1 zainstalowany we wszystkich wersjach systemu operacyjnego innych niż Windows 10 November Update|394271|
|.NET Framework 4.6 zainstalowany w systemie Windows 10|393295|
|.NET Framework 4.6 zainstalowany we wszystkich wersjach systemu operacyjnego innych niż Windows 10|393297|
|.NET Framework 4.5.2|379893|
|Program .NET Framework 4.5.1 zainstalowany z systemem Windows 8.1 lub Windows Server 2012 R2|378675|
|.NET Framework 4.5.1 zainstalowany w systemie Windows 8, Windows 7|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>Wykrywanie pakietów językowych

Można sprawdzić, czy określony pakiet językowy jest zainstalowany, sprawdzając HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* `Release`folderu w rejestrze dla wartości DWORD o nazwie . (Należy zauważyć, że "Net Framework Setup" nie zaczyna się od okresu.) *LCID* określa identyfikator ustawień regionalnych; zobacz [obsługiwane języki,](#supported-languages) aby uzyskać ich listę.

Na przykład, aby wykryć, czy jest zainstalowany pełny pakiet języka japońskiego (LCID=1041), pobierz następującą nazwaną wartość z rejestru:

| | |
|-|-|
| Klucz | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041 |
| Nazwa | Release |
| Typ | DWORD |

Aby ustalić, czy ostateczna wersja pakietu językowego jest zainstalowana dla określonej wersji programu .NET Framework od 4.5 do 4.7.2, sprawdź wartość klucza RELEASE DWORD opisaną w poprzedniej sekcji [Wykrywanie programu .NET Framework](#detect_net).

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Tworzenie pakietów językowych do konfiguracji aplikacji

Program .NET Framework udostępnia zestaw autonomicznych plików wykonywalnych pakietu językowego, które zawierają zlokalizowane zasoby dla określonych kultur. Pakiety językowe są dostępne na stronach Pobierz program .NET Framework:

- [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Framework 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [Program .NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

> [!IMPORTANT]
> Pakiety językowe nie zawierają składników .NET Framework, które są wymagane do uruchomienia aplikacji; Przed zainstalowaniem pakietu językowego należy zainstalować program .NET Framework przy użyciu instalatora sieci Web lub instalatora w trybie offline.

Począwszy od programu .NET Framework 4.5.1, nazwy pakietów `version` przybierają postać NDP `number`<>-KB<`culture`>-x86-x64-AllOS-<>.exe, `version` gdzie jest numer wersji programu `number` .NET Framework, jest numerem artykułu bazy wiedzy Microsoft Knowledge Base i `culture` określa [kraj/region](#supported-languages). Przykładem jednego z tych `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`pakietów jest . Nazwy pakietów są wymienione w sekcji [Pakiety redystrybucyjne](#redistributable-packages) wcześniej w tym artykule.

Aby zainstalować pakiet językowy za pomocą instalatora trybu offline programu .NET Framework, należy go związać z konfiguracją aplikacji. Na przykład, aby wdrożyć instalator trybu offline programu .NET Framework 4.5.1 z pakietem języka japońskiego, należy użyć następującego polecenia:

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

Nie trzeba łańcuszkowy pakietów językowych, jeśli używasz instalatora sieci web; instalator zainstaluje pakiet językowy, który pasuje do ustawienia MUI użytkownika. Jeśli chcesz zainstalować inny język, możesz `/LCID` użyć tej opcji, aby określić pakiet językowy.

Aby uzyskać pełną listę opcji wiersza polecenia, zobacz sekcję [Opcje wiersza polecenia.](#command-line-options)

### <a name="troubleshooting"></a>Rozwiązywanie problemów

#### <a name="return-codes"></a>Kody powrotne

W poniższej tabeli wymieniono najczęstsze kody zwrotne dla redystrybucyjnego instalatora .NET Framework. Kody powrotne są takie same dla wszystkich wersji instalatora. Aby uzyskać łącza do szczegółowych informacji, zobacz następną sekcję.

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

- [Kody błędów usługi inteligentnego transferu w tle (BITS)](https://go.microsoft.com/fwlink/?LinkId=180946)

- [Kody błędów monikera url](https://go.microsoft.com/fwlink/?LinkId=180947)

- [Kody błędów winhttp](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Inne kody błędów

Zobacz następującą zawartość:

- [Kody błędów Instalatora Windows](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Kody wyników programu Windows Update Agent](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Odinstalowywanie programu .NET Framework

Począwszy od systemu Windows 8, można odinstalować wersje programu .NET Framework 4.5 lub nowszych przy użyciu **funkcji włączania i wyłączania funkcji systemu Windows** w Panelu sterowania. W starszych wersjach systemu Windows można odinstalować wersje programu .NET Framework 4.5 lub nowszych za pomocą **funkcji Dodaj lub usuń programy** w Panelu sterowania.

> [!IMPORTANT]
> W przypadku systemów operacyjnych Windows 7 i wcześniejszych odinstalowywanie programu .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 lub 4.8 nie przywraca plików .NET Framework 4.5, a odinstalowanie .NET Framework 4.5 nie przywraca plików .NET Framework 4. Jeśli chcesz wrócić do starszej wersji, należy ją ponownie zainstalować i wszelkie aktualizacje.

## <a name="appendix"></a>Dodatek

### <a name="command-line-options"></a>Opcje wiersza polecenia

W poniższej tabeli wymieniono opcje, które można uwzględnić podczas łańcucha programu .NET Framework 4.5 redystrybucyjnego do konfiguracji aplikacji.

|Opcja|Opis|
|------------|-----------------|
|**/CEIPWrozumień**|Zastępuje domyślne zachowanie i wysyła anonimowe opinie do firmy Microsoft w celu poprawy przyszłych środowisk wdrażania. Tej opcji można używać tylko wtedy, gdy program instalacyjny monituje o zgodę i jeśli użytkownik udziela uprawnień do wysyłania anonimowych opinii do firmy Microsoft.|
|**/pakiet łańcuchowy**`packageName`|Określa nazwę pliku wykonywalnego, który wykonuje tworzenie łańcucha. Te informacje są wysyłane do firmy Microsoft jako anonimowa opinia w celu poprawy przyszłych środowisk wdrażania.<br /><br /> Jeśli nazwa pakietu zawiera spacje, należy użyć podwójnych cudzysłowów jako ograniczników; na przykład: **/chainingpackage "Lucerna Publishing"**. Na przykład pakietu łańcucha zobacz [Uzyskiwanie informacji o postępie z pakietu instalacyjnego](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).|
|**/LCID**  `LCID`<br /><br /> gdzie `LCID` określa identyfikator ustawień regionalnych (patrz [obsługiwane języki)](#supported-languages)|Instaluje pakiet językowy określony przez `LCID` i wymusza wyświetlanie wyświetlanego interfejsu użytkownika w tym języku, chyba że ustawiony jest tryb cichy.<br /><br /> W przypadku instalatora sieci Web ta opcja instaluje pakiet językowy z sieci Web. **Uwaga:**  Tej opcji należy używać tylko w przypadku instalatora sieci Web.|
|**/log** `file` &#124;`folder`|Określa lokalizację pliku dziennika. Wartość domyślna to folder tymczasowy dla procesu, a domyślna nazwa pliku jest oparta na pakiecie. Jeśli rozszerzenie pliku jest .txt, zostanie opracowany dziennik tekstu. Jeśli określisz inne rozszerzenie lub nie ma rozszerzenia, tworzony jest dziennik HTML.|
|**/msioptions**|Określa opcje, które mają być przekazywane dla elementów msi i msp; na przykład: `/msioptions "PROPERTY1='Value'"`.|
|**/norestart**|Zapobiega automatycznemu ponownemu uruchomieniu programu instalacyjnego. Jeśli używasz tej opcji, aplikacja łańcucha musi przechwycić kod zwrotny i obsługiwać ponowne uruchomienie (zobacz [Uzyskiwanie informacji o postępie z pakietu instalacyjnego](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))).|
|**/pasywny**|Ustawia tryb pasywny. Wyświetla pasek postępu, aby wskazać, że instalacja jest w toku, ale nie wyświetla żadnych monitów lub komunikatów o błędach dla użytkownika. W tym trybie, po dołączeniu do łańcucha przez program instalacyjny, pakiet łańcucha musi obsługiwać [kody zwrotne](#return-codes).|
|**/rura**|Tworzy kanał komunikacji, aby włączyć pakiet tworzenia łańcucha, aby uzyskać postęp.|
|**/promptrestart**|Tylko tryb pasywny, jeśli program instalacyjny wymaga ponownego uruchomienia, monituje użytkownika. Ta opcja wymaga interakcji z użytkownikiem, jeśli wymagane jest ponowne uruchomienie.|
|**/q**|Ustawia tryb cichy.|
|**/naprawa**|Wyzwala funkcję naprawy.|
|**/serialdownload**|Wymusza instalację dopiero po pobraniu pakietu.|
|**/showfinalerror**|Ustawia tryb pasywny. Wyświetla błędy tylko wtedy, gdy instalacja nie powiedzie się. Ta opcja wymaga interakcji z użytkownikiem, jeśli instalacja nie powiedzie się.|
|**/showrmui**|Używany tylko z opcją **/passive.** Wyświetla okno komunikatu z monitem o zamknięcie aplikacji programu .NET Framework, które są aktualnie uruchomione. To okno komunikatu zachowuje się tak samo w trybie pasywnym i niea passive.|
|**/odinstaluj**|Odinstalowuje program .NET Framework redystrybucyjny.|

### <a name="supported-languages"></a>Obsługiwane języki

W poniższej tabeli wymieniono pakiety językowe programu .NET Framework, które są dostępne dla platformy .NET Framework 4.5 i nowszych wersji.

|Identyfikator LCID|Język – kraj/region|Culture|
|----------|--------------------------------|-------------|
|1025|Arabski - Arabia Saudyjska|Ar|
|1028|Chiński – tradycyjny|zh-Hant|
|1029|Czeski|Cs|
|1030|duński|da|
|1031|Niemiecki – Niemcy|de|
|1032|grecki|El|
|1035|fiński|fi|
|1036|Francuski – Francja|fr|
|1037|Hebrajski|On|
|1038|węgierski|Hu|
|1040|Włoski – Włochy|it|
|1041|Japoński|ja|
|1042|Koreański|Ko|
|1043|Holenderski – Holandia|nl|
|1044|Norweski (Bokmål)|nie|
|1045|Polski|Pl|
|1046|Portugalski – Brazylia|pt-BR|
|1049|Rosyjski|ru|
|1053|szwedzki|sv|
|1055|Turecki|Tr|
|2052|Chiński – Uproszczony|zh-Hans|
|2070|Portugalski – Portugalia|pt-PT|
|3082|Hiszpański - Hiszpania (Modern Sort)|Tak|

## <a name="see-also"></a>Zobacz też

- [Przewodnik wdrażania dla administratorów](guide-for-administrators.md)
- [Wymagania systemowe](../get-started/system-requirements.md)
- [Instalowanie programu .NET Framework dla deweloperów](../install/guide-for-developers.md)
- [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
- [Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5](reducing-system-restarts.md)
- [Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)
