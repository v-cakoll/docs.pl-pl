---
title: Instalowanie zestaw .NET Core SDK w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do tworzenia aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 6e9af6c84c81b1244e10fa7d5955ab67d34b1f0a
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552205"
---
# <a name="install-the-net-core-sdk"></a>Zainstaluj zestaw .NET Core SDK

W tym artykule dowiesz się, jak zainstalować zestaw .NET Core SDK. Zestaw .NET Core SDK jest używany do tworzenia aplikacji i bibliotek platformy .NET Core. Środowisko uruchomieniowe platformy .NET Core jest zawsze instalowane z zestawem SDK.

Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:

- [Pliki do pobrania dla programu .NET Core 3,1 Preview 3](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Pliki do pobrania w programie .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Pliki do pobrania w programie .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Pliki do pobrania w programie .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

Program .NET Core można również zainstalować w ramach zintegrowanego środowiska programistycznego (IDE), szczegółowo w poniższych sekcjach.

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a>Instalowanie za pomocą Instalatora

Zarówno system Windows, jak i macOS mają autonomiczne Instalatory, których można użyć do zainstalowania zestawu SDK platformy .NET Core 3,0.

- [Procesory CPU Windows x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPU](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)
- [procesory macOS x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalowanie przy użyciu Menedżera pakietów

Zestaw .NET Core SDK można zainstalować przy użyciu wielu popularnych menedżerów pakietów systemu Linux. Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — Instalowanie programu .NET Core](linux-package-manager-rhel7.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Instalowanie za pomocą programu Visual Studio

Jeśli używasz programu Visual Studio do tworzenia aplikacji platformy .NET Core, w poniższej tabeli opisano minimalną wymaganą wersję programu Visual Studio opartą na docelowej wersji zestaw .NET Core SDK.

| Wersja zestaw .NET Core SDK | Wersja programu Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.0                   | Program Visual Studio 2019 w wersji 16,3 lub nowszej. |
| 2,2                   | Program Visual Studio 2017 w wersji 15,9 lub nowszej. |
| 2,1                   | Program Visual Studio 2017 w wersji 15,7 lub nowszej. |

Jeśli masz już zainstalowany program Visual Studio, możesz sprawdzić swoją wersję, wykonując poniższe kroki.

01. Otwórz program Visual Studio.
01. Wybierz **pomoc** > **o Microsoft Visual Studio**.
01. Odczytaj numer wersji z okna dialogowego **informacje** .

Program Visual Studio może zainstalować najnowsze zestaw .NET Core SDK i środowisko uruchomieniowe.

- [Pobierz program Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Wybierz obciążenie

Podczas instalowania lub modyfikowania programu Visual Studio wybierz jedno z następujących obciążeń, w zależności od rodzaju kompilowanej aplikacji:

- Obciążenie **Międzyplatformowe dla platformy .NET Core** w sekcji **inne zestawy narzędzi** .
- **ASP.NET i programowanie w sieci Web** w sekcji **chmury & sieci Web** .
- Obciążenie **Programowanie na platformie Azure** w sekcji **chmury & sieci Web** .
- Obciążenie **Programowanie aplikacji klasycznych na platformie .NET** znajduje się w sekcji **Desktop & Mobile** .

[![Windows Visual Studio 2019 z obciążeniem platformy .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Zainstaluj przy użyciu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac instaluje zestaw .NET Core SDK w przypadku wybrania obciążenia **.NET Core** . Aby rozpocząć pracę z programowaniem programu .NET Core w systemie macOS, zobacz [Instalowanie programu Visual Studio 2019 for Mac](/visualstudio/mac/installation).

[![macOS programu Visual Studio 2019 for Mac z funkcją obciążenia .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-from-visual-studio-code"></a>Zainstaluj z Visual Studio Code

Visual Studio Code to zaawansowany i lekki Edytor kodu źródłowego, który jest uruchamiany na pulpicie. Visual Studio Code jest dostępny dla systemów Windows, macOS i Linux.

Mimo że Visual Studio Code nie jest obsługiwana przez platformę .NET Core, Dodawanie obsługi .NET Core jest proste.

01. [Pobierz i zainstaluj Visual Studio Code](https://code.visualstudio.com/Download).
01. [Pobierz i zainstaluj zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).
01. [Zainstaluj C# rozszerzenie z witryny Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalowanie przy użyciu programu PowerShell Automation

[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK. Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1. Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalowanie przy użyciu usługi Bash Automation

[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK. Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1. Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a>Docker

Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta. Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.

Środowisko .NET Core można uruchomić w kontenerze platformy Docker. Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.

Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy. Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.

Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Następne kroki

::: zone pivot="os-windows"

- [Samouczek: C# samouczek Hello World](../tutorials/with-visual-studio.md).
- [Samouczek: Visual Basic Hello World samouczka](../tutorials/vb-with-visual-studio.md).
- [Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).
- [Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).

::: zone-end

::: zone pivot="os-macos"

- [Samouczek: Rozpoczynanie pracy w witrynie macOS](../tutorials/using-on-mac-vs.md).
- [Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).
- [Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).

::: zone-end
