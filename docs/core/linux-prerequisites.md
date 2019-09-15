---
title: Wymagania wstępne dotyczące programu .NET Core w systemie Linux
description: Obsługiwane wersje systemów Linux i .NET Core umożliwiają tworzenie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 5fcf931572f3c7e9b9857d2e91e9d620c7aad0bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969868"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Wymagania wstępne dotyczące programu .NET Core w systemie Linux

W tym artykule przedstawiono zależności, które są konieczne do tworzenia aplikacji .NET Core w systemie Linux. Obsługiwane dystrybucje i wersje systemu Linux oraz następujące zależności dotyczą dwóch sposobów tworzenia aplikacji platformy .NET Core w systemie Linux:

* [Wiersz polecenia z ulubionym edytorem](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Pakiet zestaw .NET Core SDK nie jest wymagany w przypadku serwerów produkcyjnych/środowisk. W przypadku aplikacji wdrożonych w środowiskach produkcyjnych wymagany jest tylko pakiet środowiska uruchomieniowego .NET Core. Środowisko uruchomieniowe platformy .NET Core jest wdrażane z użyciem aplikacji w ramach wdrożenia samodzielnego, jednak należy je wdrożyć osobno dla wdrożonych aplikacji zależnych od platformy. Aby uzyskać więcej informacji na temat typów wdrożeń zależnych od platformy i samodzielnych, zobacz [wdrażanie aplikacji .NET Core](./deploying/index.md). Zobacz również [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) dla określonych wytycznych.

## <a name="supported-linux-versions"></a>Obsługiwane wersje systemu Linux

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Program .NET Core 2. x traktuje system Linux jako pojedynczy systemu operacyjnego. Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux. 

Aby uzyskać linki do pobrania i więcej informacji, zobacz pliki do pobrania w [programie .net core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) lub w [programie .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

Platforma .NET Core 2. x jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:

* Red Hat Enterprise Linux 7, 6-64-bitowy (`x86_64` lub `amd64`)
* CentOS 7-64-bit (`x86_64` lub `amd64`) 
* Oracle Linux 7-64-bitowy (`x86_64` lub `amd64`) 
* Fedora 28, 27-64-bitowy (`x86_64` lub `amd64`) 
* Debian 9 (64-bitowy, `arm32`), 8,7 i nowsze wersje — 64-bit (`x86_64` lub `amd64`)
* Ubuntu 18,04 (64-bit, `arm32`), 16,04, 14,04-64-bit (`x86_64` lub `amd64`)
* Linux mennic 18, 17-64-bitowy (`x86_64` lub `amd64`)
* openSUSE 42,3 lub nowszy — 64-bitowy (`x86_64` lub) `amd64`
* SUSE Enterprise Linux (SLES) 12 z dodatkiem Service Pack 2 lub nowszym — 64`x86_64` - `amd64`bitowy (lub)
* System Alpine Linux 3,7 lub nowszy — 64-bitowy (`x86_64` lub `amd64`)

Zobacz obsługiwane wersje systemu operacyjnego .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) i [obsługiwane wersje systemu operacyjnego .NET Core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) , aby zapoznać się z pełną listą systemów operacyjnych .NET Core 2,1 i .NET Core 2,2 Obsługiwane systemy operacyjne, dystrybucje i wersje, nieobsługiwane wersje systemu operacyjnego i zasady cyklu życia linki.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Aby uzyskać linki do pobrania i więcej informacji, zobacz pliki do pobrania w [programie .net core 1,1](https://dotnet.microsoft.com/download/dotnet-core/1.1) lub w [programie .NET Core 1,0](https://dotnet.microsoft.com/download/dotnet-core/1.0).

Platforma .NET Core 1. x jest obsługiwana w następujących dystrybucjach/wersjach systemu`x86_64` Linux `amd64`64-bit (lub):

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1), 27
* Debian 8,2 lub nowszy
* Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04
* Linux Mint 17
* openSUSE 42,3 lub nowsza (.NET Core 1,1)

Zobacz [obsługiwane wersje systemu operacyjnego na platformie .NET Core 1. x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych .NET Core 1. x, wersje systemu operacyjnego i linki do zasad cyklu życia.

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET Core 3,0 — wersja zapoznawcza 1](#tab/netcore30)

Program .NET Core 3,0 w wersji zapoznawczej 1 traktuje system Linux jako pojedynczą wersję systemu operacyjnego. Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux. 

Aby uzyskać linki do pobrania i więcej informacji, zobacz temat [pobieranie z programu .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Program .NET Core 3,0 wersja zapoznawcza 1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux. 

OS                            | Wersja               | Architektury  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6                     | X64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | X64
Fedora                        | 28                    | X64
Debian                        | 9                     | x64, ARM32\*, ARM64\*
Ubuntu                        | 16.04 +, 18.04 +        | x64, ARM32\*, ARM64\*
Mennic systemu Linux                    | 18                    | X64
openSUSE                      | 42.3 +                 | X64
SUSE Enterprise Linux (SLES)  | 12 SP2+               | X64
Alpine Linux                  | 3.8 +                  | x64, ARM64

\*Obsługa ARM32 i ARM64 rozpoczyna się od Debian 9 i Ubuntu 16,04. Wcześniejsze wersje tych dystrybucje nie są obsługiwane w mikroukładach ARM.

Zobacz [obsługiwane wersje systemu operacyjnego .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucje i wersje programu .net Core 3,0, wersje systemu operacyjnego i linki do zasad cyklu życia.

Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

---

## <a name="linux-distribution-dependencies"></a>Zależności dystrybucji systemu Linux

Poniżej przedstawiono przykłady. Dokładne wersje i nazwy mogą się nieco różnić w zależności od wybranej dystrybucji systemu Linux.

### <a name="ubuntu"></a>Ubuntu

Dystrybucje Ubuntu wymagają zainstalowanych następujących bibliotek:

* liblttng-ust0
* libcurl3 (dla 14. x i 16. x)
* libcurl4 (dla 18. x)
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (dla 14. x)
* libicu55 (dla 16. x)
* libicu57 (dla 17. x)
* libicu60 (dla 18. x)

W przypadku wersji wcześniejszej niż .NET Core 2,1 wymagane są również następujące zależności:

* libunwind8
* libuuid1

### <a name="centos-and-fedora"></a>CentOS i Fedora

Dystrybucje CentOS wymagają zainstalowanych następujących bibliotek:

* lttng-ust
* libcurl
* openssl-libs
* krb5-libs
* libicu
* zlib

Fedora użytkownicy: Jeśli wersja OpenSSL > = 1,1, należy zainstalować polecenie COMPAT-openssl10.

W przypadku wersji wcześniejszej niż .NET Core 2,1 wymagane są również następujące zależności:

* libunwind
* libuuid

Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalowanie zależności programu .NET Core z natywnymi instalatorami

Natywne Instalatory platformy .NET Core są dostępne dla obsługiwanych dystrybucji lub wersji systemu Linux. Natywne Instalatory wymagają dostępu administratora (sudo) do serwera programu. Zaletą korzystania z instalatora natywnego jest to, że wszystkie zależności natywne platformy .NET Core są zainstalowane. Natywne Instalatory również instalują zestaw .NET Core SDK całego systemu.

W systemie Linux dostępne są dwa opcje pakietu Instalatora:

* Za pomocą Menedżera pakietów opartych na źródle danych, takiego jak apt-get for Ubuntu lub yum for CentOS/RHEL.
* Korzystanie z samych pakietów, DEB lub RPM.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Skrypty są instalowane za pomocą skryptu Instalatora .NET Core

[Skrypty programu dotnet-Install](./tools/dotnet-install-script.md) są używane do przeprowadzania instalacji niebędącej administratorem interfejsu wiersza polecenia łańcucha narzędzi i udostępnionego środowiska uruchomieniowego. Skrypt można pobrać z programu <https://dot.net/v1/dotnet-install.sh>.

Skrypt domyślnie instaluje najnowszą wersję "LTS", która jest obecnie platformą .NET Core 1,1. Aby zainstalować program .NET Core 2,1, uruchom skrypt z następującym przełącznikiem:

```console
./dotnet-install.sh -c Current
```

Skrypt bash Instalatora jest używany w scenariuszach automatyzacji i instalacjach niebędących administratorami. Ten skrypt odczytuje również przełączniki programu PowerShell, dzięki czemu mogą być używane z skryptem w systemach Linux/OS X.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli masz problemy z instalacją programu .NET Core w obsługiwanej dystrybucji/wersji systemu Linux, zapoznaj się z następującymi tematami dotyczącymi zainstalowanych dystrybucji/wersji:

* [Znane problemy dotyczące programu .NET Core 3,0](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [Znane problemy dotyczące programu .NET Core 2,2](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [Znane problemy dotyczące programu .NET Core 2,1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [Znane problemy dotyczące programu .NET Core 1,1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [Znane problemy dotyczące programu .NET Core 1,0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
