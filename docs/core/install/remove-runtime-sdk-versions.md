---
title: Usuwanie środowiska uruchomieniowego .NET Core i zestawu SDK
description: W tym artykule opisano sposób ustalania, które wersje środowiska uruchomieniowego i zestawu SDK platformy .NET Core są obecnie zainstalowane, a następnie sposobu ich usuwania w systemach Windows, Mac i Linux.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: f1482c243ba22fa81c69ede847a0f6b36a9cb83c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595784"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Jak usunąć środowisko uruchomieniowe programu .NET Core i zestaw SDK

Wraz z upływem czasu podczas instalowania zaktualizowanych wersji środowiska uruchomieniowego .NET Core i zestawu SDK można usunąć nieaktualne wersje programu .NET Core z komputera. Usunięcie starszych wersji środowiska uruchomieniowego może zmienić środowisko uruchomieniowe wybrane do uruchamiania aplikacji platformy udostępnionej, zgodnie z opisem w artykule na temat [wyboru wersji platformy .NET Core](../versions/selection.md).

## <a name="should-i-remove-a-version"></a>Czy należy usunąć wersję?

Zachowania [wyboru wersji .NET Core](../versions/selection.md) i zgodność środowiska uruchomieniowego programu .NET Core między aktualizacjami umożliwiają bezpieczne usuwanie poprzednich wersji. Aktualizacje środowiska uruchomieniowego programu .NET Core są zgodne z wersją główną "Band", taką jak 1. x i 2. x. Ponadto nowsze wersje zestaw .NET Core SDK zwykle utrzymują możliwość tworzenia aplikacji przeznaczonych dla wcześniejszych wersji środowiska uruchomieniowego w sposób zgodny.

Ogólnie rzecz biorąc potrzebny jest tylko najnowszy zestaw SDK i Najnowsza wersja poprawki środowiska uruchomieniowego, które są wymagane dla danej aplikacji. Wystąpienia, w których warto zachować starsze wersje zestawu SDK lub środowiska uruchomieniowego, obejmują obsługę aplikacji opartych na *programie Project. JSON*. Jeśli aplikacja nie ma określonych powodów dla wcześniejszych zestawów SDK lub środowisk uruchomieniowych, możesz bezpiecznie usunąć starsze wersje.

## <a name="determine-what-is-installed"></a>Określ, co jest zainstalowane

