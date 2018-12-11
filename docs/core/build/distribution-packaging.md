---
title: Tworzenie pakietów dystrybucji platformy .NET core
description: Dowiedz się, jak spakować, nazwa i wersja platformy .NET Core w celu dystrybucji.
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: be5767351ad1cdac15c73f718f67a0d120cf65b0
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170421"
---
# <a name="net-core-distribution-packaging"></a>Tworzenie pakietów dystrybucji platformy .NET core

.NET Core staje się dostępny na platformach coraz większe, jest przydatne informacje na temat pakietu, nazwę i wersję go. W ten sposób maintainers pakietu można zapewnić spójne środowisko niezależnie od tego, gdzie użytkownicy zdecydować się na uruchomienie platformy .NET.

## <a name="disk-layout"></a>Układ dysku

Po zainstalowaniu platformy .NET Core zawiera kilka składników, które są layed się w następujący sposób w systemie plików:

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

- (1) **dotnet** hosta (znany także jako "muxer") ma dwie różne role: Aktywacja środowiska uruchomieniowego, aby uruchomić aplikację i Aktywuj zestaw SDK do wysyłania poleceń do niego. Host jest natywny plik wykonywalny (`dotnet.exe`).

W trakcie jednego hosta większości innych składników znajdują się w określonej wersji katalogów (kwas 2,3,5,6). Oznacza to, że wiele wersji może być obecny w systemie, ponieważ są one zainstalowane side-by-side.

- (2) **hosta/fxr/\<wersji fxr >** zawiera logikę rozpoznawania framework używany przez hosta. Host używa najnowszej hostfxr, który jest zainstalowany. Hostfxr jest odpowiedzialny za wybranie odpowiedniego środowiska uruchomieniowego, podczas wykonywania aplikacji .NET Core. Na przykład aplikacja skompilowana dla platformy .NET Core 2.0.0, zostanie użyta 2.0.5 środowiska uruchomieniowego, gdy będzie ona dostępna. Podobnie hostfxr wybiera odpowiedni zestaw SDK podczas programowania.

- (3) **sdk /\<wersja zestawu sdk >** zestaw SDK (znany także jako "narzędzia") to zestaw funkcji wspomagających zarządzanych, które mogą służyć do zapisywania i tworzenia biblioteki .NET Core i aplikacji. Zestaw SDK zawiera nowe szablony projektów interfejsu wiersza polecenia, Roslyn kompilatora, MSBuild i skojarzone zadania kompilacji i elementy docelowe, NuGet, itp.

- (4) **sdk/NuGetFallbackFolder** zawiera pamięć podręczną pakietów NuGet, używane przez zestaw SDK podczas `dotnet restore` kroku.

**Udostępnionego** folder zawiera struktury. Udostępnione framework zawiera zestaw bibliotek w centralnej lokalizacji, dzięki czemu może być używany przez różne aplikacje.

- (5) **shared/Microsoft.NETCore.App/\<wersji środowiska uruchomieniowego >** ta struktura zawiera środowisko uruchomieniowe platformy .NET Core i obsługa bibliotek zarządzanych.

- (6,7) **shared/Microsoft.AspNetCore. { Aplikacja, wszystkie} /\<wersji aspnetcore >** zawiera biblioteki ASP.NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.App` opracowany i jest obsługiwany w ramach projektu .NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.All` jest nadzbiorem, co obejmuje również 3 bibliotek innych firm.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** platformy .NET Core licencji i licencji bibliotek innych firm używane w programie .NET Core.

