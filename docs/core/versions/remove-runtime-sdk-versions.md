---
title: Usuwanie środowiska uruchomieniowego .NET Core i zestawu SDK
description: W tym artykule opisano sposób ustalania, które wersje środowiska uruchomieniowego i zestawu SDK platformy .NET Core są obecnie zainstalowane, a następnie sposobu ich usuwania w systemach Windows, Mac i Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: seodec18,updateeachrelease
ms.openlocfilehash: 8c235a4b38e991b6ba2c9d2489151995f3031a27
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342928"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Jak usunąć środowisko uruchomieniowe programu .NET Core i zestaw SDK

Wraz z upływem czasu podczas instalowania zaktualizowanych wersji środowiska uruchomieniowego .NET Core i zestawu SDK można usunąć nieaktualne wersje programu .NET Core z komputera. Usunięcie starszych wersji środowiska uruchomieniowego może zmienić środowisko uruchomieniowe wybrane do uruchamiania aplikacji platformy udostępnionej, zgodnie z opisem w artykule na temat [wyboru wersji platformy .NET Core](selection.md).

## <a name="should-i-remove-a-version"></a>Czy należy usunąć wersję?

Zachowania [wyboru wersji .NET Core](selection.md) i zgodność środowiska uruchomieniowego programu .NET Core między aktualizacjami umożliwiają bezpieczne usuwanie poprzednich wersji. Aktualizacje środowiska uruchomieniowego programu .NET Core są zgodne z wersją główną "Band", taką jak 1. x i 2. x. Ponadto nowsze wersje zestaw .NET Core SDK zwykle utrzymują możliwość tworzenia aplikacji przeznaczonych dla wcześniejszych wersji środowiska uruchomieniowego w sposób zgodny.

Ogólnie rzecz biorąc potrzebny jest tylko najnowszy zestaw SDK i Najnowsza wersja poprawki środowiska uruchomieniowego, które są wymagane dla danej aplikacji. Wystąpienia, w których są zachowywane starsze wersje zestawu SDK lub środowiska uruchomieniowego, obejmują obsługę aplikacji opartych na **programie Project. JSON**. Jeśli aplikacja nie ma określonych powodów dla wcześniejszych zestawów SDK lub środowisk uruchomieniowych, możesz bezpiecznie usunąć starsze wersje.

## <a name="determine-what-is-installed"></a>Określ, co jest zainstalowane

