---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia
description: Samouczek krok po kroku pokazujący, jak rozpocząć pracę z platformą .NET Core w systemie Windows, Linux lub macOS przy użyciu interfejs wiersza polecenia platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 7658f2498b87a90b3925d83628f6ea9247a2fc15
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840874"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core

W tym artykule opisano sposób rozpoczynania opracowywania aplikacji .NET Core, które działają w systemach Windows, Linux i macOS przy użyciu interfejs wiersza polecenia platformy .NET Core.

Jeśli nie znasz interfejs wiersza polecenia platformy .NET Core, zapoznaj się z tematem [interfejs wiersza polecenia platformy .NET Core Omówienie](../tools/index.md).

## <a name="prerequisites"></a>Wymagania wstępne

- [Zestaw .NET Core SDK 3,1](https://dotnet.microsoft.com/download) lub nowszymi wersjami.
- Wybrany edytor tekstu lub edytor kodu.

## <a name="hello-console-app"></a>Witaj, Aplikacja konsolowa!

[Przykładowy kod można wyświetlić lub pobrać](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium usługi GitHub/przykłady Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*. Przejdź do utworzonego folderu i wpisz następujące.

```dotnetcli
dotnet new console
dotnet run
```

Wykonajmy szybkie wskazówki:

01. `dotnet new console`

    Program [dotnet New](../tools/dotnet-new.md) tworzy aktualny plik projektu *Hello. csproj* z zależnościami niezbędnymi do skompilowania aplikacji konsolowej. Tworzy również *program.cs*, podstawowy plik zawierający punkt wejścia dla aplikacji.

    *Witaj. csproj*:

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i skompilowania programu.

    - `<OutputType>`Element określa, że tworzysz plik wykonywalny, innymi słowy, Aplikacja konsolowa.
    - `<TargetFramework>`Element określa, która implementacja platformy .NET jest celem. W zaawansowanym scenariuszu można określić wiele platform docelowych i skompilować je do wszystkich w ramach jednej operacji. W tym samouczku dojdziemy do kompilowania tylko dla platformy .NET Core 3,1.

    *Program.cs*:

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    Program jest uruchamiany przez `using System` , co oznacza, że w zakresie tego pliku można przenieść wszystkie elementy w `System` przestrzeni nazw. `System`Przestrzeń nazw zawiera `Console` klasę.

    Następnie zdefiniujemy przestrzeń nazw o nazwie `Hello` . Możesz to zmienić w dowolny sposób. Klasa o nazwie `Program` jest zdefiniowana w tej przestrzeni nazw za pomocą `Main` metody, która pobiera tablicę ciągów o nazwie `args` . Ta tablica zawiera listę argumentów przekazaną podczas uruchamiania programu. W takim przypadku tablica nie jest używana, a program po prostu zapisuje tekst "Hello world!" w konsoli. Później wprowadzimy zmiany w kodzie, który będzie korzystał z tego argumentu.

    `dotnet new`wywołania [dotnet Restore](../tools/dotnet-restore.md) niejawnie. `dotnet restore`wywołuje pakiet [NuGet](https://www.nuget.org/) (Menedżer pakietów .NET) w celu przywrócenia drzewa zależności. Pakiet NuGet analizuje plik *Hello. csproj* , pobiera zależności zdefiniowane w pliku (lub zbiera je z pamięci podręcznej na maszynie) i zapisuje plik *obj/Project. assets. JSON* , który jest niezbędny do skompilowania i uruchomienia przykładu.

02. `dotnet run`

    [uruchomienia](../tools/dotnet-run.md) programu dotnet [kompiluje kompilacje dotnet](../tools/dotnet-build.md) , aby upewnić się, że cele kompilacji zostały skompilowane, a następnie wywołuje, `dotnet <assembly.dll>` Aby uruchomić aplikację docelową.

    ```dotnetcli
    dotnet run
    ```

    Otrzymujesz następujące dane wyjściowe.

    ```console
    Hello World!
    ```

    Alternatywnie można również uruchomić polecenie, `dotnet build` Aby skompilować kod bez uruchamiania aplikacji konsolowej kompilacji. Powoduje to skompilowaną aplikację jako plik DLL, na podstawie nazwy projektu. W takim przypadku utworzony plik ma nazwę *Hello. dll*. Ta aplikacja może być uruchamiana przy użyciu `dotnet bin\Debug\netcoreapp3.1\Hello.dll` systemu Windows (w `/` przypadku systemów innych niż Windows).

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    Otrzymujesz następujące dane wyjściowe.

    ```console
    Hello World!
    ```

    Po skompilowaniu aplikacji plik wykonywalny specyficzny dla systemu operacyjnego został utworzony razem z `Hello.dll` . W systemie Windows może to być `Hello.exe` : w systemie Linux lub macOS `hello` . W powyższym przykładzie plik ma nazwę z `Hello.exe` lub `Hello` . Można uruchomić ten plik wykonywalny bezpośrednio.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Modyfikowanie programu

Zmieńmy program na bit. Liczby Fibonacci są przyjemne, więc Dodajmy ten argument, a także użyjesz argumentu, aby powitać osobę, która uruchamia aplikację.

01. Zastąp zawartość pliku *program.cs* następującym kodem:

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. Uruchom [kompilację dotnet](../tools/dotnet-build.md) , aby skompilować zmiany.

03. Uruchom program, przekazując do aplikacji parametr. Gdy używasz `dotnet` polecenia, aby uruchomić aplikację, Dodaj `--` ją do końca. Wszystkie elementy z prawej strony `--` zostaną przesłane jako parametr do aplikacji. W poniższym przykładzie wartość `John` jest przenoszona do aplikacji.

    ```dotnetcli
    dotnet run -- John
    ```

    Otrzymujesz następujące dane wyjściowe.

    ```console
    Hello John!
    Fibonacci Numbers 1-15:
    1: 0
    2: 1
    3: 1
    4: 2
    5: 3
    6: 5
    7: 8
    8: 13
    9: 21
    10: 34
    11: 55
    12: 89
    13: 144
    14: 233
    15: 377
    ```

I to wszystko. Możesz zmodyfikować *program.cs* w dowolny sposób.

## <a name="working-with-multiple-files"></a>Praca z wieloma plikami

Pojedyncze pliki są ograniczone do prostych programów jednostronnych, ale jeśli tworzysz bardziej złożoną aplikację, prawdopodobnie będziesz mieć wiele plików kodu w projekcie. Utwórzmy od poprzedniego przykładu Fibonacci przez buforowanie niektórych wartości Fibonacci i dodanie niektórych funkcji cyklicznych.

01. Dodaj nowy plik w katalogu *Hello* o nazwie *FibonacciGenerator.cs* przy użyciu następującego kodu:

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. Zmień `Main` metodę w pliku *program.cs* , aby utworzyć wystąpienie nowej klasy i wywołać jej metodę tak jak w poniższym przykładzie:

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. Uruchom [kompilację dotnet](../tools/dotnet-build.md) , aby skompilować zmiany.

04. Uruchom aplikację, wykonując [uruchomienie programu dotnet](../tools/dotnet-run.md).

    ```dotnetcli
    dotnet run
    ```

    Otrzymujesz następujące dane wyjściowe.

    ```console
    0
    1
    1
    2
    3
    5
    8
    13
    21
    34
    55
    89
    144
    233
    377
    ```

## <a name="publish-your-app"></a>Publikowanie aplikacji

Gdy wszystko będzie gotowe do dystrybucji swojej aplikacji, użyj polecenia [dotnet Publish](../tools/dotnet-publish.md) , aby wygenerować folder _publikowania_ w polu _Debuguj debugowanie w usłudze bin \\ \\ netcoreapp 3.1 \\ \\ _ (Korzystanie `/` z systemów innych niż Windows). Zawartość folderu _publikowania_ można dystrybuować na inne platformy, o ile już zainstalowano środowisko uruchomieniowe dotnet.

```dotnetcli
dotnet publish
```

Dane wyjściowe są podobne do poniższych.

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

Powyższe dane wyjściowe mogą się różnić w zależności od bieżącego folderu i systemu operacyjnego, ale dane wyjściowe powinny być podobne.

Opublikowaną aplikację można uruchomić za pomocą polecenia [dotnet](../tools/dotnet.md) :

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

Otrzymujesz następujące dane wyjściowe.

```console
0
1
1
2
3
5
8
13
21
34
55
89
144
233
377
```

Jak wspomniano na początku tego artykułu, tworzony jest plik wykonywalny specyficzny dla systemu operacyjnego wraz z programem `Hello.dll` . W systemie Windows może to być `Hello.exe` : w systemie Linux lub macOS `hello` . W powyższym przykładzie plik ma nazwę z `Hello.exe` lub `Hello` . Można uruchomić bezpośrednio ten opublikowany plik wykonywalny.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

0
1
1
2
3
5
8
13
21
34
55
89
144
233
377
```

## <a name="conclusion"></a>Podsumowanie

I to wszystko. Teraz możesz zacząć korzystać z podstawowych pojęć zamieszczonych w tym miejscu, aby utworzyć własne programy.

## <a name="see-also"></a>Zobacz także

- [Organizowanie i testowanie projektów przy użyciu interfejs wiersza polecenia platformy .NET Core](testing-with-cli.md)
- [Publikowanie aplikacji platformy .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md)
- [Wdrażanie aplikacji .NET Core](../deploying/index.md)
