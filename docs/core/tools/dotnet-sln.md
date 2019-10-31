---
title: dotnet sln — polecenie
description: Polecenie dotnet-sln udostępnia wygodną opcję dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.
ms.date: 10/29/2019
ms.openlocfilehash: 18702c7638798117bd04d5c6a829d64cc6bf18a8
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191821"
---
# <a name="dotnet-sln"></a>dotnet sln

**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet sln` — modyfikuje plik rozwiązania .NET Core.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Opis

`dotnet sln` polecenie zapewnia wygodny sposób dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.

Aby użyć polecenia `dotnet sln`, plik rozwiązania musi już istnieć. Jeśli trzeba ją utworzyć, użyj polecenia [dotnet New](dotnet-new.md) , tak jak w poniższym przykładzie:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania, który ma być używany. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog. Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="commands"></a>Polecenia

### `add`

Dodaje projekt lub wiele projektów do pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania, który ma być używany. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog. Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.

- **`PROJECT_PATH`**

  Ścieżka do projektu, który ma zostać dodany do rozwiązania. Dodaj wiele projektów, dodając je po innych rozdzielonych spacjami. Rozszerzenia [wzorca obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki systemu UNIX/Linux są przetwarzane prawidłowo przez polecenie `dotnet sln`.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--in-root`**

  Umieszcza projekty w katalogu głównym rozwiązania zamiast tworzenia folderu rozwiązania. Dostępne od wersji .NET Core 3,0 SDK.

- **`-s|--solution-folder`**

  Ścieżka folderu rozwiązania docelowego, do którego mają zostać dodane projekty. Dostępne od wersji .NET Core 3,0 SDK.

### `remove`

Usuwa projekt lub wiele projektów z pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania, który ma być używany. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog. Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.

- **`PROJECT_PATH`**

  Ścieżka do projektu, który ma zostać usunięty z rozwiązania. Usuń wiele projektów, dodając je po innych rozdzielonych spacjami. Rozszerzenia [wzorca obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki systemu UNIX/Linux są przetwarzane prawidłowo przez polecenie `dotnet sln`.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

### `list`

Wyświetla wszystkie projekty w pliku rozwiązania.

#### <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet sln list [-h|--help]
```
  
#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Plik rozwiązania, który ma być używany. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog. Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.

#### <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="examples"></a>Przykłady

Dodaj C# projekt do rozwiązania:

```dotnetcli
dotnet sln todo.sln add todo-app/todo-app.csproj
```

Usuń C# projekt z rozwiązania:

```dotnetcli
dotnet sln todo.sln remove todo-app/todo-app.csproj
```

Dodaj wiele C# projektów do rozwiązania:

```dotnetcli
dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
```

Usuń wiele C# projektów z rozwiązania:

```dotnetcli
dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
```

Dodawanie wielu C# projektów do rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych (tylko w systemie UNIX/Linux):

```dotnetcli
dotnet sln todo.sln add **/*.csproj
```

Usuwanie wielu C# projektów z rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych (tylko w systemie UNIX/Linux):

```dotnetcli
dotnet sln todo.sln remove **/*.csproj
```
