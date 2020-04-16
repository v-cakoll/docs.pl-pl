---
title: dotnet sln, polecenie
description: Polecenie dotnet-sln zapewnia wygodną opcję dodawania, usuwania i listy projektów w pliku rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: 231287477d986f9ec4a5404cc5278e76c297faa4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463396"
---
# <a name="dotnet-sln"></a>dotnet sln

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet sln`- Wyświetla lub modyfikuje projekty w pliku rozwiązania .NET Core.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet sln` zapewnia wygodny sposób listy i modyfikowania projektów w pliku rozwiązania.

Aby użyć `dotnet sln` polecenia, plik rozwiązania musi już istnieć. Jeśli chcesz go utworzyć, użyj nowego polecenia [dotnet,](dotnet-new.md) jak w poniższym przykładzie:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania do użycia. Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog dla jednego. Jeśli nie znajdzie żadnego pliku rozwiązania lub wielu plików rozwiązania, polecenie zakończy się niepowodzeniem.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu korzystania z polecenia.

## <a name="commands"></a>Polecenia

### `list`

Wyświetla listę wszystkich projektów w pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania do użycia. Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog dla jednego. Jeśli nie znajdzie żadnego pliku rozwiązania lub wielu plików rozwiązania, polecenie zakończy się niepowodzeniem.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu korzystania z polecenia.
  
### `add`

Dodaje jeden lub więcej projektów do pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania do użycia. Jeśli jest nieokreślony, polecenie przeszukuje bieżący katalog dla jednego i kończy się niepowodzeniem, jeśli istnieje wiele plików rozwiązania.

- **`PROJECT_PATH`**

  Ścieżka do projektu lub projektów, aby dodać do rozwiązania. Rozszerzenia [wzorca skorupy](https://en.wikipedia.org/wiki/Glob_(programming)) Uniksa/Linuksa są `dotnet sln` przetwarzane poprawnie przez polecenie.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu korzystania z polecenia.

- **`--in-root`**

  Umieszcza projekty w katalogu głównym rozwiązania, zamiast tworzyć folder rozwiązania. Dostępne od .NET Core 3.0 SDK.

- **`-s|--solution-folder <PATH>`**

  Ścieżka folderu rozwiązania docelowego, do aby dodać projekty. Dostępne od .NET Core 3.0 SDK.

### `remove`

Usuwa projekt lub wiele projektów z pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania do użycia. Jeśli nie jest określony, polecenie przeszukuje bieżący katalog dla jednego i kończy się niepowodzeniem, jeśli istnieje wiele plików rozwiązania.

- **`PROJECT_PATH`**

  Ścieżka do projektu lub projektów, aby dodać do rozwiązania. Rozszerzenia [wzorca skorupy](https://en.wikipedia.org/wiki/Glob_(programming)) Uniksa/Linuksa są `dotnet sln` przetwarzane poprawnie przez polecenie.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu korzystania z polecenia.

## <a name="examples"></a>Przykłady

- Wymień projekty w rozwiązaniu:

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Dodaj projekt języka C# do rozwiązania:

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Usuń projekt języka C# z rozwiązania:

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Dodaj wiele projektów języka C# do katalogu głównego rozwiązania:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- Dodaj wiele projektów języka C# do rozwiązania:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Usuń wiele projektów języka C# z rozwiązania:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Dodaj wiele projektów języka C# do rozwiązania przy użyciu wzorca globbingu (tylko Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Dodaj wiele projektów języka C# do rozwiązania przy użyciu wzorca globbing (tylko program Windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln add (ls **/*.csproj)
  ```

- Usuń wiele projektów języka C# z rozwiązania przy użyciu wzorca globbingu (tylko Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- Usuń wiele projektów języka C# z rozwiązania przy użyciu wzorca globbing (tylko program Windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln remove (ls **/*.csproj)
  ```
