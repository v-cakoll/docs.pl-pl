---
title: Polecenie instalacji narzędzia dotnet
description: Polecenie instalacji narzędzia dotnet instaluje na komputerze określone narzędzie .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 723d25caa6009288dbb55d55f173b04d7b983450
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463365"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet tool install`- Instaluje określone [narzędzie .NET Core](global-tools.md) na komputerze.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet tool install` umożliwia zainstalowanie narzędzi .NET Core na komputerze. Aby użyć polecenia, należy określić jedną z następujących opcji instalacji:

* Aby zainstalować narzędzie globalne w lokalizacji `--global` domyślnej, użyj tej opcji.
* Aby zainstalować narzędzie globalne w lokalizacji `--tool-path` niestandardowej, użyj tej opcji.
* Aby zainstalować narzędzie lokalne, `--global` pomiń opcje i `--tool-path` opcje.

**Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.**

Narzędzia globalne są domyślnie instalowane w `-g` następujących `--global` katalogach po określeniu lub opcji:

| System operacyjny          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Narzędzia lokalne są dodawane do pliku *tool-manifest.json* w katalogu *.config* w bieżącym katalogu. Jeśli plik manifestu jeszcze nie istnieje, utwórz go, uruchamiając następujące polecenie:

```dotnetcli
dotnet new tool-manifest
```

Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie .NET Core do zainstalowania.

## <a name="options"></a>Opcje

- **`add-source <SOURCE>`**

  Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.

- **`configfile <FILE>`**

  Plik konfiguracji NuGet (*nuget.config*).

- **`framework <FRAMEWORK>`**

  Specifies the [target framework](../../standard/frameworks.md) to install the tool for. Domyślnie .NET Core SDK próbuje wybrać najbardziej odpowiednią platformę docelową.

- **`-g|--global`**

  Określa, że instalacja jest ogólna. Nie można połączyć `--tool-path` z opcją. Pominięcie obu `--global` `--tool-path` i określa instalację narzędzia lokalnego.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`tool-path <PATH>`**

  Określa lokalizację, w której należy zainstalować narzędzie globalne. ŚCIEŻKA może być bezwzględna lub względna. Jeśli PATH nie istnieje, polecenie próbuje go utworzyć. Pominięcie obu `--global` `--tool-path` i określa instalację narzędzia lokalnego.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .

- **`--version <VERSION_NUMBER>`**

  Wersja narzędzia do zainstalowania. Domyślnie jest zainstalowana najnowsza stabilna wersja pakietu. Użyj tej opcji, aby zainstalować wersje zapoznawczą lub starsze.

## <a name="examples"></a>Przykłady

- **`dotnet tool install -g dotnetsay`**

  Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w lokalizacji domyślnej.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu systemu Windows.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu Linux/macOS.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Instaluje wersję 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne.

- **`dotnet tool install dotnetsay`**

  Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie lokalne dla bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](local-tools-how-to-use.md)
