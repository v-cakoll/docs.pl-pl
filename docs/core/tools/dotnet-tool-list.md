---
title: polecenie listy narzędzi dotnet
description: Polecenie Lista narzędzi dotnet zawiera listę narzędzi .NET Core zainstalowanych na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 4035c5be233232e53c6d7150485f737108c1e18d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925465"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet tool list`-Wyświetla wszystkie [Narzędzia .NET Core](global-tools.md) określonego typu aktualnie zainstalowane na maszynie.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>Opis

`dotnet tool list`Polecenie umożliwia wyświetlenie listy wszystkich narzędzi programu .NET Core, ścieżek narzędzi i lokalnych zainstalowanych na komputerze. Polecenie wyświetla listę Nazwa pakietu, zainstalowana wersja i polecenie Narzędzia.  Aby użyć polecenia, należy określić jedną z następujących wartości:

* Aby wyświetlić narzędzia globalne zainstalowane w lokalizacji domyślnej, użyj `--global` opcji
* Aby wyświetlić narzędzia globalne zainstalowane w niestandardowej lokalizacji, użyj `--tool-path` opcji.
* Aby wyświetlić listę lokalnych narzędzi, użyj `--local` opcji lub Pomiń `--global` Opcje, `--tool-path` i `--local` .

**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**

## <a name="options"></a>Opcje

- **`-g|--global`**

  Wyświetla narzędzia globalne dla całego użytkownika. Nie można łączyć z `--tool-path` opcją. Pomijanie obu `--global` i `--tool-path` wyświetla listę lokalnych narzędzi.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--local`**

  Wyświetla listę lokalnych narzędzi dla bieżącego katalogu. Nie można łączyć z `--global` `--tool-path` opcjami ani. Pominięcie obu tych elementów `--global` i `--tool-path` wyświetlenie listy lokalnych narzędzi, nawet jeśli `--local` nie jest określony.

- **`--tool-path <PATH>`**

  Określa niestandardową lokalizację, w której mają zostać znalezione narzędzia globalne. ŚCIEŻKA może być bezwzględna lub względna. Nie można łączyć z `--global` opcją. Pomijanie obu `--global` i `--tool-path` wyświetla listę lokalnych narzędzi.

## <a name="examples"></a>Przykłady

- **`dotnet tool list -g`**

  Wyświetla wszystkie narzędzia globalne zainstalowane na komputerze (bieżący profil użytkownika).

- **`dotnet tool list --tool-path c:\global-tools`**

  Wyświetla listę globalnych narzędzi z określonego katalogu systemu Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Wyświetla listę globalnych narzędzi z określonego katalogu Linux/macOS.

- **`dotnet tool list`** oraz**`dotnet tool list --local`**

  Wyświetla listę wszystkich narzędzi lokalnych dostępnych w bieżącym katalogu.

## <a name="see-also"></a>Zobacz także

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie narzędzia globalnego platformy .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie lokalnego narzędzia .NET Core i używanie go przy użyciu interfejs wiersza polecenia platformy .NET Core](local-tools-how-to-use.md)
