---
title: Wykaz identyfikatora środowiska uruchomienionowego programu .NET Core (RID)
description: Dowiedz się więcej o identyfikatorze IDentifier (RID) i sposobie użycia identyfikatorów RID w ustonach .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: feb19632f16a047ecfb2dcb697a9b837824a1929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451736"
---
# <a name="net-core-rid-catalog"></a>Katalog RID rdzenia .NET

Rid jest skrótem od *IDentifier runtime*. Wartości RID są używane do identyfikowania platform docelowych, na których działa aplikacja.
Są one używane przez pakiety .NET do reprezentowania zasobów specyficznych dla platformy w pakietach NuGet. Następujące wartości są przykładami identyfikatorów `linux-x64`IDENTYFIKATORÓW: , `ubuntu.14.04-x64`, `win7-x64`, lub `osx.10.12-x64`.
W przypadku pakietów z zależnościami macierzystymi rid wyznacza, na których platformach pakiet może zostać przywrócony.

Pojedynczy identyfikator RID można `<RuntimeIdentifier>` ustawić w elemencie pliku projektu. Wiele identyfikatorów IDENTYFIKATORÓW MOŻNA zdefiniować jako listę rozdzielaną średnikami `<RuntimeIdentifiers>` w elemencie pliku projektu. Są one również używane `--runtime` za pomocą opcji z [następującymi poleceniami .NET Core CLI:](./tools/index.md)

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

IDENTYFIKATORY RID, które reprezentują konkretne systemy `[os].[version]-[architecture]-[additional qualifiers]` operacyjne, zwykle następują po tym wzorze: gdzie:

- `[os]`jest monikersystemu operacyjnego/platformowego. Na przykład `ubuntu`.

- `[version]`to wersja systemu operacyjnego w postaci numeru wersji`.`oddzielonej kropką ( ) numerwersji. Na przykład `15.10`.

  - Wersja **nie powinna** być wersjami marketingowymi, ponieważ często reprezentują one wiele dyskretnych wersji systemu operacyjnego o różnej powierzchni interfejsu API platformy.

- `[architecture]`jest architektura procesora. Na `x86`przykład: `x64` `arm`, `arm64`, , lub .

- `[additional qualifiers]`dalsze zróżnicowanie różnych platform. Na przykład: `aot`.

## <a name="rid-graph"></a>Wykres RID

Wykres RID lub wykres rezerwowy środowiska uruchomieniowego to lista identyfikatorów RID, które są ze sobą zgodne. Identyfikatory IDENTYFIKATORY są zdefiniowane w pakiecie [Microsoft.NETCore.Platforms.](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) Listę obsługiwanych identyfikatorów RID i wykres RID można wyświetlić w pliku [*runtime.json,*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) który znajduje się w `dotnet/runtime` repozytorium. W tym pliku widać, że wszystkie identyfikatory RID, z `"#import"` wyjątkiem podstawowego, zawierają instrukcję. Instrukcje te wskazują zgodne identyfikatory IDENTYFIKATORY.

Gdy NuGet przywraca pakiety, próbuje znaleźć dokładne dopasowanie dla określonego czasu wykonywania.
Jeśli dokładne dopasowanie nie zostanie znaleziony, NuGet cofa wykres, dopóki nie znajdzie najbliższego kompatybilnego systemu zgodnie z wykresem RID.

Poniższy przykład jest rzeczywisty wpis `osx.10.12-x64` dla RID:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Powyższy identyfikator RID `osx.10.12-x64` określa, że importuje `osx.10.11-x64`. Tak więc, gdy NuGet przywraca pakiety, próbuje `osx.10.12-x64` znaleźć dokładne dopasowanie w pakiecie. Jeśli NuGet nie może znaleźć określonego czasu wykonywania, można przywrócić pakiety, które określają `osx.10.11-x64` czas wykonywania, na przykład.

W poniższym przykładzie przedstawiono nieco większy wykres RID zdefiniowany również w pliku *runtime.json:*

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

Wszystkie identyfikatory RID ostatecznie mapują z powrotem do głównego rid. `any`

Podczas pracy z nimi należy pamiętać o identyfikatorach RID:

