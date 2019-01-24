---
title: Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)
description: Informacje o identyfikator środowiska uruchomieniowego (RID) i jak identyfikatorów RID są używane w programie .NET Core.
ms.date: 07/19/2018
ms.openlocfilehash: 5a6dda260b4be85e54f4075f3edf12210b385289
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534549"
---
# <a name="net-core-rid-catalog"></a>.NET core RID katalogu

Identyfikatorów RID jest mała w przypadku *identyfikator środowiska uruchomieniowego*. RID wartości są używane do identyfikowania platformy docelowe, w którym działa aplikacja.
Są używane przez pakiety .NET do reprezentowania zasoby specyficzne dla platformy w pakietach NuGet. Przykłady identyfikatorów RID są następujące wartości: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, lub `osx.10.12-x64`.
W przypadku pakietów zależności natywnych RID wyznacza platformy, na których można przywrócić pakietu.

Pojedynczy RID można ustawić w `<RuntimeIdentifier>` elementu z pliku projektu. Wiele identyfikatorów RID mogą być definiowane jako rozdzielaną średnikami listę w pliku projektu `<RuntimeIdentifiers>` elementu. Są również używane za pośrednictwem `--runtime` opcji z następujących [poleceń interfejsu wiersza polecenia platformy .NET Core](./tools/index.md):

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

Identyfikatorów RID, reprezentujące systemy operacyjne konkretnych zwykle skorzystaj z tego wzorca: `[os].[version]-[architecture]-[additional qualifiers]` gdzie:

- `[os]` jest krótkiej nazwy systemu operacyjnego i platformy. Na przykład `ubuntu`.

- `[version]` jest to wersja systemu operacyjnego w formie oddzielone kropką (`.`) numer wersji. Na przykład `15.10`.

  - Wersja **nie powinien** marketingowych w wersjach, jak często reprezentują wielu dyskretnych wersji systemu operacyjnego ze zróżnicowanymi obszar powierzchni interfejsu API platformy.

- `[architecture]` jest to architektura procesora. Na przykład: `x86`, `x64`, `arm`, lub `arm64`.

- `[additional qualifiers]` możliwości rozróżniania różnych platformach. Na przykład: `aot` lub `corert`.

## <a name="rid-graph"></a>Wykres RID

