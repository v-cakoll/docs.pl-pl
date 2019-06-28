---
title: polecenia DotNet-Dodaj odwołania — polecenie
description: Dotnet Dodaj odwołanie do polecenia zapewnia wygodny sposób, aby dodać odwołania projektu do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: 6e0ca40e701b62dcc18147f9de83cafa6aa2f50f
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422002"
---
# <a name="dotnet-add-reference"></a>polecenia DotNet-Dodawanie odwołania

**Ten artykuł dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet add reference` -Dodaje odwołania do projektu do projektu (P2P).

## <a name="synopsis"></a>Streszczenie

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Opis

`dotnet add reference` Polecenie zapewnia wygodny sposób, aby dodać odwołania projektu do projektu. Po uruchomieniu polecenia [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) elementy są dodawane do pliku projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Argumenty

* **`PROJECT`**

  Określa plik projektu. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.

* **`PROJECT_REFERENCES`**

  Projekt do projektu (P2P) odwołuje się do dodania. Określ co najmniej jeden projekt. [Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach opartych na systemie Unix/Linux.

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`-f|--framework <FRAMEWORK>`**

  Dodaje odwołania do projektu tylko wtedy, gdy przeznaczonych dla określonego [framework](../../standard/frameworks.md).

* **`--interactive`**

  Umożliwia polecenie, aby zatrzymać i czeka na dane wejściowe użytkownika lub akcji (na przykład w celu ukończenia uwierzytelniania). Dostępne, ponieważ .NET Core SDK w wersji 3.0.

## <a name="examples"></a>Przykłady

* Dodaj odwołanie do projektu:

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* Dodaj wielu odwołania projektu do projektu w bieżącym katalogu:

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* Dodaj wielu odwołania do projektu przy użyciu wzorca obsługi symboli wieloznacznych w systemach Linux/Unix:

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
