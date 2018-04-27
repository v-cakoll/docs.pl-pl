---
title: Wymagania wstępne dotyczące platformy .NET Core w systemie Linux
description: Obsługiwane wersje systemu Linux i zależności platformy .NET Core na tworzenie, wdrażanie i uruchamianie aplikacji .NET Core na maszynach z systemem Linux.
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 04/19/2018
ms.topic: conceptual
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload:
- dotnetcore
ms.openlocfilehash: 7ce13af00a43e1ce84f7c8af70155d0c4a5bed4c
ms.sourcegitcommit: 68b60d38043e50104ccc90c76f8599b1ffe18346
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a>Wymagania wstępne dotyczące platformy .NET Core w systemie Linux

W tym artykule opisano zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Linux. Obsługiwane Linux dystrybucje wersje i zależności, które należy wykonać dotyczą dwa sposoby tworzenia aplikacji platformy .NET Core w systemie Linux:

* [Wiersza polecenia z ulubionego edytora](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Pakiet zestawu SDK programu .NET Core nie jest wymagana dla środowisk serwerów produkcyjnych. Pakiet środowiska uruchomieniowego .NET Core jest potrzebne aplikacje wdrożone w środowisku produkcyjnym. Środowisko uruchomieniowe .NET Core jest wdrażany z aplikacji jako część wdrożenia niezależne, jednak należy ją wdrożyć dla Framework zależne aplikacje wdrażane pojedynczo. Aby uzyskać więcej informacji o typach wdrożeń framework zależne, niezależna, zobacz [wdrażanie aplikacji .NET Core](./deploying/index.md). Zobacz też [aplikacje w systemie Linux Self-contained](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) Aby uzyskać szczegółowe zasady.

## <a name="supported-linux-versions"></a>Obsługiwane wersje systemu Linux

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Traktuje 2.x .NET core Linux jako jeden system operacyjny. Brak jednej kompilacji systemu Linux (na architektura mikroukładu) dystrybucje systemu Linux obsługiwane.

NET Core 2.x jest obsługiwana w systemie Linux 64-bitowej (`x86_64` lub `amd64`) dystrybucje/wersji:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 27 26
* Debian 9 8.7 lub nowszymi wersjami
* Ubuntu 17.10, 16.04, 14.04
* Linux mennic 18, 17
* openSUSE 42.3 lub nowszej wersji
* SUSE Linux Enterprise (SLES) 12 z dodatkiem Service Pack 2 lub nowszy

Zobacz [2.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pełną listę .NET Core 2.x obsługiwanych systemów operacyjnych, dystrybucji i wersji poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Oprogramowanie .NET core 1.x jest obsługiwana w systemie Linux 64-bitowej (`x86_64` lub `amd64`) dystrybucje/wersji:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 26
* Debian 8.2 lub nowszymi wersjami
* Ubuntu 16.04, 14.04
* Linux mennic 18, 17
* openSUSE 42.3 lub nowszej wersji (.NET Core 1.1)

Zobacz [1.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) Pełna lista .NET Core 1.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.

---

## <a name="linux-distribution-dependencies"></a>Zależności dystrybucji systemu Linux

Poniżej mają być przykłady. Na wybranym dystrybucji systemu Linux, nazwy i wersje dokładne mogą się nieco różnić.

### <a name="ubuntu"></a>Ubuntu

Ubuntu dystrybucji wymagają następujących bibliotek zainstalowane:

* libunwind8
* liblttng-ust0
* libcurl3
* libssl1.0.0
* libuuid1
* libkrb5-3
* zlib1g
* libicu52 (dla 14.x)
* libicu55 (dla 16.x)
* libicu57 (dla 17.x)

### <a name="centos"></a>CentOS

CentOS dystrybucji wymagają następujących bibliotek zainstalowane:

* libunwind
* lttng-ust
* libcurl
* openssl-libs
* libuuid
* krb5-libs
* libicu
* zlib

Aby uzyskać więcej informacji o zależnościach, zobacz [aplikacje w systemie Linux Self-contained](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalowanie zależności .NET Core za pomocą natywnego instalatorów

Oprogramowanie .NET core, natywnego instalatory są dostępne dla obsługiwane dystrybucje systemu Linux/wersji. Natywny instalatorów wymagają dostępu administratora (sudo) na serwerze. Zaletą używania Instalatora natywnych jest wszystkie zależności natywnego platformy .NET Core są zainstalowane. Natywny instalatorów również zainstalować całego systemu .NET Core SDK.

W systemie Linux istnieją dwie opcje pakiet Instalatora:

* Za pomocą Menedżera pakietu na podstawie źródła danych, takich jak stanie get dla Ubuntu lub yum dla CentOS/RHEL.
* Używanie pakietów, DEB lub obr. / min.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Wykonywanie skryptów instalacji przy użyciu skryptu Instalatora .NET Core

[Skryptów instalacji dotnet](./tools/dotnet-install-script.md) są używane do wykonywania instalacji bez uprawnień administratora, łańcuch narzędzi interfejsu wiersza polecenia i udostępnionych środowiska wykonawczego. Można pobrać skryptu z [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).

Skrypt Instalatora bash jest używany w scenariuszach automatyzacji i instalacji bez uprawnień administratora. Ten skrypt również odczytuje przełączników programu PowerShell, dzięki czemu mogą być używane w przypadku skryptu w systemach Linux/OS X.

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a>Zainstaluj oprogramowanie .NET Core obsługiwane wersje Red Hat Enterprise Linux (RHEL)

Aby zainstalować oprogramowanie .NET Core w obsługiwanych wersjach RHEL:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Aby zapewnić najnowsze informacje o instalacji, należy wykonać [instrukcje Instalator środowiska uruchomieniowego i zestawu SDK 2.x .NET Core](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current) obsługiwane wersje RHEL.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2.  Najnowsze .NET Core 1.1 na informacje o instalacji Red Hat Enterprise Linux, zobacz [.NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)
     
**.NET Core 1.0**

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2.  Najnowsze .NET Core 1.0 na informacje o instalacji Red Hat Enterprise Linux, zobacz [.NET Core 1.0 — wprowadzenie](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)

Red Hat .NET kanał dostępu do rejestracji Pomoc [rozdział 1 .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) w Red Hat.

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a>Zainstaluj oprogramowanie .NET Core obsługiwanych Ubuntu Linux mennic dystrybucje/wersje (64-bitowy)

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj oprogramowanie .NET Core 2.x na obsługiwany Ubuntu Linux mennic dystrybucje/wersje i (64-bitowa):

**.NET Core 2.0**

|Środowisk uruchomieniowych / zestawów SDK          |Ubuntu 17.10  |Ubuntu 16.04 / Linux mennic 18|Ubuntu 14.04 / Linux mennic 17|
|-------------------------|--------------|----------------------------|----------------------------|
|Środowisko uruchomieniowe platformy .NET core 2.0.6  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|Środowisko uruchomieniowe platformy .NET core 2.0.5  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|Oprogramowanie .NET core SDK 2.1.103    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|Oprogramowanie .NET core SDK 2.0.3      |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |

**Oprogramowanie .NET core 2.1**

>[!IMPORTANT]
> Aby za pomocą programu Visual Studio .NET Core 2.1, musisz [zainstalować Visual Studio 2017 15.7 Preview 1 lub nowszą](https://www.visualstudio.com/vs/preview).

|Środowisk uruchomieniowych / zestawów SDK                  |Ubuntu 17.10    |Ubuntu 16.04 / Linux mennic 18|Ubuntu 14.04 / Linux mennic 17|
|---------------------------------|----------------|----------------------------|----------------------------|
|.NET core 2.1.0-preview2 środowiska wykonawczego |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview2)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview2)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview2)            |
|.NET core 2.1.0-preview1 środowiska wykonawczego |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview1)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview1)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview1)            |
|.NET core 2.1.300-preview2 zestawu SDK   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview2)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview2)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview2)
|.NET core 2.1.300-preview1 zestawu SDK   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview1)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview1)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview1)            |


# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj oprogramowanie .NET Core 1.x na obsługiwany Ubuntu Linux mennic dystrybucje/wersje i (64-bitowa):

| Środowisk uruchomieniowych / zestawów SDK         |Ubuntu 16.04 / Linux mennic 18|Ubuntu 14.04 / Linux mennic 17|
|-------------------------|----------------------------|----------------------------|
|Środowisko uruchomieniowe platformy .NET core 1.1.7  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe platformy .NET core 1.1.6  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe platformy .NET core 1.0.10 |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe platformy .NET core 1.0.9  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|Oprogramowanie .NET core SDK punktem 1.1.8      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|Oprogramowanie .NET core SDK 1.1.7      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|Oprogramowanie .NET core SDK 1.0.4      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|Oprogramowanie .NET core SDK 1.0.1      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a>Zainstaluj oprogramowanie .NET Core obsługiwane wersje Debian (64-bitowy)

Aby zainstalować oprogramowanie .NET Core w obsługiwanych wersjach Debian (64 bity):

> [!NOTE]
> Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj oprogramowanie .NET Core 2.x w obsługiwanych wersjach Debian (64-bitowa):

**.NET Core 2.0**

|Środowisk uruchomieniowych / zestawów SDK          |Debian 9       |Debian 8       |
|-------------------------|---------------|---------------|
|Środowisko uruchomieniowe platformy .NET core 2.0.6  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|Środowisko uruchomieniowe platformy .NET core 2.0.5  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|Oprogramowanie .NET core SDK 2.1.103    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|Oprogramowanie .NET core SDK 2.0.3      |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |

