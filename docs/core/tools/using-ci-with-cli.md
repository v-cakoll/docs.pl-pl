---
title: Ciągła integracja (CI) z zestaw .NET Core SDK i narzędziami
description: Dowiedz się, jak używać zestaw .NET Core SDK i narzędzi na serwerze kompilacji z ciągłą integracją.
ms.date: 05/18/2017
ms.openlocfilehash: 6e23a21dd36422a095e56519c9aa28ce2549f7b2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451041"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Używanie zestaw .NET Core SDK i narzędzi w ciągłej integracji (CI)

Ten dokument jest przedstawiony przy użyciu zestaw .NET Core SDK i jego narzędzi na serwerze kompilacji. Zestaw narzędzi platformy .NET Core działa interaktywnie, gdzie deweloperzy typów poleceń w wierszu polecenia i automatycznie, gdzie serwer ciągłej integracji (CI) uruchamia skrypt kompilacji. Polecenia, opcje, dane wejściowe i wyjściowe są takie same, a jedyne dostępne elementy to sposób uzyskania narzędzi i systemu w celu skompilowania aplikacji. Ten dokument koncentruje się na scenariuszach pozyskiwania narzędzi dla CI z zaleceniami dotyczącymi projektowania i struktury skryptów kompilacji.

## <a name="installation-options-for-ci-build-servers"></a>Opcje instalacji dla serwerów kompilacji CI

### <a name="using-the-native-installers"></a>Korzystanie z natywnych instalatorów

Natywne Instalatory są dostępne dla systemów macOS, Linux i Windows. Instalatory wymagają dostępu administratora (sudo) do serwera kompilacji. Zaletą korzystania z instalatora natywnego jest zainstalowanie wszystkich natywnych zależności wymaganych do uruchomienia narzędzi. Natywne Instalatory oferują również instalację zestawu SDK na poziomie systemu.

macOS użytkownicy powinni używać instalatorów PKG. W systemie Linux istnieje możliwość korzystania z Menedżera pakietów opartych na kanale informacyjnym, takiego jak apt-get for Ubuntu lub yum dla CentOS lub z użyciem samych pakietów, DEB lub RPM. W systemie Windows użyj Instalatora MSI.

