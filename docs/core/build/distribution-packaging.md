---
title: Tworzenie pakietów dystrybucji platformy .NET Core
description: Dowiedz się, jak spakować, nazwać i wersja .NET Core do dystrybucji.
author: tmds
ms.date: 10/09/2019
ms.custom: seodec18
ms.openlocfilehash: 715eb944c3e7626696f64e63b874e2f77595cf46
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393583"
---
# <a name="net-core-distribution-packaging"></a>Tworzenie pakietów dystrybucji platformy .NET Core

Ponieważ platforma .NET Core jest dostępna na więcej i większej liczbie platform, warto dowiedzieć się, jak spakować, nazwać i wersja. W ten sposób programy obsługi pakietów mogą pomóc w zapewnieniu spójnego środowiska bez względu na to, gdzie użytkownicy zdecydują się na uruchomienie platformy .NET. Ten artykuł jest przydatny dla użytkowników, którzy są:

- Podjęto próbę skompilowania platformy .NET Core ze źródła.
- Chce wprowadzić zmiany w interfejs wiersza polecenia platformy .NET Core, które mogą mieć wpływ na wynikowy układ lub pakiety.

## <a name="disk-layout"></a>Układ dysku

Po zainstalowaniu programu .NET Core składa się z kilku składników, które zostały wdrożone w systemie plików:

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** Host (znany również jako "muxer") ma dwie odrębne role: Aktywuj środowisko uruchomieniowe, aby uruchomić aplikację, i aktywuj zestaw SDK, aby wysłać do niego polecenia. Host jest natywnym plikiem wykonywalnym (`dotnet.exe`).

W przypadku jednego hosta większość innych składników znajduje się w katalogach z wersjami (2, 3, 5, 6). Oznacza to, że w systemie może być dostępnych wiele wersji, ponieważ są one instalowane obok siebie.

- (2) **host/FXR/@no__t 1fxr wersja >** zawiera logikę rozpoznawania architektury używaną przez hosta. Host używa najnowszej hostfxr, która jest zainstalowana. Hostfxr jest odpowiedzialny za wybór odpowiedniego środowiska uruchomieniowego podczas wykonywania aplikacji platformy .NET Core. Na przykład aplikacja skompilowana dla programu .NET Core 2.0.0 używa środowiska uruchomieniowego 2.0.5, gdy jest ono dostępne. Podobnie hostfxr wybiera odpowiedni zestaw SDK podczas opracowywania.

- (3) zestaw **SDK/\<SDK wersja >** zestaw SDK (znany również jako "Narzędzie") to zestaw narzędzi zarządzanych, które są używane do pisania i kompilowania bibliotek i aplikacji platformy .NET Core. Zestaw SDK zawiera interfejs wiersza polecenia (CLI) platformy .NET Core, kompilator języków zarządzanych, program MSBuild oraz skojarzone zadania kompilacji i cele, narzędzia NuGet, nowe szablony projektów itd.

- (4) **zestaw SDK/NuGetFallbackFolder** zawiera pamięć podręczną pakietów NuGet używanych przez zestaw SDK podczas operacji przywracania, na przykład w przypadku uruchamiania `dotnet restore` lub `dotnet build`. Ten folder jest używany tylko przed platformą .NET Core 3,0. Nie można go skompilować ze źródła, ponieważ zawiera wstępnie skompilowane zasoby binarne z `nuget.org`.

Folder **udostępniony** zawiera struktury. Struktura udostępniona udostępnia zestaw bibliotek w centralnej lokalizacji, dzięki czemu mogą one być używane przez różne aplikacje.

- (5) **Shared/Microsoft. Core. app/\<runtime wersja >** Ta struktura zawiera środowisko uruchomieniowe platformy .NET Core i obsługujące biblioteki zarządzane.

- (6) **Shared/Microsoft. AspNetCore. { Aplikacja, wszystkie}/\<aspnetcore wersja >** zawiera biblioteki ASP.NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.App` są opracowywane i obsługiwane w ramach projektu .NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.All` stanowią nadzbiór, który zawiera również biblioteki innych firm.

