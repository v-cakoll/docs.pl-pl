---
title: Wymagania wstępne dla platformy .NET Core w systemie Linux
description: Obsługiwane wersje systemu Linux i zależności platformy .NET Core, opracowywanie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem Linux.
author: jralexander
ms.author: johalex
ms.date: 08/20/2018
ms.openlocfilehash: d0e5b203dc8e1ec6807f28de7d910c74a2ffe665
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506852"
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

**.NET Core 2.1**

NET Core 2.1 jest obsługiwana na poniższe dystrybucje systemu Linux/wersje:

* Red Hat Enterprise Linux 7, 6 - 64-bitowych (`x86_64` lub `amd64`)
* CentOS 7 - 64-bitowy (`x86_64` lub `amd64`) 
* Oracle Linux 7 - 64-bitowy (`x86_64` lub `amd64`) 
* Fedora 28, 27 — 64-bitowych (`x86_64` lub `amd64`) 
* Debian 9 (wersja 64-bitowa, ARM32), 8.7 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)
* Ubuntu 18.04 (64-bitowy, ARM32), 16.04, 14.04 - 64-bitowych (`x86_64` lub `amd64`)
* Linux mennic 18, 17 — 64-bitowych (`x86_64` lub `amd64`)
* openSUSE 42.3 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)
* SUSE Linux Enterprise (SLES) 12 z dodatkiem Service Pack 2 lub nowszego - 64-bitowych (`x86_64` lub `amd64`)
* Firma Alpine Linux 3.7 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)

Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) pełną listę platformy .NET Core 2.1 obsługiwane systemy operacyjne, dystrybucji i wersji poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.

**.NET Core 2.0**

NET Core 2.0 jest obsługiwana w następujących Linux 64-bitowych (`x86_64` lub `amd64`) dystrybucje/wersji:

* Red Hat Enterprise Linux 7, 6
* CentOS 7
* Oracle Linux 7
* Fedora 27
* Debian 9 8.7 lub nowsze wersje
* Naciśnięcie i przytrzymanie 18.04 Ubuntu 16.04, 14.04
* Linux mennic 18, 17
* openSUSE 42.3 lub nowsze wersje
* SUSE Linux Enterprise (SLES) 12 z dodatkiem Service Pack 2 lub nowszy

Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.0](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pełną listę .NET Core 2.0 obsługiwane systemy operacyjne, dystrybucji i wersji poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

.NET core 1.x jest obsługiwane na następujących Linux 64-bitowych (`x86_64` lub `amd64`) dystrybucje/wersji:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1) 27
* Debian 8.2 lub nowsze wersje
* 18.04 (.NET Core 1.1), Ubuntu 16.04, 14.04
* Linux Mint 17
* openSUSE 42.3 lub nowszej wersji (.NET Core 1.1)

Zobacz [obsługiwanych wersjach systemu operacyjnego programu .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) kompletną listę platformy .NET Core 1.x obsługiwane systemy operacyjne, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.

---

## <a name="linux-distribution-dependencies"></a>Zależności do dystrybucji systemu Linux

Poniżej mają być przykłady. Na wybranej dystrybucji systemu Linux, nazwy i wersje dokładny mogą się nieco różnić.

### <a name="ubuntu"></a>Ubuntu

Dystrybucje systemu Ubuntu wymagają następujących bibliotek zainstalowane:

* liblttng-ust0
* libcurl3
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

[Skryptów instalacji dotnet](./tools/dotnet-install-script.md) są używane do wykonywania instalacji bez uprawnień administratora, łańcuch narzędzi interfejsu wiersza polecenia i udostępnionego środowiska uruchomieniowego. Możesz pobrać skrypt z [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).

Domyślnie skrypt zainstalowanie najnowszej wersji "LTS", która jest obecnie .NET Core 1.1. Do zainstalowania platformy .NET Core 2.x, uruchom skrypt przy użyciu następującego przełącznika:

```console
./dotnet-install.sh -c Current
```

Skrypt powłoki bash Instalatora jest używany w scenariuszach automatyzacji oraz przed instalacjami bez uprawnień administratora. Ten skrypt odczytuje również przełączników programu PowerShell, dzięki czemu może być używany ze skryptem w systemach Linux/OS X.

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a>Zainstaluj platformę .NET Core, obsługiwane wersje Red Hat Enterprise Linux (RHEL)

