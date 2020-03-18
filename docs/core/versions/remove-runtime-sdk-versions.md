---
title: Usuwanie czasu uruchomieniowego i sdk programu .NET Core
description: W tym artykule opisano sposób określania, które wersje środowiska uruchomieniowego i sdk .NET Core są aktualnie zainstalowane, a następnie jak je usunąć w systemach Windows, Mac i Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398840"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Jak usunąć program .NET Core Runtime i SDK

Wraz z urazem, po zainstalowaniu zaktualizowanych wersji programu .NET Core i sdk, można usunąć nieaktualne wersje programu .NET Core z komputera. Usunięcie starszych wersji programu runtime może zmienić czas wykonywania wybrany do uruchamiania udostępnionych aplikacji framework, jak wyszczególniono w artykule na [.NET Core wybór wersji](selection.md).

## <a name="should-i-remove-a-version"></a>Czy należy usunąć wersję?

Zachowania [wyboru wersji .NET Core](selection.md) i zgodność programu .NET Core w aktualizacjach umożliwiają bezpieczne usuwanie poprzednich wersji. Aktualizacje środowiska uruchomieniowego .NET Core są zgodne w ramach głównej wersji "pasma", takiej jak 1.x i 2.x. Ponadto nowsze wersje .NET Core SDK zazwyczaj zachowują możliwość tworzenia aplikacji, które są przeznaczone dla poprzednich wersji środowiska uruchomieniowego w sposób zgodny.

Ogólnie rzecz biorąc, potrzebujesz tylko najnowszego sdk i najnowszej wersji poprawki w czasie wykonywania wymaganych dla aplikacji. Wystąpienia, w których przechowywanie starszych wersji sdk lub runtime obejmują utrzymanie aplikacji opartych na **project.json.** Chyba że aplikacja ma konkretne powody wcześniejszych zestawów SDK lub kręgów, można bezpiecznie usunąć starsze wersje.

## <a name="determine-what-is-installed"></a>Określanie, co jest zainstalowane