- IDENTYFIKATORY SĄ **nieprzezroczyste ciągi** i powinny być traktowane jako czarne pola.
- Nie twórz identyfikatorów RID programowo.
- Użyj identyfikatorów IDENTYFIKATORÓW, które są już zdefiniowane dla platformy.
- IDENTYFIKATORY RID muszą być specyficzne, więc nie zakładaj niczego z rzeczywistej wartości RID.

## <a name="using-rids"></a>Korzystanie z identyfikatorów NIK

Aby móc używać identyfikatorów IDENTYFIKATORÓW, musisz wiedzieć, które identyfikatory IDENTYFIKATORÓw ISTNIEJĄ. Nowe wartości są regularnie dodawane do platformy.
Aby uzyskać najnowszą i pełną wersję, zobacz plik `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) w repozytorium.

.NET Core 2.0 SDK wprowadza koncepcję przenośnych identyfikatorów NIK. Są to nowe wartości dodane do wykresu RID, które nie są powiązane z określoną wersją lub dystrybucją systemu operacyjnego i są preferowanym wyborem podczas korzystania z .NET Core 2.0 lub nowszego. Są one szczególnie przydatne w przypadku wielu dystrybucji Linuksa, ponieważ większość dystrybucji identyfikatorów RID są mapowane na przenośne identyfikatory RID.

Na poniższej liście przedstawiono mały podzbiór najczęściej używanych identyfikatorów NIK używanych dla każdego os.

## <a name="windows-rids"></a>Identyfikatory RID systemu Windows

Wyświetlane są tylko typowe wartości. Aby uzyskać najnowszą i pełną wersję, zobacz `dotnet/runtime` plik [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) w repozytorium.

- Wersja przenośna (.NET Core 2.0 lub nowsza wersja)
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

Aby uzyskać więcej informacji, zobacz [zależności i wymagania programu .NET Core](install/dependencies.md?pivots=os-windows).

## <a name="linux-rids"></a>Identyfikatory RID linuksa

Wyświetlane są tylko typowe wartości. Aby uzyskać najnowszą i pełną wersję, zobacz plik `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) w repozytorium. Urządzenia z dystrybucją niewymienioną poniżej mogą współpracować z jedną z przenośnych identyfikatorów NIK. Na przykład urządzenia Raspberry Pi z niewymienioną `linux-arm`dystrybucją Linuksa mogą być kierowane do .

- Wersja przenośna (.NET Core 2.0 lub nowsza wersja)
  - `linux-x64`(Większość dystrybucji pulpitu, takich jak CentOS, Debian, Fedora, Ubuntu i pochodne)
  - `linux-musl-x64`(Lekkie dystrybucje za pomocą [musl](https://wiki.musl-libc.org/projects-using-musl.html) jak Alpine Linux)
  - `linux-arm`(Dystrybucje Linuksa działające na ARM jak Raspberry Pi)
- Red Hat Enterprise Linux
  - `rhel-x64`(Zastąpiony przez `linux-x64` rhel powyżej wersji 6)
  - `rhel.6-x64`(.NET Core 2.0 lub nowsze wersje)
- Tizen (.NET Core 2.0 lub nowsze wersje)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

Aby uzyskać więcej informacji, zobacz [zależności i wymagania programu .NET Core](install/dependencies.md?pivots=os-linux).

## <a name="macos-rids"></a>Identyfikatory RID systemu macOS

RIDy systemu macOS używają starszej marki "OSX". Wyświetlane są tylko typowe wartości. Aby uzyskać najnowszą i pełną wersję, zobacz plik `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) w repozytorium.

- Wersja przenośna (.NET Core 2.0 lub nowsza wersja)
  - `osx-x64`(Minimalna wersja systemu operacyjnego to macOS 10.12 Sierra)
- macOS 10.10 Yosemite
  - `osx.10.10-x64`
- macOS 10.11 El Capitan
  - `osx.10.11-x64`
- macOS 10.12 Sierra (.NET Core 1.1 lub nowsze wersje)
  - `osx.10.12-x64`
- macOS 10.13 High Sierra (.NET Core 1.1 lub nowsze wersje)
  - `osx.10.13-x64`
- macOS 10.14 Mojave (.NET Core 1.1 lub nowsze wersje)
  - `osx.10.14-x64`

Aby uzyskać więcej informacji, zobacz [zależności i wymagania programu .NET Core](install/dependencies.md?pivots=os-macos).

## <a name="see-also"></a>Zobacz też

- [Identyfikatory czasu wykonywania](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
