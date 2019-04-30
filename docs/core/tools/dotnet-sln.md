---
title: polecenie sln DotNet
description: Polecenia dotnet sln udostępnia wygodne możliwość dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.
ms.date: 06/13/2018
ms.openlocfilehash: a88e22c68f639f2a42e59f9a271e431f04e24a2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665003"
---
# <a name="dotnet-sln"></a>DotNet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet sln` — Modyfikuje plik rozwiązania .NET Core.

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

`dotnet sln` Polecenie zapewnia wygodny sposób dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.

Aby użyć `dotnet sln` polecenia Plik rozwiązania musi już istnieć. Jeśli musisz utworzyć jeden, użyj [dotnet nowe](dotnet-new.md) polecenia, podobnie jak w poniższym przykładzie:

```
dotnet new sln
```

## <a name="commands"></a>Polecenia

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Dodaje projekt lub wielu projektów do pliku rozwiązania. [Wzorce obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminale systemu Unix/Linux.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Usuwa projekt lub wieloma projektami z pliku rozwiązania. [Wzorce obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminale systemu Unix/Linux.

`list`

Wyświetla listę wszystkich projektów w pliku rozwiązania.

## <a name="arguments"></a>Argumenty

`SOLUTION_NAME`

Plik rozwiązania do użycia. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego. W przypadku wielu rozwiązań plików w katalogu, należy określić jedną.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

## <a name="examples"></a>Przykłady

Dodaj projekt C# do rozwiązania:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Usuń projekt C# za pomocą rozwiązania:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Dodawanie wielu projektów języka C# do rozwiązania:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Usuń wiele projektów języka C# za pomocą rozwiązania:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Dodawanie wielu projektów języka C# do rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych:

`dotnet sln todo.sln add **/*.csproj`

Za pomocą rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych, należy usunąć wielu projektów języka C#:

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> Symboli wieloznacznych nie jest funkcją interfejsu wiersza polecenia, ale raczej funkcja powłoki poleceń programu. Aby pomyślnie rozszerzyć plików, należy użyć powłoki, który obsługuje symboli wieloznacznych. Aby uzyskać więcej informacji na temat obsługi symboli wieloznacznych, zobacz [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).
