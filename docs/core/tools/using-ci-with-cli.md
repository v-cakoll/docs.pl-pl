---
title: Przy użyciu zestawu SDK programu .NET Core i narzędzi w ciągłej integracji (CI)
description: Informacje na temat użycia .NET Core SDK i jej narzędzi na serwerze kompilacji.
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 76165b515bace71ca9269e587a817876c0e9eecf
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Przy użyciu zestawu SDK programu .NET Core i narzędzi w ciągłej integracji (CI)

## <a name="overview"></a>Omówienie

W tym dokumencie przedstawiono przy użyciu zestawu SDK .NET Core i jej narzędzi na serwerze kompilacji. Oprogramowanie .NET Core zestawu narzędzi działa zarówno interaktywnego, gdzie projektant typów poleceń w poleceniu Monituj i automatycznie, w przypadku, gdy serwer ciągłej integracji (CI) uruchamia skrypt kompilacji. Polecenia, opcje, danych wejściowych i wyjściowych są takie same, a tylko czynności, które należy podać są sposobem uzyskania narzędzi i systemu do utworzenia aplikacji. Ten dokument koncentruje się na scenariuszach nabycia narzędzia dla elementu konfiguracji z zaleceniami dotyczącymi projektowania i definiowania struktury skrypty kompilacji.

## <a name="installation-options-for-ci-build-servers"></a>Opcje instalacji dla elementu konfiguracji kompilacji serwerów

### <a name="using-the-native-installers"></a>Za pomocą natywnego instalatorów

Natywny instalatorów są dostępne dla macOS, Linux i Windows. Pliki instalacyjne wymagają dostępu administracyjnego (sudo) do serwera kompilacji. Zaletą za pomocą natywnego Instalatora jest, że instaluje wszystkie natywnego zależności wymagane dla narzędzi do uruchomienia. Natywny instalatorów zapewniają także instalację systemowe zestawu SDK.

System macOS użytkownicy powinni używać instalatorów PKG. W systemie Linux Brak wyboru przy użyciu Menedżera pakietu na podstawie źródła danych, takich jak stanie get dla Ubuntu lub yum dla CentOS, lub pakietów, DEB lub obr. / min. W systemie Windows użyj Instalatora MSI.

