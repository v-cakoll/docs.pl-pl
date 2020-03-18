---
title: polecenie dotnet remove reference
description: Polecenie odwołania dotnet remove zapewnia wygodną opcję usuwania projektu do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503618"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet remove reference`- Usuwa odwołania projektu do projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet remove reference` zapewnia wygodną opcję usuwania odwołań do projektu z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Docelowy plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego.

`PROJECT_REFERENCES`

Odwołania do projektu (P2P) do usunięcia. Można określić jeden lub wiele projektów. [Wzorce Glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane na terminalach unixowych/linuxowych.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-f|--framework <FRAMEWORK>`**

  Usuwa odwołanie tylko podczas określania określonej [struktury](../../standard/frameworks.md).

## <a name="examples"></a>Przykłady

- Usuń odwołanie do projektu z określonego projektu:

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- Usuń wiele odwołań do projektu z projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Usuń wiele odwołań do projektu za pomocą wzoru glob na Unix/Linux:

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
