---
title: Tworzenie pakietów dystrybucji platformy .NET Core
description: Dowiedz się, jak spakować, nazwać i wersja .NET Core do dystrybucji.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394157"
---
# <a name="net-core-distribution-packaging"></a>Tworzenie pakietów dystrybucji platformy .NET Core

Ponieważ platforma .NET Core jest dostępna na więcej i większej liczbie platform, warto dowiedzieć się, jak spakować, nazwać i wersja. W ten sposób programy obsługi pakietów mogą pomóc w zapewnieniu spójnego środowiska bez względu na to, gdzie użytkownicy zdecydują się na uruchomienie platformy .NET. Ten artykuł jest przydatny dla użytkowników, którzy są:

- Podjęto próbę skompilowania platformy .NET Core ze źródła.
- Chce wprowadzić zmiany w interfejs wiersza polecenia platformy .NET Core, które mogą mieć wpływ na wynikowy układ lub pakiety.

## <a name="disk-layout"></a>Układ dysku

Po zainstalowaniu programu .NET Core składa się z kilku składników, które zostały wdrożone w systemie plików:

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** Host (znany również jako "muxer") ma dwie odrębne role: Aktywuj środowisko uruchomieniowe, aby uruchomić aplikację, i aktywuj zestaw SDK, aby wysłać do niego polecenia. Host jest natywnym plikiem wykonywalnym`dotnet.exe`().

W przypadku jednego hosta większość innych składników znajduje się w katalogach z wersjami (2, 3, 5, 6). Oznacza to, że w systemie może być dostępnych wiele wersji, ponieważ są one instalowane obok siebie.

- (2) **host/FXR/\<FXR wersja >** zawiera logikę rozpoznawania architektury używaną przez hosta. Host używa najnowszej hostfxr, która jest zainstalowana. Hostfxr jest odpowiedzialny za wybór odpowiedniego środowiska uruchomieniowego podczas wykonywania aplikacji platformy .NET Core. Na przykład aplikacja skompilowana dla programu .NET Core 2.0.0 używa środowiska uruchomieniowego 2.0.5, gdy jest ono dostępne. Podobnie hostfxr wybiera odpowiedni zestaw SDK podczas opracowywania.

- (3) **wersja zestawu\<SDK/zestawu SDK >** zestaw SDK (znany również jako "Narzędzie") to zestaw narzędzi zarządzanych, które są używane do pisania i kompilowania bibliotek i aplikacji platformy .NET Core. Zestaw SDK zawiera interfejs wiersza polecenia (CLI) platformy .NET Core, kompilator języków zarządzanych, program MSBuild oraz skojarzone zadania kompilacji i cele, narzędzia NuGet, nowe szablony projektów itd.

- (4) **zestaw SDK/NuGetFallbackFolder** zawiera pamięć podręczną pakietów NuGet używanych przez zestaw SDK podczas operacji przywracania, na przykład w przypadku `dotnet restore` uruchamiania `dotnet build /t:Restore`systemu lub. Ten folder jest używany tylko przed platformą .NET Core 3,0. Nie można go skompilować ze źródła, ponieważ zawiera wstępnie skompilowane zasoby binarne z `nuget.org`.

Folder **udostępniony** zawiera struktury. Struktura udostępniona udostępnia zestaw bibliotek w centralnej lokalizacji, dzięki czemu mogą one być używane przez różne aplikacje.

- (5) **Shared/Microsoft. Core. app/\<Runtime wersja >** Ta platforma zawiera środowisko uruchomieniowe platformy .NET Core i obsługuje biblioteki zarządzane.

- (6) **Shared/Microsoft. AspNetCore. { Aplikacja, wszystkie}/\<aspnetcore wersja >** zawiera biblioteki ASP.NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.App` programu są opracowywane i obsługiwane w ramach projektu .NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.All` stanowią nadzbiór, który zawiera również biblioteki innych firm.

- (7) **udostępniona/Microsoft. Desktop. app/\<aplikacja klasyczna >** zawiera biblioteki pulpitu systemu Windows. Nie jest to uwzględnione na platformach innych niż Windows.