- (7) **Shared/Microsoft. Desktop. app/\<desktop App version >** zawiera biblioteki pulpitu systemu Windows. Nie jest to uwzględnione na platformach innych niż Windows.

- (8) **License. txt, ThirdPartyNotices. txt** to licencja platformy .NET Core i licencje bibliotek innych firm używane odpowiednio w programie .NET Core.

- (9, 10) **dotnet. 1. gz, dotnet** `dotnet.1.gz` jest stroną ręczną dotnet. `dotnet` to link symboliczny hosta dotnet (1). Te pliki są instalowane w dobrze znanych lokalizacjach na potrzeby integracji systemu.

- (11, 12) **Microsoft. servicecore. app. ref, Microsoft. AspNetCore. app. ref** opisują interfejs API wersji `x.y` platformy .NET Core i ASP.NET Core odpowiednio. Te pakiety są używane podczas kompilowania dla tych wersji docelowych.

- (13) **Microsoft. WebCore. app. host. \<rid >** zawiera natywny plik binarny dla platformy `rid`. Ten plik binarny jest szablonem podczas kompilowania aplikacji .NET Core do natywnego pliku binarnego dla tej platformy.

- (14) **Microsoft. WindowsDesktop. app. ref** — zawiera opis interfejsu API aplikacji klasycznych systemu Windows w wersji `x.y`. Te pliki są używane podczas kompilowania dla tego obiektu docelowego. Nie jest to obsługiwane na platformach innych niż Windows.

- (15) **Standard. Library. ref** — opis interfejsu API `x.y` usługi Standard. Te pliki są używane podczas kompilowania dla tego obiektu docelowego.

- (16) **/etc/dotnet/install_location** to plik, który zawiera pełną ścieżkę do `{dotnet_root}`. Ścieżka może kończyć się znakiem nowego wiersza. Nie trzeba dodawać tego pliku, gdy katalog główny jest `/usr/share/dotnet`.

- **Szablony** (17) zawierają szablony używane przez zestaw SDK. Na przykład `dotnet new` znajduje tutaj szablon projektu.

Foldery oznaczone `(*)` są używane przez wiele pakietów. Niektóre formaty pakietów (na przykład `rpm`) wymagają specjalnej obsługi takich folderów. Należy zachować ostrożność nad pakietem.

## <a name="recommended-packages"></a>Zalecane pakiety

Wersja .NET Core jest oparta na składniku Runtime `[major].[minor]` numerach wersji.
Wersja zestawu SDK używa tego samego `[major].[minor]` i ma niezależną `[patch]`, która łączy semantykę funkcji i poprawki dla zestawu SDK.
Na przykład: zestaw SDK w wersji 2.2.302 to druga wersja poprawki zestawu SDK, która obsługuje środowisko uruchomieniowe 2,2. Aby uzyskać więcej informacji o działaniu wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).

Niektóre pakiety zawierają część numeru wersji w nazwie. Pozwala to na zainstalowanie określonej wersji.
Reszta wersji nie jest uwzględniona w nazwie wersji. Dzięki temu Menedżer pakietów systemu operacyjnego może aktualizować pakiety (na przykład automatycznie instalując poprawki zabezpieczeń). Obsługiwane menedżery pakietów są specyficzne dla systemu Linux.

Poniżej przedstawiono listę zalecanych pakietów:

- `dotnet-sdk-[major].[minor]` — instaluje najnowszy zestaw SDK dla określonego środowiska uruchomieniowego
  - **Wersja:** @no__t 1runtime wersja >
  - **Przykład:** dotnet-sdk-2,1
  - **Zawiera:** (3), (4)
  - **Zależności:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`

- `aspnetcore-runtime-[major].[minor]`-instaluje określony środowisko uruchomieniowe ASP.NET Core
  - **Wersja:** @no__t — wersja środowiska uruchomieniowego 1aspnetcore >
  - **Przykład:** aspnetcore-runtime-2,1
  - **Zawiera:** (6)
  - **Zależności:** `dotnet-runtime-[major].[minor]`

- `dotnet-runtime-deps-[major].[minor]` _(opcjonalnie)_ — instaluje zależności do uruchamiania aplikacji samodzielnych
  - **Wersja:** @no__t 1runtime wersja >
  - **Przykład:** dotnet-Runtime-deps-2,1
  - **Zależności:** _dystrybucji określonych zależności_

- `dotnet-runtime-[major].[minor]`-instaluje określone środowisko uruchomieniowe
  - **Wersja:** @no__t 1runtime wersja >
  - **Przykład:** dotnet-runtime-2,1
  - **Zawiera:** (5)
  - **Zależności:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`

