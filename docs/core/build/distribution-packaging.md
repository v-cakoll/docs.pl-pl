---
title: OPAKOWYWANIE dystrybucji .NET core
description: Dowiedz się, jak pakietu, nazwę i wersję platformy .NET Core do dystrybucji.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 63ff542dbde30f8ff72a2d257a16a18b2a9e71b8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-distribution-packaging"></a>OPAKOWYWANIE dystrybucji .NET core

W miarę wprowadzania na coraz więcej platformy .NET Core jest przydatne informacje na temat pakietu, nazwę i wersję go. W ten sposób maintainers pakietu pomoże zapewnić spójne środowisko niezależnie od tego, w której użytkownicy muszą wybrać do uruchomienia .NET.

## <a name="disk-layout"></a>Układ dysku

Podczas instalowania platformy .NET Core składa się z kilku składników, które są layed się w następujący sposób w systemie plików:

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

- (1) **dotnet** host (znanej także jako "muxer") ma dwa różne role: aktywować runtime, aby uruchomić aplikację i Aktywuj zestaw SDK, aby wysłać do niego poleceń. Host jest natywny plik wykonywalny (`dotnet.exe`).

W trakcie jednego hosta, większość innych składników znajdują się w określonej wersji katalogów (kwas 2,3,5,6). Te oznacza wiele wersji mogą być obecne w systemie, ponieważ są one zainstalowane obok siebie.

- (2) **hosta/fxr/\<wersji fxr >** zawiera logikę rozpoznawania framework używany przez hosta. Host używa najnowszych hostfxr, który jest zainstalowany. Hostfxr jest odpowiedzialny za wybranie odpowiedniego środowiska uruchomieniowego podczas wykonywania aplikacji .NET Core. Na przykład aplikacji skompilowany dla platformy .NET Core 2.0.0, zostanie użyta 2.0.5 środowiska uruchomieniowego, gdy jest ona dostępna. Podobnie hostfxr wybiera odpowiednią zestawu SDK podczas tworzenia.

- (3) **sdk /\<zestawu sdk w wersji >** SDK (znanej także jako "narzędzia") to zestaw narzędzi zarządzanych, które mogą służyć do zapisu i tworzenia bibliotek .NET Core i aplikacji. Zestaw SDK zawiera nowe szablony projektu interfejsu wiersza polecenia, Roslyn kompilatora, MSBuild i zadań kompilacji i obiekty docelowe, NuGet, itp.

- (4) **sdk/NuGetFallbackFolder** zawiera pamięć podręczną pakietów NuGet używana przez zestaw SDK podczas `dotnet restore` kroku.

**Udostępnionego** folder zawiera struktury. Udostępniony framework zawiera zestaw bibliotek w centralnej lokalizacji, dzięki mogą być używane przez różne aplikacje.

- (5) **shared/Microsoft.NETCore.App/\<wersja środowiska uruchomieniowego >** ta struktura zawiera środowisko uruchomieniowe .NET Core i obsługa bibliotek zarządzanych.

- (6,7) **shared/Microsoft.AspNetCore. { Aplikacja, wszystkie} /\<wersji aspnetcore >** zawiera biblioteki platformy ASP.NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.App` opracowany i jest obsługiwany w ramach projektu platformy .NET Core. Biblioteki w obszarze `Microsoft.AspNetCore.All` jest nadzbiorem zawierającą 3 bibliotek strony.

- 8 **LICENSE.txt,ThirdPartyNotices.txt** .NET Core licencji i licencji bibliotek innych firm używane w .NET Core.

- (9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` jest strona man dotnet. `dotnet` jest łącza symbolicznego do dotnet host(1). Pliki te są instalowane w lokalizacjach dobrze znanych integracji systemu.

## <a name="recommended-packages"></a>Zalecane pakiety

Przechowywanie wersji platformy .NET core opiera się na składnika środowiska wykonawczego `[major].[minor]` numerów wersji.
Wersja zestawu SDK wykorzystuje takie same `[major].[minor]` i ma niezależnego `[patch]` które łączy semantykę funkcji i poprawek dla zestawu SDK.
Na przykład: zestaw SDK w wersji 2.2.302 2 wersji poprawki w wersji 3 funkcji zestawu SDK, obsługujący 2,2 środowiska wykonawczego.

Pakiety między innymi część numeru wersji w ich imieniu. Dzięki temu użytkownika końcowego zainstalować określoną wersję.
W pozostałej części wersji nie jest uwzględniony w nazwie wersji. Dzięki temu pakietu systemu operacyjnego manager ma zaktualizować pakiety (np. automatyczne instalowanie zabezpieczeń poprawki błędów).

Następujące tabele są wyświetlane zalecane pakiety.