- (8) **License. txt, ThirdPartyNotices. txt** to licencja platformy .NET Core i licencje bibliotek innych firm używane odpowiednio w programie .NET Core.

- (9, 10) **dotnet. 1. gz, dotnet** `dotnet.1.gz` jest stroną ręczną dotnet. `dotnet`jest link symboliczny hosta dotnet (1). Te pliki są instalowane w dobrze znanych lokalizacjach na potrzeby integracji systemu.

- (11, 12) **Microsoft. servicecore. app. ref, Microsoft. AspNetCore. app. ref** opisują odpowiednio interfejs API `x.y` wersji programu .NET Core i ASP.NET Core. Te pakiety są używane podczas kompilowania dla tych wersji docelowych.

- (13) **Microsoft. servicecore. app. host.\< > RID** zawiera natywny plik binarny `rid`dla platformy. Ten plik binarny jest szablonem podczas kompilowania aplikacji .NET Core do natywnego pliku binarnego dla tej platformy.

- (14) **Microsoft. WindowsDesktop. app. ref** — zawiera opis interfejsu `x.y` API wersji aplikacji klasycznych systemu Windows. Te pliki są używane podczas kompilowania dla tego obiektu docelowego. Nie jest to obsługiwane na platformach innych niż Windows.

- (15) **Standard. Library. ref** — opisuje standardowy `x.y` interfejs API. Te pliki są używane podczas kompilowania dla tego obiektu docelowego.

- (16) **/etc/dotnet/install_location** to plik zawierający pełną ścieżkę do folderu, który zawiera dane `dotnet` binarne hosta. Ścieżka może kończyć się znakiem nowego wiersza. Nie trzeba dodawać tego pliku, gdy katalog główny to `/usr/share/dotnet`.

- **Szablony** (17) zawierają szablony używane przez zestaw SDK. Na przykład w `dotnet new` tym miejscu znajduje się szablon projektu.

## <a name="recommended-packages"></a>Zalecane pakiety

Wersja programu .NET Core jest oparta na numerach wersji `[major].[minor]` składnika środowiska uruchomieniowego.
Wersja zestawu SDK używa tych samych `[major].[minor]` i ma niezależną `[patch]` , która łączy semantykę funkcji i poprawki dla zestawu SDK.
Na przykład: Wersja zestawu SDK 2.2.302 to druga wersja poprawki zestawu SDK, która obsługuje środowisko uruchomieniowe 2,2. Aby uzyskać więcej informacji o działaniu wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).

Niektóre pakiety zawierają część numeru wersji w nazwie. Pozwala to na zainstalowanie określonej wersji.
Reszta wersji nie jest uwzględniona w nazwie wersji. Dzięki temu Menedżer pakietów systemu operacyjnego może aktualizować pakiety (na przykład automatycznie instalując poprawki zabezpieczeń). Obsługiwane menedżery pakietów są specyficzne dla systemu Linux.

Poniżej przedstawiono listę zalecanych pakietów:

- `dotnet-sdk-[major].[minor]`-Instaluje najnowszy zestaw SDK dla określonego środowiska uruchomieniowego
  - **Wersja:** \<wersja środowiska uruchomieniowego >
  - **Przykład:** dotnet-sdk-2,1
  - **Wyświetlana** (3), (4)
  - **Zależności:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`

- `aspnetcore-runtime-[major].[minor]`-Instaluje określone środowisko uruchomieniowe ASP.NET Core
  - **Wersja:** \<wersja środowiska uruchomieniowego aspnetcore >
  - **Przykład:** aspnetcore-runtime-2,1
  - **Wyświetlana** ust
  - **Zależności:** `dotnet-runtime-[major].[minor]`

- `dotnet-runtime-deps-[major].[minor]` _(Opcjonalnie)_ — instaluje zależności do uruchamiania aplikacji samodzielnych
  - **Wersja:** \<wersja środowiska uruchomieniowego >
  - **Przykład:** dotnet-Runtime-deps-2,1
  - **Zależności:** _dystrybucji określone zależności_

- `dotnet-runtime-[major].[minor]`-Instaluje określone środowisko uruchomieniowe
  - **Wersja:** \<wersja środowiska uruchomieniowego >
  - **Przykład:** dotnet-runtime-2,1
  - **Wyświetlana** (5)
  - **Zależności:** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`

