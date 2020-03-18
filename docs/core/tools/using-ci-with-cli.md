---
title: Ciągła integracja (CI) z zestawem .NET Core SDK i narzędziami
description: Dowiedz się, jak używać sdk .NET Core i jego narzędzi na serwerze kompilacji z ciągłą integracją.
ms.date: 05/18/2017
ms.openlocfilehash: 6e23a21dd36422a095e56519c9aa28ce2549f7b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451041"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Korzystanie z sdk i narzędzi .NET Core w ciągłej integracji (CI)

W tym dokumencie opisano przy użyciu sdk .NET Core i jego narzędzi na serwerze kompilacji. Zestaw narzędzi .NET Core działa zarówno interaktywnie, gdzie deweloper wypisuje polecenia w wierszu polecenia, jak i automatycznie, gdy serwer ciągłej integracji (CI) uruchamia skrypt kompilacji. Polecenia, opcje, dane wejściowe i dane wyjściowe są takie same, a jedyne rzeczy, które podajesz, to sposób na uzyskanie narzędzi i systemu do tworzenia aplikacji. Ten dokument koncentruje się na scenariuszach pozyskiwania narzędzi dla ci z zaleceniami dotyczącymi projektowania i struktury skryptów kompilacji.

## <a name="installation-options-for-ci-build-servers"></a>Opcje instalacji serwerów kompilacji ci

### <a name="using-the-native-installers"></a>Korzystanie z instalatorów natywnych

Instalatory natywne są dostępne dla systemów macOS, Linux i Windows. Instalatorzy wymagają administratora (sudo) dostępu do serwera kompilacji. Zaletą korzystania z instalatora macierzystego jest to, że instaluje wszystkie natywne zależności wymagane do uruchamiania narzędzi. Instalatorzy natywni zapewniają również instalację sdk w całym systemie.

Użytkownicy systemu macOS powinni korzystać z instalatorów PKG. W systemie Linux istnieje możliwość użycia menedżera pakietów opartych na pliku danych, takiego jak apt-get dla Ubuntu lub yum dla CentOS, lub przy użyciu samych pakietów, DEB lub RPM. W systemie Windows użyj instalatora MSI.

