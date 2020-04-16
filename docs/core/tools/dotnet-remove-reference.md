---
title: dotnet usunąć polecenie odwołania
description: Polecenie dotnet remove reference zapewnia wygodną opcję usuwania odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 92d36bbbde64d806abc8f223c5f08e3f3d79ce9d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463442"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet remove reference`- Usuwa odwołania do projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>] <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet remove reference` zapewnia wygodną opcję usuwania odwołań do projektu z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Docelowy plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego.

`PROJECT_REFERENCES`

Odwołania do projektu do projektu (P2P) do usunięcia. Można określić jeden lub wiele projektów. [Wzorce Glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane na terminalach opartych na systemie Unix/Linux.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-f|--framework <FRAMEWORK>`**

  Usuwa odwołanie tylko wtedy, gdy kierowanie na określoną [strukturę](../../standard/frameworks.md).

## <a name="examples"></a>Przykłady

- Usuń odwołanie do projektu z określonego projektu:

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- Usuń wiele odwołań do projektu z projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Usuń wiele odwołań do projektu przy użyciu wzorca glob w systemie Unix/Linux:

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