- `dotnet-hostfxr`-zależność
  - **Wersja:** \<wersja środowiska uruchomieniowego >
  - **Przykład:** dotnet-hostfxr
  - **Wyświetlana** (2)
  - **Zależności:** `host:<runtime version>+`

- `dotnet-host`-zależność
  - **Wersja:** \<wersja środowiska uruchomieniowego >
  - **Przykład:** dotnet-Host
  - **Wyświetlana** (1), (8), (9), (10), (16)

- `dotnet-apphost-pack-[major].[minor]`-zależność
  - **Wersja:** \<wersja środowiska uruchomieniowego >
  - **Wyświetlana** trzynast

- `dotnet-targeting-pack-[major].[minor]`-Zezwala na nienajnowszy czas wykonywania
  - **Wersja:** \<wersja środowiska uruchomieniowego >
  - **Wyświetlana** dwunastomiesięcznych

- `aspnetcore-targeting-pack-[major].[minor]`-Zezwala na nienajnowszy czas wykonywania
  - **Wersja:** \<wersja środowiska uruchomieniowego aspnetcore >
  - **Wyświetlana** 11

- `netstandard-targeting-pack-[major].[minor]`-Umożliwia kierowanie do wersji standardowej
  - **Wersja:** \<wersja zestawu SDK >
  - **Wyświetlana** 15000

- `dotnet-templates-[major].[minor]`
  - **Wersja:** \<wersja zestawu SDK >
  - **Wyświetlana** 15000

Wymaga interpretacji _konkretnych zależności dystrybucji._ `dotnet-runtime-deps-[major].[minor]` Ponieważ system kompilacji dystrybucji może być w stanie automatycznie dziedziczyć, pakiet jest opcjonalny, w takim przypadku te zależności są dodawane bezpośrednio do `dotnet-runtime-[major].[minor]` pakietu.

Gdy zawartość pakietu znajduje się w folderze z uruchomioną wersją, nazwa `[major].[minor]` pakietu jest zgodna z nazwą folderu z wersją. Wszystkie pakiety, z wyjątkiem programu `netstandard-targeting-pack-[major].[minor]`, są również zgodne z wersją .NET Core.

Zależności między pakietami powinny mieć wartość _równą lub większą niż_ wymaganie wersji. Na przykład `dotnet-sdk-2.2:2.2.401` wymaga `aspnetcore-runtime-2.2 >= 2.2.6`. Dzięki temu użytkownik może uaktualnić instalację za pośrednictwem pakietu głównego (np. `dnf update dotnet-sdk-2.2`).

Większość dystrybucji wymaga, aby wszystkie artefakty zostały skompilowane ze źródła. Ma to wpływ na pakiety:

- Bibliotek innych firm w obszarze `shared/Microsoft.AspNetCore.All` nie można łatwo skompilować ze źródła. Ten folder zostanie pominięty z `aspnetcore-runtime` pakietu.

- Jest wypełniany przy użyciu artefaktów binarnych z `nuget.org`. `NuGetFallbackFolder` Powinna pozostać pusta.

Wiele `dotnet-sdk` pakietów może dostarczyć te same pliki `NuGetFallbackFolder`dla. Aby uniknąć problemów z menedżerem pakietów, te pliki powinny być identyczne (suma kontrolna, Data modyfikacji itd.).

## <a name="building-packages"></a>Kompilowanie pakietów

Repozytorium [dotnet/Source-Build](https://github.com/dotnet/source-build) zawiera instrukcje dotyczące sposobu tworzenia źródłowej plik tar zestaw .NET Core SDK i wszystkich jego składników. Dane wyjściowe repozytorium Build source są zgodne z układem opisanym w pierwszej sekcji tego artykułu.