Aby zainstalować .NET Core na temat obsługiwanych wersji systemu RHEL:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**.NET core 2.1**

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Aby uzyskać najnowsze platformy .NET Core 2.1 na informacje dotyczące instalacji w systemie Red Hat Enterprise Linux, zobacz [.NET Core 2.1 — wprowadzenie](https://access.redhat.com/documentation/en-us/net_core/2.1/html/getting_started_guide/)

**.NET Core 2.0**

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Aby uzyskać najnowsze .NET Core 2.0 na informacje dotyczące instalacji w systemie Red Hat Enterprise Linux, zobacz [.NET Core 2.0 — wprowadzenie](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/) 

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2.  Aby uzyskać najnowsze .NET Core 1.1 na informacje dotyczące instalacji w systemie Red Hat Enterprise Linux, zobacz [.NET Core 1.1 — wprowadzenie](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)
     
**.NET Core 1.0**

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2.  Aby uzyskać najnowsze platformy .NET Core 1.0 na informacje dotyczące instalacji w systemie Red Hat Enterprise Linux, zobacz [.NET Core 1.0 — wprowadzenie](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)

Aby łatwiej rejestracji dostęp do kanału Red Hat .NET, zobacz [rozdział 1 .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) w systemie Red Hat.

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a>Zainstaluj program .NET Core dla obsługiwanych obrazów systemów Ubuntu i mennic Linux dystrybucje/wersji (64-bitowy)

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Zainstaluj program .NET Core 2.x na obsługiwanych obrazów systemów Ubuntu i mennic Linux dystrybucje/wersji (wersja 64-bitowa):

**.NET Core 2.0**

|Środowiska uruchomieniowe / zestawów SDK          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux mennic 18|Ubuntu 14.04 / Linux mennic 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|Środowisko uruchomieniowe programu .NET core 2.0.9  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.9)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.9)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.9)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.9)            |
|Środowisko uruchomieniowe programu .NET core 2.0.8  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.8)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.8)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.8)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.8)            |
|Środowisko uruchomieniowe programu .NET core 2.0.7  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.7)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.7)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.7)            |
|Środowisko uruchomieniowe programu .NET core 2.0.6  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.6)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|Środowisko uruchomieniowe programu .NET core 2.0.5  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.5)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|.NET core SDK 2.1.202    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.202)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.202)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.202)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.202)            |
|.NET core SDK 2.1.201    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.201)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.201)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.201)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.201)            |
|.NET core SDK 2.1.200    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.200)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.200)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.200)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.200)            |
|.NET core SDK 2.1.105    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.105)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.105)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.105)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.105)            |
|.NET core SDK 2.1.103    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.103)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|.NET core SDK 2.0.3      |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.3)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |
|.NET core 2.0.0 SDK      |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.0)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.0)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.0)          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.0)            |

**.NET core 2.1**

>[!IMPORTANT]
> Aby użyć platformy .NET Core 2.1 przy użyciu programu Visual Studio, musisz [instalacji programu Visual Studio 2017 w wersji 15.7 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Środowiska uruchomieniowe / zestawów SDK          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux mennic 18|Ubuntu 14.04 / Linux mennic 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|Środowisko uruchomieniowe programu .NET core 2.1.2          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.2)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.2)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.2)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.2)            |
|.NET core SDK 2.1.400     |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.400)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.400)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.400)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.400)            |
|.NET core SDK 2.1.302     |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.302)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.302)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.302)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.302)            |
|Środowisko uruchomieniowe programu .NET core 2.1.1          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.1)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.1)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.1)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.1)            |
|.NET core SDK 2.1.301     |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.301)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.301)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.301)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.301)            |
|Środowisko uruchomieniowe programu .NET core 2.1.0          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0)            |
|.NET core SDK 2.1.300     |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300)|[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300)            |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300)            |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Zainstaluj program .NET Core 1.x na obsługiwanych obrazów systemów Ubuntu i mennic Linux dystrybucje/wersji (wersja 64-bitowa):

