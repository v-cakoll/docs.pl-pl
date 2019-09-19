---
title: dotnet sln — polecenie
description: Polecenie dotnet-sln udostępnia wygodną opcję dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.
ms.date: 06/13/2018
ms.openlocfilehash: 84508aaefff61b31e2965576ebc2daaae7331951
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117584"
---
# <a name="dotnet-sln"></a>dotnet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet sln`-Modyfikuje plik rozwiązania .NET Core.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Opis

`dotnet sln` Polecenie zapewnia wygodny sposób dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.

Aby użyć `dotnet sln` polecenia, plik rozwiązania musi już istnieć. Jeśli trzeba ją utworzyć, użyj polecenia [dotnet New](dotnet-new.md) , tak jak w poniższym przykładzie:

```dotnetcli
dotnet new sln
```

## <a name="commands"></a>Polecenia

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Dodaje projekt lub wiele projektów do pliku rozwiązania. [Wzorce obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminalach opartych na systemie UNIX/Linux.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Usuwa projekt lub wiele projektów z pliku rozwiązania. [Wzorce obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminalach opartych na systemie UNIX/Linux.

`list`

Wyświetla wszystkie projekty w pliku rozwiązania.

## <a name="arguments"></a>Argumenty

`SOLUTION_NAME`

Plik rozwiązania do użycia. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog. Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótką pomoc dla polecenia.

## <a name="examples"></a>Przykłady

Dodaj C# projekt do rozwiązania:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Usuń C# projekt z rozwiązania:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Dodaj wiele C# projektów do rozwiązania:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Usuń wiele C# projektów z rozwiązania:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Dodawanie wielu C# projektów do rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych:

`dotnet sln todo.sln add **/*.csproj`

Usuwanie wielu C# projektów z rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych:

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> Obsługi symboli wieloznacznych nie jest funkcją interfejsu wiersza polecenia, ale raczej funkcją powłoki poleceń. Aby pomyślnie rozszerzyć pliki, należy użyć powłoki obsługującej obsługi symboli wieloznacznych. Aby uzyskać więcej informacji na temat obsługi symboli wieloznacznych, zobacz [witrynę Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).
