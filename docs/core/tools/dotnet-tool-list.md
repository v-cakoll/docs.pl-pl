---
title: polecenie listy narzędzi dotnet
description: Polecenie Lista narzędzi dotnet zawiera listę narzędzi .NET Core zainstalowanych na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: bb74cfeaf441cf8a1a030d97d16655f85d8267d1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543459"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet tool list` — wyświetla wszystkie [Narzędzia .NET Core](global-tools.md) określonego typu aktualnie zainstalowane na maszynie.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool list` polecenie umożliwia wyświetlenie listy wszystkich narzędzi programu .NET Core, ścieżek narzędzi i lokalnych zainstalowanych na komputerze. Polecenie wyświetla listę Nazwa pakietu, zainstalowana wersja i polecenie Narzędzia.  Aby użyć polecenia, należy określić jedną z następujących wartości:

* Globalne narzędzie zainstalowane w domyślnej lokalizacji. Użyj opcji `--global`
* Globalne narzędzie zainstalowane w niestandardowej lokalizacji. Użyj opcji `--tool-path`.
* Narzędzie lokalne. Pomiń opcje `--global` i `--tool-path`.

**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**

## <a name="options"></a>Opcje

- **`-g|--global`**

  Wyświetla narzędzia globalne dla całego użytkownika. Nie można łączyć z opcją `--tool-path`. Pominięcie obu `--global` i `--tool-path` powoduje wyświetlenie listy lokalnych narzędzi. 

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--tool-path <PATH>`**

  Określa niestandardową lokalizację, w której mają zostać znalezione narzędzia globalne. ŚCIEŻKA może być bezwzględna lub względna. Nie można łączyć z opcją `--global`. Pominięcie obu `--global` i `--tool-path` powoduje wyświetlenie listy lokalnych narzędzi. 

## <a name="examples"></a>Przykłady

- **`dotnet tool list -g`**

  Wyświetla wszystkie narzędzia globalne zainstalowane na komputerze (bieżący profil użytkownika).

- **`dotnet tool list --tool-path c:\global-tools`**

  Wyświetla listę globalnych narzędzi z określonego katalogu systemu Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Wyświetla listę globalnych narzędzi z określonego katalogu Linux/macOS.

- **`dotnet tool list`**

  Wyświetla listę wszystkich narzędzi lokalnych dostępnych w bieżącym katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