| Środowiska uruchomieniowe / zestawów SDK         |Ubuntu 16.04 / Linux mennic 18|Ubuntu 14.04 / Linux mennic 17|
|-------------------------|----------------------------|----------------------------|
|Środowisko uruchomieniowe programu .NET core 1.1.9  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.1.8  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.1.7  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.1.6  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.1.5  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.1.4  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.0.10 |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.0.9  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.0.8  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.0.7  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.0.5  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-14.04-x64-binaries)            |
|Środowisko uruchomieniowe programu .NET core 1.0.4  |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.10     |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.9      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.8      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.7      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.5      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.4      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.0.4      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core 1.0.1 zestawu SDK      |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[Łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a>Zainstaluj program .NET Core dla obsługiwanych wersji systemu Debian (64-bitowy)

Aby zainstalować .NET Core na temat obsługiwanych wersji systemu Debian (64-bitowy):

> [!NOTE]
> Katalog kontrolowanej przez użytkownika jest wymagana instalacja z tar.gz systemu Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Zainstaluj program .NET Core 2.x na obsługiwane wersje Debian (wersja 64-bitowa):

**.NET Core 2.0**

|Środowiska uruchomieniowe / zestawów SDK          |Debian 9       |Debian 8       |
|-------------------------|---------------|---------------|
|Środowisko uruchomieniowe programu .NET core 2.0.9  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.9)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.9)   |
|Środowisko uruchomieniowe programu .NET core 2.0.8  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.8)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.8)   |
|Środowisko uruchomieniowe programu .NET core 2.0.7  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.7)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.7)   |
|Środowisko uruchomieniowe programu .NET core 2.0.6  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|Środowisko uruchomieniowe programu .NET core 2.0.5  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|Środowisko uruchomieniowe programu .NET core 2.0.3  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.3)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.3)   |
|Środowisko uruchomieniowe programu .NET core 2.0.0  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.0)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.0)   |
|.NET core SDK 2.1.202    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.202)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.202)   |
|.NET core SDK 2.1.201    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.201)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.201)   |
|.NET core SDK 2.1.200    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.200)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.200)   |
|.NET core SDK 2.1.105    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET core SDK 2.1.105    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET core SDK 2.1.104    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.104)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.104)   |
|.NET core SDK 2.1.103    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|.NET core SDK 2.1.102    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.102)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.102)   |
|.NET core SDK 2.1.101    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.101)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.101)   |
|.NET core SDK 2.0.3      |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |
|.NET core 2.0.0 SDK      |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.0)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.0)   |

**.NET core 2.1**

>[!IMPORTANT]
> Aby użyć platformy .NET Core 2.1 przy użyciu programu Visual Studio, musisz [instalacji programu Visual Studio 2017 w wersji 15.7 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Środowiska uruchomieniowe / zestawów SDK                  |Debian 9       |Debian 8       |
|---------------------------------|---------------|---------------|
|Środowisko uruchomieniowe programu .NET core 2.1.2          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.2)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.2)   |
|.NET core SDK 2.1.400        |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.400)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.400)        |
|.NET core SDK 2.1.302        |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.302)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.302)        |
|Środowisko uruchomieniowe programu .NET core 2.1.1          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.1)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.1)   |
|.NET core SDK 2.1.301        |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.301)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.301)        |
|Środowisko uruchomieniowe programu .NET core 2.1.0          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0)   |
|.NET core SDK 2.1.300        |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300)   |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300)        |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Zainstaluj program .NET Core 1.x na Debian 9 lub Debian 8:

* Środowisko uruchomieniowe programu .NET core 1.1.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.6 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.5 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.2 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.0 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.0-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.10 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.5 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-debian-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-debian-x64-binaries)
* Zestaw .NET core SDK 1.1.10 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-debian-x64-binaries)
* Zestaw .NET core SDK 1.1.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-debian-x64-binaries)
* Zestaw .NET core SDK w wersji 1.1.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)
* Zestaw .NET core SDK 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)
* Zestaw .NET core SDK 1.1.5 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-debian-x64-binaries)
* Zestaw .NET core SDK 1.1.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-debian-x64-binaries)
* Zestaw .NET core SDK 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)
* Zestaw SDK platformy .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a>Zainstaluj program .NET Core dla obsługiwanych wersji Fedora (64-bitowy)

Aby zainstalować .NET Core w obsługiwanych wersjach Fedora:

> [!NOTE]
> Katalog kontrolowanej przez użytkownika jest wymagana instalacja z tar.gz systemu Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Zainstaluj program .NET Core 2.x w obsługiwanych wersjach Fedora (wersja 64-bitowa):

**.NET Core 2.0**

