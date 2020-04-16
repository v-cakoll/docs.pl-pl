---
title: dotnet dodaj polecenie odwołania
description: Polecenie dotnet add reference zapewnia wygodną opcję dodawania projektu do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: f2bd67d181784c4858b8971d05053d196df7818e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463744"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet add reference`- Dodaje odwołania projektu do projektu (P2P).

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet add reference` zapewnia wygodną opcję dodawania odwołań do projektu do projektu. Po uruchomieniu polecenia `<ProjectReference>` elementy są dodawane do pliku projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego.

- **`PROJECT_REFERENCES`**

  Odwołania do projektu do projektu (P2P) do dodania. Określ jeden lub więcej projektów. [Wzorce Glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach opartych na systemie Unix/Linux.

## <a name="options"></a>Opcje

- **`-f|--framework <FRAMEWORK>`**

  Dodaje odwołania do projektu tylko wtedy, gdy kierowanie na określoną [platformę](../../standard/frameworks.md).

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania). Dostępne od .NET Core 3.0 SDK.

## <a name="examples"></a>Przykłady

- Dodaj odwołanie do projektu:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- Dodaj wiele odwołań do projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Dodaj wiele odwołań do projektu przy użyciu wzorca globbingu w systemie Linux/Unix:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