Najnowsze stabilne pliki binarne znajdują się w [plikach do pobrania .NET](https://dotnet.microsoft.com/download). Jeśli chcesz korzystać z najnowszego (i potencjalnie niestabilnego) narzędzia wersji wstępnej, użyj łączy podanych w [repozytorium GitHub dotnet/core-sdk](https://github.com/dotnet/core-sdk#installers-and-binaries). W przypadku dystrybucji Linuksa `tar.gz` dostępne są archiwa (znane również jako). `tarballs` użyj skryptów instalacyjnych w archiwach, aby zainstalować program .NET Core.

### <a name="using-the-installer-script"></a>Korzystanie ze skryptu instalatora

Użycie skryptu instalatora umożliwia instalację nieadministracyjną na serwerze kompilacji i łatwą automatyzację uzyskiwania narzędzi. Skrypt zajmuje się pobieraniem narzędzi i wyodrębnianiem go do domyślnej lub określonej lokalizacji do użycia. Można również określić wersję narzędzi, które chcesz zainstalować i czy chcesz zainstalować cały zestaw SDK, czy tylko udostępniony program runtime.

Skrypt instalatora jest zautomatyzowany do uruchomienia na początku kompilacji w celu pobrania i zainstalowania żądanej wersji sdk. *Żądana wersja* jest niezależnie od wersji sdk projekty wymagają do kompilacji. Skrypt umożliwia zainstalowanie sdk w katalogu lokalnym na serwerze, uruchomienie narzędzi z zainstalowanej lokalizacji, a następnie oczyścić (lub pozwolić usłudze pinkowej oczyścić) po kompilacji. Zapewnia to hermetyzację i izolację całego procesu kompilacji. Odwołanie do skryptu instalacyjnego znajduje się w artykule [dotnet-install.](dotnet-install-script.md)

> [!NOTE]
> **Usługa Azure DevOps Services**
>
> Korzystając ze skryptu instalatora, zależności natywne nie są instalowane automatycznie. Należy zainstalować zależności macierzyste, jeśli system operacyjny ich nie ma. Aby uzyskać więcej informacji, zobacz [zależności i wymagania programu .NET Core](../install/dependencies.md).

## <a name="ci-setup-examples"></a>Przykłady konfiguracji ci

W tej sekcji opisano konfigurację ręczną przy użyciu skryptu programu PowerShell lub bash oraz opis kilku rozwiązań ci oprogramowania jako usługi (SaaS). Rozwiązania SaaS CI objęte są [Travis CI,](https://travis-ci.org/) [AppVeyor](https://www.appveyor.com/)i [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

### <a name="manual-setup"></a>Konfiguracja ręczna

Każda usługa SaaS ma własne metody tworzenia i konfigurowania procesu kompilacji. Jeśli używasz innego rozwiązania SaaS niż wymienione lub wymagają dostosowania poza wstępnie spakowane jałmużenie, należy wykonać co najmniej niektóre ręcznej konfiguracji.

Ogólnie rzecz biorąc, konfiguracja ręczna wymaga nabycia wersji narzędzi (lub najnowszych nocnych kompilacji narzędzi) i uruchomienia skryptu kompilacji. Za pomocą skryptu programu PowerShell lub bash można aranżować polecenia programu .NET Core lub użyć pliku projektu, który przedstawia proces kompilacji. [Sekcja aranżacji](#orchestrating-the-build) zawiera więcej szczegółów na temat tych opcji.

Po utworzeniu skryptu, który wykonuje ręczną konfigurację serwera kompilacji ci, użyj go na komputerze deweloperskim, aby utworzyć kod lokalnie do celów testowych. Po potwierdzeniu, że skrypt działa dobrze lokalnie, wdrożyć go na serwerze kompilacji ci. Stosunkowo prosty skrypt programu PowerShell pokazuje, jak uzyskać zestaw SDK .NET Core i zainstalować go na serwerze kompilacji systemu Windows:

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

Należy podać implementację dla procesu kompilacji na końcu skryptu. Skrypt uzyskuje narzędzia, a następnie wykonuje proces kompilacji. W przypadku komputerów unix następujący skrypt bash wykonuje akcje opisane w skrypcie programu PowerShell w podobny sposób:

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

### <a name="travis-ci"></a>Travis CI

Możesz skonfigurować [Travis CI](https://travis-ci.org/) do zainstalowania .NET `csharp` Core SDK przy użyciu języka i klucza. `dotnet` Aby uzyskać więcej informacji, zobacz oficjalne dokumenty Travis CI dotyczące [tworzenia projektu Języka C#, F lub Visual Basic](https://docs.travis-ci.com/user/languages/csharp/). Należy pamiętać, jak uzyskać dostęp do informacji `language: csharp` Travis CI, że identyfikator języka utrzymywane przez społeczność działa dla wszystkich języków .NET, w tym F#i Mono.

Travis CI uruchamia zadania systemu macOS i Linux w *macierzy kompilacji,* gdzie określisz kombinację środowiska uruchomieniowego, środowiska i wykluczeń/wtrąceń, aby pokryć kombinacje kompilacji dla aplikacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kompilacji](https://docs.travis-ci.com/user/customizing-the-build) artykuł w dokumentacji Travis CI. Narzędzia oparte na usylaniu MSBuild obejmują uruchamianie LTS (1.0.x) i Current (1.1.x) w pakiecie; więc instalując zestaw SDK, otrzymasz wszystko, czego potrzebujesz do zbudowania.

### <a name="appveyor"></a>AppVeyor (Zw.AppVeyor)

[AppVeyor](https://www.appveyor.com/) instaluje zestaw SDK .NET Core `Visual Studio 2017` 1.0.1 z obrazem procesu tworzenia. Dostępne są inne obrazy kompilacji z różnymi wersjami sdk .NET Core. Aby uzyskać więcej informacji, zobacz [przykład appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) i [tworzenie obrazów roboczych](https://www.appveyor.com/docs/build-environment/#build-worker-images) w dokumentach AppVeyor.

Pliki binarne sdk .NET Core są pobierane i rozpakowywane w podkatalogu przy `PATH` użyciu skryptu instalacyjnego, a następnie dodawane do zmiennej środowiskowej. Dodaj macierz kompilacji, aby uruchomić testy integracji z wieloma wersjami sdk .NET Core:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Usługa Azure DevOps Services

Skonfiguruj usługi Azure DevOps Services do tworzenia projektów .NET Core przy użyciu jednej z następujących metod:

1. Uruchom skrypt z [etapu ręcznej konfiguracji](#manual-setup) za pomocą poleceń.
1. Utwórz kompilację składającą się z kilku wbudowanych zadań kompilacji usług Azure DevOps Services skonfigurowanych do używania narzędzi .NET Core.

Oba rozwiązania są prawidłowe. Za pomocą skryptu ręcznej konfiguracji można kontrolować wersję narzędzi, które otrzymujesz, ponieważ można je pobrać jako część kompilacji. Kompilacja jest uruchamiana ze skryptu, który należy utworzyć. Ten artykuł obejmuje tylko opcję ręczną. Aby uzyskać więcej informacji na temat tworzenia kompilacji z zadaniami kompilacji usług Azure DevOps Services, zobacz dokumentację [potoków platformy Azure.](https://docs.microsoft.com/azure/devops/pipelines/index)

Aby użyć skryptu ręcznej konfiguracji w usłudze Azure DevOps Services, utwórz nową definicję kompilacji i określ skrypt do uruchomienia dla kroku kompilacji. Jest to realizowane przy użyciu interfejsu użytkownika usługi Azure DevOps Services:

1. Rozpocznij od utworzenia nowej definicji kompilacji. Po dotarciu do ekranu, który zapewnia opcję, aby zdefiniować rodzaj kompilacji, którą chcesz utworzyć, wybierz opcję **Puste.**

   ![Wybieranie pustej definicji kompilacji](./media/using-ci-with-cli/select-empty-build-definition.png)

1. Po skonfigurowaniu repozytorium do kompilacji, jesteś kierowany do definicji kompilacji. Wybierz **pozycję Dodaj krok kompilacji:**

   ![Dodawanie kroku kompilacji](./media/using-ci-with-cli/add-build-step.png)

1. Zostanie przedstawiony **katalog zadań**. Katalog zawiera zadania, które są używane w kompilacji. Ponieważ masz skrypt, wybierz przycisk **Dodaj** dla **programu PowerShell: Uruchom skrypt programu PowerShell**.

   ![Dodawanie kroku skryptu programu PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. Skonfiguruj krok kompilacji. Dodaj skrypt z repozytorium, które budujesz:

   ![Określanie skryptu programu PowerShell do uruchomienia](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a>Organizowanie kompilacji

W większości tego dokumentu opisano sposób uzyskiwania narzędzi .NET Core i konfigurowania różnych *actually build*usług pw. Wybór sposobu struktury procesu kompilacji zależy od wielu czynników, które nie mogą być omówione w sposób ogólny tutaj. Aby uzyskać więcej informacji na temat organizowania kompilacji przy każdej technologii, zapoznaj się z zasobami i przykładami podanymi w zestawach dokumentacji [Travis CI,](https://travis-ci.org/) [AppVeyor](https://www.appveyor.com/)i [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

Dwa ogólne podejścia, które można podjąć w strukturyzacji procesu kompilacji dla .NET Core kodu przy użyciu .NET Core narzędzia są przy użyciu MSBuild bezpośrednio lub przy użyciu polecenia wiersza polecenia .NET Core. To, jakie podejście powinieneś przyjąć, zależy od twojego poziomu komfortu z podejściami i kompromisami w złożoności. MSBuild zapewnia możliwość wyrażania procesu kompilacji jako zadania i obiekty docelowe, ale pochodzi z dodatkową złożoność uczenia się składni pliku projektu MSBuild. Korzystanie z narzędzi wiersza polecenia .NET Core jest być może prostsze, ale `bash` wymaga napisania logiki aranżacji w języku skryptów, takim jak program PowerShell.

## <a name="see-also"></a>Zobacz też

- [Pliki do pobrania .NET - Linux](https://dotnet.microsoft.com/download?initial-os=linux)
