---
title: dotnet-Dodaj polecenie referencyjne
description: Polecenie "Dodaj odwołanie" dotnet udostępnia wygodną opcję dodawania projektu do odwołań do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: 867596058aad8f9c38918e6d6657709d0d0699b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784046"
---
# <a name="dotnet-add-reference"></a>dotnet — Dodawanie odwołania

**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet add reference`-Dodaje odwołania projektu do projektu (P2P).

## <a name="synopsis"></a>Streszczenie

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Opis

`dotnet add reference` Polecenie udostępnia wygodną opcję dodawania odwołań projektu do projektu. Po uruchomieniu polecenia `<ProjectReference>` elementy są dodawane do pliku projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Argumenty

* **`PROJECT`**

  Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.

* **`PROJECT_REFERENCES`**

  Odwołania projektu do projektu (P2P) do dodania. Określ jeden lub więcej projektów. [Wzorce globalizowania](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach UNIX/Linux.

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`-f|--framework <FRAMEWORK>`**

  Dodaje odwołania do projektu tylko w przypadku określania konkretnej [struktury](../../standard/frameworks.md).

* **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania). Dostępne od wersji .NET Core 3,0 SDK.

## <a name="examples"></a>Przykłady

* Dodaj odwołanie do projektu:

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* Dodaj wiele odwołań projektu do projektu w bieżącym katalogu:

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* Dodaj odwołania do wielu projektów za pomocą wzorca obsługi symboli wieloznacznych w systemie Linux/UNIX:

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