**Oprogramowanie .NET core 2.1**

>[!IMPORTANT]
> Aby za pomocą programu Visual Studio .NET Core 2.1, musisz [zainstalować Visual Studio 2017 15.7 Preview 1 lub nowszą](https://www.visualstudio.com/vs/preview).

|Środowisk uruchomieniowych / zestawów SDK                  |Debian 9       |Debian 8       |
|---------------------------------|---------------|---------------|
|.NET core 2.1.0-preview2 środowiska wykonawczego |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview2)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview2)   |
|.NET core 2.1.0-preview1 środowiska wykonawczego |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview1)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview1)   |
|.NET core 2.1.300-preview2 zestawu SDK   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview2)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview2)   |
|.NET core 2.1.300-preview1 zestawu SDK   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview1)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview1)   |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj program .NET Core 1.x na Debian 9 lub Debian 8:

* Środowisko uruchomieniowe platformy .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)
* Środowisko uruchomieniowe platformy .NET core 1.1.6 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)
* Środowisko uruchomieniowe platformy .NET core 1.0.10 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)
* Środowisko uruchomieniowe platformy .NET core 1.0.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)
* Zestaw SDK programu .NET core punktem 1.1.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)
* Zestaw SDK programu .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)
* .NET core SDK 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)
* Zestaw SDK programu .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a>Zainstaluj oprogramowanie .NET Core obsługiwane wersje Fedora (64-bitowy)

Aby zainstalować oprogramowanie .NET Core w obsługiwanych wersjach Fedora:

> [!NOTE]
> Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj oprogramowanie .NET Core 2.x w obsługiwanych wersjach Fedora (64-bitowa):

**.NET Core 2.0**

|Środowisk uruchomieniowych / zestawów SDK          |Fedora 26 lub nowszy |Fedora 25 lub poprzedniego |
|-------------------------|-------------------|----------------------|
|Środowisko uruchomieniowe platformy .NET core 2.0.6  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|Środowisko uruchomieniowe platformy .NET core 2.0.5  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|Oprogramowanie .NET core SDK 2.1.103    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|Oprogramowanie .NET core SDK 2.0.3      |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

**Oprogramowanie .NET core 2.1**

>[!IMPORTANT]
> Aby za pomocą programu Visual Studio .NET Core 2.1, musisz [zainstalować Visual Studio 2017 15.7 Preview 1 lub nowszą](https://www.visualstudio.com/vs/preview).

|Środowisk uruchomieniowych / zestawów SDK                  |Fedora 26 lub nowszy |Fedora 25 lub poprzedniego |
|---------------------------------|-------------------|----------------------|
|.NET core 2.1.0-preview2 środowiska wykonawczego |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview2)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.1.0-preview2)           |
|.NET core 2.1.0-preview1 środowiska wykonawczego |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview1)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.1.0-preview1)           |
|.NET core 2.1.300-preview2 zestawu SDK   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-preview2)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.300-preview2)           |
|.NET core 2.1.300-preview1 zestawu SDK   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-preview1)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.300-preview1)           |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj oprogramowanie .NET Core 1.x obsługiwane Fedora wersje (64 bity):

**Fedora 24**

* Środowisko uruchomieniowe platformy .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)
* Środowisko uruchomieniowe platformy .NET core 1.1.6 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)
* Zestaw SDK programu .NET core punktem 1.1.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)
* Zestaw SDK programu .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)
* Zestaw SDK programu .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

