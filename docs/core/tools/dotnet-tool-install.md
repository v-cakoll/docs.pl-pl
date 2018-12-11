---
title: polecenia instalacji narzędzia DotNet
description: Narzędzia dotnet zainstalować polecenie instaluje określonego narzędzia globalnej podstawowych platformy .NET na maszynie.
ms.date: 05/29/2018
ms.openlocfilehash: 251e7b04be96ac2340727fa03dbaa2d548110fa9
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168718"
---
# <a name="dotnet-tool-install"></a>Instalowanie narzędzi DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool install` -Instaluje określony [narzędzia programu .NET Core globalnego](global-tools.md) na swojej maszynie.

## <a name="synopsis"></a>Streszczenie

```console
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool install` Polecenie umożliwia zainstalowanie narzędzia globalnej platformy .NET Core na swojej maszynie. Można użyć polecenia, to należy określić ma użytkownika całej instalacji przy użyciu `--global` opcji lub możesz określić ścieżkę do je zainstalować za pomocą `--tool-path` opcji.

Globalne narzędzia są instalowane w następujących katalogach domyślnie po określeniu `-g` (lub `--global`) opcja:

| System operacyjny          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwy/Identyfikatora pakietu NuGet, który zawiera narzędzie globalnego .NET Core do zainstalowania.

## <a name="options"></a>Opcje

`--add-source <SOURCE>`

Dodaje dodatkowe źródła pakietu NuGet do użycia podczas instalacji.

`--configfile <FILE>`

Konfiguracja NuGet (*nuget.config*) plik do użycia.

`--framework <FRAMEWORK>`

Określa [platformę docelową](../../standard/frameworks.md) do zainstalowania tego narzędzia na potrzeby. Domyślnie program .NET Core SDK próbuje wybierz najbardziej odpowiednią platformę docelową.

`-g|--global`

Określa, czy instalacja się szerokie użytkownika. Nie można połączyć z `--tool-path` opcji. Jeśli nie określisz tę opcję, należy określić `--tool-path` opcji.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--tool-path <PATH>`

Określa lokalizację, gdzie zainstalować narzędzie globalne. ŚCIEŻKA może być bezwzględny lub względny. Jeśli ŚCIEŻKA nie istnieje, polecenie próbuje je utworzyć. Nie można połączyć z `--global` opcji. Jeśli nie określisz tę opcję, należy określić `--global` opcji.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--version <VERSION_NUMBER>`

Wersja narzędzia do zainstalowania. Domyślnie jest zainstalowana najnowsza wersja stabilny pakiet. Użyj tej opcji do zainstalowania wersji zapoznawczej lub starsze wersje tego narzędzia.

## <a name="examples"></a>Przykłady

Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w domyślnej lokalizacji:

`dotnet tool install -g dotnetsay`

Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w określonym folderze Windows:

`dotnet tool install dotnetsay --tool-path c:\global-tools`

Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w określonym folderze Linux/macOS:

`dotnet tool install dotnetsay --tool-path ~/bin`

Instaluje wersję 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>Zobacz także

* [Narzędzia globalnej platformy .NET core](global-tools.md)