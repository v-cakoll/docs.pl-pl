---
title: Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)
description: Informacje o identyfikator środowiska uruchomieniowego (RID) i jak identyfikatorów RID są używane w programie .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: 0d03e39c755b43e145edf5efe48422cbae7abcab
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745745"
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

- `[additional qualifiers]` możliwości rozróżniania różnych platformach. Na przykład: `aot`.

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

.NET core 2.0 SDK wprowadzono pojęcie przenośne identyfikatorów RID. Są one nowe wartości dodane do grafu identyfikatorów RID, które nie są powiązane z konkretną wersję lub dystrybucji systemu operacyjnego i są preferowanych przez, korzystając z platformy .NET Core 2.0 lub nowszej. Są one szczególnie użyteczne w przypadku, gdy zajmowanie wielu dystrybucje systemu Linux, ponieważ większość RID dystrybucji są mapowane na przenośnym identyfikatorów RID.

Na poniższej liście przedstawiono małego podzbioru typowych identyfikatorów RID, używane dla każdego systemu operacyjnego.

## <a name="windows-rids"></a>Windows identyfikatorów RID

Tylko wartości typowych są wyświetlane. Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku w repozytorium CoreFX.

- Przenośna (.NET Core 2.0 lub nowszy)
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
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

Tylko wartości typowych są wyświetlane. Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku w repozytorium CoreFX. Urządzenia z systemem dystrybucji nie są wymienione poniżej mogą działać z jedną przenośne identyfikatorów RID. Na przykład, można zastosować urządzenia Raspberry Pi korzystania z dystrybucji systemu Linux, niewymienionych `linux-arm`.

- Przenośna (.NET Core 2.0 lub nowszy)
  - `linux-x64` (Większość dystrybucje pulpitu, takie jak CentOS, Debian, Fedora, Ubuntu i ich pochodnych)
  - `linux-musl-x64` (Dystrybucje lightweight przy użyciu [musl](https://wiki.musl-libc.org/projects-using-musl.html) Alpine Linux, takie jak)
  - `linux-arm` (Dystrybucje systemu Linux w systemie ARM, takich jak Raspberry Pi)
- Red Hat Enterprise Linux
  - `rhel-x64` (Zastąpiona `linux-x64` systemu RHEL powyżej w wersji 6)
  - `rhel.6-x64` (.NET core 2.0 lub nowszy)
- Tizen (.NET Core 2.0 lub nowszy)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

Zobacz [wymagania wstępne dla platformy .NET Core w systemie Linux](linux-prerequisites.md) Aby uzyskać więcej informacji.

## <a name="macos-rids"></a>RID z systemem macOS

RID z systemem macOS za pomocą starszej znakowania "OSX". Tylko wartości typowych są wyświetlane. Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku w repozytorium CoreFX.

- Przenośna (.NET Core 2.0 lub nowszy)
  - `osx-x64` (Minimalna wersja systemu operacyjnego jest macOS 10.12 Sierra)
- macOS 10.10 Yosemite
  - `osx.10.10-x64`
- System macOS 10.11 El Capitan
  - `osx.10.11-x64`
- System macOS 10.12 Sierra (.NET Core 1.1 lub nowszy)
  - `osx.10.12-x64`
- macOS 10.13 High Sierra (.NET Core 1.1 lub nowszy)
  - `osx.10.13-x64`
- System macOS 10.14 Mojave (.NET Core 1.1 lub nowszy)
  - `osx.10.14-x64`

Zobacz [wymagania wstępne dla platformy .NET Core w systemie macOS](macos-prerequisites.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

- [Identyfikatory środowiska uruchomieniowego](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
