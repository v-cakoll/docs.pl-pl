---
title: dotnet sln, polecenie
description: Polecenie dotnet-sln zapewnia wygodną opcję dodawania, usuwania i wystawiania projektów w pliku rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543485"
---
# <a name="dotnet-sln"></a>dotnet sln

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet sln`- Wyświetla listę lub modyfikuje projekty w pliku rozwiązania .NET Core.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet sln` zapewnia wygodny sposób wystawiania i modyfikowania projektów w pliku rozwiązania.

Aby użyć `dotnet sln` polecenia, plik rozwiązania musi już istnieć. Jeśli chcesz go utworzyć, użyj polecenia [dotnet new,](dotnet-new.md) jak w poniższym przykładzie:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania do użycia. Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego. Jeśli nie znajdzie żadnego pliku rozwiązania lub wielu plików rozwiązania, polecenie nie powiedzie się.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu używania polecenia.

## <a name="commands"></a>Polecenia

### `list`

Wyświetla listę wszystkich projektów w pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania do użycia. Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego. Jeśli nie znajdzie żadnego pliku rozwiązania lub wielu plików rozwiązania, polecenie nie powiedzie się.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu używania polecenia.
  
### `add`

Dodaje jeden lub więcej projektów do pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania do użycia. Jeśli nie jest określony, polecenie przeszukuje bieżący katalog dla jednego i kończy się niepowodzeniem, jeśli istnieje wiele plików rozwiązania.

- **`PROJECT_PATH`**

  Ścieżka do projektu lub projektów, aby dodać do rozwiązania. Rozszerzenia [wzorców globbing](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki Unix/Linux są `dotnet sln` przetwarzane poprawnie przez polecenie.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu używania polecenia.

- **`--in-root`**

  Umieszcza projekty w katalogu głównym rozwiązania, zamiast tworzyć folder rozwiązania. Dostępne od sdk .NET Core 3.0.

- **`-s|--solution-folder`**

  Ścieżka folderu rozwiązania docelowego, do którą chcesz dodać projekty. Dostępne od sdk .NET Core 3.0.

### `remove`

Usuwa projekt lub wiele projektów z pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania do użycia. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego i nie powiedzie się, jeśli istnieje wiele plików rozwiązania.

- **`PROJECT_PATH`**

  Ścieżka do projektu lub projektów, aby dodać do rozwiązania. Rozszerzenia [wzorców globbing](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki Unix/Linux są `dotnet sln` przetwarzane poprawnie przez polecenie.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu używania polecenia.

## <a name="examples"></a>Przykłady

- Lista projektów w rozwiązaniu:

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

- Dodaj wiele projektów Języka C# do rozwiązania przy użyciu wzorca globbing (tylko Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Usuń wiele projektów Języka C# z rozwiązania przy użyciu wzorca globbing (tylko Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