|Środowiska uruchomieniowe / zestawów SDK          |Fedora 26 lub nowszy |Fedora 25 lub poprzedniego |
|-------------------------|-------------------|----------------------|
|Środowisko uruchomieniowe programu .NET core 2.0.9  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.9)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.9)           |
|Środowisko uruchomieniowe programu .NET core 2.0.8  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.8)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.8)           |
|Środowisko uruchomieniowe programu .NET core 2.0.7  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.7)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.7)           |
|Środowisko uruchomieniowe programu .NET core 2.0.6  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|Środowisko uruchomieniowe programu .NET core 2.0.5  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|Środowisko uruchomieniowe programu .NET core 2.0.3  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.3)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.3)           |
|Środowisko uruchomieniowe programu .NET core 2.0.0  |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.0)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.0)           |
|.NET core SDK 2.1.200    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.200)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.200)           |
|.NET core SDK 2.1.105    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.105)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.105)           |
|.NET core SDK 2.1.103    |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|.NET core SDK 2.0.3      |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

**.NET core 2.1**

>[!IMPORTANT]
> Aby użyć platformy .NET Core 2.1 przy użyciu programu Visual Studio, musisz [instalacji programu Visual Studio 2017 w wersji 15.7 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Środowiska uruchomieniowe / zestawów SDK                  |Fedora 28          |Fedora 27             |
|---------------------------------|-------------------|----------------------|
|Środowisko uruchomieniowe programu .NET core 2.1.2          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.2)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.2)           |
|.NET core SDK 2.1.400          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.400)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.400)           |
|.NET core SDK 2.1.302          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.302)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.302)           |
|Środowisko uruchomieniowe programu .NET core 2.1.1          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.1)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.1)           |
|.NET core SDK 2.1.301          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.301)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.301)           |
|Środowisko uruchomieniowe programu .NET core 2.1.0          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.0)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0)           |
|.NET core SDK 2.1.300          |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.300)       |[Łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.300)           |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Instalowanie wersji Fedora 1.x obsługiwane platformy .NET Core (64-bitowy):

**Fedora 24**

* Środowisko uruchomieniowe programu .NET core 1.1.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-fedora-24-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.6 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.5 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-fedora-24-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-24-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.2 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-24-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-24-x64-binaries)
* Zestaw .NET core SDK 1.1.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-fedora-24-x64-binaries)
* Zestaw .NET core SDK w wersji 1.1.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)
* Zestaw .NET core SDK 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)
* Zestaw .NET core SDK 1.1.5 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries)
* Zestaw .NET core SDK 1.1.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries)
* Zestaw SDK platformy .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

**Fedora 23**

* Środowisko uruchomieniowe programu .NET core 1.1.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-23-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.2 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-23-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-23-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-fedora-23-x64-binaries)
* Zestaw .NET core SDK 1.1.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4linux-fedora-23-x64-binaries)
* Zestaw .NET core SDK 1.1.2 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries)
* Zestaw .NET core SDK 1.1.2 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries)
* Zestaw .NET core SDK 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)
* Zestaw SDK platformy .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a>Zainstaluj platformę .NET Core, obsługiwane CentOS i Oracle Linux dystrybucje/wersji (64-bitowy)

Aby zainstalować .NET Core obsługiwane CentOS i Oracle Linux dystrybucje/wersji (64-bitowy):

> [!NOTE]
> Katalog kontrolowanej przez użytkownika jest wymagana instalacja z tar.gz systemu Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Zainstaluj program .NET Core 2.x na obsługiwane CentOS i Oracle Linux dystrybucje/wersji (64-bitowy):

**.NET Core 2.0**