- (9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` jest stroną man dotnet. `dotnet` jest Link symboliczny do dotnet host(1). Te pliki są instalowane w lokalizacjach dobrze znanych dla integracji systemów.

## <a name="recommended-packages"></a>Zalecane pakiety

Przechowywanie wersji platformy .NET core opiera się na składnika środowiska wykonawczego `[major].[minor]` numerów wersji.
Wersja zestawu SDK używa tych samych `[major].[minor]` i ma niezależny `[patch]` której łączy semantykę funkcji i poprawek dla zestawu SDK.
Na przykład: Zestaw SDK w wersji 2.2.302 2nd wydaniu poprawek w wersji 3 funkcji zestawu SDK, który obsługuje środowisko wykonawcze 2,2.

Pakiety między innymi część numeru wersji w ich imieniu. Dzięki temu użytkownik końcowy zainstalować określoną wersję.
W pozostałej części wersji nie są objęte nazwą wersji. Dzięki temu pakietu systemu operacyjnego Menedżer aktualizację pakietów (np. automatyczne instalowanie zabezpieczeń poprawki).

Poniższych tabelach przedstawiono zalecane pakiety.

| Nazwa                                    | Przykład                | Przypadek użycia: Zainstaluj...           | Zawiera           | Zależności                                   | Wersja            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Najnowszy zestaw sdk dla środowiska uruchomieniowego główne    |                    | dotnet-sdk-[major].[latestminor]               | \<Wersja zestawu SDK >     |
| dotnet-sdk-[major].[minor]              | dotnet-sdk-2.1         | Najnowszy zestaw sdk dla określonego środowiska uruchomieniowego |                    | DotNet - sdk-[główna]. [pomocnicza]. [najnowszy zestaw sdk feat] xx | \<Wersja zestawu SDK >     |
| DotNet - sdk-[główna]. [pomocnicza]. xx [sdk feat] | dotnet-sdk-2.1.3xx     | Wydawanie funkcji określonego zestawu sdk    | (3),(4)            | aspnetcore-runtime-[major].[minor]             | \<Wersja zestawu SDK >     |
| aspnetcore-runtime-[major].[minor]      | aspnetcore-runtime-2.1 | Określonego środowiska uruchomieniowego platformy ASP.NET Core   | (6),[(7)]          | dotnet-runtime-[major].[minor]                 | \<wersja środowiska uruchomieniowego > |
| dotnet-runtime-[major].[minor]          | dotnet-runtime-2.1     | Określonego środowiska uruchomieniowego                | (5)                | host-fxr:\<runtime version>+                   | \<wersja środowiska uruchomieniowego > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _Zależności_                    | (2)                | Host:\<wersji środowiska uruchomieniowego > +                       | \<wersja środowiska uruchomieniowego > |
| dotnet-host                             | dotnet-host            | _Zależności_                    | (1),(8),(9),(10)   |                                                | \<wersja środowiska uruchomieniowego > |

Większości dystrybucji wymagają wszystkich artefaktów, które ma zostać utworzony ze źródła. Ma pewne wpływ na pakiety:

- 3 bibliotek innych firm pod `shared/Microsoft.AspNetCore.All` nie można łatwo utworzyć ze źródła. Aby ten folder jest pomijane w `aspnetcore-runtime` pakietu.

- `NuGetFallbackFolder` Jest wypełniana przy użyciu artefaktów binarnych z `nuget.org`. Powinna pozostać pusta.

Wiele `dotnet-sdk` pakietów może dostarczyć tych samych plików dla `NuGetFallbackFolder`. Aby uniknąć problemów przy użyciu Menedżera pakietów, pliki te powinny być identyczne (sumy kontrolnej, Data modyfikacji,...).

#### <a name="preview-versions"></a>Wersje (wersja zapoznawcza)

Pakiet maintainers może zdecydować o zapewniają wersje zapoznawcze udostępnionej platformy i zestaw SDK. Wersje zapoznawcze mogą podać przy użyciu `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]`, `dotnet-runtime-[major].[minor]` pakietów. Dla wersji zapoznawczych główna wersja pakietu musi być równa zero. W ten sposób ostatecznej wersji zostanie zainstalowany jako uaktualnienie pakietu.

#### <a name="patch-packages"></a>Pakiety poprawek

Ponieważ wersję poprawki pakietów może spowodować istotną zmianę, Element utrzymujący pakietu może wystąpić potrzeba zapewnienia _patch pakietów_. Te pakiety umożliwia zainstalowanie wersji określona poprawka, która nie zostanie automatycznie uaktualniona. Pakiety Patch powinny można używać tylko w rzadkich przypadkach, jak nie zostaną uaktualnione za pomocą (zabezpieczenia) poprawki.

W poniższej tabeli przedstawiono zalecane pakiety i **patch pakietów**.

| Nazwa                                           | Przykład                  | Zawiera         | Zależności                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | DotNet - sdk-[główna]. [najnowszy zestaw sdk pomocnicza]                     |
| dotnet-sdk-[major].[minor]                     | dotnet-sdk-2.1           |                  | DotNet - sdk-[główna]. [pomocnicza]. [najnowszy zestaw sdk feat] xx            |
| DotNet - sdk-[główna]. [pomocnicza]. xx [sdk feat]        | dotnet-sdk-2.1.3xx       |                  | DotNet - sdk-[główna]. [pomocnicza]. [najnowszą poprawkę sdk]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3),(4)          | aspnetcore — środowisko uruchomieniowe — [główna]. [pomocnicza]. [poprawki zestawu sdk środowiska wykonawczego]    |
| aspnetcore-runtime-[major].[minor]             | aspnetcore-runtime-2.1   |                  | aspnetcore — środowisko uruchomieniowe — [główna]. [pomocnicza]. [najnowszą poprawkę środowiska wykonawczego] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore-runtime-2.1.0 | (6),[(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| dotnet-runtime-[major].[minor]                 | dotnet-runtime-2.1       |                  | DotNet — środowisko uruchomieniowe — [główna]. [pomocnicza]. [najnowszą poprawkę środowiska wykonawczego]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | (5)              | host-fxr:\<runtime version>+                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | Host:\<wersji środowiska uruchomieniowego > +                                  |
| dotnet-host                                    | dotnet-host              | (1),(8),(9),(10) |                                                           |

Alternatywą do korzystania z pakietów poprawki jest _przypinanie_ pakietów do określonej wersji przy użyciu Menedżera pakietów. Aby uniknąć wpływu na innych użytkowników/aplikacji, takich aplikacji można skompilować i wdrożyć w kontenerze.

## <a name="building-packages"></a>Tworzenie pakietów

[Źródła dotnet-build](https://github.com/dotnet/source-build) repozytorium zawiera instrukcje dotyczące sposobu tworzenia pliku tar źródła programu .NET Core SDK wraz ze wszystkimi składnikami. Dane wyjściowe repozytorium źródła kompilacji odpowiada układ opisane w pierwszej sekcji tego artykułu.