RID wykresu lub grafu rezerwowego środowisko uruchomieniowe znajduje się lista identyfikatorów RID, które są ze sobą zgodne. Identyfikatorów RID są zdefiniowane w [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) pakietu. Można wyświetlić listę obsługiwanych identyfikatorów RID i wykres RID [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku, który znajduje się w repozytorium CoreFX. W tym pliku widać, że wszystkich identyfikatorów RID, z wyjątkiem dla nich podstawowy zawiera `"#import"` instrukcji. Te instrukcje wskazują zgodnych identyfikatorów RID.

Gdy NuGet przywraca pakietów, próbuje odnaleźć dokładnego dopasowania dla określonego środowiska uruchomieniowego.
Jeśli nie zostanie znalezione dokładne dopasowanie, NuGet przedstawia powrót wykresu do momentu znalezienia najbliższego zgodny system zgodnie z wykresu identyfikatorów RID.

Poniższy przykład jest to rzeczywiste zapis `osx.10.12-x64` identyfikatorów RID:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Powyższe RID Określa, że `osx.10.12-x64` importuje `osx.10.11-x64`. Tak, gdy NuGet przywraca pakietów, próbuje odnaleźć dokładnego dopasowania dla `osx.10.12-x64` w pakiecie. Jeśli NuGet nie może odnaleźć określonego środowiska uruchomieniowego, przywracanie pakietów, które określają `osx.10.11-x64` środowisk wykonawczych, na przykład.

W poniższym przykładzie przedstawiono wykres RID nieco większy, również zdefiniowanej w *runtime.json* pliku:

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

Wszystkich identyfikatorów RID po pewnym czasie zamapować powrót do katalogu głównego `any` identyfikatorów RID.

Istnieją pewne zagadnienia dotyczące identyfikatorów RID, które trzeba mieć na uwadze podczas pracy z nimi:

- Identyfikatorów RID są **nieprzezroczyste ciągi** i powinny być traktowane jako pola czarny.
- Nie twórz programowo identyfikatorów RID.
- Użyj identyfikatorów RID, które są już zdefiniowane dla platformy.
- RID muszą być określone, dzięki czemu nie wolno zakładać cokolwiek — od rzeczywistej wartości identyfikatorów RID.

## <a name="using-rids"></a>Przy użyciu identyfikatorów RID

Aby można było używać identyfikatorów RID, musisz wiedzieć, który istnieje identyfikatorów RID. Nowe wartości są regularnie dodawane do korzystania z platformy.
Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku w repozytorium CoreFX.

.NET core 2.0 SDK wprowadzono pojęcie przenośne identyfikatorów RID. Są one nowe wartości dodane do grafu identyfikatorów RID, które nie są powiązane z konkretną wersję lub dystrybucji systemu operacyjnego. Są one szczególnie przydatne podczas pracy z wieloma dystrybucje systemu Linux.

Na poniższej liście przedstawiono najbardziej typowe identyfikatorów RID, używane dla każdego systemu operacyjnego. Nie omówiono `arm` lub `corert` wartości.

## <a name="windows-rids"></a>Windows identyfikatorów RID

- Przenośna
  - `win-x86`
  - `win-x64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8 / Windows Server 2012
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- Windows 8.1 / Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 / Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

Zobacz [wymagania wstępne dla platformy .NET Core w Windows](windows-prerequisites.md) Aby uzyskać więcej informacji.

## <a name="linux-rids"></a>Identyfikatorów RID w systemie Linux

- Przenośna
  - `linux-x64`
- CentOS
  - `centos-x64`
  - `centos.7-x64`
- Debian
  - `debian-x64`
  - `debian.8-x64`
  - `debian.9-x64` (.NET core 1.1 lub nowszy)
- Fedora
  - `fedora-x64`
  - `fedora.27-x64`
  - `fedora.28-x64` (.NET core 1.1 lub nowszy)
- Gentoo (.NET Core 2.0 lub nowszy)
  - `gentoo-x64`
- openSUSE
  - `opensuse-x64`
  - `opensuse.42.3-x64`
- Oracle Linux
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
  - `ol.7.3-x64`
  - `ol.7.4-x64`
- Red Hat Enterprise Linux
  - `rhel-x64`
  - `rhel.6-x64` (.NET core 2.0 lub nowszy)
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - `rhel.7.3-x64` (.NET core 2.0 lub nowszy)
  - `rhel.7.4-x64` (.NET core 2.0 lub nowszy)
- Tizen (.NET Core 2.0 lub nowszy)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`
- Ubuntu
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.17.10-x64`
  - `ubuntu.18.04-x64`
- Pochodne Ubuntu
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64` (.NET core 2.0 lub nowszy)
  - `linuxmint.18.1-x64` (.NET core 2.0 lub nowszy)
  - `linuxmint.18.2-x64` (.NET core 2.0 lub nowszy)
  - `linuxmint.18.3-x64` (.NET core 2.0 lub nowszy)
- SUSE Enterprise Linux (SLES) (.NET Core 2.0 lub nowszy)
  - `sles-x64`
  - `sles.12-x64`
  - `sles.12.1-x64`
  - `sles.12.2-x64`
  - `sles.12.3-x64`
- Alpine Linux (.NET Core 2.1 lub nowszy)
  - `alpine-x64`
  - `alpine.3.7-x64`

Zobacz [wymagania wstępne dla platformy .NET Core w systemie Linux](linux-prerequisites.md) Aby uzyskać więcej informacji.

## <a name="macos-rids"></a>RID z systemem macOS

RID z systemem macOS za pomocą starszej znakowania "OSX".

- `osx-x64` (.NET core 2.0 lub nowszej wersji, minimalna wersja to `osx.10.12-x64`)
- `osx.10.10-x64`
- `osx.10.11-x64`
- `osx.10.12-x64` (.NET core 1.1 lub nowszy)
- `osx.10.13-x64`

Zobacz [wymagania wstępne dla platformy .NET Core w systemie macOS](macos-prerequisites.md) Aby uzyskać więcej informacji.

## <a name="android-rids-net-core-20-or-later-versions"></a>Android RID (.NET Core 2.0 lub nowszy)

- `android`
- `android.21`

## <a name="see-also"></a>Zobacz także

- [Identyfikatory środowiska uruchomieniowego](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
