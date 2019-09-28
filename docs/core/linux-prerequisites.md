---
title: Wymagania wstępne dotyczące programu .NET Core w systemie Linux
description: Obsługiwane wersje systemów Linux i .NET Core umożliwiają tworzenie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem Linux.
author: leecow
ms.author: leecow
ms.date: 09/25/2019
ms.openlocfilehash: 4c5d79459c9d69111ca6452d9305f0deb37212b8
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591701"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Wymagania wstępne dotyczące programu .NET Core w systemie Linux

W tym artykule przedstawiono zależności, które są konieczne do tworzenia aplikacji .NET Core w systemie Linux. Obsługiwane dystrybucje i wersje systemu Linux oraz następujące zależności dotyczą dwóch sposobów tworzenia aplikacji platformy .NET Core w systemie Linux:

* [Wiersz polecenia z ulubionym edytorem](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Pakiet zestaw .NET Core SDK nie jest wymagany w przypadku serwerów produkcyjnych/środowisk. W przypadku aplikacji wdrożonych w środowiskach produkcyjnych wymagany jest tylko pakiet środowiska uruchomieniowego .NET Core. Środowisko uruchomieniowe platformy .NET Core jest wdrażane z użyciem aplikacji w ramach wdrożenia samodzielnego, jednak należy je wdrożyć osobno dla wdrożonych aplikacji zależnych od platformy. Aby uzyskać więcej informacji na temat typów wdrożeń zależnych od platformy i samodzielnych, zobacz [wdrażanie aplikacji .NET Core](./deploying/index.md). Zobacz również [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) dla określonych wytycznych.

## <a name="supported-linux-versions"></a>Obsługiwane wersje systemu Linux

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Program .NET Core 3,0 traktuje system Linux jako pojedynczy systemu operacyjnego. Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux. 

Aby uzyskać linki do pobrania i więcej informacji, zobacz temat [pobieranie z programu .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Platforma .NET Core 3,0 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| OS                             | Version               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6 +, 7                 | x64 |
| Oracle Linux                   | 7                     | x64 |
| CentOS                         | 7                     | x64 |
| Fedora                         | 29 +                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 +                | x64, ARM32, ARM64 |
| Mennic systemu Linux                     | 18 +                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.8 +                  | x64, ARM64 |

Zobacz [obsługiwane wersje systemu operacyjnego .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucje i wersje programu .net Core 3,0, wersje systemu operacyjnego i linki do zasad cyklu życia.

Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

Program .NET Core 2,2 traktuje system Linux jako pojedynczy systemu operacyjnego. Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.

Aby uzyskać linki do pobrania i więcej informacji, zobacz temat [pobieranie z programu .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2).

Platforma .NET Core 2,2 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| OS                             |  Version                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| Oracle Linux                   |  7                      | x64 |
| CentOS                         |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 18,10    | x64, ARM32 |
| Mennic systemu Linux                     |  17, 18                 | x64 |
| openSUSE                       |  15 +                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.7 +                   | x64 |

Zobacz [obsługiwane wersje systemu operacyjnego .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucje i wersje programu .net Core 2,2, wersje systemu operacyjnego i linki do zasad cyklu życia.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

Program .NET Core 2,1 traktuje system Linux jako pojedynczy systemu operacyjnego. Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.

Aby uzyskać linki do pobrania i więcej informacji, zobacz temat [pobieranie z programu .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

Platforma .NET Core 2,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:

| OS                             |  Version                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| Oracle Linux                   |  7                      | x64 |
| CentOS                         |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 19,04    | x64, ARM32 |
| Mennic systemu Linux                     |  17, 18                 | x64 |
| openSUSE                       |  42.3 +                  | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.7 +                   | x64 |

Zobacz [obsługiwane wersje systemu operacyjnego .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucje i wersje programu .net Core 2,1, wersje systemu operacyjnego i linki do zasad cyklu życia.

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

```bash
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
