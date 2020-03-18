---
title: Instalowanie środowiska uruchomieniowego .NET Core w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować program .NET Core w systemach Windows, Linux i macOS. Odnajdowanie zależności wymaganych do uruchamiania aplikacji .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399015"
---
# <a name="install-the-net-core-runtime"></a>Instalowanie programu runowego .NET Core

W tym artykule dowiesz się, jak pobrać i zainstalować program .NET Core. Czas uruchomieniowy .NET Core służy do uruchamiania aplikacji utworzonych za pomocą programu .NET Core.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instalacja z instalatorem

System Windows ma autonomiczne instalatory, za których można zainstalować środowisko uruchomieniowe .NET Core 3.1:

- [x64 (64-bitowe) procesory](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32-bitowe) procesory](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instalacja z instalatorem

System macOS ma autonomiczne instalatory, za których można zainstalować program .NET Core 3.1:

- [x64 (64-bitowe) procesory](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Pobieranie i ręczne instalowanie

Jako alternatywę dla instalatorów systemu macOS dla platformy .NET Core można pobrać i ręcznie zainstalować program runtime.

Aby zainstalować program runtime i włączyć polecenia cli .NET Core dostępne na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core. Następnie otwórz terminal i uruchom następujące polecenia. Zakłada się, że czas wykonywania `~/Downloads/dotnet-runtime.pkg` jest pobierany do pliku.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalowanie za pomocą menedżera pakietów

Program .NET Core Runtime można zainstalować z wieloma typowymi menedżerami pakietów systemu Linux. Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — instalowanie programu .NET Core](linux-package-managers.md).

Instalowanie go za pomocą menedżera pakietów jest obsługiwane tylko w architekturze x64. Jeśli instalujesz program .NET Core Runtime o innej architekturze, takiej jak ARM, postępuj zgodnie z instrukcjami w sekcji [Pobieranie i instaluj ręcznie.](#download-and-manually-install) Aby uzyskać więcej informacji na temat obsługiwanych architektur, zobacz [zależności i wymagania programu .NET Core](dependencies.md).

## <a name="download-and-manually-install"></a>Pobieranie i ręczne instalowanie

Aby wyodrębnić czas wykonywania i udostępnić polecenia wiersza polecenia .NET Core na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core. Następnie otwórz terminal i uruchom następujące polecenia.

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
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

Takie podejście umożliwia instalowanie różnych wersji w oddzielnych lokalizacjach i jawnie wybrać, który z nich do użycia przez którą aplikację.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalacja za pomocą automatyzacji programu PowerShell

[Skrypty dotnet-install](../tools/dotnet-install-script.md) są używane do automatyzacji i instalacji innych niż administrator w czasie wykonywania. Skrypt można pobrać ze [strony referencyjnej skryptu dotnet-install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą wersję [obsługi długoterminowej (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) która jest .NET Core 3.1. Można wybrać określoną wersję, określając `Channel` przełącznik. Dołącz `Runtime` przełącznik, aby zainstalować czas wykonywania. W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> Powyższe polecenie instaluje ASP.NET core'u w celu zapewnienia maksymalnej zgodności. ASP.NET Core runtime zawiera również standardowy program .NET Core.

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

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalacja z automatyzacją bash

[Skrypty dotnet-install](../tools/dotnet-install-script.md) są używane do automatyzacji i instalacji innych niż administrator w czasie wykonywania. Skrypt można pobrać ze [strony referencyjnej skryptu dotnet-install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą wersję [obsługi długoterminowej (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) która jest .NET Core 3.1. Można wybrać określoną wersję, określając `current` przełącznik. Dołącz `runtime` przełącznik, aby zainstalować czas wykonywania. W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> Powyższe polecenie instaluje ASP.NET core'u w celu zapewnienia maksymalnej zgodności. ASP.NET Core runtime zawiera również standardowy program .NET Core.

::: zone-end

## <a name="all-net-core-downloads"></a>Wszystkie pliki do pobrania programu .NET Core

Program .NET Core można pobrać i zainstalować bezpośrednio za pomocą jednego z następujących łączy:

- [Pliki do pobrania programu .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Pliki do pobrania programu .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kontenery zapewniają lekki sposób izolowania aplikacji od reszty systemu hosta. Kontenery na tym samym komputerze współużytkują tylko jądro i używają zasobów podanych do aplikacji.

Program .NET Core można uruchomić w kontenerze platformy Docker. Oficjalne obrazy platformy Docker platformy .NET Core są publikowane w rejestrze kontenerów firmy Microsoft (MCR) i można je wykryć w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Każde repozytorium zawiera obrazy dla różnych kombinacji .NET (SDK lub Runtime) i OS, których można użyć.

Firma Microsoft udostępnia obrazy dostosowane do określonych scenariuszy. Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy, które są tworzone do uruchamiania ASP.NET aplikacji Core w środowisku produkcyjnym.

Aby uzyskać więcej informacji na temat używania programu .NET Core w kontenerze platformy Docker, zobacz [Wprowadzenie do platformy .NET i platformy Docker](../docker/introduction.md) oraz [samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Następne kroki

- [Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md).
