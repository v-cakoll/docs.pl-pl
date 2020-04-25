---
title: polecenie "Usuń odwołanie" dotnet
description: Polecenie "Usuń odwołanie" dotnet zapewnia wygodną opcję usuwania projektu do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: a45153376d7d6eb764c1d2c6b473d04a273a2de1
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158336"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet remove reference`-Usuwa odwołania z projektu do projektu (P2P).

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a>Opis

`dotnet remove reference` Polecenie zapewnia wygodną opcję usuwania odwołań projektu z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Docelowy plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.

`PROJECT_REFERENCES`

Odwołania między projektami i projektami (P2P) do usunięcia. Można określić jeden lub wiele projektów. [Wzorce globalizowania](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminalach opartych na systemie UNIX/Linux.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-f|--framework <FRAMEWORK>`**

  Usuwa odwołanie tylko w przypadku określania konkretnej [struktury](../../standard/frameworks.md) przy użyciu formatu TFM.

## <a name="examples"></a>Przykłady

- Usuń odwołanie do projektu z określonego projektu:

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- Usuń odwołania do wielu projektów z projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Usuń odwołania do wielu projektów za pomocą wzorca globalizowania w systemie UNIX/Linux:

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
