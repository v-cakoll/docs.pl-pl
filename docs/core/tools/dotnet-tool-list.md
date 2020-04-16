---
title: Polecenie lista narzędzi dotnet
description: Polecenie lista narzędzi dotnet zawiera listę narzędzi .NET Core zainstalowanych na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 28f9155407d1238f8b0960b69b34ea329ca0e8e6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463347"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet tool list`- Wyświetla listę wszystkich [narzędzi .NET Core](global-tools.md) określonego typu aktualnie zainstalowanego na komputerze.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet tool list` umożliwia wyświetlenie listy wszystkich narzędzi globalnych, ścieżki narzędzi lub narzędzi lokalnych zainstalowanych na komputerze. Polecenie zawiera listę nazwy pakietu, zainstalowanej wersji i polecenia narzędzia.  Aby użyć polecenia, należy określić jedną z następujących czynności:

* Narzędzie globalne zainstalowane w lokalizacji domyślnej. Użyj `--global` tej opcji
* Narzędzie globalne zainstalowane w lokalizacji niestandardowej. Użyj `--tool-path` tej opcji.
* Narzędzie lokalne. Pomiń `--global` `--tool-path` opcje i.

**Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.**

## <a name="options"></a>Opcje

- **`-g|--global`**

  Wyświetla listę narzędzi globalnych dla całego użytkownika. Nie można połączyć `--tool-path` z opcją. Pominięcie obu `--global` `--tool-path` i listy narzędzi lokalnych.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--tool-path <PATH>`**

  Określa niestandardową lokalizację, w której można znaleźć narzędzia globalne. ŚCIEŻKA może być bezwzględna lub względna. Nie można połączyć `--global` z opcją. Pominięcie obu `--global` `--tool-path` i listy narzędzi lokalnych.

## <a name="examples"></a>Przykłady

- **`dotnet tool list -g`**

  Wyświetla listę wszystkich narzędzi globalnych zainstalowanych w całym urządzeniu (bieżący profil użytkownika).

- **`dotnet tool list --tool-path c:\global-tools`**

  Wyświetla listę narzędzi globalnych z określonego katalogu systemu Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Wyświetla listę narzędzi globalnych z określonego katalogu Linux/macOS.

- **`dotnet tool list`**

  Wyświetla listę wszystkich narzędzi lokalnych dostępnych w bieżącym katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](local-tools-how-to-use.md)
