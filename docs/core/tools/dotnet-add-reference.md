---
title: polecenie "Add Reference" dotnet
description: Polecenie "Dodaj odwołanie" dotnet udostępnia wygodną opcję dodawania projektu do odwołań do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: dc8bc01a2bff4f2cf3a8af9efb233448d7de337f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733271"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet add reference` — dodaje odwołania projektu do projektu (P2P).

## <a name="synopsis"></a>Streszczenie

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Opis

Polecenie `dotnet add reference` udostępnia wygodną opcję dodawania odwołań projektu do projektu. Po uruchomieniu polecenia elementy `<ProjectReference>` są dodawane do pliku projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.

- **`PROJECT_REFERENCES`**

  Odwołania projektu do projektu (P2P) do dodania. Określ jeden lub więcej projektów. [Wzorce globalizowania](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach UNIX/Linux.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-f|--framework <FRAMEWORK>`**

  Dodaje odwołania do projektu tylko w przypadku określania konkretnej [struktury](../../standard/frameworks.md).

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania). Dostępne od wersji .NET Core 3,0 SDK.

## <a name="examples"></a>Przykłady

- Dodaj odwołanie do projektu:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- Dodaj wiele odwołań projektu do projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Dodaj odwołania do wielu projektów za pomocą wzorca obsługi symboli wieloznacznych w systemie Linux/UNIX:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
