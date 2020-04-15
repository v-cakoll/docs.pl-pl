---
title: Polecenie przywracanie narzędzia dotnet
description: Polecenie przywracania narzędzia dotnet instaluje na komputerze narzędzia lokalne .NET Core, które są w zakresie dla bieżącego katalogu.
ms.date: 02/14/2020
ms.openlocfilehash: 0d1e67ec809ddd725721698cc741f9acc99e1ce7
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389616"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**Ten artykuł dotyczy:** ✔️.NET Core 3.0 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet tool restore`- Instaluje na komputerze narzędzia lokalne .NET Core, które są w zakresie dla bieżącego katalogu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [--interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a>Opis

Polecenie `dotnet tool restore` znajduje plik manifestu narzędzia, który znajduje się w zakresie bieżącego katalogu i instaluje narzędzia, które są w nim wymienione. Aby uzyskać informacje o plikach manifestu, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool) i [Wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie .NET Core do zainstalowania.

## <a name="options"></a>Opcje

- **`--configfile <FILE>`**

  Plik konfiguracji NuGet (*nuget.config*).

- **`--add-source <SOURCE>`**

  Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.

- **`--tool-manifest <PATH>`**

  Ścieżka do pliku manifestu.

- **`--disable-parallel`**

  Zapobiegaj przywracaniu wielu projektów równolegle.

- **`--ignore-failed-sources`**

  Traktuj błędy źródła pakietu jako ostrzeżenia.

- **`--no-cache`**

  Nie buforuj pakietów i żądań http.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .

## <a name="example"></a>Przykład

- **`dotnet tool restore`**

  Przywraca narzędzia lokalne dla bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](local-tools-how-to-use.md)