**Fedora 23**

* Środowisko uruchomieniowe platformy .NET core 1.0.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)
* .NET core SDK 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)
* Zestaw SDK programu .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a>Zainstaluj oprogramowanie .NET Core dla obsługiwanych CentOS i Oracle Linux dystrybucje/wersje (64-bitowy)

Do zainstalowania .NET Core dla obsługiwanych CentOS i Oracle Linux dystrybucje/wersje (64 bity):

> [!NOTE]
> Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj oprogramowanie .NET Core 2.x na obsługiwanych CentOS i Oracle Linux dystrybucje/wersje (64 bity):

**.NET Core 2.0**

* Środowisko uruchomieniowe platformy .NET core 2.0.6 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* Środowisko uruchomieniowe platformy .NET core 2.0.5 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)
* .NET core SDK 2.1.103 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)
* .NET core SDK 2.0.3 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)
 
**Oprogramowanie .NET core 2.1**

>[!IMPORTANT]
> Aby za pomocą programu Visual Studio .NET Core 2.1, musisz [zainstalować Visual Studio 2017 15.7 Preview 1 lub nowszą](https://www.visualstudio.com/vs/preview/).

* Środowisko uruchomieniowe platformy .NET core 2.1.0-preview2 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview2)
* Środowisko uruchomieniowe platformy .NET core 2.1.0-preview1 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)
* 2.1.300-preview2 .NET core SDK [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview2)
* 2.1.300-preview1 .NET core SDK [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj oprogramowanie .NET Core 1.x na obsługiwanych CentOS i Oracle Linux dystrybucje/wersje (64 bity):

* Środowisko uruchomieniowe platformy .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)
* Środowisko uruchomieniowe platformy .NET core 1.1.6 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)
* Środowisko uruchomieniowe platformy .NET core 1.0.10 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)
* Środowisko uruchomieniowe platformy .NET core 1.0.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)
* Zestaw SDK programu .NET core punktem 1.1.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)
* Zestaw SDK programu .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)
* .NET core SDK 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)
* Zestaw SDK programu .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a>Zainstaluj oprogramowanie .NET Core obsługiwane SUSE Linux Enterprise Server i OpenSUSE dystrybucje/wersje (64-bitowy)

Aby zainstalować oprogramowanie .NET Core 2.x dla obsługiwane SUSE Linux Enterprise Server i OpenSUSE dystrybucje/wersje (64 bity):

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj oprogramowanie .NET Core 2.x na obsługiwane SUSE Linux Enterprise Server i OpenSUSE dystrybucje/wersje (64-bitowa):

**.NET Core 2.0**

* Środowisko uruchomieniowe platformy .NET core 2.0.6 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)
* Środowisko uruchomieniowe platformy .NET core 2.0.5 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)
* .NET core SDK 2.1.103 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)
* .NET core SDK 2.0.3 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)
 
**Oprogramowanie .NET core 2.1**

>[!IMPORTANT]
> Aby za pomocą programu Visual Studio .NET Core 2.1, musisz [zainstalować Visual Studio 2017 15.7 Preview 1 lub nowszą](https://www.visualstudio.com/vs/preview).

* Środowisko uruchomieniowe platformy .NET core 2.1.0-preview2 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview2)
* Środowisko uruchomieniowe platformy .NET core 2.1.0-preview1 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)
* 2.1.300-preview2 .NET core SDK [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview2)
* 2.1.300-preview1 .NET core SDK [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Zainstaluj oprogramowanie .NET Core 1.x na obsługiwane SUSE Linux Enterprise Server i OpenSUSE dystrybucje/wersje (64-bitowa):

**SUSE Linux Enterprise Server 13.2**

* Środowisko uruchomieniowe platformy .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)
* Środowisko uruchomieniowe platformy .NET core 1.1.6 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)
* Zestaw SDK programu .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)

**openSUSE 24**

* .NET core SDK 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)
* Zestaw SDK programu .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)

---

> [!IMPORTANT]
> Jeśli masz problemy z instalacją .NET Core w obsługiwanych dystrybucji systemu Linux/wersji, poszukaj z zainstalowanych dystrybucje/wersji następujące tematy:
> * [.NET core 2.1 znane problemy](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [.NET core 2.0 znane problemy](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [.NET core 1.1 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [.NET core 1.0 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0)