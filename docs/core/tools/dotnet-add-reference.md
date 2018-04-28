---
title: DotNet — Dodaj polecenie odwołanie - .NET Core interfejsu wiersza polecenia
description: Dotnet Dodaj odwołanie polecenie zapewnia to wygodny sposób, aby dodać odwołania projektu do projektu.
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: c82696eee2fbe4bbad86e59cf5de1c2e74d048f6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-reference"></a>DotNet — Dodaj odwołanie

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet add reference` -Dodaje odwołania do projektu do projektu (P2P).

## <a name="synopsis"></a>Streszczenie

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Opis

`dotnet add reference` Polecenie zapewnia to wygodny sposób, aby dodać odwołania projektu do projektu. Po uruchomieniu polecenia [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) elementy są dodawane do pliku projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Argumenty

`PROJECT`

Określa plik projektu. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.

`PROJECT_REFERENCES`

Projekt do projektu (P2P) odwołuje się do dodania. Określ co najmniej jeden projekt. [Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach opartych na systemie Unix/Linux.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-f|--framework <FRAMEWORK>`

Dodaje odwołania do projektu, tylko gdy jest określony [framework](../../standard/frameworks.md).

## <a name="examples"></a>Przykłady

Dodaj odwołanie do projektu:

`dotnet add app/app.csproj reference lib/lib.csproj`

Dodaj wiele odwołań do projektu do projektu w bieżącym katalogu:

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Dodaj wiele odwołań do projektu przy użyciu wzorca globbing na systemie Linux/Unix:

`dotnet add app/app.csproj reference **/*.csproj`
