---
title: polecenie sln DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie dotnet sln oferuje wygodny możliwość dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 845e666b9d8a8b206c7e1978a7dde9f33ffb8a32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-sln"></a>DotNet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet sln` -Modyfikuje plik rozwiązania .NET Core.

## <a name="synopsis"></a>Streszczenie

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Opis

`dotnet sln` Polecenia oferuje wygodny sposób dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.

## <a name="commands"></a>Polecenia

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Dodaje projekt lub wielu projektach pliku rozwiązania. [Wzorce globbing](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminali z systemem Unix/Linux.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Usuwa projekt lub wielu projektów z pliku rozwiązania. [Wzorce globbing](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminali z systemem Unix/Linux.

`list`

Lista wszystkich projektów w pliku rozwiązania.

## <a name="arguments"></a>Argumenty

`SOLUTION_NAME`

Plik rozwiązania do użycia. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego. Jeśli istnieje wiele plików rozwiązania w katalogu, co jest wymagane.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

## <a name="examples"></a>Przykłady

Dodaj projekt C# do rozwiązania:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Usuwanie projektu C# z rozwiązania:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Dodawanie wielu projektów C# do rozwiązania:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Usuń wiele projektów C# z rozwiązania:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Dodawanie wielu projektów C# do rozwiązania przy użyciu wzorca globbing:

`dotnet sln todo.sln add **/*.csproj`

Usuń wiele projektów C# z rozwiązania przy użyciu wzorca globbing:

`dotnet sln todo.sln remove **/*.csproj`
