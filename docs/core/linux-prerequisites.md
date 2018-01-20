---
title: "Wymagania wstępne dotyczące platformy .NET Core w systemie Linux"
description: "Obsługiwane wersje systemu Linux i zależności platformy .NET Core na tworzenie, wdrażanie i uruchamianie aplikacji .NET Core na maszynach z systemem Linux."
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 12/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: d3c5dde443f848831f7c0585633339c35213357b
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a>Wymagania wstępne dotyczące platformy .NET Core w systemie Linux

W tym artykule opisano zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Linux. Obsługiwane Linux dystrybucje wersje i zależności, które należy wykonać dotyczą dwa sposoby tworzenia aplikacji platformy .NET Core w systemie Linux:

* [Wiersza polecenia z ulubionego edytora](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a>Obsługiwane wersje systemu Linux

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET core 2.0 traktuje Linux jako jeden system operacyjny. Brak jednej kompilacji systemu Linux (na architektura mikroukładu) dla obsługiwanych dystrybucjach systemu Linux.

NET Core 2.x jest obsługiwana w systemie Linux 64-bitowej (`x86_64` lub `amd64`) dystrybucje/wersji:

 * Red Hat Enterprise Linux 7
 * CentOS 7
 * Oracle Linux 7
 * Fedora 25, Fedora 26
 * Debian 8.7 lub nowszymi wersjami 
 * Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04
 * Linux mennic 18, Linux mennic 17
 * openSUSE 42,2 lub nowszej wersji
 * SUSE Linux Enterprise (SLES) 12 z dodatkiem SP2 lub nowszy

Zobacz [2.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) Pełna lista .NET Core 2.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Oprogramowanie .NET core 1.x jest obsługiwana w systemie Linux 64-bitowej (`x86_64` lub `amd64`) dystrybucje/wersji:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 24
* Debian 8.2 lub nowszymi wersjami
* Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*
 * Ubuntu 16.10 jest obsługiwana przez najnowszej wersji poprawki .NET Core 1.1
* Linux Mint 17
* openSUSE 42.1 lub nowszej wersji (.NET Core 1.1)

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
* libicu52 (dla 14.X)
* libicu55 (dla 16.X)
* libicu57 (dla 17.X)

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

`dotnet-install` Skrypty są używane do wykonywania instalacji bez uprawnień administratora, łańcuch narzędzi interfejsu wiersza polecenia i udostępnionych środowiska wykonawczego. Można pobrać skryptu z: https://dot.net/v1/dotnet-install.sh

Skrypt Instalatora bash jest używany w scenariuszach automatyzacji i instalacji bez uprawnień administratora. Ten skrypt również odczytuje przełączników programu PowerShell, dzięki czemu mogą być używane w przypadku skryptu w systemach Linux/OS X.

> [!IMPORTANT]
> Przed uruchomieniem skryptu, zainstalować wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a>Zainstaluj oprogramowanie .NET Core Red Hat Enterprise Linux (RHEL) 7

Aby zainstalować oprogramowanie .NET Core na RHEL 7:

1. Włącz kanału Red Hat .NET, dostępne w ramach Twojej subskrypcji RHEL 7.
    * Red Hat Enterprise 7 Server użyć:
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * Red Hat Enterprise 7 stacji roboczej użyć:
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * Red Hat Enterprise 7 HPC obliczeniowe węzła należy użyć:
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. Zainstaluj narzędzie scl.

    ```bash
    yum install scl-utils
    ```
    
3. Zainstaluj oprogramowanie .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Zainstaluj oprogramowanie .NET Core 2.0 SDK i środowiska uruchomieniowego:

   ```bash
   yum install rh-dotnet20
   ```

Włącz .NET Core SDK/środowiska uruchomieniowego 2.0 w danym środowisku:

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

Zainstaluj oprogramowanie .NET Core 1.1 SDK i środowiska uruchomieniowego:

   ```bash
   yum install rh-dotnetcore11
   ```

Włącz zestawu SDK programu .NET Core 1.1 i środowiska uruchomieniowego w danym środowisku:

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

**.NET Core 1.0**

Zainstaluj program .NET Core 1.0 SDK i środowiska uruchomieniowego:

   ```bash
   yum install rh-dotnetcore10
   ```

Włącz .NET Core 1.0 SDK i środowiska uruchomieniowego w danym środowisku:

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.

     ```bash
     dotnet --version
     ```

Red Hat .NET kanał dostępu do rejestracji Pomoc [rozdział 1 .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) w Red Hat.

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a>Zainstaluj oprogramowanie .NET Core dla Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 i Linux mennic 17, 18 mennic systemu Linux (64-bitowy)

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Zarejestruj klucz Product Microsoft jako zaufany.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. Skonfiguruj pakietów hosta żądanej wersji źródła danych.

   **Ubuntu 17.10**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   **Ubuntu 17.04**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 16.04 / Linux Mint 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 14.04 / Linux Mint 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. Zainstaluj oprogramowanie .NET Core.

   ```bash
   sudo apt-get install dotnet-sdk-2.1.3
   ```

4. Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. Skonfiguruj pakietów hosta żądanej wersji źródła danych.

   **Ubuntu 16.10**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  **Ubuntu 16.04 / Linux Mint 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   **Ubuntu 14.04 / Linux Mint 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. Zainstaluj program .NET Core 1.x Ubuntu lub mennic Linux:

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a>Zainstaluj oprogramowanie .NET Core Debian 8 lub Debian 9 (64-bitowy)

Aby zainstalować oprogramowanie .NET Core na Debian 8 lub Debian 9 (64 bity):

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

> [!NOTE]
> Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Zainstaluj składniki systemu.

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. Zarejestruj zaufanego klucza Product firmy Microsoft.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. Zarejestruj Product Microsoft źródła danych.

   **Debian 9 (Stretch)**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   **Debian 8 (Joasia)**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. Zainstaluj oprogramowanie .NET Core SDK.

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. Dodaj dotnet do ścieżki.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. Pobierz wymagania wstępne.

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. Pobierz pliki binarne .NET Core SDK (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. Wyodrębnij pliki binarne .NET Core SDK.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Dodaj dotnet do ścieżki.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a>Zainstaluj oprogramowanie .NET Core dla Fedora 24, Fedora 25 lub Fedora 26 (64-bitowy)

Aby zainstalować oprogramowanie .NET Core 2.x Fedora 26 lub Fedora 25 lub .NET Core 1.x na Fedora 24:

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

> [!NOTE]
> Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Fedora 26 lub Fedora 25**

2. Zarejestruj klucz podpisu firmy Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Dodaj produkt dotnet źródła danych.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. Zainstaluj oprogramowanie .NET Core SDK.

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. Dodaj dotnet do ścieżki.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Fedora 24**

2. Pobierz wymagania wstępne.

   ```bash
   sudo dnf install libunwind libicu
   ```

3. Pobierz plik binarny .NET Core SDK (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. Wyodrębnij pliki binarne .NET Core SDK.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Dodaj dotnet do ścieżki.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a>Zainstaluj oprogramowanie .NET Core CentOS 7.1 (64-bitowym) i Oracle Linux 7.1 (64-bitowy)

Aby zainstalować oprogramowanie .NET Core CentOS 7.1 (64-bitowym) i Oracle Linux 7.1 (64 bity):

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

> [!NOTE]
> Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Zarejestruj klucz podpisu firmy Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Dodaj Product firmy Microsoft, źródła danych.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. Zainstaluj oprogramowanie .NET Core SDK.

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. Dodaj do ścieżki dotnet

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. Pobierz wymagania wstępne.

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. Pobierz plik binarny .NET Core SDK (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. Wyodrębnij pliki binarne .NET Core SDK.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Dodaj dotnet do ścieżki.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a>Zainstaluj oprogramowanie .NET Core dla systemu SUSE Linux Enterprise Server (64-bitowy)

Aby zainstalować oprogramowanie .NET Core 2.x dla SUSE Linux Enterprise Server (SLES) 12 z dodatkiem SP2 (64 bity):

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

2. Dodaj produkt dotnet źródła danych.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. Zainstaluj oprogramowanie .NET Core SDK.

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. Dodaj dotnet do ścieżki.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a>Zainstaluj oprogramowanie .NET Core dla openSUSE (64-bitowy)

Aby zainstalować oprogramowanie .NET Core 2.x openSUSE lub .NET Core 1.x dla openSUSE (64 bity):

1. Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.

> [!NOTE]
> Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Zarejestruj klucz podpisu firmy Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Dodaj produkt dotnet źródła danych.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. Zainstaluj oprogramowanie .NET Core SDK.

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. Dodaj dotnet do ścieżki.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. Pobierz wymagania wstępne.

   ```bash
   sudo zypper install libunwind libicu
   ```

3. Pobierz plik binarny .NET Core SDK (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. Wyodrębnij pliki binarne .NET Core SDK.
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Dodaj dotnet do ścieżki.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> Jeśli masz problemy z instalacją 2.x .NET Core w obsługiwanych dystrybucji systemu Linux/wersji, należy skontaktować się [2.0 znane problemy](https://github.com/dotnet/core/tree/master/release-notes/2.0) tematu dla programu zainstalowanych dystrybucje/wersji. 
>
> Jeśli masz problemy z instalacją 1.x .NET Core w obsługiwanych dystrybucji systemu Linux/wersji, należy skontaktować się [1.0.0 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) i [1.0.1 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) tematy z zainstalowanych dystrybucji / wersje.