* Środowisko uruchomieniowe programu .NET core 2.0.9 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.9)
* Środowisko uruchomieniowe programu .NET core 2.0.8 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.8)
* Środowisko uruchomieniowe programu .NET core 2.0.7 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.7)
* Środowisko uruchomieniowe programu .NET core 2.0.6 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* Środowisko uruchomieniowe programu .NET core 2.0.5 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)
* Środowisko uruchomieniowe programu .NET core 2.0.3 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.3)
* Środowisko uruchomieniowe programu .NET core 2.0.0 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.0)
* Zestaw .NET core SDK 2.1.202 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.202)
* Zestaw .NET core SDK 2.1.201 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.201)
* Zestaw .NET core SDK 2.1.200 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.200)
* Zestaw .NET core SDK 2.1.105 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.105)
* Zestaw .NET core SDK 2.1.104 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.104)
* Zestaw .NET core SDK 2.1.103 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)
* Zestaw .NET core SDK 2.1.102 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.102)
* Zestaw .NET core SDK 2.0.3 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)
* Zestaw SDK platformy .NET core 2.0.0 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> Aby użyć platformy .NET Core 2.1 przy użyciu programu Visual Studio, musisz [instalacji programu Visual Studio 2017 w wersji 15.7 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

* Środowisko uruchomieniowe programu .NET core 2.1.2 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.2)
* Zestaw .NET core SDK 2.1.400 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.400)
* Zestaw .NET core SDK 2.1.302 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.302)
* Środowisko uruchomieniowe programu .NET core 2.1.1 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.1)
* Zestaw .NET core SDK 2.1.301 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.301)
* Środowisko uruchomieniowe programu .NET core 2.1.0 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0)
* Zestaw .NET core SDK 2.1.300 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Zainstaluj program .NET Core 1.x obsługiwane CentOS i Oracle Linux dystrybucje/wersji (64-bitowy):

* Środowisko uruchomieniowe programu .NET core 1.1.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.6 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.5 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.2 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.12 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.12-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.11 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.11-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.10 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.5 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-centos-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-centos-x64-binaries)
* Zestaw .NET core SDK 1.1.10 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-centos-x64-binaries)
* Zestaw .NET core SDK 1.1.9 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-centos-x64-binaries)
* Zestaw .NET core SDK w wersji 1.1.8 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)
* Zestaw .NET core SDK 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)
* Zestaw .NET core SDK 1.1.5 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-centos-x64-binaries)
* Zestaw .NET core SDK 1.1.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-centos-x64-binaries)
* Zestaw .NET core SDK 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)
* Zestaw SDK platformy .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a>Zainstaluj program .NET Core dla obsługiwanych SUSE Linux Enterprise Server i OpenSUSE dystrybucje/wersji (64-bitowy)

Do zainstalowania platformy .NET Core 2.x dla obsługiwanych SUSE Linux Enterprise Server i OpenSUSE dystrybucje/wersji (64-bitowy):

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Zainstaluj program .NET Core 2.x na obsługiwanych SUSE Linux Enterprise Server i OpenSUSE dystrybucje/wersji (wersja 64-bitowa):

**.NET Core 2.0**

**SUSE Linux Enterprise Server**

* Środowisko uruchomieniowe programu .NET core 2.0.9 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.9)
* Środowisko uruchomieniowe programu .NET core 2.0.8 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.8)
* Środowisko uruchomieniowe programu .NET core 2.0.7 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.7)
* Środowisko uruchomieniowe programu .NET core 2.0.6 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.6)
* Środowisko uruchomieniowe programu .NET core 2.0.5 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.5)
* Środowisko uruchomieniowe programu .NET core 2.0.3 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.3)
* Środowisko uruchomieniowe programu .NET core 2.0.0 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.0)
* Zestaw .NET core SDK 2.1.202 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.202)
* Zestaw .NET core SDK 2.1.201 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.201)
* Zestaw .NET core SDK 2.1.200 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.200)
* Zestaw .NET core SDK 2.1.105 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.105)
* Zestaw .NET core SDK 2.1.104 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.104)
* Zestaw .NET core SDK 2.1.103 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.103)
* Zestaw .NET core SDK 2.1.102 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.102)
* Zestaw .NET core SDK 2.1.101 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.101)
* Zestaw .NET core SDK 2.1.100 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.100)
* Zestaw .NET core SDK w wersji 2.1.4 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.4)
* Zestaw .NET core SDK 2.1.2 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.2)
* Zestaw .NET core SDK 2.0.3 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.3)
* Zestaw SDK platformy .NET core 2.0.0 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.0)

**openSUSE**

