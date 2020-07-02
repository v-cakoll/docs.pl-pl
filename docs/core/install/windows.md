---
title: Zainstaluj platformę .NET Core w systemie Windows
description: Dowiedz się więcej na temat wersji systemu Windows, na których można zainstalować program .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: e26494de7e9246b241cb965d8d735a781aab5478
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85804508"
---
# <a name="install-net-core-on-windows"></a>Zainstaluj platformę .NET Core w systemie Windows

> [!div class="op_single_selector"]
>
> - [Instalowanie w systemie Windows](windows.md)
> - [Instalowanie w systemie macOS](macos.md)
> - [Instalowanie w systemie Linux](linux.md)

W tym artykule dowiesz się, jak zainstalować platformę .NET Core w systemie Windows. Program .NET Core składa się z środowiska uruchomieniowego i zestawu SDK. Środowisko uruchomieniowe służy do uruchamiania aplikacji platformy .NET Core i może być dołączane do aplikacji. Zestaw SDK służy do tworzenia aplikacji i bibliotek platformy .NET Core. Środowisko uruchomieniowe platformy .NET Core jest zawsze instalowane z zestawem SDK.

Najnowsza wersja platformy .NET Core to 3,1.

[Pobierz program .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>Obsługiwane wersje

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core i wersje systemu Windows, w których są obsługiwane. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [systemu Windows osiągnie koniec cyklu życia](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

Daty końca usługi systemu Windows 10 są poddane segmentacji według wersji. W poniższej tabeli są brane pod uwagę tylko wersje **Home**, **Pro**, **Pro Education**i **Pro for Workstations** . Szczegółowe informacje znajdują się w [arkuszu faktów cyklu życia systemu Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) .

- ✔️ wskazuje, że wersja systemu Windows lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja systemu Windows lub .NET Core nie jest obsługiwana w tej wersji systemu Windows.
- Gdy zarówno wersja systemu Windows, jak i wersja programu .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| System operacyjny                      | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) |
|-----------------------------|---------------|---------------|----------------|
| ✔️ Windows 10, wersja 2004 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ Windows 10, wersja 1909 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ Windows 10, wersja 1903 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ Windows 10, wersja 1809 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ❌Windows 10, wersja 1803 | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌Windows 10, wersja 1709 | ❌2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌Windows 10, wersja 1703 | ❌2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌Windows 10, wersja 1607 | ❌2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌Windows 10, wersja 1511 | ❌2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌Windows 10, wersja 1507 | ❌2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |

## <a name="unsupported-releases"></a>Nieobsługiwane wersje

Następujące wersje programu .NET Core nie są ❌ już obsługiwane. Pliki do pobrania dla tych nadal są publikowane:

- 3.0
- 2.2
- 2.0

## <a name="runtime-information"></a>Informacje o środowisku uruchomieniowym

Środowisko uruchomieniowe służy do uruchamiania aplikacji utworzonych za pomocą platformy .NET Core. Gdy autor aplikacji publikuje aplikację, może ona obejmować środowisko uruchomieniowe wraz z ich aplikacjami. Jeśli nie obejmują środowiska uruchomieniowego, można zainstalować środowisko uruchomieniowe.

Istnieją trzy różne środowiska uruchomieniowe, które można zainstalować w systemie Windows:

*Środowisko uruchomieniowe ASP.NET Core*\
Uruchamia ASP.NET Core aplikacje. Zawiera środowisko uruchomieniowe platformy .NET Core.

*Środowisko uruchomieniowe pulpitu*\
Uruchamia platformy .NET Core WPF i .NET Core Windows Forms aplikacje klasyczne dla systemu Windows. Zawiera środowisko uruchomieniowe platformy .NET Core.

*Środowisko uruchomieniowe platformy .NET Core*\
To środowisko uruchomieniowe jest najprostszym środowiskiem uruchomieniowym i nie zawiera żadnego innego środowiska uruchomieniowego. Zdecydowanie zaleca się zainstalowanie środowiska *uruchomieniowego ASP.NET Core* i środowiska *uruchomieniowego Desktop* w celu uzyskania najlepszej zgodności z aplikacjami .NET Core.

[Pobierz środowisko uruchomieniowe programu .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>Informacje o zestawie SDK

Zestaw SDK służy do kompilowania i publikowania aplikacji i bibliotek platformy .NET Core. Instalowanie zestawu SDK obejmuje wszystkie trzy [środowiska uruchomieniowe](#runtime-information): ASP.NET Core, Desktop i .NET Core.

[Pobierz zestaw .NET Core SDK.](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a>Zależności

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3,1](#tab/netcore31)

W przypadku programu .NET Core 3,1 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> `+`Symbol reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 8.1                            | x64, x86        |
| Klient systemu Windows 10             | Wersja 1609 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Wersja 1803 +                  | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*Platforma .NET Core 3,0 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

W przypadku programu .NET Core 3,0 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> `+`Symbol reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 Z DODATKIEM SP1 +, 8,1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Wersja 1803 +                  | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2,2](#tab/netcore22)

*Platforma .NET Core 2,2 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

W przypadku programu .NET Core 2,2 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> `+`Symbol reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 Z DODATKIEM SP1 +, 8,1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 Z DODATKIEM SP1 +                   | x64, x86        |
| Nano Server                   | Wersja 1803 +                   | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

W przypadku programu .NET Core 2,1 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> `+`Symbol reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 Z DODATKIEM SP1 +, 8,1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 Z DODATKIEM SP1 +                   | x64, x86        |
| Nano Server                   | Wersja 1803 +                  | procesorów            |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a>Windows 7/Vista/8,1/Server 2008 R2/serwer 2012 R2

Jeśli instalujesz zestaw .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows, wymagane są dodatkowe zależności:

- ❌Windows 7 z dodatkiem SP1
- ❌Windows Vista z dodatkiem SP 2
- ✔️ Windows 8.1
- ✔️ Windows Server 2008 R2
- ✔️ Windows Server 2012 R2

Zainstaluj następujące elementy:

- [Microsoft Visual C++ 2015 redystrybucyjnej aktualizacji 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [POPRAWKI KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Powyższe wymagania są również wymagane w przypadku wystąpienia jednego z następujących błędów:

> Nie można uruchomić programu, ponieważ na komputerze nie ma *api-ms-win-crt-runtime-l1-1-0.dll* . Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.
>
> \-oraz
>
> Nie można uruchomić programu, ponieważ na komputerze nie ma *api-ms-win-cor-timezone-l1-1-0.dll* . Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.
>
> \-oraz
>
> Znaleziono bibliotekę *hostfxr.dll* , ale ładowanie jej z *dysku C: \\ \<path_to_app> \\hostfxr.dll* nie powiodło się.

## <a name="install-with-powershell-automation"></a>Instalowanie przy użyciu programu PowerShell Automation

[Skrypty dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji ci i instalacji niezwiązanych z administratorami środowiska uruchomieniowego. Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1. Możesz wybrać określoną wersję, określając `Channel` przełącznik. Dołącz `Runtime` przełącznik, aby zainstalować środowisko uruchomieniowe. W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

Zainstaluj zestaw SDK, pomijając `-Runtime` przełącznik. `-Channel`Przełącznik jest ustawiany w tym przykładzie do `Current` , który instaluje najnowszą obsługiwaną wersję.

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a>Instalowanie za pomocą programu Visual Studio

Jeśli używasz programu Visual Studio do tworzenia aplikacji platformy .NET Core, w poniższej tabeli opisano minimalną wymaganą wersję programu Visual Studio opartą na docelowej wersji zestaw .NET Core SDK.

| Wersja zestaw .NET Core SDK | Wersja programu Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3,1                   | Program Visual Studio 2019 w wersji 16,4 lub nowszej. |
| 3.0                   | Program Visual Studio 2019 w wersji 16,3 lub nowszej. |
| 2.2                   | Program Visual Studio 2017 w wersji 15,9 lub nowszej. |
| 2.1                   | Program Visual Studio 2017 w wersji 15,7 lub nowszej. |

Jeśli masz już zainstalowany program Visual Studio, możesz sprawdzić swoją wersję, wykonując poniższe kroki.

01. Otwórz program Visual Studio.
01. Wybierz **Pomoc**dotyczącą  >  **Microsoft Visual Studio**.
01. Odczytaj numer wersji z okna dialogowego **informacje** .

Program Visual Studio może zainstalować najnowsze zestaw .NET Core SDK i środowisko uruchomieniowe.

- [Pobierz program Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Wybierz obciążenie

Podczas instalowania lub modyfikowania programu Visual Studio wybierz co najmniej jedno z następujących obciążeń, w zależności od rodzaju kompilowanej aplikacji:

- Obciążenie **Międzyplatformowe dla platformy .NET Core** w sekcji **inne zestawy narzędzi** .
- **ASP.NET i programowanie w sieci Web** w sekcji **chmury & sieci Web** .
- Obciążenie **Programowanie na platformie Azure** w sekcji **chmury & sieci Web** .
- Obciążenie **Programowanie aplikacji klasycznych na platformie .NET** znajduje się w sekcji **Desktop & Mobile** .

[![Windows Visual Studio 2019 z obciążeniem platformy .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Zainstaluj obok Visual Studio Code

Visual Studio Code to zaawansowany i lekki Edytor kodu źródłowego, który jest uruchamiany na pulpicie. Visual Studio Code jest dostępny dla systemów Windows, macOS i Linux.

Mimo że Visual Studio Code nie jest dołączony do zautomatyzowanego Instalatora .NET Core, takiego jak Visual Studio, Dodawanie obsługi .NET Core jest proste.

01. [Pobierz i zainstaluj Visual Studio Code](https://code.visualstudio.com/Download).
01. [Pobierz i zainstaluj zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).
01. [Zainstaluj rozszerzenie C# z witryny Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

## <a name="download-and-manually-install"></a>Pobierz i ręcznie zainstaluj

Alternatywnie w przypadku instalatorów systemu Windows dla platformy .NET Core można pobrać i ręcznie zainstalować zestaw SDK lub środowisko uruchomieniowe. Instalacja ręczna jest zwykle wykonywana w ramach testowania ciągłej integracji. Dla deweloperów lub użytkowników zazwyczaj lepiej jest użyć [Instalatora](https://dotnet.microsoft.com/download/dotnet-core).

Zarówno zestaw .NET Core SDK, jak i środowisko uruchomieniowe platformy .NET Core można zainstalować ręcznie po pobraniu. W przypadku zainstalowania zestaw .NET Core SDK nie trzeba instalować odpowiedniego środowiska uruchomieniowego. Najpierw pobierz wydanie binarne dla zestawu SDK lub środowiska uruchomieniowego z jednej z następujących lokacji:

- ✔️ [pobierania wersji zapoznawczej programu .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)
- [pliki do pobrania ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [pliki do pobrania ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Wszystkie pliki do pobrania z platformy .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Utwórz katalog, aby wyodrębnić platformę .NET do programu, na przykład `%USERPROFILE%\dotnet` . Następnie wyodrębnij pobrany plik zip do tego katalogu.

Domyślnie interfejs wiersza polecenia platformy .NET Core polecenia i aplikacje nie będą używać platformy .NET Core w ten sposób i musisz jawnie wybrać jej użycie. W tym celu Zmień zmienne środowiskowe, z którymi aplikacja jest uruchomiona:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

Takie podejście umożliwia zainstalowanie wielu wersji w oddzielnych lokalizacjach, a następnie jawne wybranie lokalizacji instalacji, która ma być używana przez aplikację, uruchamiając aplikację ze zmiennymi środowiskowymi wskazującymi w tej lokalizacji.

Gdy `DOTNET_MULTILEVEL_LOOKUP` jest ustawiona na `0` , .NET Core ignoruje wszystkie globalnie zainstalowane wersje .NET Core. Usuń to ustawienie środowiska, aby umożliwić programowi .NET Core uwzględnienie domyślnej globalnej lokalizacji instalacji podczas wybierania najlepszej platformy do uruchamiania aplikacji. Wartość domyślna to zwykle `C:\Program Files\dotnet` , czyli miejsce, w którym instalatorzy instalują platformę .NET Core.

## <a name="docker"></a>Docker

Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta. Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.

Środowisko .NET Core można uruchomić w kontenerze platformy Docker. Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.

Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy. Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.

Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Następne kroki

- [Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md?pivots=os-windows).
- [Samouczek: samouczek Hello World](../tutorials/with-visual-studio.md).
- [Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).
