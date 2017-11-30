---
title: "Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)"
description: "Więcej informacji na temat identyfikatora środowiska uruchomieniowego (RID) i używania identyfikatorów RID w .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 067f9cfc283a14b7ea59a7454b7f593ce6eb5806
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="net-core-rid-catalog"></a>.NET core RID katalogu

Identyfikatorów RID jest skrót *identyfikator środowiska uruchomieniowego*. Wartości identyfikatorów RID są używane do identyfikacji platform docelowych, którym działa aplikacja.
Są one używane przez pakiety .NET do reprezentowania zasoby specyficzne dla platformy w pakietach NuGet. Przykłady identyfikatorów RID są następujące wartości: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, lub `osx.10.12-x64`.
Pakietów z zależnościami natywnego RID wyznacza platformy, na których można przywrócić pakietu.

Można ustawić identyfikatorów RID w `<RuntimeIdentifier>` element pliku projektu. Są również używane za pośrednictwem `--runtime` opcji z następującymi [polecenia interfejsu wiersza polecenia platformy .NET Core](./tools/index.md):

- [Kompilacja DotNet](./tools/dotnet-build.md)
- [Wyczyść DotNet](./tools/dotnet-clean.md)
- [Pakiet DotNet](./tools/dotnet-pack.md)
- [Publikowanie DotNet](./tools/dotnet-publish.md)
- [Przywracanie DotNet](./tools/dotnet-restore.md)
- [Uruchom DotNet](./tools/dotnet-run.md)
- [Magazyn DotNet](./tools/dotnet-store.md)

Identyfikatorów RID, reprezentują konkretnych systemów operacyjnych zwykle skorzystaj z tego wzorca: `[os].[version]-[architecture]-[additional qualifiers]` gdzie:

- `[os]`jest krótkiej nazwy systemu operacyjnego platformy. Na przykład `ubuntu`.

- `[version]`jest to wersja systemu operacyjnego w formie oddzielona kropkami (`.`) numer wersji. Na przykład `15.10`.

  - Wersja **nie powinny** marketingowe w wersji, ponieważ stanowią one często wielu odrębny wersji systemu operacyjnego ze zróżnicowanymi powierzchni interfejsu API platformy.

- `[architecture]`to architektura procesora. Na przykład: `x86`, `x64`, `arm`, lub `arm64`.

- `[additional qualifiers]`rozróżniania różnych platform. Na przykład: `aot` lub `corert`.

## <a name="rid-graph"></a>Wykres identyfikatorów RID

