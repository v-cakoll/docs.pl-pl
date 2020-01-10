---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia interfejs wiersza polecenia platformy .NET Core
description: Samouczek krok po kroku pokazujący, jak rozpocząć pracę z platformą .NET Core w systemie Windows, Linux lub macOS przy użyciu interfejsu wiersza polecenia (CLI) platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 6c394ad2721bcdd91fb750fe93c03f16ca9f799f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714077"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Rozpoczynanie pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia

W tym artykule pokazano, jak rozpocząć tworzenie aplikacji dla wielu platform na maszynie przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core.

Jeśli nie znasz zestawu narzędzi interfejs wiersza polecenia platformy .NET Core, zapoznaj się z tematem [zestaw .NET Core SDK Omówienie](../tools/index.md).

## <a name="prerequisites"></a>Wymagania wstępne

- [Zestaw .NET Core SDK 3,1](https://dotnet.microsoft.com/download) lub nowszymi wersjami.
- Wybrany edytor tekstu lub edytor kodu.

## <a name="hello-console-app"></a>Witaj, Aplikacja konsolowa!

[Przykładowy kod można wyświetlić lub pobrać](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium usługi GitHub/przykłady Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*. Przejdź do utworzonego folderu i wpisz następujące:

```dotnetcli
dotnet new console
dotnet run
```

Wykonajmy szybkie wskazówki:

01. `dotnet new console`

    Program [dotnet New](../tools/dotnet-new.md) tworzy aktualny plik projektu *Hello. csproj* z zależnościami niezbędnymi do skompilowania aplikacji konsolowej. Tworzy również *program.cs*, podstawowy plik zawierający punkt wejścia dla aplikacji.
    
    *Witaj. csproj*:
    
    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]
    
    Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i skompilowania programu.
    
    - `<OutputType>` element określa, że tworzysz plik wykonywalny, innymi słowy, Aplikacja konsolowa.
    - `<TargetFramework>` element określa, która implementacja platformy .NET jest celem. W zaawansowanym scenariuszu można określić wiele platform docelowych i skompilować je do wszystkich w ramach jednej operacji. W tym samouczku dojdziemy do kompilowania tylko dla platformy .NET Core 3,1.
    
    *Program.cs*:
    
    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]
    
    Program jest uruchamiany przez `using System`, co oznacza, że w zakresie dla tego pliku można przenieść wszystko w przestrzeni nazw `System`. Przestrzeń nazw `System` zawiera klasę `Console`.
    
    Następnie zdefiniujemy przestrzeń nazw o nazwie `Hello`. Możesz to zmienić w dowolny sposób. Klasa o nazwie `Program` jest zdefiniowana w tej przestrzeni nazw, z metodą `Main`, która pobiera tablicę ciągów o nazwie `args`. Ta tablica zawiera listę argumentów przekazaną podczas uruchamiania programu. W takim przypadku tablica nie jest używana, a program po prostu zapisuje tekst "Hello world!" w konsoli. Później wprowadzimy zmiany w kodzie, który będzie korzystał z tego argumentu.
    
    wywołania `dotnet new` [dotnet Restore](../tools/dotnet-restore.md) niejawnie. `dotnet restore` wywołania [NuGet](https://www.nuget.org/) (Menedżer pakietów .NET) w celu przywrócenia drzewa zależności. Pakiet NuGet analizuje plik *Hello. csproj* , pobiera zależności zdefiniowane w pliku (lub zbiera je z pamięci podręcznej na maszynie) i zapisuje plik *obj/Project. assets. JSON* , który jest niezbędny do skompilowania i uruchomienia przykładu.

02. `dotnet run`

    [uruchomienia](../tools/dotnet-run.md) programu dotnet [Kompiluj kompilacje dotnet](../tools/dotnet-build.md) , aby upewnić się, że cele kompilacji zostały skompilowane, a następnie wywoła `dotnet <assembly.dll>`, aby uruchomić aplikację docelową.
    
    ```console
    dotnet run

    Hello World!
    ```
    
    Alternatywnie można również uruchomić `dotnet build`, aby skompilować kod bez uruchamiania aplikacji konsolowej kompilacji. Powoduje to skompilowaną aplikację jako plik DLL, na podstawie nazwy projektu. W takim przypadku utworzony plik ma nazwę *Hello. dll*. Ta aplikacja może być uruchamiana z `dotnet bin\Debug\netcoreapp3.1\Hello.dll` w systemie Windows (Użyj `/` dla systemów innych niż Windows).
    
    ```console
    dotnet bin\Debug\netcoreapp3.1\Hello.dll

    Hello World!
    ```
    
    Po skompilowaniu aplikacji tworzony jest plik wykonywalny specyficzny dla systemu operacyjnego wraz z `Hello.dll`. W systemie Windows `Hello.exe`; w systemie Linux lub macOS `hello`. W powyższym przykładzie plik ma nazwę z `Hello.exe` lub `Hello`. Można uruchomić ten plik wykonywalny bezpośrednio.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Modyfikowanie programu

Zmieńmy program na bit. Liczby Fibonacci są przyjemne, więc Dodajmy ten argument, a także użyjesz argumentu, aby powitać osobę, która uruchamia aplikację.

01. Zastąp zawartość pliku *program.cs* następującym kodem:

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. Uruchom [kompilację dotnet](../tools/dotnet-build.md) , aby skompilować zmiany.

03. Uruchom program, przekazując do aplikacji parametr. Korzystając z `dotnet` polecenia, aby uruchomić aplikację, Dodaj `--` do końca. Wszystkie elementy z prawej strony `--` zostaną przesłane jako parametr do aplikacji. W poniższym przykładzie wartość `John` jest przenoszona do aplikacji.

    ```console
    $ dotnet run -- John
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

I to już wszystko! Możesz zmodyfikować *program.cs* w dowolny sposób.

## <a name="working-with-multiple-files"></a>Praca z wieloma plikami

Pojedyncze pliki są ograniczone do prostych programów jednostronnych, ale jeśli tworzysz bardziej złożoną aplikację, prawdopodobnie będziesz mieć wiele plików kodu w projekcie. Utwórzmy od poprzedniego przykładu Fibonacci przez buforowanie niektórych wartości Fibonacci i dodanie niektórych funkcji cyklicznych.

01. Dodaj nowy plik w katalogu *Hello* o nazwie *FibonacciGenerator.cs* przy użyciu następującego kodu:

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. Zmień metodę `Main` w pliku *program.cs* , aby utworzyć wystąpienie nowej klasy i wywołać jej metodę, tak jak w poniższym przykładzie:

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. Uruchom [kompilację dotnet](../tools/dotnet-build.md) , aby skompilować zmiany.

04. Uruchom aplikację, wykonując [uruchomienie programu dotnet](../tools/dotnet-run.md). Poniżej przedstawiono dane wyjściowe programu:

    ```console
    $ dotnet run
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

Gdy wszystko będzie gotowe do dystrybucji swojej aplikacji, użyj polecenia [dotnet Publish](../tools/dotnet-publish.md) w celu wygenerowania folderu _publikowania_ w _bin\\Debuguj\\netcoreapp 3.1\\publikowania\\_ (Użyj `/` w przypadku systemów innych niż Windows). Zawartość folderu _publikowania_ można dystrybuować na inne platformy, o ile już zainstalowano środowisko uruchomieniowe dotnet.

```console
dotnet publish
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

Powyższe dane wyjściowe mogą się różnić w zależności od bieżącego folderu i systemu operacyjnego, ale dane wyjściowe powinny być podobne.

Opublikowaną aplikację można uruchomić za pomocą polecenia [dotnet](../tools/dotnet.md) :

```console
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll

Hello World!
```

Jak wspomniano na początku tego artykułu, tworzony jest plik wykonywalny specyficzny dla systemu operacyjnego wraz z `Hello.dll`. W systemie Windows `Hello.exe`; w systemie Linux lub macOS `hello`. W powyższym przykładzie plik ma nazwę z `Hello.exe` lub `Hello`. Można uruchomić bezpośrednio ten opublikowany plik wykonywalny.

```console
.\bin\Debug\netcoreapp3.1\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Wniosek

I to już wszystko! Teraz możesz zacząć korzystać z podstawowych pojęć zamieszczonych w tym miejscu, aby utworzyć własne programy.

## <a name="see-also"></a>Zobacz także

- [Organizowanie i testowanie projektów przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core](testing-with-cli.md)
- [Publikowanie aplikacji platformy .NET Core za pomocą interfejsu wiersza polecenia](../deploying/deploy-with-cli.md)
- [Dowiedz się więcej o wdrażaniu aplikacji](../deploying/index.md)
