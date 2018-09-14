---
title: Przy użyciu zestawu .NET Core SDK i narzędzi w ciągłej integracji (CI)
description: Informacje na temat użycia programu .NET Core SDK i jego narzędzi na serwerze kompilacji.
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.openlocfilehash: 207a6740f2a483d532c194b2bf8112898e9c3463
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521051"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Przy użyciu zestawu .NET Core SDK i narzędzi w ciągłej integracji (CI)

## <a name="overview"></a>Omówienie

W tym dokumencie przedstawiono przy użyciu zestawu .NET Core SDK i jego narzędzi na serwerze kompilacji. .NET Core narzędzi działa zarówno interaktywnie, gdzie deweloper typów poleceń w poleceniu monit i automatycznie w przypadku, gdy serwer ciągłej integracji (CI) uruchamia skrypt kompilacji. Poleceń, opcje, dane wejściowe i wyjściowe są takie same, a tylko rzeczy, które podasz służą do nabycia narzędzi i systemu do kompilowania aplikacji. Ten dokument koncentruje się na scenariuszach nabycia narzędzi do ciągłej integracji z zaleceniami dotyczącymi projektowania i struktury skrypty kompilacji.

## <a name="installation-options-for-ci-build-servers"></a>Opcje instalacji dla ciągłej integracji, serwerów kompilacji

### <a name="using-the-native-installers"></a>Przy użyciu natywnych instalatorów

Natywnych instalatorów są dostępne dla systemu macOS, Linux i Windows. Pliki instalacyjne wymagają dostępu administratora ("sudo") do serwera kompilacji. Zalet za pomocą natywnego Instalatora jest, że instaluje wszystkie zależności natywnych wymaganych narzędzi do uruchamiania. Natywnych instalatorów oferują również systemowe instalacji zestawu SDK.

użytkowników systemu macOS należy używać programów instalacyjnych pakietu. W systemie Linux, wybór jest przy użyciu Menedżera pakietów na podstawie źródła danych, takich jak polecenia apt-get dla systemu Ubuntu lub yum, centos, lub za pomocą pakietów, Mistrzostwo DEB lub obr. / min. W Windows użyj Instalatora MSI.

