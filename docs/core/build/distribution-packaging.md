---
title: Tworzenie pakietów dystrybucji platformy .NET Core
description: Dowiedz się, jak spakować, nazwać i wersja .NET Core do dystrybucji.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: 5d23147c8a38fbeea9e88c0a18e1f220e854fec1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105413"
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
└── shared
    ├── Microsoft.NETCore.App
    │   └── <runtime version>    (5)
    └── Microsoft.AspNetCore.App
        └── <aspnetcore version> (6)
    └── Microsoft.AspNetCore.All
        └── <aspnetcore version> (7)
/
├─usr/share/man/man1
│       └── dotnet.1.gz          (9)
└─usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** Host (znany również jako "muxer") ma dwie odrębne role: Aktywuj środowisko uruchomieniowe, aby uruchomić aplikację, i aktywuj zestaw SDK, aby wysłać do niego polecenia. Host jest natywnym plikiem wykonywalnym`dotnet.exe`().

W przypadku jednego hosta większość innych składników znajduje się w katalogach z wersjami (2, 3, 5, 6). Oznacza to, że w systemie może być dostępnych wiele wersji, ponieważ są one instalowane obok siebie.

- (2) **host/FXR/\<FXR wersja >** zawiera logikę rozpoznawania architektury używaną przez hosta. Host używa najnowszej hostfxr, która jest zainstalowana. Hostfxr jest odpowiedzialny za wybór odpowiedniego środowiska uruchomieniowego podczas wykonywania aplikacji platformy .NET Core. Na przykład aplikacja skompilowana dla programu .NET Core 2.0.0 używa środowiska uruchomieniowego 2.0.5, gdy jest ono dostępne. Podobnie hostfxr wybiera odpowiedni zestaw SDK podczas opracowywania.

- (3) **wersja zestawu\<SDK/zestawu SDK >** zestaw SDK (znany również jako "Narzędzie") to zestaw narzędzi zarządzanych, które są używane do pisania i kompilowania bibliotek i aplikacji platformy .NET Core. Zestaw SDK zawiera interfejs wiersza polecenia (CLI) platformy .NET Core, kompilator języków zarządzanych, program MSBuild oraz skojarzone zadania kompilacji i cele, narzędzia NuGet, nowe szablony projektów itd.

- (4) **zestaw SDK/NuGetFallbackFolder** zawiera pamięć podręczną pakietów NuGet używanych przez zestaw SDK podczas operacji przywracania, na przykład w przypadku `dotnet restore` uruchamiania `dotnet build /t:Restore`systemu lub.

Folder **udostępniony** zawiera struktury. Struktura udostępniona udostępnia zestaw bibliotek w centralnej lokalizacji, dzięki czemu mogą one być używane przez różne aplikacje.

- (5) **Shared/Microsoft. Core. app/\<Runtime wersja >** Ta platforma zawiera środowisko uruchomieniowe platformy .NET Core i obsługuje biblioteki zarządzane.

- (6, 7) **Shared/Microsoft. AspNetCore. { Aplikacja, wszystkie}/\<aspnetcore wersja >** zawiera biblioteki ASP.NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.App` programu są opracowywane i obsługiwane w ramach projektu .NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.All` stanowią nadzbiór, który zawiera również biblioteki innych firm.

- (8) **License. txt, ThirdPartyNotices. txt** to licencja platformy .NET Core i licencje bibliotek innych firm używane odpowiednio w programie .NET Core.

- (9, 10) **dotnet. 1. gz, dotnet** `dotnet.1.gz` jest stroną ręczną dotnet. `dotnet`jest link symboliczny hosta dotnet (1). Te pliki są instalowane w dobrze znanych lokalizacjach na potrzeby integracji systemu.

## <a name="recommended-packages"></a>Zalecane pakiety

Wersja programu .NET Core jest oparta na numerach wersji `[major].[minor]` składnika środowiska uruchomieniowego.
Wersja zestawu SDK używa tych samych `[major].[minor]` i ma niezależną `[patch]` , która łączy semantykę funkcji i poprawki dla zestawu SDK.
Na przykład: Wersja zestawu SDK 2.2.302 to druga wersja poprawki zestawu SDK, która obsługuje środowisko uruchomieniowe 2,2. Aby uzyskać więcej informacji o działaniu wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).

Niektóre pakiety zawierają część numeru wersji w nazwie. Pozwala to na zainstalowanie określonej wersji.
Reszta wersji nie jest uwzględniona w nazwie wersji. Dzięki temu Menedżer pakietów systemu operacyjnego może aktualizować pakiety (na przykład automatycznie instalując poprawki zabezpieczeń). Obsługiwane menedżery pakietów są specyficzne dla systemu Linux.

W poniższej tabeli przedstawiono zalecane pakiety:

