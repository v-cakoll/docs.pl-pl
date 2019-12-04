---
title: Instalowanie środowiska uruchomieniowego platformy .NET Core w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do uruchamiania aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: fbe9b9e12dc53d9ab6570299e03f2b0a8868fb53
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567271"
---
# <a name="install-the-net-core-runtime"></a>Instalowanie środowiska uruchomieniowego platformy .NET Core

W tym artykule dowiesz się, jak pobrać i zainstalować środowisko uruchomieniowe programu .NET Core. Środowisko uruchomieniowe platformy .NET Core służy do uruchamiania aplikacji utworzonych za pomocą platformy .NET Core.

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a>Instalowanie za pomocą Instalatora

Zarówno system Windows, jak i macOS mają autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,0.

- Procesory Windows [x64 (64-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [procesora x86 (32-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [procesory macOS x64 (64-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.0)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalowanie przy użyciu Menedżera pakietów

Środowisko uruchomieniowe platformy .NET Core można zainstalować przy użyciu wielu popularnych menedżerów pakietów systemu Linux. Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — Instalowanie programu .NET Core](linux-package-manager-rhel7.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalowanie przy użyciu programu PowerShell Automation

[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego. Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1. Aby zainstalować bieżącą wersję programu .NET Core (3,0), uruchom skrypt z następującym przełącznikiem:

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalowanie przy użyciu usługi Bash Automation

[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego. Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).

Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1. Aby zainstalować bieżącą wersję programu .NET Core (3,0), uruchom skrypt z następującym przełącznikiem:

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>Wszystkie pliki do pobrania z platformy .NET Core

Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:

- [Pobieranie z wersji zapoznawczej programu .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Pliki do pobrania w programie .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Pliki do pobrania w programie .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Pliki do pobrania w programie .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta. Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.

Środowisko .NET Core można uruchomić w kontenerze platformy Docker. Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.

Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy. Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.

Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Następne kroki

- [Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md).