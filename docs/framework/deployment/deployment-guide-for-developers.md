---
title: .NET framework — przewodnik wdrażania dla deweloperów
ms.custom: updateeachrelease
ms.date: 12/14/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b2083efabd6c16bafd8b241980c4cd413258ae5
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="net-framework-deployment-guide-for-developers"></a>.NET framework — przewodnik wdrażania dla deweloperów
Ten temat zawiera informacje dla deweloperów, którzy chcą zainstalować dowolnej wersji programu .NET Framework z .NET Framework 4.5 do [!INCLUDE[net_current](../../../includes/net-current-version.md)] w swoich aplikacjach.

Pobieranie łączy, zobacz sekcję [pakiety redystrybucyjne](#redistributable-packages). Możesz również pobrać pakiet redystrybucyjny pakiety i pakiety językowe z tych stronach witryny Microsoft Download Center:

- .NET framework 4.7.1 we wszystkich systemach operacyjnych ([Instalator sieci web](http://go.microsoft.com/fwlink/?LinkId=852095) lub [Instalatora w trybie offline](http://go.microsoft.com/fwlink/p/?LinkId=852107))

- .NET framework 4.7 we wszystkich systemach operacyjnych ([Instalator sieci web](http://go.microsoft.com/fwlink/?LinkId=825299) lub [Instalatora w trybie offline](http://go.microsoft.com/fwlink/p/?LinkId=825303))

- [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] we wszystkich systemach operacyjnych ([Instalator sieci web](http://go.microsoft.com/fwlink/?LinkId=780597) lub [Instalatora w trybie offline](http://go.microsoft.com/fwlink/p/?LinkId=780601))

- [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] we wszystkich systemach operacyjnych ([Instalator sieci web](http://go.microsoft.com/fwlink/?LinkId=671729) lub [Instalatora w trybie offline](http://go.microsoft.com/fwlink/p/?LinkId=671744))

- [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] we wszystkich systemach operacyjnych ([Instalator sieci web](http://go.microsoft.com/fwlink/?LinkId=528222) lub [Instalatora w trybie offline](http://go.microsoft.com/fwlink/p/?LinkId=528232))

- .NET framework 4.5.2 we wszystkich systemach operacyjnych ([Instalator sieci web](http://go.microsoft.com/fwlink/p/?LinkId=397703) lub [Instalatora w trybie offline](http://go.microsoft.com/fwlink/p/?LinkId=397706))

- .NET framework 4.5.1 we wszystkich systemach operacyjnych ([Instalator sieci web](http://go.microsoft.com/fwlink/p/?LinkId=310158) lub [Instalatora w trybie offline](http://go.microsoft.com/fwlink/p/?LinkId=310159))

- [Program .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)

 Ważne informacje:

> [!NOTE]
> Wyrażenie " [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i zwalnia jego punktu" odwołuje się do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i wszystkich nowszych wersji.

- Wersje programu .NET Framework z [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] za pośrednictwem [!INCLUDE[net_current](../../../includes/net-current-version.md)] są aktualizacje w miejscu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], co oznacza korzystają z tej samej wersji środowiska uruchomieniowego, ale wersji zestawu są aktualizowane i zawiera nowe typy i składniki.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i zwalnia jego punktu są tworzone przyrostowo na [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Po zainstalowaniu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub zwalnia jego punktu w systemie, który ma [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zainstalowane, zestawy w wersji 4 są zamieniane na nowsze wersje.

- Jeśli utworzono odwołanie do firmy Microsoft [pakietu poza pasmem](http://msdn.microsoft.com/library/dn151288\(v=vs.110\).aspx) w aplikacji, zestaw zostaną uwzględnione w pakiecie aplikacji.

- Musi mieć uprawnienia administratora, aby zainstalować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i zwalnia jego punktu.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Znajduje się w [!INCLUDE[win8](../../../includes/win8-md.md)] i [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], więc nie trzeba wdrożyć ją z aplikacją w tych systemach operacyjnych. Podobnie [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] znajduje się w [!INCLUDE[win81](../../../includes/win81-md.md)] i Windows Server 2012 R2. .NET Framework 4.5.2 nie jest zawarty w systemy operacyjne. [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] Znajduje się w systemie Windows 10 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] znajduje się w systemie Windows 10 listopada aktualizacji i [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] znajduje się w systemie Windows 10 Anniversary aktualizacji.  .NET Framework 4.7 jest zawarta w systemie Windows 10 twórców aktualizacji, a .NET Framework 4.7.1 jest dołączony do systemu Windows 10 spadek twórców aktualizacji. Aby uzyskać pełną listę wymagań sprzętowych i programowych, zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).

- Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], użytkowników można wyświetlić listę uruchamianie aplikacji programu .NET Framework podczas instalacji i łatwo je zamknąć. Może to pomóc uniknąć ponownego uruchomienia systemu spowodowany instalacja programu .NET Framework. Zobacz [zmniejszenie liczby systemu ponownych uruchomień](../../../docs/framework/deployment/reducing-system-restarts.md).

- Odinstalowywanie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub jeden z jego punktu zwalnia również usuwa istniejące [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] plików. Jeśli chcesz powrócić do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], musisz ponownie zainstalować go i wszelkie aktualizacje. (Zobacz [Instalowanie programu .NET Framework 4](http://msdn.microsoft.com/library/5a4x27ek\(v=vs.100\).aspx).)

- Pakiet redystrybucyjny systemu .NET Framework 4.5 został zaktualizowany na 9 października 2012 r. Aby rozwiązać problem związany z nieprawidłowej znacznik czasu certyfikatu cyfrowego, który spowodował podpisu cyfrowego plików utworzony i podpisany przez firmę Microsoft przedwcześnie wygaśnie. Jeśli wcześniej zainstalowane środowisko .NET Framework 4.5 pakietu redystrybucyjnego z 16 sierpień 2012, zaleca się aktualizację kopii z najnowszych pakiet redystrybucyjny programu z [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=245484). Aby uzyskać więcej informacji na temat tego problemu, zobacz [Microsoft Security Advisory 2749655](http://technet.microsoft.com/security/advisory/2749655).

 Aby dowiedzieć się jak administrator systemu może wdrożenia programu .NET Framework i jego zależności systemu w sieci, zobacz [przewodnik wdrażania dla administratorów](../../../docs/framework/deployment/guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Opcje wdrażania aplikacji
 Jeśli wszystko jest gotowe do opublikowania aplikacji do serwera sieci web lub innych centralnej lokalizacji, dzięki czemu użytkownicy mogą zainstalować ją, można z kilku metod wdrażania. Niektóre z nich są wyposażone w Visual Studio. Poniższa tabela zawiera listę opcje wdrażania aplikacji i określa pakiet redystrybucyjny programu .NET Framework obsługującą każdej opcji. Oprócz tych można zapisywać niestandardowego Instalatora dla aplikacji; Aby uzyskać więcej informacji, zobacz sekcję [łańcucha instalacji programu .NET Framework do Instalatora aplikacji platformy](#chaining).

|Strategię wdrażania aplikacji|Dostępne metody wdrażania|.NET framework do dystrybucji do użycia|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Zainstaluj z sieci web|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Zestaw narzędzi](#wix)<br />- [Instalacja ręczna](#installing_manually)|[Instalator sieci Web](#redistributable-packages)|
|Zainstaluj z dysku|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Zestaw narzędzi](#wix)<br />- [Instalacja ręczna](#installing_manually)|[Instalatora w trybie offline](#redistributable-packages)|
|Zainstaluj z sieci lokalnej (dla aplikacji enterprise)|- [ClickOnce](#clickonce-deployment)|Albo [Instalator sieci web](#redistributable-packages) (zobacz [ClickOnce](#clickonce-deployment) dla ograniczenia) lub [Instalatora w trybie offline](#redistributable-packages)|

## <a name="redistributable-packages"></a>Pakiety redystrybucyjne
 .NET Framework jest dostępny w dwóch pakiety redystrybucyjne: sieci web Instalatora (programu inicjującego) i Instalatora w trybie offline (autonomiczny pakiet redystrybucyjny). W poniższej tabeli porównano dwa pakiety.

||Instalator sieci Web|Instalatora w trybie offline|
|-|-------------------|-----------------------|
|Pobierz plik|.NET Framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](http://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>.NET framework 4.7: <br />[NDP47-KB3186500-Web.exe](http://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151802-Web.exe](http://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]:<br />[NDP461-KB3102438-Web.exe](http://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]:<br />[NDP46-KB3045560-Web.exe](http://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](http://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2859818-Web.exe](http://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_setup.exe](http://go.microsoft.com/fwlink/?LinkId=225704)|.NET Framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET framework 4.7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_x86_x64.exe](http://go.microsoft.com/fwlink/?LinkId=225702)|
|Wymagane połączenie z Internetem?|Tak|Nie|
|Rozmiar pobierania|Mniejsze (zawiera Instalatora dla docelowej platformy) *|Larger*|
|Pakiety językowe|Included**|Musi być [instalowane osobno,](#chain_langpack), chyba że używasz pakietu, który jest przeznaczony dla wszystkich systemów operacyjnych|
|Metody wdrażania|Obsługuje wszystkie metody:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Instalator Windows XML (WiX)](#wix)<br />- [Instalacja ręczna](#installing_manually)<br />- [Instalacja niestandardowa (łańcucha)](#chaining)|Obsługuje wszystkie metody:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Instalator Windows XML (WiX)](#wix)<br />- [Instalacja ręczna](#installing_manually)<br />- [Instalacja niestandardowa (łańcucha)](#chaining)|
|Lokalizacja pobierania wdrożenia ClickOnce|Centrum pobierania Microsoft:<br /><br /> - [.NET Framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET Framework 4.5.2](http://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET Framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [Program .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|Własny serwer lub Microsoft Download Center:<br /><br /> - [.NET Framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET Framework 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET Framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [Program .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|

 \* Instalatora w trybie offline jest większy, ponieważ zawiera składniki na wszystkich platformach docelowych. Po zakończeniu uruchamiania Instalatora systemu operacyjnego Windows buforuje Instalator, który został użyty. Jeśli Instalatora w trybie offline zostanie usunięty po zakończeniu instalacji, użycie miejsca na dysku jest taka sama, jak używany przez Instalator sieci web. Jeśli używasz narzędzia (na przykład [InstallAware](#installaware-deployment) lub [InstallShield](#installshield-deployment)) do tworzenia aplikacji, program instalacyjny zawiera folder pliku konfiguracji, który zostanie usunięty po zakończeniu instalacji, może być Instalatora w trybie offline automatycznie usuwane przez umieszczenie go w folderze instalacyjnym.

 ** Jeśli Instalator sieci web jest używany z instalacji niestandardowej, może użyć domyślnych ustawień języka na podstawie ustawienia wielojęzycznego interfejsu użytkownika (MUI) użytkownika, lub określ inny pakiet językowy, używając `/LCID` opcji w wierszu polecenia. Zobacz sekcję [łańcucha przy użyciu interfejsu użytkownika domyślne Framework .NET](#chaining_default) przykłady.

## <a name="deployment-methods"></a>Metody wdrażania
 Dostępne są cztery metody wdrażania:

- Można ustawić zależności w programie .NET Framework. Warunkiem wstępnym instalacji aplikacji przy użyciu jednej z tych metod, można określić programu .NET Framework:

    - Użyj [wdrażania ClickOnce](#clickonce-deployment) (dostępnych z programem Visual Studio)

    - Utwórz [projektu InstallAware](#installaware-deployment) (bezpłatna wersja dostępne dla użytkowników programu Visual Studio)

    - Utwórz [projektu InstallShield](#installshield-deployment) (dostępnych z programem Visual Studio)

    - Użyj [zestaw narzędzi XML Instalatora Windows (WiX)](#wix)

- Poproś użytkowników, aby [ręcznie zainstaluj program .NET Framework](#installing_manually).

- Może być powiązane (Dołącz) programu .NET Framework konfiguracji w ustawieniach aplikacji i zdecydować, jak obsłużyć środowisko .NET Framework instalacji:

    - [Użyj domyślnego interfejsu użytkownika](#chaining_default). Pozwolić, aby zapewnić środowisko instalacji Instalator .NET Framework.

    - [Dostosowywanie interfejsu użytkownika](#chaining_custom) przedstawienia środowisko unified instalacji i monitorować postęp instalacji platformy .NET Framework.

 Te metody wdrażania opisano szczegółowo w poniższych sekcjach.

## <a name="setting-a-dependency-on-the-net-framework"></a>Ustawienie zależności w programie .NET Framework
Użycie ClickOnce, InstallAware, InstallShield lub WiX do wdrożenia aplikacji, dlatego może być zainstalowana jako część aplikacji można dodać zależności w programie .NET Framework.

### <a name="clickonce-deployment"></a>wdrożenie ClickOnce
 Wdrożenie ClickOnce jest dostępne dla projektów utworzonych za pomocą języka Visual Basic i Visual C#, ale nie jest dostępna dla programu Visual C++.

 W programie Visual Studio, aby wybrać wdrażania ClickOnce i Dodawanie zależności w programie .NET Framework:

1.  Otwórz projekt aplikacji, którą chcesz opublikować.

2.  W Eksploratorze rozwiązań Otwórz menu skrótów projektu, a następnie wybierz **właściwości**.

3.  Wybierz **publikowania** okienka.

4.  Wybierz **wymagania wstępne** przycisku.

5.  W **wymagania wstępne** okna dialogowego upewnij się, że **Utwórz Instalatora, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.

6.  Na liście wymagania wstępne Znajdź i wybierz wersję programu .NET Framework, która była używana do tworzenia projektu.

7.  Wybierz opcję, aby określić lokalizację źródłową wymagania wstępne, a następnie wybierz **OK**.

     Podaj adres URL lokalizacji pobierania .NET Framework, można określić witryny Microsoft Download Center lub lokacji własny. Jeśli pakiet redystrybucyjny umieszczanie na danym serwerze, musi być Instalatora w trybie offline i nie Instalator sieci web. Można połączyć tylko Instalator sieci web w Microsoft Download Center. Adres URL można także określić dysk, na którym jest dystrybuowany własnych aplikacji.

8.  W **strony właściwości** oknie dialogowym wybierz **OK**.

<a name="installaware"></a> 
### <a name="installaware-deployment"></a>InstallAware wdrożenia
InstallAware tworzy aplikację systemu Windows (APPX), Instalatora Windows (MSI), kodu natywnego (EXE) i pakiety App-V (Wirtualizacja aplikacji) z jednego źródła. Łatwe [obejmują dowolnej wersji programu .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) w ustawieniach, dostosowywanie opcjonalnie instalacji przez [edycji skryptów domyślne](https://www.installaware.com/msicode.htm). Na przykład InstallAware instaluje wstępnie certyfikatów w systemie Windows 7, bez których instalacja programu .NET Framework 4.7 zakończy się niepowodzeniem. Aby uzyskać więcej informacji o InstallAware, zobacz [InstallAware dla Instalatora Windows](https://www.installaware.com/) witryny sieci Web.

### <a name="installshield-deployment"></a>InstallShield wdrożenia
 W programie Visual Studio, aby wybrać InstallShield wdrożenia i dodać zależności w programie .NET Framework:

1.  Na pasku menu programu Visual Studio wybierz **pliku**, **nowy**, **projektu**.

2.  W lewym okienku **nowy projekt** oknie dialogowym wybierz **inne typy projektów**, **instalacji i wdrażania**, **InstallShield LE**.

3.  W **nazwa** wpisz nazwę projektu, a następnie wybierz pozycję **OK**.

4.  W przypadku tworzenia projektu Instalatora i wdrażanie po raz pierwszy, wybierz **przejdź do InstallShield** lub **Włącz InstallShield Limited Edition** pobrać InstallShield Limited Edition dla używanej wersji programu Microsoft Visual Studio. Uruchom ponownie program Visual Studio.

5.  Przejdź do **Asystentem projektu** kreatora i wybrać **pliki aplikacji** można dodać danych wyjściowych projektu. Inne atrybuty projektu można skonfigurować za pomocą tego kreatora.

6.  Przejdź do **wymagania dotyczące instalacji** i wybierz systemów operacyjnych i wersji programu .NET Framework, które chcesz zainstalować.

7.  Otwórz menu skrótów projektu Instalatora i wybrać **kompilacji**.
 
<a name="wix"></a> 
### <a name="windows-installer-xml-wix-deployment"></a>Wdrożenie XML Instalatora Windows (WiX)
 Zestaw narzędzi XML Instalatora Windows (WiX) tworzy pakiety instalacyjne systemu Windows z kodu źródłowego XML. WiX obsługuje środowisko z wiersza polecenia, które można zastosować do procesów kompilacji do kompilacji z rozszerzeniami MSI i MSM pakiety instalacyjne. Za pomocą WiX, można [Określ platformę .NET jako warunek wstępny](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html), lub [utworzyć moduł łańcucha](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) pełnej kontroli środowisko .NET Framework wdrożenia. Aby uzyskać więcej informacji o WiX, zobacz [zestaw narzędzi XML Instalatora Windows (WiX)](http://wixtoolset.org/) witryny sieci Web.

<a name="installing_manually"></a> 
## <a name="installing-the-net-framework-manually"></a>Ręczne instalowanie programu .NET Framework
 W niektórych sytuacjach może być niemożliwe do automatycznego zainstalowania programu .NET Framework z aplikacją. W takim przypadku można mieć użytkownicy sami zainstalują program .NET Framework. Pakiet redystrybucyjny jest dostępny w [dwa pakiety](#redistributable-packages). W procesie instalacji zawierają instrukcje, jak użytkownicy należy zlokalizować i zainstalować program .NET Framework.

<a name="chaining"></a> 
## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Tworzenie łańcuchów instalacji programu .NET Framework do ustawień aplikacji
 Jeśli tworzysz niestandardowego Instalatora dla aplikacji, tworzenia łańcucha (Dołącz) .NET Framework procesu instalacji w procesie instalacji. Tworzenie łańcuchów oferuje dwie opcje interfejsu użytkownika dla instalacji programu .NET Framework:

- Użyj domyślnego interfejsu użytkownika udostępniane przez Instalator .NET Framework.

- Tworzenie niestandardowego interfejsu użytkownika dla instalacji programu .NET Framework w celu zachowania spójności z Instalatorem aplikacji.

 Obie metody umożliwiają używanie Instalator sieci web lub Instalatora w trybie offline. Każdy pakiet ma jego zalety:

- Jeśli używasz Instalator sieci web, proces instalacji platformy .NET Framework zdecydować, które pakiet instalacyjny jest wymagane i pobierze i zainstaluje tylko tego pakietu z sieci web.

- Jeśli korzystasz z Instalatora w trybie offline, można dołączyć pełny zestaw pakietów instalacyjnych .NET Framework z multimediów redystrybucji, aby użytkownicy nie musieli wszelkie dodatkowe pliki z sieci web podczas instalacji.

<a name="chaining_default"></a> 
### <a name="chaining-by-using-the-default-net-framework-ui"></a>Tworzenie łańcuchów przy użyciu domyślnego interfejsu użytkownika programu .NET Framework
 Aby dyskretnie łańcucha .NET Framework procesu instalacji i umożliwić Instalator .NET Framework, podaj interfejsu użytkownika, należy dodać następujące polecenie do programu Instalatora:

```
<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>
```

 Na przykład, jeśli program wykonywalny jest Contoso.exe i chcesz dyskretnie zainstalować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pakiet redystrybucyjny trybu offline, użyj polecenia:

```
dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso
```

 Dodatkowe opcje wiersza polecenia umożliwia dostosowanie instalacji. Na przykład:

- Aby umożliwiają użytkownikom zamknąć uruchomionych aplikacji .NET Framework zminimalizować ponownego uruchomienia systemu, należy ustawić w trybie pasywnym i użyj `/showrmui` opcji w następujący sposób:

    ```
    dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso
    ```

     To polecenie umożliwia Menedżer ponownego uruchomienia, aby wyświetlić komunikat, który daje użytkownikom możliwość zamknąć aplikacji .NET Framework, przed zainstalowaniem programu .NET Framework.

- Jeśli używasz programu Instalator sieci web, możesz użyć `/LCID` opcję, aby określić pakiet językowy. Na przykład do łańcucha [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora do programu Instalatora firmy Contoso w sieci web i zainstaluj pakiet języka japońskiego, Dodaj następujące polecenie, aby proces instalacji aplikacji:

    ```
    dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041
    ```

     W przypadku pominięcia `/LCID` opcji, Instalator zainstaluje pakiet językowy odpowiadający ustawienie MUI użytkownika.

    > [!NOTE]
    > Pakiety językowe różnych może mieć inną wersję daty. Jeśli pakiet językowy, które określisz nie jest dostępny w Centrum pobierania Microsoft, Instalator zainstaluje platformę .NET bez pakiet językowy. Jeśli programu .NET Framework jest już zainstalowana na komputerze, Instalator zainstaluje tylko pakiet językowy.

 Aby uzyskać pełną listę opcji, zobacz [opcje wiersza polecenia](#command-line-options) sekcji.

 Aby typowe kody powrotu, zobacz [kody powrotne](#return-codes) sekcji.

<a name="chaining_custom"></a>
### <a name="chaining-by-using-a-custom-ui"></a>Tworzenie łańcuchów przy użyciu niestandardowego interfejsu użytkownika
 Jeśli masz pakiet instalacyjny niestandardowych można dyskretnie uruchamianie i śledzić Instalatora programu .NET Framework podczas pokazywania widoku postęp instalacji. Jeśli jest to możliwe, upewnij się, że kod obejmuje następujące zagadnienia:

- Sprawdź, czy [wymagania dotyczące sprzętu i oprogramowania .NET Framework](../../../docs/framework/get-started/system-requirements.md).

- [Wykryj](#detect_net) czy poprawna wersja programu .NET Framework jest już zainstalowane na komputerze użytkownika.

    > [!IMPORTANT]
    > W określeniu, czy jest już zainstalowana poprawna wersja programu .NET Framework, należy sprawdzić, czy wersji docelowej *lub* zainstalowana nowsza wersja nie, czy jest zainstalowana wersja programu docelowego. Innymi słowy, należy ocenić, czy klucz wersji, możesz pobrać z rejestru jest większa niż lub równa klucz wersji wersji docelowej *nie* Określa, czy jest równe klucz wersji wersji docelowej.

- [Wykryj](#detecting-the-language-packs) Określa, czy pakiety językowe są już zainstalowane na komputerze użytkownika.

- Jeśli chcesz kontrolować wdrożenia dyskretnie uruchamianie i śledzić proces instalacji platformy .NET Framework (zobacz [porady: uzyskiwanie postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)).

- Jeśli wdrażasz Instalatora w trybie offline, [łańcucha oddzielnie pakiety językowe](#chain_langpack).

- Dostosowywanie wdrożenia przy użyciu [opcje wiersza polecenia](#command-line-options). Na przykład, jeśli jest łańcucha Instalator sieci web .NET Framework, ale chcesz przesłonić domyślny pakiet językowy, użyj `/LCID` opcji, zgodnie z opisem w poprzedniej sekcji.

- [Rozwiązywanie problemów z](#troubleshooting).

<a name="detect_net"></a>
### <a name="detecting-the-net-framework"></a>Wykrywanie programu .NET Framework
 Instalator .NET Framework zapisuje klucze rejestru, po pomyślnej instalacji. Można sprawdzić, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszy jest zainstalowany sprawdzając `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` folderu w rejestrze dla `DWORD` wartość o nazwie `Release`. (Należy pamiętać, że "NET Framework instalacji" nie rozpoczyna się kropką). Obecności klucza oznacza to, że [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszy został zainstalowany na tym komputerze. Wartość `Release` wskazuje, która wersja architektury .NET Framework jest zainstalowana.

> [!IMPORTANT]
> Należy sprawdzić, czy wartość **większa niż lub równa** wartość słowa kluczowego wersji podczas próby wykryć, czy występuje określonej wersji.

|Wersja|Wartość DWORD dotycząca wersji|
|-------------|--------------------------------|
|.NET framework w systemie Windows 10 spadek twórców Update 4.7.1|461308|
|.NET framework 4.7.1 zainstalowane we wszystkich wersjach systemu operacyjnego innego niż Windows 10 spadek twórców aktualizacji|461310|
|4.7 framework .NET zainstalowany w systemie Windows 10 twórców Update|460798|
|4.7 framework .NET zainstalowany we wszystkich wersjach systemu operacyjnego innego niż system Windows 10 twórców aktualizacji|460805|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] zainstalowane w systemie Windows 10 Anniversary Edition|394802|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] zainstalowane we wszystkich wersjach systemu operacyjnego innego niż system Windows 10 Anniversary Edition|394806|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] zainstalowane w systemie Windows 10 listopada Update|394254|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] zainstalowane we wszystkich wersjach systemu operacyjnego innego niż system Windows 10 listopada aktualizacji|394271|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] zainstalowane w systemie Windows 10|393295|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] zainstalowane we wszystkich wersjach systemu operacyjnego innego niż Windows 10|393297|
|.NET Framework 4.5.2|379893|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] zainstalowane z [!INCLUDE[win81](../../../includes/win81-md.md)] lub Windows Server 2012 R2|378675|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] zainstalowana na [!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7|378758|
|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|378389|

### <a name="detecting-the-language-packs"></a>Wykrywanie pakietów językowych
 Można sprawdzić, czy określony pakiet jest zainstalowana, sprawdzając HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* folderu w rejestrze wartość DWORD o nazwie `Release`. (Należy pamiętać, że "NET Framework instalacji" nie rozpoczyna się kropką). *Identyfikator LCID* Określa identyfikator ustawień regionalnych; zobacz [obsługiwanych języków](#supported-languages) Aby uzyskać listę.

 Na przykład wykryć czy pełnej japoński pakiet językowy (LCID = 1041) jest zainstalowany, sprawdź, czy następujące wartości rejestru:

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041
Name: Release
Type: DWORD
```

 Aby określić, czy wersji ostatecznej programu pakiet językowy jest zainstalowany dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 lub 4.7.1, sprawdź wartość wydania klucza opisane w poprzedniej sekcji, wartość DWORD [wykrywanie programu .NET Framework](#detect_net).

<a name="chain_langpack"></a> 
### <a name="chaining-the-language-packs-to-your-app-setup"></a>Tworzenie łańcuchów język pakietów do ustawień aplikacji
 .NET Framework zawiera zestaw języka autonomiczny pakiet plików wykonywalnych, zawierające zlokalizowanych zasobów dla określonej kultury. Pakiety językowe są dostępne z Microsoft Download Center:

- [.NET framework 4.7.1 pakietów językowych](http://go.microsoft.com/fwlink/p/?LinkId=852090)

- [Pakiety językowe programu .NET framework 4.7](http://go.microsoft.com/fwlink/p/?LinkId=825306)

- [.NET framework 4.6.2 pakietów językowych](http://go.microsoft.com/fwlink/p/?LinkId=780604)

- [.NET framework 4.6.1 pakietów językowych](http://go.microsoft.com/fwlink/p/?LinkId=671747)

- [Pakiety językowe programu .NET framework 4.6](http://go.microsoft.com/fwlink/p/?LinkId=528314)

- [Pakiety językowe .NET framework 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397701)

- [Pakiety językowe .NET framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=322101)

- [Pakiety językowe programu .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Pakiety językowe nie mogą zawierać składników .NET Framework, które są wymagane do uruchomienia aplikacji; .NET Framework należy zainstalować za pomocą sieci web lub Instalatora w trybie offline, przed zainstalowaniem pakietu językowego.

 Począwszy od [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], nazwy pakietu formę npr <`version`>-KB <`number`>-x86-x64 - AllOS - <`culture`> .exe, gdzie `version` jest numer wersji programu .NET Framework, `number` jest Numer artykułu bazy wiedzy Microsoft Knowledge Base, i `culture` Określa [kraj/region](#supported-languages). Na przykład z jednego z tych pakietów `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Nazwy pakietu są wymienione w [pakiety redystrybucyjne](#redistributable-packages) wcześniej w tym artykule.

 Aby zainstalować pakiet językowy przy użyciu Instalatora w trybie offline środowiska .NET Framework, tworzenia łańcucha go do Instalatora aplikacji. Na przykład, aby wdrożyć [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] Instalatora w trybie offline z pakiet języka japońskiego, użyj następującego polecenia:

```
NDP451-KB2858728-x86-x64-AllOS-JPN.exe/q /norestart /ChainingPackage <ProductName>
```

 Nie masz do łańcucha pakietów językowych, jeśli używasz Instalator sieci web; Instalator zainstaluje pakiet językowy odpowiadający ustawienie MUI użytkownika. Jeśli chcesz zainstalować w innym języku, możesz użyć `/LCID` opcję, aby określić pakiet językowy.

 Aby uzyskać pełną listę opcji wiersza polecenia, zobacz [opcje wiersza polecenia](#command-line-options) sekcji.

### <a name="troubleshooting"></a>Rozwiązywanie problemów

#### <a name="return-codes"></a>Kody powrotne
 W poniższej tabeli wymieniono najczęstsze kody powrotne pakiet redystrybucyjny Instalatora .NET Framework. Kody powrotne są takie same dla wszystkich wersji instalatora. Łącza do szczegółowych informacji zobacz następną sekcję.

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

- [Kody błędów Background Intelligent Transfer Service (BITS)](http://go.microsoft.com/fwlink/?LinkId=180946)

- [Kody błędów moniker adresu URL](http://go.microsoft.com/fwlink/?LinkId=180947)

- [Kody błędów WinHttp](http://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Inne kody błędów
 Zobacz następującą zawartość:

- [Kody błędów Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=180949)

- [Kody wyników programu Windows Update Agent](http://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Odinstalowywanie programu .NET Framework
 Począwszy od [!INCLUDE[win8](../../../includes/win8-md.md)], można odinstalować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub jeden z jego punktu zwalnia przy użyciu **funkcje systemu Windows i wyłącza** w Panelu sterowania. W starszych wersjach systemu Windows, można odinstalować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub jeden z jego punktu zwalnia przy użyciu **Dodaj lub usuń programy** w Panelu sterowania.

> [!IMPORTANT]
> Dla systemów Windows 7 i starszych systemach operacyjnych, odinstalowywanie [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 lub 4.7.1 nie przywrócić [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] plików i odinstalowywania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie przywrócić [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] plików. Jeśli chcesz powrócić do starszej wersji, należy ponownie zainstalować go i wszelkie aktualizacje.

## <a name="appendix"></a>Dodatek

### <a name="command-line-options"></a>Opcje wiersza polecenia
 W poniższej tabeli wymieniono opcje, które można uwzględnić podczas tworzenia łańcucha [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pakiet redystrybucyjny Instalatora aplikacji.

|Opcja|Opis|
|------------|-----------------|
|**/CEIPConsent**|Zastępuje domyślne zachowanie i wysyła anonimowych informacji zwrotnych do firmy Microsoft, aby poprawić przyszłego wdrożenia środowiska. Tej opcji można używać tylko wtedy, gdy Instalator wyświetla monit o zgodę, a użytkownik przyznaje uprawnienia do wysyłania anonimowych informacji zwrotnych do firmy Microsoft.|
|**/chainingpackage** `packageName`|Określa nazwę pliku wykonywalnego, który wykonuje łańcucha. Te informacje są wysyłane do firmy Microsoft jako napotyka anonimowych informacji zwrotnych, aby pomóc w udoskonalaniu przyszłego wdrożenia.<br /><br /> Jeśli nazwa pakietu zawiera spacje, użyj podwójnych cudzysłowów prostych jako ograniczników; na przykład: **/chainingpackage "Lucerny publikowania"**. Na przykład pakiet CBC zobacz [uzyskiwanie informacji o postępie z pakietu instalacyjnego](http://go.microsoft.com/fwlink/?LinkId=181926) w bibliotece MSDN.|
|**/LCID**  `LCID`<br /><br /> gdzie `LCID` Określa identyfikator ustawień regionalnych (zobacz [obsługiwanych języków](#supported-languages))|Instaluje pakiet językowy określony przez `LCID` i wymusza wyświetlanych interfejsu użytkownika do pokazania w tym języku, chyba że ustawiono tryb cichy.<br /><br /> Instalatora sieci web ta opcja łańcucha — instaluje pakiet językowy z sieci web. **Uwaga:** Użyj tej opcji tylko przy użyciu Instalatora sieci web.|
|**/ log** `file`&#124; `folder`|Określa lokalizację pliku dziennika. Wartość domyślna to folder tymczasowy dla procesu, a domyślna nazwa pliku opiera się na pakiet. Jeśli rozszerzenie pliku jest txt, jest tworzony dziennik tekstowy. Jeśli określisz inne rozszerzenie lub bez rozszerzenia, tworzony jest dziennik HTML.|
|**/msioptions**|Określa opcje do przekazania do elementów .msi i .msp. na przykład: `/msioptions "PROPERTY1='Value'"`.|
|**/norestart**|Program instalacyjny uniemożliwia automatyczne ponowne uruchomienie. Jeśli używasz tej opcji, CBC aplikacja ma kod powrotny przechwytywania i ponowny rozruch (zobacz [uzyskiwanie informacji o postępie z pakietu instalacyjnego](http://go.microsoft.com/fwlink/?LinkId=179606) w bibliotece MSDN).|
|**/ passive**|Zestawy w trybie pasywnym. Wyświetla pasek postępu, aby wskazać, że instalacja jest w toku, lecz nie wyświetla żadnych monitów ani komunikaty o błędach dla użytkownika. W tym trybie, gdy łańcuchowej przez program instalacyjny CBC pakietu musi obsługiwać [kody powrotne](#return-codes).|
|**/pipe**|Tworzy kanał komunikacji, aby włączyć CBC pakiet do pobrania w toku.|
|**/promptrestart**|Tylko tryb pasywny, jeśli Instalator wymaga ponownego uruchomienia, użytkownik jest monitowany. Ta opcja wymaga interakcji użytkownika, jeśli wymagane jest ponowne uruchomienie komputera.|
|**/q**|Ustawia tryb cichy.|
|**/ Repair**|Wyzwala funkcji naprawy.|
|**/serialdownload**|Wymusza instalacji nastąpić dopiero po pobraniu pakietu.|
|**/showfinalerror**|Zestawy w trybie pasywnym. Przedstawia błędy tylko wtedy, gdy instalacja się nie powiedzie. Ta opcja wymaga interakcji użytkownika, jeśli instalacja się nie powiedzie.|
|**/showrmui**|Używany tylko z **/passive** opcji. Wyświetla okno komunikatu, które monituje użytkowników o konieczności zamykania aplikacji .NET Framework, które są aktualnie uruchomione. To okno komunikatu działa tak samo w trybie biernym i -pasywny.|
|**/uninstall**|Odinstalowuje pakiet redystrybucyjny programu .NET Framework.|

### <a name="supported-languages"></a>Obsługiwane języki
Poniższa tabela zawiera listę pakietów językowych .NET Framework, które są dostępne dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i zwalnia jego punktu.

|LCID|Język — kraj/region|Kultury|
|----------|--------------------------------|-------------|
|1025|Arabski - Arabia Saudyjska|ar|
|1028|Chiński tradycyjny|zh-Hant|
|1029|czeski|CS|
|1030|duński|da|
|1031|Niemiecki — Niemcy|Niemcy|
|1032|grecki|el|
|1035|fiński|fi|
|1036|Francuski — Francja|FR|
|1037|Hebrajski|ADAM|
|1038|węgierski|hu|
|1040|Włoski — Włochy|it|
|1041|japoński|ja|
|1042|koreański|ko|
|1043|Holenderski — Holandia|nl|
|1044|Norwegian (Bokmål)|Brak|
|1045|polski|pl|
|1046|Portugalski — Brazylia|pt-BR|
|1049|Rosyjski|ru|
|1053|szwedzki|sv|
|1055|turecki|TR|
|2052|Chiński uproszczony|zh-Hans|
|2070|Portugalski — Portugalia|pt-PT|
|3082|Hiszpański (Hiszpania) (sortowanie nowoczesne)|ES|

## <a name="see-also"></a>Zobacz także
 [Przewodnik wdrażania dla administratorów](../../../docs/framework/deployment/guide-for-administrators.md)  
 [Wymagania systemowe](../../../docs/framework/get-started/system-requirements.md)  
 [Zainstaluj program .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md)  
 [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
 [Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)  
 [Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