Najnowsze stabilne pliki binarne są dostępne na [platformie .NET](https://dotnet.microsoft.com/download). Jeśli chcesz użyć najnowszych (i potencjalnie niestabilnych) narzędzi w wersji wstępnej, Skorzystaj z linków dostarczonych w [repozytorium GitHub/Core-SDK](https://github.com/dotnet/core-sdk#installers-and-binaries)w ramach programu dotnet. W przypadku dystrybucji systemu Linux dostępne są `tar.gz` archiwa (znane także jako `tarballs`); Użyj skryptów instalacji w archiwach, aby zainstalować platformę .NET Core.

### <a name="using-the-installer-script"></a>Korzystanie z skryptu Instalatora

Użycie skryptu Instalatora pozwala na instalację nieadministracyjną na serwerze kompilacji i łatwą automatyzację w celu uzyskania narzędzi. Skrypt wymaga pobrania narzędzi i wyodrębnienia go do domyślnej lub określonej lokalizacji do użycia. Możesz również określić wersję narzędzi, którą chcesz zainstalować, i zdecydować, czy chcesz zainstalować cały zestaw SDK, czy tylko udostępnione środowisko uruchomieniowe.

Skrypt Instalatora jest zautomatyzowany do uruchomienia na początku kompilacji, aby pobrać i zainstalować żądaną wersję zestawu SDK. *Wymagana wersja* to Poprzednia wersja zestawu SDK, których projekty wymagają do skompilowania. Skrypt umożliwia zainstalowanie zestawu SDK w katalogu lokalnym na serwerze, uruchomienie narzędzi z zainstalowanej lokalizacji, a następnie oczyszczenie (lub umożliwienie oczyszczenia usługi CI) po kompilacji. Zapewnia to hermetyzację i izolację całego procesu kompilacji. Informacje o skrypcie instalacji znajdują się w artykule [dotnet-Install](dotnet-install-script.md) .

> [!NOTE]
> **Azure DevOps Services**
>
> W przypadku korzystania z skryptu Instalatora zależności natywne nie są instalowane automatycznie. Jeśli system operacyjny ich nie ma, należy zainstalować zależności natywne. Aby uzyskać więcej informacji, zobacz [zależności i wymagania dotyczące platformy .NET Core](../install/dependencies.md).

## <a name="ci-setup-examples"></a>Przykłady konfiguracji elementu konfiguracji

W tej sekcji opisano konfigurację ręczną przy użyciu skryptu PowerShell lub bash, a także opis kilku rozwiązań CI (Software as a Service). Rozwiązania CI SaaS CI obejmują [rozwiązania Travis Ci](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)i [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

### <a name="manual-setup"></a>Konfiguracja ręczna

Każda usługa SaaS ma własne metody tworzenia i konfigurowania procesu kompilacji. Jeśli używasz innego rozwiązania SaaS niż wymienione lub wymagają dostosowania poza wstępnie spakowaną obsługą, należy wykonać co najmniej konfigurację ręczną.

Ogólnie Konfiguracja ręczna wymaga pozyskania wersji narzędzi (lub najnowszych, nocnych kompilacji narzędzi) i uruchomienia skryptu kompilacji. Za pomocą skryptu PowerShell lub bash można organizować polecenia .NET Core lub używać pliku projektu, który zawiera opis procesu kompilacji. [Sekcja aranżacja](#orchestrating-the-build) zawiera więcej szczegółów na temat tych opcji.

Po utworzeniu skryptu, który wykonuje ręczną konfigurację serwera kompilacji, użyj go na komputerze deweloperskim, aby utworzyć kod lokalnie na potrzeby testowania. Po upewnieniu się, że skrypt działa prawidłowo, wdróż go na serwerze kompilacji CI. Stosunkowo prosty skrypt programu PowerShell pokazuje, jak uzyskać zestaw .NET Core SDK i zainstalować go na serwerze kompilacji systemu Windows:

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

Implementację procesu kompilacji można dostarczyć na końcu skryptu. Skrypt uzyskuje narzędzia, a następnie wykonuje proces kompilacji. W przypadku maszyn z systemem UNIX następujący skrypt bash wykonuje akcje opisane w skrypcie programu PowerShell w podobny sposób:

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

Można skonfigurować [rozwiązania Travis Ci](https://travis-ci.org/) do instalowania zestaw .NET Core SDK przy użyciu języka `csharp` i klucza `dotnet`. Aby uzyskać więcej informacji, zobacz oficjalne dokumenty rozwiązania Travis Ci na [Kompilowanie C#projektu F#, lub Visual Basic](https://docs.travis-ci.com/user/languages/csharp/). Zwróć uwagę na to, że uzyskujesz dostęp do informacji o CI, które są obsługiwane przez społeczność `language: csharp` identyfikator języka dla F#wszystkich języków .NET, w tym i mono.

Rozwiązania Travis CI uruchamia zarówno zadania macOS, jak i Linux w *macierzy kompilacji*, w której można określić kombinację środowiska uruchomieniowego, środowiska i wykluczeń/dołączeń w celu pokrycia kombinacji kompilacji dla aplikacji. Aby uzyskać więcej informacji, zobacz artykuł [Dostosowywanie kompilacji](https://docs.travis-ci.com/user/customizing-the-build) w dokumentacji elementu konfiguracji rozwiązania Travis. Narzędzia oparte na programie MSBuild obejmują środowiska uruchomieniowe LTS (1.0. x) i bieżące (1.1. x) w pakiecie; Dzięki zainstalowaniu zestawu SDK otrzymujesz wszystko, czego potrzebujesz do skompilowania.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) instaluje zestaw .NET Core 1.0.1 SDK przy użyciu obrazu procesu roboczego kompilacji `Visual Studio 2017`. Dostępne są inne obrazy kompilacji z różnymi wersjami zestaw .NET Core SDK. Aby uzyskać więcej informacji, zobacz [przykład appveyor. yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) oraz artykuł [Build Worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) w dokumentacji appveyor.

Pliki binarne zestaw .NET Core SDK są pobierane i rozpakowane w podkatalogu przy użyciu skryptu instalacji, a następnie są dodawane do zmiennej środowiskowej `PATH`. Dodaj macierz kompilacji, aby uruchomić testy integracji z wieloma wersjami zestaw .NET Core SDK:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Usługa Azure DevOps Services

Skonfiguruj Azure DevOps Services do kompilowania projektów .NET Core przy użyciu jednej z następujących metod:

1. Uruchom skrypt z [kroku instalacji ręcznej](#manual-setup) przy użyciu poleceń.
1. Utwórz kompilację składającą się z kilku Azure DevOps Services wbudowanych zadań kompilacji, które są skonfigurowane do korzystania z narzędzi .NET Core.

Oba rozwiązania są prawidłowe. Za pomocą ręcznego skryptu konfiguracji kontrolujesz wersję narzędzi, które otrzymujesz, ponieważ pobierasz je w ramach kompilacji. Kompilacja jest uruchamiana ze skryptu, który należy utworzyć. W tym artykule omówiono tylko opcję ręczną. Aby uzyskać więcej informacji na temat tworzenia kompilacji z zadaniami kompilacji Azure DevOps Services, zobacz dokumentację [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) .

Aby użyć ręcznego skryptu konfiguracji w Azure DevOps Services, Utwórz nową definicję kompilacji i określ skrypt do uruchomienia dla kroku kompilacji. Jest to realizowane przy użyciu Azure DevOps Services interfejsu użytkownika:

1. Zacznij od utworzenia nowej definicji kompilacji. Po osiągnięciu ekranu, który udostępnia opcję definiowania rodzaju kompilacji, którą chcesz utworzyć, wybierz opcję **pustą** .

   ![Wybieranie pustej definicji kompilacji](./media/using-ci-with-cli/select-empty-build-definition.png)

1. Po skonfigurowaniu repozytorium do kompilacji, nastąpi przekierowanie do definicji kompilacji. Wybierz pozycję **Dodaj krok kompilacji**:

   ![Dodawanie kroku kompilacji](./media/using-ci-with-cli/add-build-step.png)

1. Zostanie wyświetlony **katalog zadań**. Wykaz zawiera zadania, które są używane w kompilacji. Ponieważ masz skrypt, wybierz przycisk **Dodaj** dla **programu PowerShell: Uruchom skrypt programu PowerShell**.

   ![Dodawanie kroku skryptu programu PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. Skonfiguruj krok kompilacji. Dodaj skrypt z repozytorium, które tworzysz:

   ![Określanie skryptu programu PowerShell do uruchomienia](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a>Organizowanie kompilacji

W większości tego dokumentu opisano, jak uzyskać narzędzia .NET Core i skonfigurować różne usługi CI, bez przekazywania informacji na temat sposobu organizowania lub *kompilowania*kodu za pomocą platformy .NET Core. Wybór sposobu struktury procesu kompilacji zależy od wielu czynników, które nie mogą być omówione w ogólny sposób. Aby uzyskać więcej informacji na temat organizowania kompilacji z każdą technologią, zapoznaj się z zasobami i przykładami dostępnymi w zestawach dokumentacji [rozwiązania Travis Ci](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)i [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

Dwa ogólne podejścia do tworzenia struktury procesu kompilacji dla kodu platformy .NET Core przy użyciu narzędzi .NET Core Tools używają programu MSBuild bezpośrednio lub przy użyciu poleceń wiersza polecenia programu .NET Core. Podejście, które należy podjąć, zależy od poziomu komfortu i podejść. Program MSBuild umożliwia wyrażanie procesu kompilacji jako zadań i obiektów docelowych, ale zawiera dodaną złożoność uczenia składni pliku projektu programu MSBuild. Korzystanie z narzędzi wiersza polecenia platformy .NET Core może być prostsze, ale wymaga to zapisania logiki aranżacji w języku skryptowym, takim jak `bash` lub PowerShell.

## <a name="see-also"></a>Zobacz też

- [Pliki do pobrania dla platformy .NET — Linux](https://dotnet.microsoft.com/download?initial-os=linux)
