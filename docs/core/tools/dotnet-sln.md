---
title: dotnet sln — polecenie
description: Polecenie dotnet-sln udostępnia wygodną opcję dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543485"
---
# <a name="dotnet-sln"></a>dotnet sln

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Name (Nazwa)

`dotnet sln` — wyświetla lub modyfikuje projekty w pliku rozwiązania .NET Core.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Opis

`dotnet sln` polecenie zapewnia wygodny sposób wyświetlania i modyfikowania projektów w pliku rozwiązania.

Aby użyć polecenia `dotnet sln`, plik rozwiązania musi już istnieć. Jeśli trzeba ją utworzyć, użyj polecenia [dotnet New](dotnet-new.md) , jak w poniższym przykładzie:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania, który ma być używany. Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog. Jeśli nie zostanie znaleziony żaden plik rozwiązania lub wiele plików rozwiązania, polecenie nie powiedzie się.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu użycia polecenia.

## <a name="commands"></a>Polecenia

### `list`

Wyświetla wszystkie projekty w pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania, który ma być używany. Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog. Jeśli nie zostanie znaleziony żaden plik rozwiązania lub wiele plików rozwiązania, polecenie nie powiedzie się.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu użycia polecenia.
  
### `add`

Dodaje jeden lub więcej projektów do pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania, który ma być używany. Jeśli nie jest określony, polecenie przeszukuje bieżący katalog dla jednego i kończy się niepowodzeniem, jeśli istnieje wiele plików rozwiązania.

- **`PROJECT_PATH`**

  Ścieżka do projektu lub projektów, które mają zostać dodane do rozwiązania. Rozszerzenia [wzorca obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki systemu UNIX/Linux są przetwarzane prawidłowo przez polecenie `dotnet sln`.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu użycia polecenia.

- **`--in-root`**

  Umieszcza projekty w katalogu głównym rozwiązania zamiast tworzenia folderu rozwiązania. Dostępne od wersji .NET Core 3,0 SDK.

- **`-s|--solution-folder`**

  Ścieżka folderu rozwiązania docelowego, do którego mają zostać dodane projekty. Dostępne od wersji .NET Core 3,0 SDK.

### `remove`

Usuwa projekt lub wiele projektów z pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania, który ma być używany. Jeśli pozostanie nieokreślony, polecenie przeszukuje bieżący katalog dla jednego i kończy się niepowodzeniem, jeśli istnieje wiele plików rozwiązania.

- **`PROJECT_PATH`**

  Ścieżka do projektu lub projektów, które mają zostać dodane do rozwiązania. Rozszerzenia [wzorca obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki systemu UNIX/Linux są przetwarzane prawidłowo przez polecenie `dotnet sln`.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje opis sposobu użycia polecenia.

## <a name="examples"></a>Przykłady

- Utwórz listę projektów w rozwiązaniu:

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Dodaj C# projekt do rozwiązania:

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Usuń C# projekt z rozwiązania:

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Dodaj wiele C# projektów do katalogu głównego rozwiązania:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- Dodaj wiele C# projektów do rozwiązania:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Usuń wiele C# projektów z rozwiązania:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Dodawanie wielu C# projektów do rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych (tylko w systemie UNIX/Linux):

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Usuwanie wielu C# projektów z rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych (tylko w systemie UNIX/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
