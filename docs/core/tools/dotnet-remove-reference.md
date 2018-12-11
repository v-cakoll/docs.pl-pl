---
title: polecenie odwołania remove DotNet
description: Polecenia dotnet Usuń odwołanie zapewnia wygodny sposób, aby usunąć odwołania projekt-projekt.
ms.date: 05/29/2018
ms.openlocfilehash: bfac4721743babcf48fd8e86a50c8df136e1bfce
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170616"
---
# <a name="dotnet-remove-reference"></a>polecenia DotNet Usuń odwołanie

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet remove reference` -Usuwa odwołania projekt projekt.

## <a name="synopsis"></a>Streszczenie

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Opis

`dotnet remove reference` Polecenie zapewnia wygodny sposób, aby usunąć odwołania do projektu z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Docelowy plik projektu. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.

`PROJECT_REFERENCES`

Projekt do projektu (P2P) odwołuje się do usunięcia. Można określić jeden lub wiele projektów. [Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminale systemu Unix/Linux.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-f|--framework <FRAMEWORK>`

Usuwa odwołanie, tylko wtedy, gdy przeznaczonych dla określonego [framework](../../standard/frameworks.md).

## <a name="examples"></a>Przykłady

Usuń odwołanie do projektu z określonego projektu:

`dotnet remove app/app.csproj reference lib/lib.csproj`

Usuń wiele odwołań do projektu z projektu w bieżącym katalogu:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

Usuń wiele odwołania do projektu przy użyciu wzorca glob w systemie Unix/Linux:

`dotnet remove app/app.csproj reference **/*.csproj`