Stabilna najnowsze pliki binarne znajdują się w [Rozpoczynanie pracy z platformą .NET Core](https://aka.ms/dotnetcoregs). Jeśli chcesz użyć narzędzia wstępną najnowsze (i potencjalnie niestabilny), użyj linków dostępnych na [repozytorium GitHub dotnet/cli](https://github.com/dotnet/cli#installers-and-binaries). Dystrybucje systemu Linux, aby uzyskać `tar.gz` archiwów (znanej także jako `tarballs`) są dostępne, zainstaluj oprogramowanie .NET Core przy użyciu skryptów instalacji w archiwum.

### <a name="using-the-installer-script"></a>Przy użyciu skryptu Instalatora

Przy użyciu skryptu Instalatora umożliwia innych niż administracyjne instalacji serwera kompilacji i łatwe automatyzacji do uzyskania narzędzi. Skrypt zapewnia obsługę narzędzia pobierania i wyodrębnij go do domyślnej lub określonej lokalizacji do użycia. Można również określić wersję narzędzi, które mają zostać zainstalowane i czy chcesz zainstalować całego zestawu SDK lub tylko udostępnionego środowiska wykonawczego.

Skrypt Instalatora jest automatyczne uruchamianie na początku kompilacji, aby pobrać i zainstalować odpowiednią wersję zestawu SDK. *Żądanej wersji* jest niezależnie od wersji zestawu SDK dla projektów wymagają kompilacji. Skrypt umożliwia instalowanie zestawu SDK w katalogu lokalnym na serwerze, uruchamiania narzędzi z lokalizacji zainstalowanych i wyczyścić (a lub zezwolić CI, wyczyść) po kompilacji. Zapewnia hermetyzację i izolacja do całego procesu kompilacji. Odwołanie do skryptu instalacji znajduje się w [instalacji dotnet](dotnet-install-script.md) tematu.

> [!NOTE]
> Przy użyciu skryptu Instalatora, natywnego zależności nie są instalowane automatycznie. Jeśli system operacyjny nie ma ich, należy zainstalować natywnej zależności. Zobacz listę warunków wstępnych w [natywnego wymagania wstępne platformy .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) tematu.

## <a name="ci-setup-examples"></a>Przykłady ustawień elementu konfiguracji

W tej sekcji opisano instalacji ręcznej, za pomocą skryptu programu PowerShell lub bash, wraz z opisami kilka oprogramowania jako rozwiązania CI usługa (SaaS). Rozwiązania SaaS CI omówione są [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), i [programu Visual Studio Team Services Build](https://docs.microsoft.com/vsts/build-release/index).

### <a name="manual-setup"></a>Instalacji ręcznej

Każda usługa SaaS ma własną metod tworzenia i konfigurowania procesu kompilacji. Jeśli za pomocą innego rozwiązania SaaS niż wymienione lub wymagają dostosowania poza opakowanych pomocy technicznej, należy wykonać co najmniej pewne czynności konfiguracyjne.

Ogólnie rzecz biorąc instalacji ręcznej należy uzyskać wersji narzędzi (lub kompilacje co noc najnowsza wersja narzędzi) i uruchomić skrypt kompilacji. Można użyć programu PowerShell lub bash skrypt służący do organizowania poleceń .NET Core lub użyć pliku projektu, który zawiera opis procesu kompilacji. [Sekcji aranżacji](#orchestrating-the-build) zawiera więcej szczegółów na temat tych opcji.

Po utworzeniu skrypt, który wykonuje ręcznego CI Tworzenie instalacji serwera, użyj go na komputerze deweloperskim, aby skompilować kod lokalnie do celów testowych. Po upewnieniu się, że skrypt jest uruchamiany oraz lokalnie, wdrożyć ją do serwera kompilacji elementu konfiguracji. Stosunkowo proste skrypt programu PowerShell pokazano, jak uzyskać .NET Core SDK i zainstalować go na serwerze kompilacji systemu Windows:

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

Musisz podać wykonania procesu kompilacji na końcu skryptu. Skrypt uzyskuje narzędzia, a następnie wykonuje procesu kompilacji. Na komputerach UNIX poniższy skrypt bash wykonuje czynności opisane w skrypcie programu PowerShell w podobny sposób:

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

### <a name="travis-ci"></a>Travis elementu konfiguracji

Można skonfigurować [Travis CI](https://travis-ci.org/) zainstalować za pomocą zestawu SDK programu .NET Core `csharp` języka i `dotnet` klucza. Zobacz oficjalna dokumentacja Travis CI na [tworzenia C#, F # lub Visual Basic projektu](https://docs.travis-ci.com/user/languages/csharp/) Aby uzyskać więcej informacji. Należy zwrócić uwagę, jak dostęp do informacji Travis CI który Wspólnotę utrzymane `language: csharp` identyfikator języka działa dla wszystkich języków .NET, w tym F # i Mono.

Travis CI działa zarówno system macOS (OS X 10.11, OS X 10.12) i systemu Linux (Ubuntu 14.04) zadania w *kompilacji macierzy*, gdzie Określ kombinację środowiska uruchomieniowego, środowiska i wykluczenia/dołączenia, aby pokrywał się z kombinacji kompilacji dla aplikacji. Zobacz [. przykład travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) pliku i [Dostosowywanie kompilacji](https://docs.travis-ci.com/user/customizing-the-build) w docs Travis CI, aby uzyskać więcej informacji. Narzędzia MSBuild zawiera LTS (1.0.x) i bieżącego środowiska uruchomieniowe (1.1.x) w pakiecie; Dzięki przez zainstalowanie zestawu SDK, pojawi się wszystko, co jest potrzebne do tworzenia.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) instaluje oprogramowanie .NET Core 1.0.1 SDK z `Visual Studio 2017` utworzyć obraz procesu roboczego. Inne obrazy kompilacji różne wersje programu .NET Core SDK są dostępne; zobacz [przykład appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) i [tworzyć obrazy procesu roboczego](https://www.appveyor.com/docs/build-environment/#build-worker-images) tematu w docs AppVeyor, aby uzyskać więcej informacji.

Pliki binarne .NET Core SDK są pobierane i rozpakowane w podkatalogu przy użyciu skryptu instalacji, a następnie jest dodawana do `PATH` zmiennej środowiskowej. Dodanie macierzy kompilację do uruchomienia testów integracji z wieloma wersjami programu .NET Core SDK:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a>Visual Studio Team Services (VSTS)

Konfigurowanie programu Visual Studio Team Services (VSTS) do tworzenia projektów .NET Core przy użyciu jednej z tych metod:

1. Uruchom skrypt z [krok instalacji ręcznej](#manual-setup) przy użyciu poleceń.
1. Utwórz kompilację składa się z kilka zadań programu VSTS wbudowanych kompilacji, które są skonfigurowane do używania narzędzi platformy .NET Core.

Oba rozwiązania są prawidłowe. Przy użyciu skryptu instalacji ręcznej, możesz kontrolować wersji narzędzia, które zostanie wyświetlone, ponieważ możesz pobrać jako część kompilacji. Kompilacja jest uruchamiana skrypt, który należy utworzyć. W tym temacie omówiono tylko opcja ręcznego odbierania. Aby uzyskać więcej informacji na temat tworzenia kompilacji z programu VSTS zadania kompilacji, odwiedź witrynę programu VSTS [ciągłej integracji i wdrażania](https://docs.microsoft.com/vsts/build-release/index) tematu.

Aby użyć skryptu instalacji ręcznej w VSTS, Utwórz nową definicję kompilacji i określ skrypt do uruchomienia kroku kompilacji. Jest to realizowane przy użyciu interfejsu użytkownika programu VSTS:

1. Rozpocznij od utworzenia nowej definicji kompilacji. Po osiągnięciu ekranu, która udostępnia opcję, aby określić, jaki rodzaj kompilacji chcesz utworzyć, wybierz opcję **pusty** opcji.

   ![Wybieranie definicji kompilacji pusty](./media/using-ci-with-cli/screen1.png)

1. Po skonfigurowaniu repozytorium do kompilacji, są kierowane do definicji kompilacji. Wybierz **kroku kompilacji Dodaj**:

   ![Dodawanie kroku kompilacji](./media/using-ci-with-cli/screen2.png)

1. Aby wyświetlić dostępne **katalogu zadania**. Katalog zawiera zadania, których można użyć w kompilacji. Ponieważ masz skryptu, wybierz opcję **Dodaj** przycisk dla **środowiska PowerShell: Uruchom skrypt programu PowerShell**.

   ![Dodawanie etapu skryptu PowerShell](./media/using-ci-with-cli/screen3.png)

1. Skonfiguruj kroku kompilacji. Dodaj skrypt z repozytorium, które tworzysz:

   ![Określanie uruchomienie skryptu programu PowerShell](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a>Organizowanie kompilacji

Większość ten dokument zawiera opis sposobu uzyskania narzędzia .NET Core i konfigurowanie różnych usług CI bez podawania informacji na temat sposobu organizowania, lub *zbudowaniem*, kodu za pomocą platformy .NET Core. Opcje dostępne na struktury procesu kompilacji są zależne od wielu czynników, w których nie można w sposób ogólny, w tym miejscu. Eksploruj zasobów i przykłady podane w dokumentacji zestawy [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), i [VSTS](https://docs.microsoft.com/vsts/build-release/index) uzyskać więcej informacji o kompilacji z każdym organizowanie Technologia.

Dwa podejścia ogólnych, które wykonujesz w struktury procesu kompilacji dla kodu platformy .NET Core za pomocą narzędzi platformy .NET Core są bezpośrednio za pomocą programu MSBuild lub przy użyciu poleceń wiersza polecenia platformy .NET Core. Podejście, które należy podjąć jest określana przez poziom komfort z podejścia i kompromisy złożonością. MSBuild zapewnia możliwość express procesu kompilacji jako zadań i elementów docelowych, ale ma dodany złożoność uczenia składni pliku projektu MSBuild. Za pomocą narzędzia wiersza polecenia platformy .NET Core prawdopodobnie jest prostsze, ale wymaga do pisania logiki aranżacji w języku skryptów, takich jak `bash` lub programu PowerShell.

## <a name="see-also"></a>Zobacz także

[Ubuntu nabycia kroki](https://www.microsoft.com/net/core#linuxubuntu)   
