---
title: polecenie lista narzędzi dotnet
description: Polecenie lista narzędzi dotnet zawiera listę narzędzi .NET Core zainstalowanych na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847875"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet tool list`- Wyświetla listę wszystkich [narzędzi .NET Core](global-tools.md) określonego typu aktualnie zainstalowanych na komputerze.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
```

## <a name="description"></a>Opis

Polecenie `dotnet tool list` umożliwia wyświetlenie wszystkich globalnych, ścieżkowych narzędzi lub lokalnych narzędzi zainstalowanych na komputerze. Polecenie zawiera nazwę pakietu, zainstalowaną wersję i polecenie narzędzia.  Aby użyć tego polecenia, należy określić jedną z następujących czynności:

* Narzędzie globalne zainstalowane w lokalizacji domyślnej. Użyj `--global` opcji
* Narzędzie globalne zainstalowane w lokalizacji niestandardowej. Użyj `--tool-path` tej opcji.
* Narzędzie lokalne. Pomiń `--global` `--tool-path` opcje i opcje.

**Lokalne narzędzia są dostępne począwszy od .NET Core SDK 3.0.**

## <a name="options"></a>Opcje

- **`-g|--global`**

  Wyświetla listę globalnych narzędzi dla całego użytkownika. Nie można połączyć z `--tool-path` tą opcją. Pominięcie obu `--global` `--tool-path` i listy narzędzi lokalnych.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--tool-path <PATH>`**

  Określa niestandardową lokalizację, w której można znaleźć narzędzia globalne. PATH może być bezwzględny lub względny. Nie można połączyć z `--global` tą opcją. Pominięcie obu `--global` `--tool-path` i listy narzędzi lokalnych.

## <a name="examples"></a>Przykłady

- **`dotnet tool list -g`**

  Wyświetla listę wszystkich narzędzi globalnych zainstalowanych dla użytkownika na komputerze (bieżący profil użytkownika).

- **`dotnet tool list --tool-path c:\global-tools`**

  Wyświetla listę narzędzi globalnych z określonego katalogu systemu Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Wyświetla listę narzędzi globalnych z określonego katalogu Linux/macOS.

- **`dotnet tool list`**

  Wyświetla listę wszystkich narzędzi lokalnych dostępnych w bieżącym katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core](local-tools-how-to-use.md)
