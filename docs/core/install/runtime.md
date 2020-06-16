---
title: Instalowanie środowiska uruchomieniowego platformy .NET Core w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do uruchamiania aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d3f7083366e2019d01884b5dff6e60d05ed565dd
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768290"
---
# <a name="install-the-net-core-runtime"></a>Instalowanie środowiska uruchomieniowego platformy .NET Core

W tym artykule dowiesz się, jak pobrać i zainstalować środowisko uruchomieniowe programu .NET Core. Środowisko uruchomieniowe platformy .NET Core służy do uruchamiania aplikacji utworzonych za pomocą platformy .NET Core.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instalowanie za pomocą Instalatora

System Windows ma autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,1:

- [Procesory x64 (64-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Procesory x86 (32-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instalowanie za pomocą Instalatora

macOS ma autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,1:

- [Procesory x64 (64-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Pobierz i ręcznie zainstaluj

Jako alternatywę dla instalatorów macOS dla platformy .NET Core można pobrać i ręcznie zainstalować środowisko uruchomieniowe.

Aby zainstalować środowisko uruchomieniowe i włączyć interfejs wiersza polecenia platformy .NET Core polecenia dostępne w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core. Następnie otwórz Terminal i uruchom następujące polecenia. Przyjęto założenie, że środowisko uruchomieniowe jest pobierane do `~/Downloads/dotnet-runtime.pkg` pliku.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a>Instalowanie w systemie Linux

Ten artykuł zostanie wkrótce usunięty. Jest ona zastępowana przez [zainstalowanie platformy .NET Core w systemie Linux](linux.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalowanie przy użyciu programu PowerShell Automation

[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego. Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1. Możesz wybrać określoną wersję, określając `Channel` przełącznik. Dołącz `Runtime` przełącznik, aby zainstalować środowisko uruchomieniowe. W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> Powyższe polecenie instaluje środowisko uruchomieniowe ASP.NET Core, aby uzyskać maksymalną zgodność. Środowisko uruchomieniowe ASP.NET Core obejmuje również standardowe środowisko uruchomieniowe programu .NET Core.

## <a name="download-and-manually-install"></a>Pobierz i ręcznie zainstaluj

Aby wyodrębnić środowisko uruchomieniowe i udostępnić interfejs wiersza polecenia platformy .NET Core polecenia w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core. Następnie Utwórz katalog do zainstalowania na przykład `%USERPROFILE%\dotnet` . Na koniec Wyodrębnij pobrany plik zip do tego katalogu.

Domyślnie interfejs wiersza polecenia platformy .NET Core polecenia i aplikacje nie będą używać platformy .NET Core w ten sposób i musisz jawnie wybrać jej użycie. W tym celu Zmień zmienne środowiskowe, z którymi aplikacja jest uruchomiona:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Takie podejście umożliwia zainstalowanie wielu wersji w oddzielnych lokalizacjach, a następnie jawne wybranie lokalizacji instalacji, która ma być używana przez aplikację, uruchamiając aplikację ze zmiennymi środowiskowymi wskazującymi w tej lokalizacji.

Nawet jeśli są ustawione te zmienne środowiskowe, program .NET Core nadal uznaje domyślną lokalizację instalacji globalnej podczas wybierania najlepszej platformy do uruchamiania aplikacji. Wartość domyślna to zwykle `C:\Program Files\dotnet` , których instalatorzy używają. Można wydać instrukcje środowiska uruchomieniowego, aby używać niestandardowej lokalizacji instalacji przez ustawienie tej zmiennej środowiskowej również:

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a>Instalowanie przy użyciu usługi Bash Automation

[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego. Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1. Możesz wybrać określoną wersję, określając `current` przełącznik. Dołącz `runtime` przełącznik, aby zainstalować środowisko uruchomieniowe. W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> Powyższe polecenie instaluje środowisko uruchomieniowe ASP.NET Core, aby uzyskać maksymalną zgodność. Środowisko uruchomieniowe ASP.NET Core obejmuje również standardowe środowisko uruchomieniowe programu .NET Core.

::: zone-end

## <a name="all-net-core-downloads"></a>Wszystkie pliki do pobrania z platformy .NET Core

Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:

- [Pliki do pobrania w programie .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Pliki do pobrania w programie .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta. Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.

Środowisko .NET Core można uruchomić w kontenerze platformy Docker. Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.

Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy. Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.

Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Następne kroki

- [Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md).