| Nazwa                                    | Przykład                | Przypadek użycia: Zainstaluj...           | Zawiera           | Zależności                                   | Wersja            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Najnowsza wersja zestawu SDK dla środowiska uruchomieniowego    |                    | dotnet-sdk-[major].[latestminor]               | \<wersja zestawu SDK >     |
| dotnet-sdk-[major].[minor]              | dotnet-sdk-2.1         | Najnowszy zestaw SDK dla określonego środowiska uruchomieniowego |                    | dotnet-SDK-[główna]. [pomocnicza]. [najnowszy zestaw SDK feat] XX | \<wersja zestawu SDK >     |
| dotnet-sdk-[major].[minor].[sdk feat]xx | dotnet-sdk-2.1.3xx     | Określona wersja funkcji zestawu SDK    | (3), (4)            | aspnetcore-runtime-[major].[minor]             | \<wersja zestawu SDK >     |
| aspnetcore-runtime-[major].[minor]      | aspnetcore-runtime-2.1 | Określony ASP.NET Core środowiska uruchomieniowego   | (6),[(7)]          | dotnet-runtime-[major].[minor]                 | \<wersja środowiska uruchomieniowego > |
| dotnet-runtime-[major].[minor]          | dotnet-runtime-2.1     | Określone środowisko uruchomieniowe                | (5)                | host-fxr:\<runtime version>+                   | \<wersja środowiska uruchomieniowego > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _zależności_                    | (2)                | Host:\<wersja środowiska uruchomieniowego > +                       | \<wersja środowiska uruchomieniowego > |
| dotnet-host                             | dotnet-host            | _zależności_                    | (1), (8), (9), (10)   |                                                | \<wersja środowiska uruchomieniowego > |

Większość dystrybucji wymaga, aby wszystkie artefakty zostały skompilowane ze źródła. Ma to wpływ na pakiety:

- Bibliotek innych firm w obszarze `shared/Microsoft.AspNetCore.All` nie można łatwo skompilować ze źródła. Ten folder zostanie pominięty z `aspnetcore-runtime` pakietu.

- Jest wypełniany przy użyciu artefaktów binarnych z `nuget.org`. `NuGetFallbackFolder` Powinna pozostać pusta.

Wiele `dotnet-sdk` pakietów może dostarczyć te same pliki `NuGetFallbackFolder`dla. Aby uniknąć problemów z menedżerem pakietów, te pliki powinny być identyczne (suma kontrolna, Data modyfikacji itd.).

### <a name="preview-versions"></a>Wersje zapoznawcze

W celu udostępnienia wersji zapoznawczej udostępnionej struktury i zestawu SDK mogą oni podejmować decyzje. Wersje zapoznawcze mogą być dostarczane przy `dotnet-sdk-[major].[minor].[sdk feat]xx`użyciu `aspnetcore-runtime-[major].[minor]`pakietów, `dotnet-runtime-[major].[minor]` lub. W przypadku wersji zapoznawczych główna wersja pakietu musi mieć wartość zero. W ten sposób ostateczne wydanie zostanie zainstalowane jako uaktualnienie pakietu.

### <a name="patch-packages"></a>Pakiety poprawek

Ponieważ wersja poprawki pakietu może spowodować istotną zmianę, element utrzymujący pakietu może chcieć udostępnić _pakiety poprawek_. Te pakiety umożliwiają zainstalowanie określonej wersji poprawki, która nie jest automatycznie uaktualniana. Pakiety poprawek Używaj tylko w rzadkich przypadkach, ponieważ nie są one uaktualnione za pomocą poprawek (Security).

W poniższej tabeli przedstawiono zalecane pakiety i **pakiety poprawek**:

| Nazwa                                           | Przykład                  | Zawiera         | Zależności                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | dotnet-SDK-[główna]. [Najnowsza wersja pomocnicza zestawu SDK]                     |
| dotnet-sdk-[major].[minor]                     | dotnet-sdk-2.1           |                  | dotnet-SDK-[główna]. [pomocnicza]. [najnowszy zestaw SDK feat] XX            |
| dotnet-sdk-[major].[minor].[sdk feat]xx        | dotnet-sdk-2.1.3xx       |                  | dotnet-SDK-[główna]. [pomocnicza]. [Najnowsza poprawka zestawu SDK]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3), (4)          | aspnetcore — środowisko uruchomieniowe — [główna]. [pomocnicza]. [poprawka środowiska uruchomieniowego SDK]    |
| aspnetcore-runtime-[major].[minor]             | aspnetcore-runtime-2.1   |                  | aspnetcore — środowisko uruchomieniowe — [główna]. [pomocnicza]. [Najnowsza poprawka środowiska uruchomieniowego] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore-runtime-2.1.0 | (6),[(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| dotnet-runtime-[major].[minor]                 | dotnet-runtime-2.1       |                  | dotnet-Runtime-[główna]. [pomocnicza]. [Najnowsza poprawka środowiska uruchomieniowego]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | (5)              | host-fxr:\<runtime version>+                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | Host:\<wersja środowiska uruchomieniowego > +                                  |
| dotnet-host                                    | dotnet-host              | (1), (8), (9), (10) |                                                           |

Alternatywą dla korzystania z pakietów poprawek jest Przypinanie pakietów do określonej wersji za pomocą Menedżera pakietów. Aby uniknąć wpływu na inne aplikacje/użytkowników, takie aplikacje można skompilować i wdrożyć w kontenerze.

## <a name="building-packages"></a>Kompilowanie pakietów

Repozytorium [dotnet/Source-Build](https://github.com/dotnet/source-build) zawiera instrukcje dotyczące sposobu tworzenia źródłowej plik tar zestaw .NET Core SDK i wszystkich jego składników. Dane wyjściowe repozytorium Build source są zgodne z układem opisanym w pierwszej sekcji tego artykułu.
