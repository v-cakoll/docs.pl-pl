---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia
description: Samouczek krok po kroku przedstawiający sposób rozpoczynania pracy z programem .NET Core w systemach Windows, Linux lub macOS przy użyciu procesora CLI .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240860"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>Wprowadzenie do programu .NET Core przy użyciu procesora CLI .NET Core

W tym artykule przedstawiono sposób uruchamiania tworzenia aplikacji .NET Core działających w systemach Windows, Linux i macOS przy użyciu procesora CLI .NET Core.

Jeśli nie znasz cli programu .NET Core, zobacz [omówienie.NET Core CLI](../tools/index.md).

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download) lub nowsze wersje.
- Wybrany edytor tekstu lub edytor kodu.

## <a name="hello-console-app"></a>Witam, Aplikacja konsolowa!

Przykładowy kod można [wyświetlić lub pobrać](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium GitHub dotnet/samples. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otwórz wiersz polecenia i utwórz folder o nazwie *Hello*. Przejdź do utworzonego folderu i wpisz następujące elementy.

```dotnetcli
dotnet new console
dotnet run
```

Zróbmy szybki przewodnik:

01. `dotnet new console`

    [dotnet new](../tools/dotnet-new.md) tworzy aktualny plik projektu *Hello.csproj* z zależnościami niezbędnymi do utworzenia aplikacji konsoli. Tworzy również *Program.cs*, podstawowy plik zawierający punkt wejścia dla aplikacji.

    *Hello.csproj*:

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i skompilowania programu.

    - Element `<OutputType>` określa, że budujemy plik wykonywalny, innymi słowy aplikacji konsoli.
    - Element `<TargetFramework>` określa, na co kierujemy implementację .NET. W zaawansowanym scenariuszu można określić wiele struktur docelowych i skompilować do wszystkich tych w jednej operacji. W tym samouczku będziemy trzymać się budynku tylko dla .NET Core 3.1.

    *Program.cs:*

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    Program rozpoczyna `using System`się od , co `System` oznacza "przynieś wszystko w przestrzeni nazw do zakresu dla tego pliku". Obszar `System` nazw zawiera `Console` klasę.

    Następnie definiujemy obszar `Hello`nazw o nazwie . Możesz to zmienić na doc, co chcesz. Klasa o `Program` nazwie jest zdefiniowana w `Main` tym obszarze nazw, z `args`metodą, która przyjmuje tablicę ciągów o nazwie . Ta tablica zawiera listę argumentów przekazywanych po uruchomieniu programu. Jak to jest, ta tablica nie jest używany, a program po prostu pisze tekst "Hello World!" w konsoli. Później wprowadzimy zmiany w kodzie, które będą korzystać z tego argumentu.

    `dotnet new`wywołuje [przywracanie dotnet](../tools/dotnet-restore.md) niejawnie. `dotnet restore`wywołania [nuget](https://www.nuget.org/) (menedżer pakietów.NET), aby przywrócić drzewo zależności. NuGet analizuje plik *Hello.csproj,* pobiera zależności zdefiniowane w pliku (lub pobiera je z pamięci podręcznej na komputerze) i zapisuje plik *obj/project.assets.json,* który jest niezbędny do skompilowania i uruchomienia próbki.

02. `dotnet run`

    [dotnet uruchom](../tools/dotnet-run.md) [wywołania dotnet kompilacji,](../tools/dotnet-build.md) aby upewnić się, że cele kompilacji zostały zbudowane, a następnie wywołuje `dotnet <assembly.dll>` do uruchomienia aplikacji docelowej.

    ```dotnetcli
    dotnet run
    ```

    Otrzymasz następujące dane wyjściowe.

    ```console
    Hello World!
    ```

    Alternatywnie można również `dotnet build` uruchomić, aby skompilować kod bez uruchamiania aplikacji konsoli kompilacji. Powoduje to skompilowany aplikacji, jako plik DLL, na podstawie nazwy projektu. W takim przypadku utworzony plik nosi nazwę *Hello.dll*. Ta aplikacja może `dotnet bin\Debug\netcoreapp3.1\Hello.dll` być uruchamiana `/` w systemie Windows (używany dla systemów innych niż Windows).

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    Otrzymasz następujące dane wyjściowe.

    ```console
    Hello World!
    ```

    Po skompilowaniu aplikacji utworzono plik wykonywalny `Hello.dll`specyficzny dla systemu operacyjnego wraz z plikiem . W systemie Windows `Hello.exe`byłoby to ; na Linuksie lub macOS, byłoby `hello`to . W powyższym przykładzie plik ma `Hello.exe` `Hello`nazwę lub . Można uruchomić ten plik wykonywalny bezpośrednio.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Modyfikowanie programu

Zmieńmy nieco program. Numery Fibonacciego są zabawne, więc dodajmy to, a także użyjmy argumentu, aby powitać osobę uruchamiającą aplikację.

01. Zastąp zawartość pliku *Program.cs* następującym kodem:

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. Uruchom [kompilację dotnet,](../tools/dotnet-build.md) aby skompilować zmiany.

03. Uruchom program przekazujący parametr do aplikacji. Gdy używasz `dotnet` polecenia, aby uruchomić `--` aplikację, dodaj do końca. Wszystko po prawej `--` stronie zostanie przekazane jako parametr do aplikacji. W poniższym przykładzie `John` wartość jest przekazywana do aplikacji.

    ```dotnetcli
    dotnet run -- John
    ```

    Otrzymasz następujące dane wyjściowe.

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

I to wszystko. Możesz modyfikować *Program.cs* dowolny sposób.

## <a name="working-with-multiple-files"></a>Praca z wieloma plikami

Pojedyncze pliki są w porządku dla prostych jednorazowych programów, ale jeśli budujesz bardziej złożoną aplikację, prawdopodobnie będziesz mieć wiele plików kodu w projekcie. Zbudujmy poprzedni przykład Fibonacciego, buforując niektóre wartości Fibonacciego i dodajmy niektóre funkcje cykliczne.

01. Dodaj nowy plik w katalogu *Hello* o nazwie *FibonacciGenerator.cs* z następującym kodem:

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. Zmień `Main` metodę w pliku *Program.cs,* aby utworzyć wystąpienie nowej klasy i wywołać jej metodę, jak w poniższym przykładzie:

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. Uruchom [kompilację dotnet,](../tools/dotnet-build.md) aby skompilować zmiany.

04. Uruchom aplikację, wykonując [dotnet uruchom](../tools/dotnet-run.md).

    ```dotnetcli
    dotnet run
    ```

    Otrzymasz następujące dane wyjściowe.

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

Gdy wszystko będzie gotowe do dystrybucji aplikacji, użyj polecenia [publikowania dotnet,](../tools/dotnet-publish.md) aby wygenerować folder `/` _publikowania_ w _bin\\debugnetcoreapp3.1\\\\publish\\ _ (używany dla systemów innych niż Windows). Zawartość folderu _publikowania_ można rozpowszechniać na innych platformach, o ile zostały już zainstalowane w czasie wykonywania dotnet.

```dotnetcli
dotnet publish
```

Otrzymasz dane wyjściowe podobne do następującego.

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

Powyższe dane wyjściowe mogą się różnić w zależności od bieżącego folderu i systemu operacyjnego, ale dane wyjściowe powinny być podobne.

Opublikowaną aplikację można uruchomić za pomocą polecenia [dotnet:](../tools/dotnet.md)

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

Otrzymasz następujące dane wyjściowe.

```console
Hello World!
```

Jak wspomniano na początku tego artykułu, plik wykonywalny specyficzny `Hello.dll`dla systemu operacyjnego został utworzony wraz z plikiem . W systemie Windows `Hello.exe`byłoby to ; na Linuksie lub macOS, byłoby `hello`to . W powyższym przykładzie plik ma `Hello.exe` `Hello`nazwę lub . Ten opublikowany plik wykonywalny można uruchomić bezpośrednio.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Podsumowanie

I to wszystko. Teraz możesz zacząć korzystać z podstawowych pojęć, które zostały tutaj nauczone, aby tworzyć własne programy.

## <a name="see-also"></a>Zobacz też

- [Organizowanie i testowanie projektów za pomocą cli .NET Core](testing-with-cli.md)
- [Publikowanie aplikacji .NET Core za pomocą wiersza wiersza wiersza wiersza wiersza .NET Core](../deploying/deploy-with-cli.md)
- [Wdrażanie aplikacji .NET Core](../deploying/index.md)