Począwszy od .NET Core 2.1, .NET CLI ma opcje, których można użyć do wyświetlenia wersji sdk i czasu uruchomieniowego, które są zainstalowane na komputerze.  Służy [`dotnet --list-sdks`](../tools/dotnet.md#options) do wyświetlanie listy zestawów SDK zainstalowanych na komputerze. Służy [`dotnet --list-runtimes`](../tools/dotnet.md#options) do wyświetlanie listy uruchomień zainstalowanych na komputerze. Poniższy tekst przedstawia typowe dane wyjściowe dla systemów Windows, macOS lub Linux:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Uruchamiając następujące polecenie:

```dotnetcli
dotnet --list-sdks
```

Otrzymujesz dane wyjściowe podobne do następujących:

```console
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
```

I uruchamiając następujące polecenie:

```dotnetcli
dotnet --list-runtimes
```

Otrzymujesz dane wyjściowe podobne do następujących:

```console
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

# <a name="linux"></a>[Linux](#tab/linux)

Uruchamiając następujące polecenie:

```dotnetcli
dotnet --list-sdks
```

Otrzymujesz dane wyjściowe podobne do następujących:

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

I uruchamiając następujące polecenie:

```dotnetcli
dotnet --list-runtimes
```

Otrzymujesz dane wyjściowe podobne do następujących:

```console
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

# <a name="macos"></a>[Macos](#tab/macos)

Uruchamiając następujące polecenie:

```dotnetcli
dotnet --list-sdks
```

Otrzymujesz dane wyjściowe podobne do następujących:

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

I uruchamiając następujące polecenie:

```dotnetcli
dotnet --list-runtimes
```

Otrzymujesz dane wyjściowe podobne do następujących:

```console
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

## <a name="uninstall-net-core"></a>Odinstaluj program .NET Core

# <a name="windows"></a>[Windows](#tab/windows)

Program .NET Core używa okna dialogowego **Dodawanie/usuwanie programów** systemu Windows w celu usunięcia wersji środowiska uruchomieniowego i sdk programu .NET Core. Na poniższej ilustracji przedstawiono okno **dialogowe Dodawanie/usuwanie programów** z kilkoma wersjami zainstalowanego programu .NET i sdk.

![Dodawanie / usuwanie programów w celu usunięcia programu .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Wybierz dowolne wersje, które chcesz usunąć z komputera, a następnie kliknij przycisk **Odinstaluj**.

# <a name="linux"></a>[Linux](#tab/linux)

Istnieje więcej opcji odinstalowania programu .NET Core (sdk lub w czasie wykonywania) w systemie Linux. Najlepszym sposobem odinstalowania programu .NET Core jest dublowanie akcji użytej do zainstalowania programu .NET Core. Specyfika zależy od wybranej dystrybucji i metody instalacji.

> [!IMPORTANT]
> W przypadku instalacji programu Red Hat zapoznaj się z [przewodnikiem Red Hat Wprowadzenie,](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) aby uzyskać informacje na temat instalowania i odinstalowywania programu .NET Core.

Począwszy od .NET Core 2.1, nie ma potrzeby odinstalowywania zestawu SDK .NET Core podczas uaktualniania go za pomocą Menedżera pakietów. Menedżer `update` pakietów `refresh` lub polecenia automatycznie usunie starszą wersję po pomyślnej instalacji nowszej wersji.

Jeśli program .NET Core został zainstalowany przy użyciu menedżera pakietów, do odinstalowania zestawu SDK lub programu runtime jest używany przez tego samego menedżera pakietów. Instalacje .NET Core obsługują najpopularniejsze menedżery pakietów. Dokładne opis składni środowiska można znaleźć w dokumentacji menedżera pakietów dystrybucji:

- [apt-get(8)](https://linux.die.net/man/8/apt-get) jest używany przez systemy debianowe, w tym Ubuntu.
- [yum(8)](https://linux.die.net/man/8/yum) jest używany w Fedorze, CentOS i Oracle Linux.
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używany w openSUSE i SUSE Linux Enterprise System (SLES).
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) jest stosowany w Fedorze.

W prawie wszystkich przypadkach polecenie usunięcia `remove`pakietu jest .

Nazwa pakietu dla instalacji sdk .NET Core `dotnet-sdk`dla większości menedżerów pakietów to , po którym następuje numer wersji. Począwszy od wersji 2.1.300 zestawu .NET Core `2.1` SDK i wersji programu runtime, wymagane są tylko numery wersji głównych i pomocniczych: na przykład jako pakiet `dotnet-sdk-2.1`można odwoływać się do zestawu .NET Core SDK w wersji 2.1.300 . Wcześniejsze wersje wymagają całego ciągu `dotnet-sdk-2.1.200` wersji: na przykład będzie wymagane dla wersji 2.1.200 .NET Core SDK.

W przypadku komputerów, które zainstalowały tylko czas wykonywania, a `dotnet-runtime-<version>` nie zestaw SDK, `aspnetcore-runtime-<version>` nazwa pakietu jest dla programu runtime .NET Core i dla całego stosu wykonywania.

Instalacje programu .NET Core wcześniejsze niż 2.0 nie odinstalowano aplikacji hosta podczas odinstalowywania zestawu SDK przy użyciu Menedżera pakietów. Za `apt-get`pomocą polecenia jest:

```bash
apt-get remove dotnet-host
```

Należy pamiętać, że nie `dotnet-host`ma dołączonej wersji .

Jeśli zainstalowano przy użyciu tarball, należy usunąć .NET Core przy użyciu metody ręcznej.

Zestawy SDK i programy wykonywania są usuwane oddzielnie, usuwając katalog zawierający tę wersję. Na przykład, aby usunąć zestaw SDK 1.0.1 i czas wykonywania, należy użyć następujących poleceń bash:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

Katalogi nadrzędne dla sdk i czasu wykonywania są `dotnet --list-sdks` `dotnet --list-runtimes` wyświetlane w danych wyjściowych z i polecenia, jak pokazano we wcześniejszej tabeli.

# <a name="macos"></a>[Macos](#tab/macos)

Na komputerze Mac należy usunąć zestawy SDK i programy wykonywania oddzielnie, usuwając katalog zawierający tę wersję. Na przykład, aby usunąć zestaw SDK 1.0.1 i czas wykonywania, należy użyć następujących poleceń bash:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

Katalogi nadrzędne dla sdk i czasu wykonywania są `dotnet --list-sdks` `dotnet --list-runtimes` wyświetlane w danych wyjściowych z i polecenia, jak pokazano we wcześniejszej tabeli.

---

## <a name="net-core-uninstall-tool"></a>Narzędzie do dezinstalacji platformy .NET Core

[Narzędzie .NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) umożliwia usunięcie zestawów SDK i runi .NET Core z systemu. Dostępna jest kolekcja opcji określających, które wersje mają zostać odinstalowane.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>Zależność programu Visual Studio od wersji sdk programu .NET Core

Przed programiem Visual Studio 2019 w wersji 16.3 instalatory programu Visual Studio nazywali samodzielnyinstalator sdk .NET Core. W rezultacie wersje sdk są wyświetlane w oknie dialogowym **Dodawanie/usuwanie programów** systemu Windows. Usunięcie zestawów SDK .NET Core, które zostały zainstalowane przez program Visual Studio przy użyciu instalatora autonomicznego, może snąć program Visual Studio. Jeśli program Visual Studio ma problemy po odinstalowaniu zestawów SDK, uruchom program Repair w tej określonej wersji programu Visual Studio. W poniższej tabeli przedstawiono niektóre zależności programu Visual Studio w wersjach sdk programu .NET Core:

| Wersja programu Visual Studio | Wersja SDK programu .NET Core |
| -- | -- |
|  Program Visual Studio 2019 w wersji 16.2  | .NET Core SDK 2.2.4xx, 2.1.8xx |
| Visual Studio 2019 w wersji 16.1 | .NET Core SDK 2.2.3xx, 2.1.7xx |
| Visual Studio 2019 w wersji 16.0 | .NET Core SDK 2.2.2xx, 2.1.6xx |
| Visual Studio 2017 w wersji 15.9 | .NET Core SDK 2.2.1xx, 2.1.5xx |
| Program Visual Studio 2017 w wersji 15.8 | .NET Core SDK 2.1.4xx |

Począwszy od programu Visual Studio 2019 w wersji 16.3, program Visual Studio jest odpowiedzialny za własną kopię .NET Core SDK. Z tego powodu nie są już widoczne te wersje sdk w oknie dialogowym **Dodawanie/usuwanie programów.**

## <a name="remove-the-nuget-fallback-folder"></a>Usuwanie folderu rezerwowego NuGet

Przed zestawem SDK .NET Core 3.0 instalatorzy sdk .NET Core używali *NuGetFallbackFolder* do przechowywania pamięci podręcznej pakietów NuGet. Ta pamięć podręczna `dotnet restore` była `dotnet build /t:Restore`używana podczas operacji, takich jak lub . Znajduje `NuGetFallbackFolder` się w *C:\Program Files\dotnet\sdk* w systemie Windows oraz w */usr/local/share/dotnet/sdk* w systemie macOS.

Możesz usunąć ten folder, jeśli:

* Tworzysz tylko przy użyciu .NET Core 3.0 SDK lub nowszych wersji.
* Tworzysz przy użyciu .NET Core SDK wersje wcześniej niż 3.0, ale można pracować w trybie online i rzeczy mogą być wolniejsze raz.

Jeśli chcesz usunąć folder rezerwowy NuGet, możesz go usunąć, ale do tego potrzebne są uprawnienia administratora.

Nie zaleca się usuwania folderu *dotnet.* Spowoduje to usunięcie wszystkich narzędzi globalnych, które zostały wcześniej zainstalowane. Ponadto w systemie Windows:

- Złamiesz visual studio 2019 w wersji 16.3 i nowszych wersjach. Można uruchomić **naprawa,** aby odzyskać.
- Jeśli w oknie dialogowym **Dodawanie/usuwanie programów** znajdują się wpisy sdk .NET Core, zostaną one oddzielone.