* Środowisko uruchomieniowe programu .NET core 2.0.9 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.9)
* Środowisko uruchomieniowe programu .NET core 2.0.8 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.8)
* Środowisko uruchomieniowe programu .NET core 2.0.7 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.7)
* Środowisko uruchomieniowe programu .NET core 2.0.6 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)
* Środowisko uruchomieniowe programu .NET core 2.0.5 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)
* Środowisko uruchomieniowe programu .NET core 2.0.3 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.3)
* Środowisko uruchomieniowe programu .NET core 2.0.0 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.0)
* Zestaw .NET core SDK 2.1.202 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.202)
* Zestaw .NET core SDK 2.1.201 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.201)
* Zestaw .NET core SDK 2.1.200 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.200)
* Zestaw .NET core SDK 2.1.105 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.105)
* Zestaw .NET core SDK 2.1.103 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)
* Zestaw .NET core SDK 2.1.102 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.102)
* Zestaw .NET core SDK 2.1.101 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.101)
* Zestaw .NET core SDK 2.1.100 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.100)
* Zestaw .NET core SDK w wersji 2.1.4 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.4)
* Zestaw .NET core SDK 2.1.2 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.2)
* Zestaw .NET core SDK 2.0.3 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)
* Zestaw SDK platformy .NET core 2.0.0 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> Aby użyć platformy .NET Core 2.1 przy użyciu programu Visual Studio, musisz [instalacji programu Visual Studio 2017 w wersji 15.7 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

**SUSE Linux Enterprise Server**

* Środowisko uruchomieniowe programu .NET core 2.1.2 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.2)
* Zestaw .NET core SDK 2.1.400 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.400)
* Zestaw .NET core SDK 2.1.302 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.302)
* Środowisko uruchomieniowe programu .NET core 2.1.1 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.1)
* Zestaw .NET core SDK 2.1.301 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.301)
* Środowisko uruchomieniowe programu .NET core 2.1.0 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0)
* Zestaw .NET core SDK 2.1.300 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300)

**openSUSE**

* Środowisko uruchomieniowe programu .NET core 2.1.2 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.2)
* Zestaw .NET core SDK 2.1.400 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.400)
* Zestaw .NET core SDK 2.1.302 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.302)
* Środowisko uruchomieniowe programu .NET core 2.1.1 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.1)
* Zestaw .NET core SDK 2.1.301 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.301)
* Środowisko uruchomieniowe programu .NET core 2.1.0 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0)
* Zestaw .NET core SDK 2.1.300 [łącze instalacji](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersje programu .NET Core w systemie.

2. Zainstaluj program .NET Core 1.x na obsługiwanych SUSE Linux Enterprise Server i OpenSUSE dystrybucje/wersji (wersja 64-bitowa):

**SUSE Linux Enterprise Server 13.2**

* Środowisko uruchomieniowe programu .NET core 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)
* Środowisko uruchomieniowe programu .NET core 1.1.6 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)
* Zestaw .NET core SDK 1.1.7 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)
* Zestaw .NET core SDK 1.0.4 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-13.2-x64-binaries)
* Zestaw SDK platformy .NET core 1.0.1 [łącze instalacji](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-13.2-x64-binaries)

---

## <a name="install-net-core-for-supported-alpine-linux-versions-64-bit"></a>Zainstaluj program .NET Core dla obsługiwanych wersji Alpine Linux (64-bitowy)

> [!NOTE]
> Katalog kontrolowanej przez użytkownika jest wymagana instalacja z tar.gz systemu Linux.

Pobierz i wykonaj instrukcje dotyczące instalacji platformy .NET Core 2.1 dla obsługiwanych wersji systemu Alpine Linux (64-bitowy) z następujących łączy:

* Środowisko uruchomieniowe programu .NET core 2.1.2 [link pobierania](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.2-linux-x64-alpine-binaries)
* Zestaw .NET core SDK 2.1.400 [link pobierania](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.400-linux-x64-alpine-binaries)
* Zestaw .NET core SDK 2.1.302 [link pobierania](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.302-linux-x64-alpine-binaries)
* Środowisko uruchomieniowe programu .NET core 2.1.1 [link pobierania](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.1-linux-x64-alpine-binaries)
* Zestaw .NET core SDK 2.1.301 [link pobierania](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.301-linux-x64-alpine-binaries)
* Środowisko uruchomieniowe programu .NET core 2.1.0 [link pobierania](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.0-linux-x64-alpine-binaries)
* Zestaw .NET core SDK 2.1.300 [link pobierania](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.300-linux-x64-alpine-binaries)

> [!IMPORTANT]
> Jeśli masz problemy z instalacją .NET Core w obsługiwanych dystrybucji systemu Linux/wersji dla Twojej dystrybucji zainstalowanych/wersji należy zapoznać się następujące tematy:
> * [Znane problemy dotyczące programu .NET core 2.1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [Znane problemy dotyczące programu .NET core 2.0](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [Znane problemy dotyczące programu .NET core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [Znane problemy dotyczące programu .NET core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
