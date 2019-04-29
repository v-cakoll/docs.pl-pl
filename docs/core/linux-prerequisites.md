---
title: Wymagania wstępne dla platformy .NET Core w systemie Linux
description: Obsługiwane wersje systemu Linux i zależności platformy .NET Core, opracowywanie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 0bd3287535ba2c398f6577890d1d39f42a806364
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614508"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Wymagania wstępne dla platformy .NET Core w systemie Linux

W tym artykule przedstawiono zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Linux. Obsługiwane dystrybucje systemu Linux/wersje i zależności, które należy wykonać są stosowane na dwa sposoby tworzenia aplikacji platformy .NET Core w systemie Linux:

* [Wiersza polecenia za pomocą ulubionego edytora](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Pakiet .NET Core SDK nie jest wymagana dla środowisk serwerów produkcyjnych. Pakiet środowiska uruchomieniowego .NET Core jest potrzebna w przypadku aplikacji wdrożonych na środowisko produkcyjne. Środowisko uruchomieniowe platformy .NET Core jest wdrażana przy użyciu aplikacji jako część wdrożenia niezależna, jednak musi zostać wdrożony jako zależny od struktury aplikacji wdrożona oddzielnie. Aby uzyskać więcej informacji na temat typów wdrożeń zależny od struktury, niezależna zobacz [wdrażanie aplikacji .NET Core](./deploying/index.md). Zobacz też [aplikacje dla systemu Linux Self-contained](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) dla szczególnych wytycznych.

## <a name="supported-linux-versions"></a>Obsługiwane wersje systemu Linux

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET core 2.x traktuje Linux jako jeden system operacyjny. Brak pojedynczej kompilacji systemu Linux (na architektura mikroukładu) obsługiwane dystrybucje systemu Linux. 

Łącza pobierania oraz więcej informacji, zobacz [platformy .NET Core 2.2 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/2.2) lub [platformy .NET Core 2.1 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/2.1).

.NET core 2.x obsługuje poniższe dystrybucje systemu Linux/wersji:

* Red Hat Enterprise Linux 7, 6 - 64-bitowych (`x86_64` lub `amd64`)
* CentOS 7 - 64-bitowy (`x86_64` lub `amd64`) 
* Oracle Linux 7 - 64-bitowy (`x86_64` lub `amd64`) 
* Fedora 28, 27 — 64-bitowych (`x86_64` lub `amd64`) 
* Debian 9 (64-bitowy, `arm32`), 8.7 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)
* Ubuntu 18.04 (64-bitowy, `arm32`), 16.04, 14.04 - 64-bitowych (`x86_64` lub `amd64`)
* Linux mennic 18, 17 — 64-bitowych (`x86_64` lub `amd64`)
* openSUSE 42.3 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)
* SUSE Linux Enterprise (SLES) 12 z dodatkiem Service Pack 2 lub nowszego - 64-bitowych (`x86_64` lub `amd64`)
* Firma Alpine Linux 3.7 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)

Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) i [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pełną listę platformy .NET Core 2.1 i .NET Core 2.2 obsługiwane systemy operacyjne, dystrybucji i wersji, z obsługuje wersje systemów operacyjnych i łącza zasad cyklu życia.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Łącza pobierania oraz więcej informacji, zobacz [pobiera .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) lub [platformy .NET Core 1.0 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/1.0).

.NET core 1.x jest obsługiwane na następujących Linux 64-bitowych (`x86_64` lub `amd64`) dystrybucje/wersji:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1), 27
* Debian 8.2 lub nowsze wersje
* Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04
* Linux Mint 17
* openSUSE 42.3 lub nowszej wersji (.NET Core 1.1)