Począwszy od platformy .NET Core 2,1, interfejs wiersza polecenia platformy .NET zawiera opcje, których można użyć do wyświetlenia listy wersji zestawu SDK i środowiska uruchomieniowego, które są zainstalowane na komputerze.  Użyj [`dotnet --list-sdks`](../tools/dotnet.md#options) , aby wyświetlić listę zestawów SDK zainstalowanych na maszynie. Użyj [`dotnet --list-runtimes`](../tools/dotnet.md#options) , aby wyświetlić listę środowisk uruchomieniowych zainstalowanych na maszynie. Poniższy tekst przedstawia typowe dane wyjściowe dla systemu Windows, macOS lub Linux:

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

```console
C:\> dotnet --list-sdks
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]

C:\> dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macostabmacos"></a>[macOS](#tab/macos)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstalling-net-core"></a>Odinstalowywanie programu .NET Core

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

.NET Core używa okna dialogowego **Dodawanie/usuwanie programów** systemu Windows do usuwania wersji środowiska uruchomieniowego i zestawu SDK platformy .NET Core. Na poniższej ilustracji przedstawiono okno dialogowe **Dodawanie/usuwanie programów** z kilkoma wersjami środowiska uruchomieniowego .NET i ZAINSTALOWANYm zestawem SDK.

![Dodawanie/usuwanie programów w celu usunięcia programu .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Wybierz wszystkie wersje, które chcesz usunąć z komputera, a następnie kliknij przycisk **Odinstaluj**.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Istnieje więcej opcji odinstalowywania platformy .NET Core (zestawu SDK lub środowiska uruchomieniowego) w systemie Linux. Najlepszym sposobem odinstalowania programu .NET Core jest dublowanie akcji użytej do zainstalowania programu .NET Core. Informacje te zależą od wybranej dystrybucji i metody instalacji.

> [!IMPORTANT]
> Aby uzyskać informacje na temat instalowania i odinstalowywania programu .NET Core, należy zapoznać się z [przewodnikiem](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) w witrynie red Hat wprowadzenie.

Począwszy od platformy .NET Core 2,1, nie ma potrzeby odinstalowywania zestaw .NET Core SDK podczas uaktualniania go przy użyciu Menedżera pakietów. Polecenie `update` lub `refresh` Menedżera pakietów automatycznie usunie starszą wersję po pomyślnej instalacji nowszej wersji.

Jeśli zainstalowano program .NET Core przy użyciu Menedżera pakietów, należy użyć tego samego Menedżera pakietów do odinstalowania zestawu .NET SDK lub środowiska uruchomieniowego. Instalacje .NET Core obsługują najpopularniejszych menedżerów pakietów. Zapoznaj się z dokumentacją Menedżera pakietów dystrybucji, aby uzyskać dokładną składnię w Twoim środowisku:

- [apt-get (8)](https://linux.die.net/man/8/apt-get) jest używany przez systemy oparte na Debian, w tym Ubuntu.
- [yum (8)](https://linux.die.net/man/8/yum) jest używany na Fedora, CentOS i Oracle Linux.
- [użyciu narzędzia zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używany w systemach OPENSUSE i SUSE Linux Enterprise System (SLES).
- [DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) jest używany w Fedora.

Niemal we wszystkich przypadkach polecenie usunięcia pakietu jest `remove`.

Nazwa pakietu dla zestaw .NET Core SDK instalacji większości menedżerów pakietów jest `dotnet-sdk`, a po niej numer wersji. Począwszy od wersji 2.1.300 zestaw .NET Core SDK i wersji `2.1` środowiska uruchomieniowego, wymagane są tylko główne i pomocnicze numery wersji: na przykład zestaw .NET Core SDK wersja 2.1.300 może być przywoływana jako `dotnet-sdk-2.1`pakietu. Wcześniejsze wersje wymagają całego ciągu wersji: na przykład, `dotnet-sdk-2.1.200` być wymagana dla wersji 2.1.200 zestaw .NET Core SDK.

W przypadku maszyn, na których zainstalowano tylko środowisko uruchomieniowe, a nie zestawu SDK, nazwa pakietu jest `dotnet-runtime-<version>` dla środowiska uruchomieniowego .NET Core i `aspnetcore-runtime-<version>` dla całego stosu środowiska uruchomieniowego.

Instalacje .NET Core starsze niż 2,0 nie odinstalowały aplikacji hosta podczas odinstalowywania zestawu SDK przy użyciu Menedżera pakietów. Przy użyciu `apt-get`polecenie to:

```bash
apt-get remove dotnet-host
```

Należy zauważyć, że nie ma wersji dołączonej do `dotnet-host`.

Jeśli zainstalowano program przy użyciu plik tar, należy usunąć platformę .NET Core przy użyciu metody ręcznej.

Zestawy SDK i środowiska uruchomieniowe należy usunąć oddzielnie, usuwając katalog zawierający tę wersję. Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych polecenia `dotnet --list-sdks` i `dotnet --list-runtimes`, jak pokazano w wcześniejszej tabeli.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Na komputerach Mac należy osobno usunąć zestawy SDK i środowiska uruchomieniowe, usuwając katalog zawierający tę wersję. Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych polecenia `dotnet --list-sdks` i `dotnet --list-runtimes`, jak pokazano w wcześniejszej tabeli.

---

## <a name="net-core-uninstall-tool"></a>Narzędzie do dezinstalacji programu .NET Core

[Narzędzie do dezinstalacji programu .NET Core](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) umożliwia usuwanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core z systemu. Dostępna jest kolekcja opcji, aby określić, które wersje mają być odinstalowane.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>Zależność programu Visual Studio od wersji zestaw .NET Core SDK

Przed dodaniem programu Visual Studio 2019 w wersji 16,3, instalatorzy programu Visual Studio o nazwie autonomiczne zestaw .NET Core SDK Instalatora. W związku z tym wersje zestawu SDK pojawiają się w oknie dialogowym **Dodaj/Usuń programy** systemu Windows. Usunięcie zestawów SDK platformy .NET Core zainstalowanych przez program Visual Studio za pomocą autonomicznego Instalatora może spowodować przerwanie programu Visual Studio. Jeśli program Visual Studio ma problemy po odinstalowaniu zestawów SDK, należy uruchomić polecenie Repair dla tej konkretnej wersji programu Visual Studio. W poniższej tabeli przedstawiono niektóre zależności programu Visual Studio na zestaw .NET Core SDK wersje:

| Wersja programu Visual Studio | Wersja zestaw .NET Core SDK |
| -- | -- |
| Visual Studio 2019 w wersji 16,2 | Zestaw .NET Core SDK 2.2.4 XX, 2.1.8 XX |
| Visual Studio 2019 w wersji 16,1 | Zestaw .NET Core SDK 2.2.3 XX, 2.1.7 XX |
| Visual Studio 2019 w wersji 16,0 | Zestaw .NET Core SDK 2.2.2 XX, 2.1.6 XX |
| Visual Studio 2017 w wersji 15,9 | Zestaw .NET Core SDK 2.2.1 XX, 2.1.5 XX |
| Visual Studio 2017 w wersji 15.8 | Zestaw .NET Core SDK 2.1.4 XX |

Począwszy od programu Visual Studio 2019 16,3, program Visual Studio jest odpowiedzialny za własną kopię zestaw .NET Core SDK. Z tego powodu nie widzisz już tych wersji zestawu SDK w oknie dialogowym **Dodaj/Usuń programy** .

## <a name="remove-the-nuget-fallback-folder"></a>Usuń folder rezerwowy NuGet

Przed zestawem SDK platformy .NET Core 3,0, instalatorzy zestaw .NET Core SDK używają *NuGetFallbackFolder* do przechowywania pamięci podręcznej pakietów NuGet. Ta pamięć podręczna została użyta podczas operacji takich jak `dotnet restore` lub `dotnet build /t:Restore`. `NuGetFallbackFolder` znajduje się w *katalogu C:\Program Files\dotnet\sdk* w systemie Windows i w */usr/local/share/dotnet/SDK* na macOS.

Możesz chcieć usunąć ten folder, jeśli:

* Program jest opracowywany tylko przy użyciu zestawu .NET Core 3,0 SDK lub jego nowszych wersji.
* Opracowujesz program przy użyciu wersji zestaw .NET Core SDK wcześniejszej niż 3,0, ale możesz pracować w trybie online, a rzeczy mogą przebiegać wolniej.

Jeśli chcesz usunąć folder rezerwowy NuGet, możesz go usunąć, ale musisz mieć uprawnienia administratora.

Nie zaleca się usuwania folderu *dotnet* . Spowoduje to usunięcie wszystkich wcześniej zainstalowanych narzędzi globalnych. Ponadto w systemie Windows:

- Spowoduje to przerwanie programu Visual Studio 2019 w wersji 16,3 i nowszych. Aby odzyskać, możesz wykonać **naprawę** .
- Jeśli w oknie dialogowym **Dodaj/Usuń programy** znajdują się zestaw .NET Core SDK wpisy, zostaną one oddzielone.