Najnowsze stabilne pliki binarne znajdują się w [Rozpoczynanie pracy z platformą .NET Core](https://aka.ms/dotnetcoregs). Jeśli chcesz użyć narzędzi najnowsze (i potencjalnie niestabilne) w wersji wstępnej, należy użyć linków dostępnych na [repozytorium GitHub interfejsu wiersza poleceniadotnet/](https://github.com/dotnet/cli#installers-and-binaries). Dystrybucje systemu Linux `tar.gz` archiwów (znany także jako `tarballs`) są dostępne; Instalowanie programu .NET Core za pomocą skryptów instalacji, w archiwum.

### <a name="using-the-installer-script"></a>Przy użyciu skryptu Instalatora

Przy użyciu skryptu Instalatora umożliwia innych niż administracyjne instalacji na serwerze kompilacji i łatwe uzyskiwanie narzędzi automatyzacji. Skrypt dba o pobranie narzędzi i wyodrębnij go do domyślnej lub określonej lokalizacji do użycia. Można również określić wersję narzędzia, które mają zostać zainstalowane i czy chcesz zainstalować całego zestawu SDK lub tylko udostępnionego środowiska uruchomieniowego.

Skrypt Instalatora jest zautomatyzowany do uruchomienia na początku kompilacji, aby pobrać i zainstalować odpowiednią wersję zestawu SDK. *Żądaną wersję* jest niezależnie od wersji zestawu SDK swoje projekty wymagają do kompilacji. Skrypt umożliwia zainstalowanie zestawu SDK w katalogu lokalnym na serwerze, uruchomić narzędzia w lokalizacji instalacji i wyczyścić (a lub zezwala na CI oczyszczania) po kompilacji. Zapewnia to, że hermetyzacji i izolacji całego procesu kompilacji. Odwołanie do skryptu instalacji znajduje się w [instalacji dotnet](dotnet-install-script.md) tematu.

> [!NOTE]
> **Azure DevOps Services**
>
> Przy użyciu skryptu Instalatora, natywne zależności nie są instalowane automatycznie. Musisz zainstalować zależności natywnych, jeśli system operacyjny nie ma ich. Zobacz listę wymagań wstępnych w [natywnych wymagania wstępne platformy .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) tematu.

## <a name="ci-setup-examples"></a>Przykłady konfiguracji ciągłej integracji

W tej sekcji opisano instalację ręczną przy użyciu skryptu programu PowerShell lub bash, wraz z opisami kilka oprogramowania jako rozwiązania ciągłej integracji usługi (SaaS). Rozwiązania SaaS CI omówione są [rozwiązania Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), i [ kompilacji](https://docs.microsoft.com/azure/devops/build-release/index).

### <a name="manual-setup"></a>Instalacji ręcznej

Każda usługa SaaS ma swoje własne metody tworzenia i konfigurowania procesu kompilacji. Jeśli używasz innego rozwiązania SaaS niż te wymienione, lub wymagać dostosowania poza obsługą wstępnie spakowanej, należy wykonać co najmniej pewne czynności konfiguracyjne.

Ogólnie rzecz biorąc instalacji ręcznej należy uzyskać wersję narzędzia (lub nocnych najnowszej kompilacji narzędzi) i uruchomić skrypt kompilacji. Można użyć programu PowerShell lub bash skrypt służący do organizowania poleceń platformy .NET Core lub użyć pliku projektu, który zawiera omówienie procesu kompilacji. [Sekcji aranżacji](#orchestrating-the-build) zapewnia więcej szczegółów na temat tych opcji.

Po utworzeniu skryptu, który wykonuje ręcznego CI build instalacji serwera, użyj go na komputerze deweloperskim do kompilacji kodu lokalnie do celów testowych. Po upewnieniu się, czy skrypt działa dobrze lokalnie, wdrożyć serwer kompilacji ciągłej integracji. Stosunkowo prosty skrypt programu PowerShell pokazuje, jak uzyskać zestaw .NET Core SDK i zainstaluj go na serwerze kompilacji Windows:

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it
#   does, it's removed. This is not strictly required, but it's a
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

Możesz podać implementacja dla procesu kompilacji na końcu skryptu. Skrypt uzyskuje narzędzia, a następnie uruchamia proces kompilacji. W przypadku komputerów UNIX poniższego skryptu powłoki systemowej wykonuje akcje opisane w skrypcie programu PowerShell w podobny sposób:

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a>Rozwiązania Travis CI

Można skonfigurować [rozwiązania Travis CI](https://travis-ci.org/) można zainstalować przy użyciu zestawu .NET Core SDK `csharp` języka i `dotnet` klucza. Zobacz oficjalna dokumentacja rozwiązania Travis CI na [tworzenia języka C#, F # lub projekcie Visual Basic](https://docs.travis-ci.com/user/languages/csharp/) Aby uzyskać więcej informacji. Należy zauważyć, jak dostęp do informacji rozwiązania Travis CI, obsługiwane społeczności `language: csharp` identyfikator języka działa dla wszystkich języków .NET, w tym języka F # i platformy Mono.

Rozwiązania Travis CI działa zarówno z systemem macOS (OS X 10.11, OS X 10.12) i systemu Linux (Ubuntu 14.04) zadania w *kompilacji macierzy*, gdzie należy określić kombinacji środowiska uruchomieniowego, środowiska i wyjątki/dołączenia do obejmują swojej kombinacji kompilacji dla aplikacji. Zobacz [. przykład travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) pliku i [dostosowywania kompilacji](https://docs.travis-ci.com/user/customizing-the-build) w dokumentacji rozwiązania Travis CI, aby uzyskać więcej informacji. Narzędzia oparte na MSBuild obejmują LTS (1.0.x) i bieżącego środowiska uruchomieniowe (1.1.x) w pakiecie; Dlatego po zainstalowaniu zestawu SDK, otrzymasz wszystko, czego potrzebujesz do tworzenia.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) instaluje .NET Core 1.0.1 SDK `Visual Studio 2017` budowania obrazu procesu roboczego. Inne obrazy kompilacji z różnymi wersjami programu .NET Core SDK są dostępne; zobacz [przykład appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) i [kompilowanie obrazów procesu roboczego](https://www.appveyor.com/docs/build-environment/#build-worker-images) temat w dokumentacji usług AppVeyor, aby uzyskać więcej informacji.

Pliki binarne .NET Core SDK są pobierane i rozpakowanej w podkatalogu przy użyciu skryptu instalacji, a następnie są one dodawane do `PATH` zmiennej środowiskowej. Dodaj macierz kompilacji, aby uruchomić testy integracji z wieloma wersjami programu .NET Core SDK:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Usługom DevOps platformy Azure

Skonfiguruj usługom DevOps platformy Azure do kompilowania projektów .NET Core przy użyciu jednej z następujących podejść:

1. Uruchom skrypt z [kroku instalacji ręcznej](#manual-setup) przy użyciu poleceń.
1. Tworzenie kompilacji składa się z kilku zadań kompilacji wbudowanych usługom DevOps platformy Azure, które są skonfigurowane do używania narzędzi .NET Core.

Oba rozwiązania są prawidłowe. Za pomocą skryptu instalacji ręcznej, możesz kontrolować wersję narzędzia, które otrzymujesz, ponieważ możesz pobrać jako część kompilacji. Kompilacja jest uruchamiana ze skryptu, który należy utworzyć. W tym temacie omówiono tylko opcji ręcznej. Aby uzyskać więcej informacji na temat tworzenia kompilacji dzięki usługom DevOps platformy Azure można tworzyć zadania, odwiedź usługom DevOps platformy Azure [ciągłej integracji i ciągłego wdrażania](https://docs.microsoft.com/azure/devops/build-release/index) tematu.

Aby użyć skryptu instalacji ręcznej w usługom DevOps platformy Azure, Utwórz nową definicję kompilacji i określ skrypt do uruchomienia dla kroku kompilacji. Jest to realizowane przy użyciu interfejsu użytkownika usługom DevOps platformy Azure:

1. Rozpocznij od utworzenia nowej definicji kompilacji. Po osiągnięciu ekran, który udostępnia opcję, aby określić, jakiego rodzaju kompilacji chcesz utworzyć, wybierz **pusty** opcji.

   ![Wybierając definicję kompilacji pusty](./media/using-ci-with-cli/screen1.png)

1. Po skonfigurowaniu repozytorium do tworzenia, użytkownik jest kierowany do definicji kompilacji. Wybierz **Dodaj krok kompilacji**:

   ![Dodawanie kroku kompilacji](./media/using-ci-with-cli/screen2.png)

1. Pojawi się informacja o **wykazu zadań**. Katalog zawiera zadania, których używasz w kompilacji. Ponieważ masz skrypt, wybierz opcję **Dodaj** przycisku **programu PowerShell: Uruchom skrypt programu PowerShell**.

   ![Dodawanie kroku skrypt programu PowerShell](./media/using-ci-with-cli/screen3.png)

1. Skonfiguruj kroku kompilacji. Dodaj skrypt z repozytorium, którą tworzysz:

   ![Określanie uruchomienie skryptu programu PowerShell](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a>Organizowanie kompilacji

Większość w tym dokumencie opisano, jak uzyskać narzędzia .NET Core oraz skonfigurować różne usługi CI bez przekazywania informacji na temat sposobu organizowania, lub *faktyczne utworzenie*, kod za pomocą platformy .NET Core. Opcje dotyczące sposobu struktury procesu kompilacji są zależne od wielu czynników, w których nie można w ogólny sposób, w tym miejscu. Zapoznaj się z zasobami i przykłady przekazane w zestawach dokumentacji [rozwiązania Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), i [usługom DevOps platformy Azure](https://docs.microsoft.com/azure/devops/build-release/index) więcej informacji na temat organizowania usługi kompilacje z poszczególnych technologii.

Dwa podejścia ogólne, które wykonujesz w tworzenie struktury procesu kompilacji dla kodu platformy .NET Core za pomocą narzędzi .NET Core przy użyciu programu MSBuild, bezpośrednio lub przy użyciu poleceń wiersza polecenia platformy .NET Core. Podejście, które należy podjąć zależy od poziomu komfortu przy użyciu podejścia i charakterystyczne kompromisowe złożonością. Program MSBuild zapewnia możliwość wyrażanie proces kompilacji jako zadania i elementy docelowe, ale chodzi o złożonością dodaną przez uczenia Składnia pliku projektu MSBuild. Za pomocą narzędzia wiersza polecenia platformy .NET Core jest prawdopodobnie prostsze, ale wymaga umożliwia pisanie logiki aranżacji w języku skryptów, takich jak `bash` lub programu PowerShell.

## <a name="see-also"></a>Zobacz także

* [Kroki pozyskiwania Ubuntu](https://www.microsoft.com/net/core#linuxubuntu)