Zobacz [obsługiwanych wersjach systemu operacyjnego programu .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) kompletną listę platformy .NET Core 1.x obsługiwane systemy operacyjne, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET core 3.0 w wersji zapoznawczej 1](#tab/netcore30)

.NET core 3.0 w wersji zapoznawczej 1 traktuje systemu Linux jako jeden system operacyjny. Brak pojedynczej kompilacji systemu Linux (na architektura mikroukładu) obsługiwane dystrybucje systemu Linux. 

Łącza pobierania oraz więcej informacji, zobacz [.NET Core 3.0 to pliki do pobrania](https://dotnet.microsoft.com/download/dotnet-core/3.0).

.NET core 3.0 w wersji zapoznawczej 1 jest obsługiwane na poniższe dystrybucje systemu Linux/wersje. 

System operacyjny                            | Wersja               | Architektury  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6                     | X64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | X64
Fedora                        | 28                    | X64
Debian                        | 9                     | x64, ARM32\*, ARM64\*
Ubuntu                        | 16.04+, 18.04+        | x64, ARM32\*, ARM64\*
Mennic systemu Linux                    | 18                    | X64
openSUSE                      | 42.3+                 | X64
SUSE Linux Enterprise (SLES)  | 12 SP2+               | X64
Firma Alpine Linux                  | 3.8+                  | x64, ARM64

\* Obsługa ARM32 i ARM64 rozpoczyna się od Debian 9 i Ubuntu 16.04. Wcześniejszych wersjach te dystrybucje nie są obsługiwane na mikroukładami ARM.

Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .NET Core 3.0 to pełna lista obsługiwanych systemów operacyjnych, dystrybucji i wersji poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.

Aby uzyskać więcej informacji o sposobie instalowania programu .NET Core 3.0 dla procesorów ARM64, zobacz [instalowanie platformy .NET Core 3.0 dla procesorów Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

---

## <a name="linux-distribution-dependencies"></a>Zależności do dystrybucji systemu Linux

Poniżej mają być przykłady. Na wybranej dystrybucji systemu Linux, nazwy i wersje dokładny mogą się nieco różnić.

### <a name="ubuntu"></a>Ubuntu

Dystrybucje systemu Ubuntu wymagają następujących bibliotek zainstalowane:

* liblttng-ust0
* libcurl3 (dla 14.x i 16.x)
* libcurl4 (w przypadku 18.x)
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (w przypadku 14.x)
* libicu55 (w przypadku 16.x)
* libicu57 (w przypadku 17.x)
* libicu60 (w przypadku 18.x)

W wersjach wcześniejszych niż .NET Core 2.1, następujące zależności wymagane są również:

* libunwind8
* libuuid1

### <a name="centos-and-fedora"></a>CentOS i Fedora

Dystrybucje centOS wymagają następujących bibliotek zainstalowane:

* lttng-ust
* libcurl
* openssl-libs
* krb5-libs
* libicu
* zlib

Użytkownicy fedora: Jeśli Twoje openssl wersji > = 1.1, musisz zainstalować openssl10 zgodności.

W wersjach wcześniejszych niż .NET Core 2.1, następujące zależności wymagane są również:

* libunwind
* libuuid

Aby uzyskać więcej informacji o zależnościach, zobacz [aplikacje dla systemu Linux Self-contained](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalacja zależności platformy .NET Core z natywnych instalatorów

.NET core, który natywnych instalatorów są dostępne dla obsługiwane wersje dystrybucje systemu Linux. Natywnych instalatorów wymaga dostępu administratora ("sudo") do serwera. Zalet za pomocą natywnego Instalatora jest, że są zainstalowane wszystkie zależności natywnego platformy .NET Core. Natywnych instalatorów także zainstalować całego systemu .NET Core SDK.

W systemie Linux istnieją dwie opcje pakiet Instalatora:

* Przy użyciu Menedżera pakietów na podstawie źródła danych, takich jak polecenia apt-get dla systemu Ubuntu lub yum na CentOS/RHEL.
* Za pomocą pakietów, Mistrzostwo DEB lub obr. / min.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Skrypty instalacji przy użyciu skryptu Instalatora platformy .NET Core

[Skryptów instalacji dotnet](./tools/dotnet-install-script.md) są używane do wykonywania instalacji bez uprawnień administratora, łańcuch narzędzi interfejsu wiersza polecenia i udostępnionego środowiska uruchomieniowego. Możesz pobrać skrypt z <https://dot.net/v1/dotnet-install.sh>.

Domyślnie skrypt zainstalowanie najnowszej wersji "LTS", która jest obecnie .NET Core 1.1. Aby zainstalować program .NET Core 2.1, uruchom skrypt przy użyciu następującego przełącznika:

```console
./dotnet-install.sh -c Current
```

Skrypt powłoki bash Instalatora jest używany w scenariuszach automatyzacji oraz przed instalacjami bez uprawnień administratora. Ten skrypt odczytuje również przełączników programu PowerShell, dzięki czemu może być używany ze skryptem w systemach Linux/OS X.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli masz problemy z instalacją .NET Core w obsługiwanych dystrybucji systemu Linux/wersji dla Twojej dystrybucji zainstalowanych/wersji należy zapoznać się następujące tematy:

* [.NET core 3.0 to znane problemy](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [.NET core 2.2 znane problemy](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [Znane problemy dotyczące programu .NET core 2.1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [Znane problemy dotyczące programu .NET core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [Znane problemy dotyczące programu .NET core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