Począwszy od platformy .NET Core 2,1, interfejs wiersza polecenia platformy .NET zawiera opcje, których można użyć do wyświetlenia listy wersji zestawu SDK i środowiska uruchomieniowego, które są zainstalowane na komputerze.  Użyj [`dotnet --list-sdks`](../tools/dotnet.md#options) , aby wyświetlić listę zestawów SDK zainstalowanych na komputerze. Użyj [`dotnet --list-runtimes`](../tools/dotnet.md#options) , aby wyświetlić listę środowisk uruchomieniowych zainstalowanych na maszynie. Aby uzyskać więcej informacji, zobacz [Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md).

## <a name="uninstall-net-core"></a>Odinstalowywanie programu .NET Core

::: zone pivot="os-windows"

.NET Core korzysta z okna dialogowego **funkcje & aplikacje** systemu Windows, aby usunąć wersje środowiska uruchomieniowego i zestawu SDK platformy .NET Core. Na poniższej ilustracji przedstawiono okno dialogowe **aplikacje & funkcje** . Możesz wyszukać **podstawowy zestaw SDK** , aby przefiltrować i pokazać zainstalowane wersje platformy .NET Core.

![Dodawanie/usuwanie programów w celu usunięcia programu .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Wybierz wszystkie wersje, które chcesz usunąć z komputera, a następnie kliknij przycisk **Odinstaluj**.

::: zone-end

::: zone pivot="os-linux"

Istnieje więcej opcji odinstalowywania platformy .NET Core (zestawu SDK lub środowiska uruchomieniowego) w systemie Linux. Najlepszym sposobem odinstalowania programu .NET Core jest dublowanie akcji użytej do zainstalowania programu .NET Core. Informacje te zależą od wybranej dystrybucji i metody instalacji.

> [!IMPORTANT]
> Aby uzyskać informacje na temat instalowania i odinstalowywania programu .NET Core, należy zapoznać się z [przewodnikiem](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) w witrynie red Hat wprowadzenie.

Począwszy od platformy .NET Core 2,1, nie ma potrzeby odinstalowywania zestaw .NET Core SDK podczas uaktualniania go przy użyciu Menedżera pakietów. Menedżer `update` pakietów lub `refresh` polecenia automatycznie usuwają starszą wersję po pomyślnej instalacji nowszej wersji.

Jeśli zainstalowano program .NET Core przy użyciu Menedżera pakietów, należy użyć tego samego Menedżera pakietów do odinstalowania zestawu .NET SDK lub środowiska uruchomieniowego. Instalacje .NET Core obsługują najpopularniejszych menedżerów pakietów. Zapoznaj się z dokumentacją Menedżera pakietów dystrybucji, aby uzyskać dokładną składnię w Twoim środowisku:

- [apt-get (8)](https://linux.die.net/man/8/apt-get) jest używany przez systemy oparte na Debian, w tym Ubuntu.
- [yum (8)](https://linux.die.net/man/8/yum) jest używany na Fedora, CentOS i Oracle Linux.
- [użyciu narzędzia zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używany w systemach OPENSUSE i SUSE Linux Enterprise System (SLES).
- [DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) jest używany w Fedora.

Niemal we wszystkich przypadkach polecenie usunięcia pakietu ma `remove`wartość.

Nazwa pakietu zestaw .NET Core SDK instalacji dla większości menedżerów pakietów ma `dotnet-sdk`numer wersji. Począwszy od wersji 2.1.300 zestaw .NET Core SDK i wersji `2.1` środowiska uruchomieniowego, wymagane są tylko główne i pomocnicze numery wersji: na przykład zestaw .NET Core SDK wersja 2.1.300 może być przywoływana jako pakiet. `dotnet-sdk-2.1` Wcześniejsze wersje wymagają, aby cały ciąg wersji był wymagany, `dotnet-sdk-2.1.200` na przykład w przypadku wersji 2.1.200 zestaw .NET Core SDK.

W przypadku maszyn, na których zainstalowano tylko środowisko uruchomieniowe, a nie zestawu SDK `dotnet-runtime-<version>` , nazwa pakietu jest dla środowiska uruchomieniowego .NET Core oraz `aspnetcore-runtime-<version>` dla całego stosu środowiska uruchomieniowego.

Instalacje .NET Core starsze niż 2,0 nie odinstalowały aplikacji hosta podczas odinstalowywania zestawu SDK przy użyciu Menedżera pakietów. Za `apt-get`pomocą polecenia jest:

```bash
apt-get remove dotnet-host
```

Zwróć uwagę, że nie ma żadnej wersji `dotnet-host`dołączonej do programu.

Jeśli zainstalowano program przy użyciu plik tar, należy usunąć platformę .NET Core przy użyciu metody ręcznej.

W systemie Linux należy osobno usunąć zestawy SDK i środowiska uruchomieniowe, usuwając katalogi z wersjami. Usunięcie ich spowoduje usunięcie zestawu SDK i środowiska uruchomieniowego z dysku. Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych `dotnet --list-sdks` wyjściowych `dotnet --list-runtimes` polecenia i, jak pokazano w wcześniejszej tabeli.

::: zone-end

::: zone pivot="os-macos"

Na komputerach Mac należy osobno usunąć zestawy SDK i środowiska uruchomieniowe, usuwając katalogi z wersjami. Usunięcie ich spowoduje usunięcie zestawu SDK i środowiska uruchomieniowego z dysku. Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych `dotnet --list-sdks` wyjściowych `dotnet --list-runtimes` polecenia i, jak pokazano w wcześniejszej tabeli.

::: zone-end

## <a name="net-core-uninstall-tool"></a>Narzędzie do dezinstalacji platformy .NET Core

[Narzędzie do dezinstalacji programu .NET Core](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) umożliwia usuwanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core z systemu. Dostępna jest kolekcja opcji, aby określić, które wersje mają być odinstalowane.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>Zależność programu Visual Studio od wersji zestaw .NET Core SDK

Przed dodaniem programu Visual Studio 2019 w wersji 16,3, instalatorzy programu Visual Studio o nazwie autonomiczne zestaw .NET Core SDK Instalatora. W związku z tym wersje zestawu SDK pojawiają się w oknie dialogowym aplikacje systemu Windows **& funkcje** . Usunięcie zestawów SDK platformy .NET Core zainstalowanych przez program Visual Studio za pomocą autonomicznego Instalatora może spowodować przerwanie programu Visual Studio. Jeśli program Visual Studio ma problemy po odinstalowaniu zestawów SDK, należy uruchomić polecenie Repair dla tej konkretnej wersji programu Visual Studio. W poniższej tabeli przedstawiono niektóre zależności programu Visual Studio na zestaw .NET Core SDK wersje:

| Wersja programu Visual Studio           | Wersja zestaw .NET Core SDK          |
|---------------------------------|--------------------------------|
|  Program Visual Studio 2019 w wersji 16.2  | Zestaw .NET Core SDK 2.2.4 XX, 2.1.8 XX |
| Visual Studio 2019 w wersji 16.1 | Zestaw .NET Core SDK 2.2.3 XX, 2.1.7 XX |
| Visual Studio 2019 w wersji 16,0 | Zestaw .NET Core SDK 2.2.2 XX, 2.1.6 XX |
| Visual Studio 2017 w wersji 15,9 | Zestaw .NET Core SDK 2.2.1 XX, 2.1.5 XX |
| Visual Studio 2017 w wersji 15,8 | Zestaw .NET Core SDK 2.1.4 XX          |

Począwszy od programu Visual Studio 2019 w wersji 16,3, program Visual Studio jest odpowiedzialny za własną kopię zestaw .NET Core SDK. Z tego powodu te wersje zestawu SDK nie są już widoczne w oknie dialogowym **aplikacje & funkcje** .

## <a name="remove-the-nuget-fallback-folder"></a>Usuń folder rezerwowy NuGet

Przed zestawem SDK platformy .NET Core 3,0, Instalatory zestaw .NET Core SDK używały folderu o nazwie *NuGetFallbackFolder* do przechowywania pamięci podręcznej pakietów NuGet. Ta pamięć podręczna została użyta podczas `dotnet restore` operacji `dotnet build /t:Restore`takich jak lub. *NuGetFallbackFolder* znajduje się w *katalogu C:\Program Files\dotnet\sdk* w systemie Windows i na */usr/local/share/dotnet/SDK* na macOS.

Możesz chcieć usunąć ten folder, jeśli:

- Program jest opracowywany tylko przy użyciu zestawu .NET Core 3,0 SDK lub jego nowszych wersji.
- Opracowujesz przy użyciu wersji zestaw .NET Core SDK wcześniejszej niż 3,0, ale możesz korzystać z trybu online.

Jeśli chcesz usunąć folder rezerwowy NuGet, możesz go usunąć, ale musisz mieć uprawnienia administratora.

Nie zaleca się usuwania folderu *dotnet* . Spowoduje to usunięcie wszystkich wcześniej zainstalowanych narzędzi globalnych. Ponadto w systemie Windows:

- Spowoduje to przerwanie programu Visual Studio 2019 w wersji 16,3 i nowszych. Aby odzyskać, możesz wykonać **naprawę** .
- Jeśli w oknie dialogowym **aplikacje & funkcji** znajdują się wpisy zestaw .NET Core SDK, zostaną one oddzielone.