| Nazwa                                    | Przykład                | Przypadek użycia: Zainstaluj...           | Zawiera           | Zależności                                   | Wersja            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Najnowszej wersji zestawu sdk dla środowiska uruchomieniowego głównych    |                    | dotnet-sdk-[major].[latestminor]               | \<Wersja zestawu SDK >     |
| dotnet-sdk-[major].[minor]              | dotnet-sdk-2.1         | Najnowszej wersji zestawu sdk dla określonego środowiska wykonawczego |                    | DotNet - sdk-[główna]. [pomocnicza]. [najnowszy zestaw sdk feat] xx | \<Wersja zestawu SDK >     |
| DotNet - sdk-[główna]. [pomocnicza]. xx [sdk feat] | dotnet-sdk-2.1.3xx     | Wersja funkcji określonego zestawu sdk    | (3),(4)            | aspnetcore-runtime-[major].[minor]             | \<Wersja zestawu SDK >     |
| aspnetcore-runtime-[major].[minor]      | aspnetcore-runtime-2.1 | Określone platformy ASP.NET Core środowiska wykonawczego   | (6),[(7)]          | dotnet-runtime-[major].[minor]                 | \<wersja środowiska uruchomieniowego > |
| dotnet-runtime-[major].[minor]          | dotnet-runtime-2.1     | Określonego środowiska wykonawczego                | (5)                | host-fxr:\<runtime version>+                   | \<wersja środowiska uruchomieniowego > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _zależności_                    | (2)                | Host:\<wersja środowiska uruchomieniowego > +                       | \<wersja środowiska uruchomieniowego > |
| dotnet-host                             | dotnet-host            | _zależności_                    | (1),(8),(9),(10)   |                                                | \<wersja środowiska uruchomieniowego > |

Większości dystrybucji wymagają wszystkie artefakty ma zostać utworzony ze źródła. Ma pewien wpływ na pakiety:

- 3 bibliotek firmy w obszarze `shared/Microsoft.AspNetCore.All` nie można łatwo utworzyć ze źródła. Dlatego ten folder został pominięty `aspnetcore-runtime` pakietu.

- `NuGetFallbackFolder` Jest wypełniana przy użyciu binarnej artefaktów z `nuget.org`. Powinna pozostać pusta.

Wiele `dotnet-sdk` pakiety może udostępnić tych samych plików dla `NuGetFallbackFolder`. Aby uniknąć problemów z Menedżera pakietów, pliki te powinny być identyczne (sumy kontrolnej, daty modyfikacji,...).

#### <a name="preview-versions"></a>Wersji Preview

Maintainers pakietu może zadecydować o Podaj wersji zapoznawczych udostępnionego framework i zestawu SDK. Wersje zapoznawcze mogą być dostarczane za pomocą `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]`, `dotnet-runtime-[major].[minor]` pakietów. Dla wersji preview główna wersja pakietu musi mieć ustawioną wartość zero. W ten sposób ostateczną wersją zostanie zainstalowany jako uaktualnienie pakietu.

#### <a name="patch-packages"></a>Pakiety poprawek

Ponieważ wersja poprawki pakiety może spowodować istotne zmiany, Element utrzymujący pakietu może być zapewnienie _poprawka pakiety_. Te pakiety umożliwia zainstalowanie wersji określonych patch, który nie zostanie automatycznie uaktualniona. Pakiety poprawek należy używać w rzadkich przypadkach tylko, ponieważ nie będą poprawki uaktualnionym z (zabezpieczenia).

W poniższej tabeli przedstawiono zalecane pakiety i **poprawka pakiety**.

| Nazwa                                           | Przykład                  | Zawiera         | Zależności                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | DotNet - sdk-[główna]. [najnowszej wersji zestawu sdk pomocnicza]                     |
| dotnet-sdk-[major].[minor]                     | dotnet-sdk-2.1           |                  | DotNet - sdk-[główna]. [pomocnicza]. [najnowszy zestaw sdk feat] xx            |
| DotNet - sdk-[główna]. [pomocnicza]. xx [sdk feat]        | dotnet-sdk-2.1.3xx       |                  | DotNet - sdk-[główna]. [pomocnicza]. [najnowsze poprawki sdk]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3),(4)          | aspnetcore — środowisko uruchomieniowe — [główna]. [pomocnicza]. [poprawka zestawu sdk środowiska wykonawczego]    |
| aspnetcore-runtime-[major].[minor]             | aspnetcore-runtime-2.1   |                  | aspnetcore — środowisko uruchomieniowe — [główna]. [pomocnicza]. [najnowsze poprawki środowiska wykonawczego] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore-runtime-2.1.0 | (6),[(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| dotnet-runtime-[major].[minor]                 | dotnet-runtime-2.1       |                  | DotNet — środowisko uruchomieniowe — [główna]. [pomocnicza]. [najnowsze poprawki środowiska wykonawczego]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | (5)              | host-fxr:\<runtime version>+                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | Host:\<wersja środowiska uruchomieniowego > +                                  |
| dotnet-host                                    | dotnet-host              | (1),(8),(9),(10) |                                                           |

Jest to alternatywa dla użycia pakietów poprawki _przypinanie_ pakietów do określonej wersji za pomocą Menedżera pakietów. Aby uniknąć wpływu na inne aplikacje/użytkownicy, można wbudowane i wdrażać w kontenerze takich aplikacji.

## <a name="building-packages"></a>Tworzenie pakietów

https://github.com/dotnet/source-build Repozytorium zawiera instrukcje dotyczące sposobu konstruowania tarball źródła .NET Core SDK i wszystkich jego składników. Dane wyjściowe repozytorium źródło kompilacji odpowiada układu opisane w pierwszej sekcji tego artykułu.