---
title: "Rozpoczynanie pracy z platformą .NET Core za pomocą interfejsu wiersza polecenia"
description: "Samouczek krok po kroku, pokazujący sposób rozpocząć pracę z platformą .NET Core w systemie Windows, Linux lub macOS przy użyciu interfejsu wiersza polecenia (CLI) platformy .NET Core."
keywords: Oprogramowanie .NET core, interfejsu wiersza polecenia
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 41632e63-d5c6-4427-a09e-51dc1116d45f
ms.openlocfilehash: 19622cca1dd28d4d2248d69f1b4081c352a0c4f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Rozpoczynanie pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia

W tym temacie opisano, jak można rozpocząć tworzenie aplikacji cross platform na tym komputerze przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core.

Jeśli znasz zestaw narzędzi interfejsu wiersza polecenia platformy .NET Core odczytu [Omówienie zestawu SDK programu .NET Core](../tools/index.md).

## <a name="prerequisites"></a>Wymagania wstępne

- [Oprogramowanie .NET core SDK 1.0](https://www.microsoft.com/net/download/core).
- Edytor tekstu lub dowolnego edytora kodu.

## <a name="hello-console-app"></a>Witaj, aplikacji konsoli!

Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild) z dotnet/docs repozytorium GitHub. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*. Przejdź do folderu, który został utworzony i wpisz następujące polecenie:

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

Poznajmy Szybkie wskazówki:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md)Tworzy aktualne `Hello.csproj` pliku projektu z zależnościami, które są niezbędne do tworzenia aplikacji konsoli.  Tworzy również `Program.cs`, podstawowe plik zawierający punkt wejścia dla aplikacji.
   
   `Hello.csproj`:

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i kompilacji programu.

   * `OutputType` Określa tag tworzymy plik wykonywalny, innymi słowy aplikacji konsoli.
   * `TargetFramework` Tag Określa, jakie implementacji .NET możemy docelowych. W scenariuszu zaawansowanym, można określić wiele platform docelowych i kompilacji do wszystkich tych w ramach jednej operacji. W tym samouczku firma Microsoft będzie osadzania kompilowanie tylko dla platformy .NET Core 1.0.

   `Program.cs`:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   Program, który rozpoczyna się od `using System`, co oznacza, że "Przenieś wszystko `System` przestrzeni nazw do zakresu dla tego pliku". `System` Przestrzeń nazw zawiera podstawowe konstrukcji `string`, lub typy liczbowe.

   Następnie definicję przestrzeni nazw o nazwie `Hello`. Można to zmienić, do dowolnych znaków. Klasa o nazwie `Program` jest zdefiniowany w tej przestrzeni nazw z `Main` metody pobierającej tablicy ciągów jako jej argument. Ta tablica zawiera listę argumentów przekazana wywołanego skompilowany program. Ta tablica nie jest używany, jak: wszystkich zadań programu jest napisanie "Witaj świecie!" w konsoli. Później, wybierzemy zmiany do kodu, który będzie używać tego argumentu.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md)Wywołano [NuGet](https://www.nuget.org/) (.NET package manager) w celu przywrócenia drzewie zależności. Analizuje NuGet *Hello.csproj* plików, pliki do pobrania zależności określone w pliku (lub grabs je z pamięci podręcznej na komputerze) i zapisuje *obj/project.assets.json* pliku.  *Project.assets.json* plik jest niezbędny można było skompilować i uruchomić.
   
   *Project.assets.json* plik jest utrwalona i pełny zestaw wykres zależności NuGet i inne informacje opisujące aplikację.  Ten plik jest odczytywany przez innych narzędzi, takich jak [ `dotnet build` ](../tools/dotnet-build.md) i [ `dotnet run` ](../tools/dotnet-run.md), umożliwiając im procesu kodu źródłowego z poprawny zestaw zależności NuGet i powiązanie rozwiązania.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md)wywołania [ `dotnet build` ](../tools/dotnet-build.md) do upewnij się, że kompilacji są wbudowane elementy docelowe, a następnie wywołania `dotnet <assembly.dll>` do uruchomienia aplikacji docelowej.
   
    ```
    $ dotnet run
    Hello World!
    ```

    Alternatywnie można również wykonywać [ `dotnet build` ](../tools/dotnet-build.md) skompilować kod bez uruchamiania Kompilowanie aplikacji konsoli. Powoduje to skompilowanej aplikacji jako plik DLL, który może być uruchamiane przy `dotnet bin\Debug\netcoreapp1.0\Hello.dll` w systemie Windows (Użyj `/` dla systemów z systemem innym niż Windows). Argumenty do aplikacji mogą określać również, jak można zauważyć później na temat.

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    W ramach scenariusza zaawansowanego jest możliwe utworzenie aplikacji jako autonomiczny zestaw plików specyficzne dla platformy, które mogą być wdrożone i uruchom na komputerze, na którym nie muszą być .NET Core zainstalowane. Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) szczegółowe informacje.

### <a name="augmenting-the-program"></a>Rozbudować program

Zmieńmy nieco program. Numery Fibonacci fun, więc Dodajmy oprócz Użyj argument greet osoby uruchomiona aplikacja.

1. Zastąp zawartość z *Program.cs* pliku następującym kodem:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. Wykonanie [ `dotnet build` ](../tools/dotnet-build.md) do kompilacji zmian.

3. Uruchom program przekazanie parametru do aplikacji:

   ```
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

I to już wszystko!  Można rozszerzyć `Program.cs` żadnym chcesz.

## <a name="working-with-multiple-files"></a>Praca z wieloma plikami

Pojedynczych plików jest poprawna dla programów jednorazowe prostego, ale jeśli tworzysz złożonych aplikacji jest teraz zawierają wiele plików źródłowych w projekcie najczęściej kompilacji wylogowuje na poprzednim przykładzie Fibonacci przez buforowanie niektórych wartości Fibonacci i dodać niektóre cykliczne funkcje. 

1. Dodaj nowy plik wewnątrz *Hello* katalog o nazwie *FibonacciGenerator.cs* następującym kodem:

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. Zmień `Main` metody w Twojej *Program.cs* plik, aby utworzyć wystąpienia klasy nowy i Wywołaj jej metodę jak w poniższym przykładzie:

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Wykonanie [ `dotnet build` ](../tools/dotnet-build.md) do kompilacji zmian.

4. Uruchamianie aplikacji, wykonując [ `dotnet run` ](../tools/dotnet-run.md). Poniżej przedstawiono dane wyjściowe programu:

   ```
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

I to już wszystko! Teraz możesz rozpocząć używać, podstawowe koncepcje przedstawiono w tym miejscu do tworzenia własnych programów.

Należy pamiętać, że poleceń i kroki opisane w tym samouczku do uruchamiania aplikacji są używane tylko w czasie tworzenia. Gdy wszystko jest gotowe do wdrożenia aplikacji, należy spojrzeć na różnych [strategii wdrażania](../deploying/index.md) dla aplikacji .NET Core i [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia.

## <a name="see-also"></a>Zobacz także

[Organizowanie i testowanie projektów przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core](testing-with-cli.md)