Wykres identyfikatorów RID lub wykres rezerwowy środowiska uruchomieniowego znajduje się lista identyfikatorów RID, które są zgodne ze sobą. Identyfikatorów RID są zdefiniowane w [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) pakietu. Można wyświetlić listę obsługiwanych identyfikatorów RID i wykres identyfikatorów RID w [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku, który znajduje się w repozytorium CoreFX. W tym pliku widać, że wszystkie identyfikatorów RID, z wyjątkiem podstawowego katalogu zawiera `"#import"` instrukcji. Te instrukcje wskazują zgodne identyfikatorów RID.

Gdy NuGet przywraca pakietów, próbuje znaleźć dokładnego dopasowania dla określonego środowiska wykonawczego.
Jeśli nie znaleziono dokładnego dopasowania, NuGet przeprowadzi Cię wstecz wykresu aż do znalezienia najbliższego zgodny system zgodnie z wykresu identyfikatorów RID.

Poniższy przykład jest to rzeczywiste zapis `osx.10.12-x64` identyfikatorów RID:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Powyżej RID Określa, że `osx.10.12-x64` importuje `osx.10.11-x64`. Tak, gdy NuGet przywraca pakietów, próbuje znaleźć dokładnego dopasowania dla `osx.10.12-x64` w pakiecie. Jeśli NuGet nie może znaleźć określonego środowiska uruchomieniowego, można przywrócić pakiety, które określają `osx.10.11-x64` środowisk uruchomieniowych, na przykład.

W poniższym przykładzie przedstawiono nieco większy wykres RID też definiowany w *runtime.json* pliku:

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

Wszystkie identyfikatorów RID po pewnym czasie mapy od głównego `any` identyfikatorów RID.

Istnieje kilka dodatkowych kwestii dotyczących identyfikatorów RID, które należy mieć na uwadze podczas pracy z nimi:

- Identyfikatorów RID są **nieprzezroczyste ciągów** i powinien być traktowany jako czarne pola.
- Nie Konstruuj programowo identyfikatorów RID.
- Użyj identyfikatorów RID, które zostały już zdefiniowane dla platformy.
- RID muszą być określone, więc nie wolno zakładać nic rzeczywistej wartości identyfikatorów RID.

## <a name="using-rids"></a>Przy użyciu identyfikatorów RID

Aby można było użyć identyfikatorów RID, trzeba znać istniejących identyfikatorów RID. Regularnie dodawane nowe wartości dla platformy.
Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku na CoreFX repozytorium.

.NET core 2.0 SDK wprowadza pojęcia przenośne identyfikatorów RID. Są one nowe wartości dodawać do wykresu identyfikatorów RID, które nie są powiązane określonej wersji lub dystrybucji systemu operacyjnego. Są one szczególnie użyteczne w przypadku wielu dystrybucjach systemu Linux.

Poniższa lista przedstawia najbardziej typowe identyfikatorów RID używane dla każdego systemu operacyjnego. Nie obejmuje ona `arm` lub `corert` wartości.

## <a name="windows-rids"></a>RID systemu Windows

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

Zobacz [wymagania wstępne dotyczące .NET Core w systemie Windows](windows-prerequisites.md) Aby uzyskać więcej informacji.

## <a name="linux-rids"></a>Linux identyfikatorów RID

- Przenośna
  - `linux-x64`
- CentOS
  - `centos-x64`
  - `centos.7-x64`
- Debian
  - `debian-x64`
  - `debian.8-x64`
- Fedora
  - `fedora-x64`
  - `fedora.24-x64`
  - `fedora.25-x64`(.NET core w wersji 2.0 lub nowszy)
  - `fedora.26-x64`(.NET core w wersji 2.0 lub nowszy)
- Gentoo (.NET Core w wersji 2.0 lub nowszy)
  - `gentoo-x64`
- openSUSE
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- Oracle Linux
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- Red Hat Enterprise Linux
  - `rhel-x64`
  - `rhel.6-x64`(.NET core w wersji 2.0 lub nowszy)
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - `rhel.7.3-x64`(.NET core w wersji 2.0 lub nowszy)
  - `rhel.7.4-x64`(.NET core w wersji 2.0 lub nowszy)
- Tizen (.NET Core w wersji 2.0 lub nowszy)
  - `tizen`
- Ubuntu
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- Ubuntu pochodne
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - `linuxmint.18.1-x64`(.NET core w wersji 2.0 lub nowszy)

Zobacz [wymagania wstępne dotyczące .NET Core w systemie Linux](linux-prerequisites.md) Aby uzyskać więcej informacji.

## <a name="macos-rids"></a>System macOS identyfikatorów RID

System macOS RID za pomocą starszej znakowania "OS x".

- `osx-x64`(.NET core w wersji 2.0 lub nowszy, minimalna wersja to `osx.10.12-x64`)
- `osx.10.10-x64`
- `osx.10.11-x64`
- `osx.10.12-x64`(.NET core 1.1 lub nowszy)
- `osx.10.13-x64`

Zobacz [wymagania wstępne dotyczące .NET Core na macOS](macos-prerequisites.md) Aby uzyskać więcej informacji.

## <a name="android-rids-net-core-20-or-later-versions"></a>Android identyfikatorów RID (.NET Core w wersji 2.0 lub nowszy)

- `android`
- `android.21`

## <a name="see-also"></a>Zobacz także

[Identyfikatory środowiska wykonawczego](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
