---
title: Usuwanie środowiska uruchomieniowego .NET Core i zestawu SDK
description: W tym artykule opisano sposób ustalania, które wersje środowiska uruchomieniowego i zestawu SDK platformy .NET Core są obecnie zainstalowane, a następnie sposobu ich usuwania w systemach Windows, Mac i Linux.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 6d1012b8ddc5fd4a5ee8227902886727dbb10739
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970296"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Jak usunąć środowisko uruchomieniowe programu .NET Core i zestaw SDK

Wraz z upływem czasu podczas instalowania zaktualizowanych wersji środowiska uruchomieniowego .NET Core i zestawu SDK można usunąć nieaktualne wersje programu .NET Core z komputera. Usunięcie starszych wersji środowiska uruchomieniowego może zmienić środowisko uruchomieniowe wybrane do uruchamiania aplikacji platformy udostępnionej, zgodnie z opisem w artykule na temat [wyboru wersji platformy .NET Core](selection.md).

## <a name="should-i-remove-a-version"></a>Czy należy usunąć wersję?

Zachowania [wyboru wersji .NET Core](selection.md) i zgodność środowiska uruchomieniowego programu .NET Core między aktualizacjami umożliwiają bezpieczne usuwanie poprzednich wersji. Aktualizacje środowiska uruchomieniowego programu .NET Core są zgodne z wersją główną "Band", taką jak 1. x i 2. x. Ponadto nowsze wersje zestaw .NET Core SDK zwykle utrzymują możliwość tworzenia aplikacji przeznaczonych dla wcześniejszych wersji środowiska uruchomieniowego w sposób zgodny.

Ogólnie rzecz biorąc potrzebny jest tylko najnowszy zestaw SDK i Najnowsza wersja poprawki środowiska uruchomieniowego, które są wymagane dla danej aplikacji. Wystąpienia, w których zachowano starsze wersje zestawu SDK lub środowiska uruchomieniowego, obejmują obsługę aplikacji opartych na **programie Project. JSON**. Jeśli aplikacja nie ma określonych powodów dla wcześniejszych zestawów SDK lub środowisk uruchomieniowych, możesz bezpiecznie usunąć starsze wersje.

## <a name="determine-what-is-installed"></a>Określ, co jest zainstalowane

Począwszy od platformy .NET Core 2,1, interfejs wiersza polecenia platformy .NET zawiera opcje, których można użyć do wyświetlenia listy wersji zestawu SDK i środowiska uruchomieniowego, które są zainstalowane na komputerze.  Użyj [`dotnet --list-sdks`](../tools/dotnet.md#options) , aby wyświetlić listę zestawów SDK zainstalowanych na komputerze. Użyj [`dotnet --list-runtimes`](../tools/dotnet.md#options) , aby wyświetlić listę środowisk uruchomieniowych zainstalowanych na maszynie. Poniższy tekst przedstawia typowe dane wyjściowe dla systemu Windows, macOS lub Linux:

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

Począwszy od platformy .NET Core 2,1, nie ma potrzeby odinstalowywania zestaw .NET Core SDK podczas uaktualniania go przy użyciu Menedżera pakietów. Menedżer `update` pakietów lub `refresh` polecenia automatycznie usuwają starszą wersję po pomyślnej instalacji nowszej wersji.

Jeśli zainstalowano program .NET Core przy użyciu Menedżera pakietów, należy użyć tego samego Menedżera pakietów do odinstalowania zestawu .NET SDK lub środowiska uruchomieniowego. Instalacje .NET Core obsługują najpopularniejszych menedżerów pakietów. Zapoznaj się z dokumentacją Menedżera pakietów dystrybucji, aby uzyskać dokładną składnię w Twoim środowisku:

- [apt-get (8)](https://linux.die.net/man/8/apt-get) jest używany przez systemy oparte na Debian, w tym Ubuntu.
- [yum (8)](https://linux.die.net/man/8/yum) jest używany na Fedora, CentOS i Oracle Linux.
- [użyciu narzędzia zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używany w systemach OPENSUSE i SUSE Linux Enterprise System (SLES).
- [DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) jest używany w Fedora.

Niemal we wszystkich przypadkach polecenie usunięcia pakietu ma `remove`wartość.

Nazwa pakietu zestaw .NET Core SDK instalacji dla większości menedżerów pakietów ma `dotnet-sdk`numer wersji. Począwszy od wersji 2.1.300 zestaw .NET Core SDK i wersji `2.1` środowiska uruchomieniowego, wymagane są tylko główne i pomocnicze numery wersji: na przykład zestaw .NET Core SDK wersja 2.1.300 może być przywoływana jako pakiet. `dotnet-sdk-2.1` Wcześniejsze wersje wymagają, aby cały ciąg wersji był wymagany, `dotnet-sdk-2.1.200` na przykład w przypadku wersji 2.1.200 zestaw .NET Core SDK.

W przypadku maszyn, na których zainstalowano tylko środowisko uruchomieniowe, a nie zestawu SDK `dotnet-runtime-<version>` , nazwa pakietu jest dla środowiska uruchomieniowego .NET Core oraz `aspnetcore-runtime-<version>` dla całego stosu środowiska uruchomieniowego.

Instalacje .NET Core przed 2,0 nie odinstalowały aplikacji hosta podczas odinstalowywania zestawu SDK przy użyciu Menedżera pakietów. Za `apt-get`pomocą polecenia jest:

```bash
apt-get remove dotnet-host
```

Należy zauważyć, że nie ma żadnej wersji `dotnet-host`dołączonej do programu.

Jeśli zainstalowano program przy użyciu plik tar, należy usunąć platformę .NET Core przy użyciu metody ręcznej.

Zestawy SDK i środowiska uruchomieniowe należy usunąć oddzielnie, usuwając katalog zawierający tę wersję. Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych `dotnet --list-sdks` wyjściowych `dotnet --list-runtimes` polecenia i, jak pokazano w wcześniejszej tabeli.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Na komputerach Mac należy osobno usunąć zestawy SDK i środowiska uruchomieniowe, usuwając katalog zawierający tę wersję. Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych `dotnet --list-sdks` wyjściowych `dotnet --list-runtimes` polecenia i, jak pokazano w wcześniejszej tabeli.

---
