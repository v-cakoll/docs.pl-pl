---
title: polecenie - .NET Core interfejsu wiersza polecenia instalacji narzędzia DotNet
description: Narzędzie dotnet zainstalować instaluje polecenia określonego .NET Core globalne narzędzia na komputerze.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f3068848910d6672a10ecfb639bac8e18a72818d
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697290"
---
# <a name="dotnet-tool-install"></a>Instalowanie narzędzi DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool install` -Instaluje określony [narzędzie globalne .NET Core](global-tools.md) na tym komputerze.

## <a name="synopsis"></a>Streszczenie

```
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool install` Polecenie umożliwia do zainstalowania narzędzia globalne .NET Core na tym komputerze. Aby polecenie, albo należy określić, że instalacja na poziomie użytkownika przy użyciu `--global` opcji lub określ ścieżkę do zainstalowania go przy użyciu `--tool-path` opcji.

Narzędzia globalny są instalowane w następujących katalogów domyślnie po określeniu `-g` (lub `--global`) opcja:

| SYSTEM OPERACYJNY          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie globalne .NET Core do zainstalowania.

## <a name="options"></a>Opcje

`--add-source <SOURCE>`

Dodaje dodatkowe źródła pakietów NuGet podczas instalacji.

`--configfile <FILE>`

Konfiguracja nuget projektu (*nuget.config*) pliku do użycia.

`--framework <FRAMEWORK>`

Określa [platformy docelowej](../../standard/frameworks.md) zainstalować za pomocą narzędzia. Domyślnie program .NET Core SDK próbuje wybierz najbardziej odpowiednią platformę docelową.

`-g|--global`

Określa, że instalacja jest szeroki użytkownika. Nie można połączyć z `--tool-path` opcji. Jeśli nie określisz tej opcji, należy określić `--tool-path` opcji.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--tool-path <PATH>`

Określa lokalizację, gdzie zainstalować narzędzie globalne. ŚCIEŻKA może być bezwzględny lub względny. Jeśli ŚCIEŻKA nie istnieje, polecenie próbuje je utworzyć. Nie można połączyć z `--global` opcji. Jeśli nie określisz tej opcji, należy określić `--global` opcji.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--version <VERSION_NUMBER>`

Wersja narzędzia do zainstalowania. Domyślnie jest zainstalowana najnowsza wersja stabilne wersje pakietów. Ta opcja służy do instalowania wersji zapoznawczej lub starsze wersje tego narzędzia.

## <a name="examples"></a>Przykłady

Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w domyślnej lokalizacji:

`dotnet tool install -g dotnetsay`

Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w określonym folderze systemu Windows:

`dotnet tool install dotnetsay --tool-path c:\global-tools`

Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w określonym folderze Linux/macOS:

`dotnet tool install dotnetsay --tool-path ~/bin`

Instaluje wersję 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>Zobacz także

[Narzędzia globalne .NET core](global-tools.md)