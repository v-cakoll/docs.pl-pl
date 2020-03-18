---
title: polecenie dotnet add reference
description: Polecenie dotnet add reference zapewnia wygodną opcję dodawania projektu do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 84ea25e94efc8d84aebfeccf62c30a64551c5019
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503788"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet add reference`- Dodaje odwołania projektu do projektu (P2P).

## <a name="synopsis"></a>Streszczenie

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Opis

Polecenie `dotnet add reference` zapewnia wygodną opcję dodawania odwołań do projektu. Po uruchomieniu polecenia `<ProjectReference>` elementy są dodawane do pliku projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego.

- **`PROJECT_REFERENCES`**

  Odwołania do projektu do projektu (P2P) do dodania. Określ jeden lub więcej projektów. [Wzorce Glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach unix/linux.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-f|--framework <FRAMEWORK>`**

  Dodaje odwołania do projektu tylko wtedy, gdy jest przeznaczony dla określonej [struktury](../../standard/frameworks.md).

- **`--interactive`**

  Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie). Dostępne od sdk .NET Core 3.0.

## <a name="examples"></a>Przykłady

- Dodaj odwołanie do projektu:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- Dodaj wiele odwołań do projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Dodaj wiele odwołań do projektu przy użyciu wzorca globbing w systemie Linux/Unix:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