- `dotnet-hostfxr-[major].[minor]` — zależność
  - **Wersja:** @no__t 1runtime wersja >
  - **Przykład:** dotnet-hostfxr-3,0
  - **Zawiera:** (2)
  - **Zależności:** `dotnet-host`

- `dotnet-host` — zależność
  - **Wersja:** @no__t 1runtime wersja >
  - **Przykład:** dotnet-Host
  - **Zawiera:** (1), (8), (9), (10), (16)

- `dotnet-apphost-pack-[major].[minor]` — zależność
  - **Wersja:** @no__t 1runtime wersja >
  - **Zawiera:** (13)

- `dotnet-targeting-pack-[major].[minor]` — umożliwia kierowanie do nienajnowszego środowiska uruchomieniowego
  - **Wersja:** @no__t 1runtime wersja >
  - **Zawiera:** (12)

- `aspnetcore-targeting-pack-[major].[minor]` — umożliwia kierowanie do nienajnowszego środowiska uruchomieniowego
  - **Wersja:** @no__t — wersja środowiska uruchomieniowego 1aspnetcore >
  - **Zawiera:** (11)

- `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` — umożliwia kierowanie do wersji standardowej
  - **Wersja:** @no__t 1sdk wersja >
  - **Zawiera:** (15)

- `dotnet-templates-[major].[minor]`
  - **Wersja:** @no__t 1sdk wersja >
  - **Zawiera:** (15)

@No__t-0 wymaga interpretacji _zależności specyficznych dla dystrybucji_. Ponieważ system kompilacji dystrybucji może być w stanie automatycznie dziedziczyć, pakiet jest opcjonalny, w takim przypadku te zależności są dodawane bezpośrednio do pakietu `dotnet-runtime-[major].[minor]`.

Gdy zawartość pakietu znajduje się w folderze z uruchomioną wersją, nazwa pakietu `[major].[minor]` pasuje do nazwy folderu z wersją. Dla wszystkich pakietów, z wyjątkiem `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, jest to również zgodne z wersją .NET Core.

Zależności między pakietami powinny mieć wartość _równą lub większą niż_ wymaganie wersji. Na przykład `dotnet-sdk-2.2:2.2.401` wymaga `aspnetcore-runtime-2.2 >= 2.2.6`. Dzięki temu użytkownik może uaktualnić instalację za pośrednictwem pakietu głównego (na przykład `dnf update dotnet-sdk-2.2`).

Większość dystrybucji wymaga, aby wszystkie artefakty zostały skompilowane ze źródła. Ma to wpływ na pakiety:

- Bibliotek innych firm w `shared/Microsoft.AspNetCore.All` nie można z łatwością skompilować ze źródła. Ten folder zostanie pominięty w pakiecie `aspnetcore-runtime`.

- @No__t-0 jest wypełniana przy użyciu artefaktów binarnych z `nuget.org`. Powinna pozostać pusta.

Wiele pakietów `dotnet-sdk` może zapewnić te same pliki dla `NuGetFallbackFolder`. Aby uniknąć problemów z menedżerem pakietów, te pliki powinny być identyczne (suma kontrolna, Data modyfikacji itd.).

## <a name="building-packages"></a>Kompilowanie pakietów

Repozytorium [dotnet/Source-Build](https://github.com/dotnet/source-build) zawiera instrukcje dotyczące sposobu tworzenia źródłowej plik tar zestaw .NET Core SDK i wszystkich jego składników. Dane wyjściowe repozytorium Build source są zgodne z układem opisanym w pierwszej sekcji tego artykułu.
