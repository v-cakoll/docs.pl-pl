---
title: polecenie aktualizacji narzędzia DotNet — interfejs wiersza polecenia platformy .NET Core
description: Polecenie aktualizacji narzędzi dotnet aktualizuje określonego narzędzia globalnej podstawowe w .NET na maszynie.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 90b0dc91f74d890420dc7185642aa89100cadba8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44069396"
---
# <a name="dotnet-tool-update"></a>Aktualizacja narzędzi DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool update` — Aktualizuje określony [narzędzia programu .NET Core globalnego](global-tools.md) na swojej maszynie.

## <a name="synopsis"></a>Streszczenie

```console
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool update` Polecenia umożliwia aktualizacji narzędzia globalnej platformy .NET Core na urządzeniu do najnowszej stabilnej wersji pakietu. Polecenie powoduje odinstalowanie i ponowne zainstalowanie narzędziem skutecznie aktualizowania. Aby polecenie, albo musisz określić, czy chcesz zaktualizować narzędzie instalacji na poziomie użytkownika, w którym używana jest `--global` opcję lub określ ścieżkę do miejsca narzędzie jest instalowana za pomocą `--tool-path` opcji.

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwy/Identyfikatora pakietu NuGet, który zawiera narzędzie globalnego .NET Core można zaktualizować. Możesz znaleźć przy użyciu nazwy pakietu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.

## <a name="options"></a>Opcje

`--add-source <SOURCE>`

Dodaje dodatkowe źródła pakietu NuGet do użycia podczas instalacji.

`--configfile <FILE>`

Konfiguracja NuGet (*nuget.config*) plik do użycia.

`--framework <FRAMEWORK>`

Określa [platformę docelową](../../standard/frameworks.md) można zaktualizować tego narzędzia na potrzeby.

`-g|--global`

Określa, czy aktualizacja jest narzędziem użytkownika na poziomie. Nie można połączyć z `--tool-path` opcji. Jeśli nie określisz tę opcję, należy określić `--tool-path` opcji.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--tool-path <PATH>`

Określa lokalizację, w którym zainstalowano narzędzie globalne. ŚCIEŻKA może być bezwzględny lub względny. Nie można połączyć z `--global` opcji. Jeśli nie określisz tę opcję, należy określić `--global` opcji.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

## <a name="examples"></a>Przykłady

Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:

`dotnet tool update -g dotnetsay`

Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzia globalnych znajduje się w określonym folderze Windows:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzia globalnych znajduje się w określonym folderze Linux/macOS:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Zobacz także

* [Narzędzia globalnej platformy .NET core](global-tools.md)