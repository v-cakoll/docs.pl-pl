---
title: polecenie aktualizacji narzędzi DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie aktualizacji narzędzi dotnet aktualizuje określonego narzędzia globalne Core w .NET na tym komputerze.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 35a0bd0f85f0beed06d4250d8f195ce4fe4fcca4
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696692"
---
# <a name="dotnet-tool-update"></a>Aktualizacja narzędzi DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool update` — Aktualizuje określony [narzędzie globalne .NET Core](global-tools.md) na tym komputerze.

## <a name="synopsis"></a>Streszczenie

```
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool update` Polecenie umożliwia aktualizacji na tym komputerze do najnowsza stabilna wersja pakietu narzędzia globalne .NET Core. Polecenie powoduje odinstalowanie i ponowne zainstalowanie narzędzia, efektywnie zaktualizowaniem go. Polecenia, albo należy określić chcesz zaktualizować narzędzie instalacji na poziomie użytkownika używającego `--global` opcji lub określ ścieżkę, aby wskazywała narzędzie jest instalowana za pomocą `--tool-path` opcji.

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie globalne .NET Core do aktualizacji. Można znaleźć przy użyciu nazwy pakietu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.

## <a name="options"></a>Opcje

`--add-source <SOURCE>`

Dodaje dodatkowe źródła pakietów NuGet podczas instalacji.

`--configfile <FILE>`

Konfiguracja nuget projektu (*nuget.config*) pliku do użycia.

`--framework <FRAMEWORK>`

Określa [platformy docelowej](../../standard/frameworks.md) można zaktualizować za pomocą narzędzia.

`-g|--global`

Określa, czy aktualizacja jest narzędziem użytkownika na poziomie. Nie można połączyć z `--tool-path` opcji. Jeśli nie określisz tej opcji, należy określić `--tool-path` opcji.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--tool-path <PATH>`

Określa lokalizację, w którym zainstalowano narzędzie globalne. ŚCIEŻKA może być bezwzględny lub względny. Nie można połączyć z `--global` opcji. Jeśli nie określisz tej opcji, należy określić `--global` opcji.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

## <a name="examples"></a>Przykłady

Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:

`dotnet tool update -g dotnetsay`

Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzia globalnych znajduje się w określonym folderze systemu Windows:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzia globalnych znajduje się w określonym folderze Linux/macOS:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Zobacz także

[Narzędzia globalne .NET core](global-tools.md)