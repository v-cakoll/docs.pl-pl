---
title: polecenie Narzędzia dotnet
description: Polecenie programu dotnet narzędzie do przywracania instaluje na komputerze środowisko .NET Core Local Tools znajdujące się w zakresie dla bieżącego katalogu.
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543909"
---
# <a name="dotnet-tool-restore"></a>Przywracanie narzędzia dotnet

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet tool restore` — instaluje na komputerze lokalne narzędzia platformy .NET Core, które znajdują się w zakresie dla bieżącego katalogu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool restore` polecenie znajduje plik manifestu narzędzia, który znajduje się w zakresie dla bieżącego katalogu i instaluje narzędzia, które są w nim wymienione. Aby uzyskać informacje na temat plików manifestu, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool) i [wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

Nazwa/identyfikator pakietu NuGet zawierającego narzędzie .NET Core do zainstalowania.

## <a name="options"></a>Opcje

- **`--configfile <FILE>`**

  Plik konfiguracji NuGet (*NuGet. config*) do użycia.

- **`--add-source <SOURCE>`**

  Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.

- **`--tool-manifest <PATH>`**

  Ścieżka do pliku manifestu.

- **`--disable-parallel`**

  Zapobiegaj równoległemu przywracaniu wielu projektów.

- **`--ignore-failed-sources`**

  Traktuj błędy źródłowe pakietu jako ostrzeżenia.

- **`--no-cache`**

  Nie Buforuj pakietów i żądań HTTP.

- **`--interactive`**

  Umożliwia zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład zakończenie uwierzytelniania).

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.

## <a name="example"></a>Przykład

- **`dotnet tool restore`**

  Przywraca lokalne narzędzia dla bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
