---
title: Instalowanie .NET Core SDK w systemach Windows, Linux i macOS - .NET Core
description: Dowiedz się, jak zainstalować program .NET Core w systemach Windows, Linux i macOS. Odnajdowanie zależności wymaganych do tworzenia aplikacji .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399008"
---
# <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

W tym artykule dowiesz się, jak zainstalować zestaw SDK .NET Core. Zestaw SDK .NET Core służy do tworzenia aplikacji i bibliotek .NET Core. Czas uruchomieniowy .NET Core jest zawsze instalowany przy ks.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instalacja z instalatorem

System Windows ma autonomiczne instalatory, za których można zainstalować zestaw SDK .NET Core 3.1:

- [x64 (64-bitowe) procesory](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32-bitowe) procesory](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instalacja z instalatorem

System macOS ma autonomiczne instalatory, za których można zainstalować zestaw SDK .NET Core 3.1:

- [x64 (64-bitowe) procesory](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Pobieranie i ręczne instalowanie

Jako alternatywę dla instalatorów systemu macOS dla platformy .NET Core można pobrać i ręcznie zainstalować zestaw SDK.

Aby wyodrębnić zestaw SDK i udostępnić polecenia wiersza polecenia .NET Core na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core. Następnie otwórz terminal i uruchom następujące polecenia. Zakłada się, że czas wykonywania `~/Downloads/dotnet-sdk.pkg` jest pobierany do pliku.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalowanie za pomocą menedżera pakietów

Zestaw SDK .NET Core można zainstalować z wieloma typowymi menedżerami pakietów systemu Linux. Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — instalowanie programu .NET Core](linux-package-managers.md).

Instalacja z menedżerem pakietów jest obsługiwana tylko w architekturze x64. Jeśli instalujesz zestaw SDK .NET Core o innej architekturze, takiej jak ARM, postępuj zgodnie z poniższą [instrukcją pobierania i ręcznie zainstaluj.](#download-and-manually-install) Aby uzyskać więcej informacji na temat obsługiwanych architektur, zobacz [zależności i wymagania programu .NET Core](dependencies.md).

## <a name="download-and-manually-install"></a>Pobieranie i ręczne instalowanie

Aby wyodrębnić zestaw SDK i udostępnić polecenia wiersza polecenia .NET Core na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core. Następnie otwórz terminal i uruchom następujące polecenia.

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Poprzednie `export` polecenia udostępniają tylko polecenia cli .NET Core dla sesji terminala, w której została ona uruchamiana.
>
> Profil powłoki można edytować, aby trwale dodawać polecenia. Istnieje wiele różnych powłok dostępnych dla Linuksa i każdy ma inny profil. Przykład:
>
> - **Powłoka Bash**: *~/.bash_profile*, *~/.bashrc*
> - **Korn Shell**: *~/.kshrc* lub *.profile*
> - **Z Powłoka**: *~/.zshrc* lub *.zprofil*
>
> Edytowanie odpowiedniego pliku źródłowego dla `:$HOME/dotnet` powłoki i `PATH` dodanie na końcu istniejącej instrukcji. Jeśli `PATH` instrukcja nie jest dołączona, dodaj nowy wiersz z . `export PATH=$PATH:$HOME/dotnet`
>
> Ponadto dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Instalowanie w programie Visual Studio

Jeśli używasz programu Visual Studio do tworzenia aplikacji .NET Core, w poniższej tabeli opisano minimalną wymaganą wersję programu Visual Studio na podstawie docelowej wersji sdk .NET Core.

| Wersja SDK programu .NET Core | Wersja programu Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Program Visual Studio 2019 w wersji 16.4 lub nowszej. |
| 3.0                   | Program Visual Studio 2019 w wersji 16.3 lub nowszej. |
| 2.2                   | Program Visual Studio 2017 w wersji 15.9 lub nowszej. |
| 2.1                   | Program Visual Studio 2017 w wersji 15.7 lub nowszej. |

Jeśli masz już zainstalowany program Visual Studio, możesz sprawdzić wersję, wykonując następujące kroki.

01. Otwórz program Visual Studio.
01. Wybierz **pozycję Pomoc dotyczącą** > **programu Microsoft Visual Studio**.
01. Przeczytaj numer wersji z okna dialogowego **Informacje.**

Program Visual Studio może zainstalować najnowszy zestaw SDK i program .NET Core SDK i program runtime.

- [Pobierz program Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Wybieranie obciążenia

Podczas instalowania lub modyfikowania programu Visual Studio wybierz co najmniej jeden z następujących obciążeń, w zależności od rodzaju aplikacji, którą budujesz:

- **Obciążenie programistyczne programu .NET Core na wielu platformach** w sekcji **Inne zestawy narzędzi.**
- Obciążenie **ASP.NET i tworzeniem stron internetowych** w sekcji Web & **Cloud.**
- Obciążenie **programistyczne platformy Azure** w sekcji **& chmura w sieci Web.**
- Obciążenie **programistyczne dla komputerów stacjonarnych .NET** w sekcji **Desktop & Mobile.**

[![Program Windows Visual Studio 2019 z obciążeniem programu .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="download-and-manually-install"></a>Pobieranie i ręczne instalowanie

Aby wyodrębnić czas wykonywania i udostępnić polecenia wiersza polecenia .NET Core na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core. Następnie utwórz katalog do zainstalowania `%USERPROFILE%\dotnet`na przykład . Na koniec wyodrębnij pobrany plik zip do tego katalogu.

Domyślnie polecenia i aplikacje cli programu .NET Core nie będą używać zainstalowanego w ten sposób programu .NET Core. Musisz jawnie zdecydować się na jego użycie. W tym celu należy zmienić zmienne środowiskowe, z którymi aplikacja jest uruchamiana:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Takie podejście umożliwia zainstalowanie wielu wersji w oddzielnych lokalizacjach, a następnie jawnie wybrać lokalizację instalacji, której aplikacja powinna używać, uruchamiając aplikację ze zmiennymi środowiskowymi wskazującymi w tej lokalizacji.

Nawet wtedy, gdy te zmienne środowiskowe są ustawione, .NET Core nadal bierze pod uwagę domyślną globalną lokalizację instalacji podczas wybierania najlepszej struktury do uruchamiania aplikacji. Wartością domyślną `C:\Program Files\dotnet`jest zazwyczaj , z której korzystają instalatorzy. Środowisko uruchomieniowe można poinstruować, aby używały tylko niestandardowej lokalizacji instalacji, ustawiając również tę zmienną środowiskową:

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Instalowanie w programie Visual Studio dla komputerów Mac

Program Visual Studio dla komputerów Mac instaluje zestaw SDK .NET Core po wybraniu obciążenia **.NET Core.** Aby rozpocząć pracę z programami .NET Core w systemie macOS, zobacz [Instalowanie programu Visual Studio 2019 dla komputerów Mac](/visualstudio/mac/installation). Aby uzyskać najnowszą wersję .NET Core 3.1, należy użyć programu Visual Studio preview dla komputerów Mac 8.4.

[![MacOS Visual Studio 2019 dla komputerów Mac z funkcją obciążenia .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-alongside-visual-studio-code"></a>Instalowanie obok kodu programu Visual Studio

Visual Studio Code to zaawansowany i lekki edytor kodu źródłowego, który jest uruchamiany na pulpicie. Kod programu Visual Studio jest dostępny dla systemów Windows, macOS i Linux.

Chociaż kod programu Visual Studio nie pochodzi z automatycznego instalatora .NET Core, jak Visual Studio nie, dodawanie .NET Core obsługuje jest prosta.

01. [Pobierz i zainstaluj kod programu Visual Studio](https://code.visualstudio.com/Download).
01. [Pobierz i zainstaluj zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).
01. [Zainstaluj rozszerzenie C# z portalu Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalacja za pomocą automatyzacji programu PowerShell

[Skrypty dotnet-install](../tools/dotnet-install-script.md) są używane do automatyzacji i instalacji bez administratora sdk. Skrypt można pobrać ze [strony referencyjnej skryptu dotnet-install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą wersję [obsługi długoterminowej (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) która jest .NET Core 3.1. Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt za pomocą następującego przełącznika.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalacja z automatyzacją bash

[Skrypty dotnet-install](../tools/dotnet-install-script.md) są używane do automatyzacji i instalacji bez administratora sdk. Skrypt można pobrać ze [strony referencyjnej skryptu dotnet-install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą wersję [obsługi długoterminowej (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) która jest .NET Core 3.1. Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt za pomocą następującego przełącznika.

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>Wszystkie pliki do pobrania programu .NET Core

Program .NET Core można pobrać i zainstalować bezpośrednio za pomocą jednego z następujących łączy:

- [Pliki do pobrania programu .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Pliki do pobrania programu .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Pliki do pobrania programu .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Pliki do pobrania programu .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kontenery zapewniają lekki sposób izolowania aplikacji od reszty systemu hosta. Kontenery na tym samym komputerze współużytkują tylko jądro i używają zasobów podanych do aplikacji.

Program .NET Core można uruchomić w kontenerze platformy Docker. Oficjalne obrazy platformy Docker platformy .NET Core są publikowane w rejestrze kontenerów firmy Microsoft (MCR) i można je wykryć w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Każde repozytorium zawiera obrazy dla różnych kombinacji .NET (SDK lub Runtime) i OS, których można użyć.

Firma Microsoft udostępnia obrazy dostosowane do określonych scenariuszy. Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy, które są tworzone do uruchamiania ASP.NET aplikacji Core w środowisku produkcyjnym.

Aby uzyskać więcej informacji na temat używania programu .NET Core w kontenerze platformy Docker, zobacz [Wprowadzenie do platformy .NET i platformy Docker](../docker/introduction.md) oraz [samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Następne kroki

::: zone pivot="os-windows"

- [Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).
- [Samouczek: Tworzenie nowej aplikacji z kodem programu Visual Studio](../tutorials/with-visual-studio-code.md).
- [Samouczek: Konteneryzuj aplikację .NET Core](../docker/build-container.md).

::: zone-end

::: zone pivot="os-macos"

- [Praca z notarialną macOS Catalina](macos-notarization-issues.md).
- [Samouczek: Wprowadzenie do systemu macOS](../tutorials/using-on-mac-vs.md).
- [Samouczek: Tworzenie nowej aplikacji z kodem programu Visual Studio](../tutorials/with-visual-studio-code.md).
- [Samouczek: Konteneryzuj aplikację .NET Core](../docker/build-container.md).

::: zone-end

::: zone pivot="os-linux"

- [Samouczek: Tworzenie nowej aplikacji z kodem programu Visual Studio](../tutorials/with-visual-studio-code.md).
- [Samouczek: Konteneryzuj aplikację .NET Core](../docker/build-container.md).

::: zone-end
