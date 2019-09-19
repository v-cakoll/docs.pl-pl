---
title: polecenie instalacji narzędzia dotnet
description: Polecenie instalacji narzędzia dotnet służy do instalowania na komputerze określonego narzędzia globalnego platformy .NET Core.
ms.date: 05/29/2018
ms.openlocfilehash: d6f691117e93a39c9837b282dca19e452515c80a
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117463"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool install`-Instaluje określone [Narzędzie globalne platformy .NET Core](global-tools.md) na komputerze.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool install` Polecenie umożliwia instalację narzędzi globalnych platformy .NET Core na komputerze. Aby użyć polecenia, musisz określić, że ma być używana instalacja obejmująca wiele użytkowników przy użyciu `--global` opcji, lub określić ścieżkę instalacji `--tool-path` przy użyciu opcji.

Narzędzia globalne są instalowane domyślnie w następujących katalogach po określeniu `-g` opcji (lub `--global`):

| OS          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do zainstalowania.

## <a name="options"></a>Opcje

`--add-source <SOURCE>`

Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.

`--configfile <FILE>`

Plik konfiguracji NuGet (*NuGet. config*) do użycia.

`--framework <FRAMEWORK>`

Określa [platformę docelową](../../standard/frameworks.md) do zainstalowania narzędzia dla programu. Domyślnie zestaw .NET Core SDK próbuje wybrać najbardziej odpowiednią platformę docelową.

`-g|--global`

Określa, że instalacja jest szeroka. Nie można łączyć z `--tool-path` opcją. Jeśli ta opcja nie zostanie określona, należy określić `--tool-path` opcję.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--tool-path <PATH>`

Określa lokalizację, w której ma zostać zainstalowane narzędzie globalne. ŚCIEŻKA może być bezwzględna lub względna. Jeśli ścieżka nie istnieje, polecenie próbuje ją utworzyć. Nie można łączyć z `--global` opcją. Jeśli ta opcja nie zostanie określona, należy określić `--global` opcję.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

`--version <VERSION_NUMBER>`

Wersja narzędzia do zainstalowania. Domyślnie jest zainstalowana najnowsza stabilna wersja pakietu. Użyj tej opcji, aby zainstalować Podgląd lub starsze wersje narzędzia.

## <a name="examples"></a>Przykłady

Instaluje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) w domyślnej lokalizacji:

`dotnet tool install -g dotnetsay`

Instaluje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) w określonym folderze systemu Windows:

`dotnet tool install dotnetsay --tool-path c:\global-tools`

Instaluje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) w określonym folderze systemu Linux/macOS:

`dotnet tool install dotnetsay --tool-path ~/bin`

Instaluje wersję 2.0.0 narzędzia globalnego [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>Zobacz także

- [Narzędzia globalne platformy .NET Core](global-tools.md)
