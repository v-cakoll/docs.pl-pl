---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia
description: Samouczek krok po kroku, pokazujący sposób rozpocząć pracę z platformą .NET Core w Windows, Linux lub macOS przy użyciu interfejsu wiersza polecenia (CLI) platformy .NET Core.
author: cartermp
ms.date: 09/10/2018
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 664ff07bad596ae38b4e31a00c7af0579d8245b8
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788313"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Rozpoczynanie pracy z platformą .NET Core w Windows/Linux/macOS przy użyciu wiersza polecenia

W tym temacie pokazują sposób rozpoczęcia tworzenia aplikacji dla wielu platform, na komputerze przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core.

Jeśli jesteś zaznajomiony z zestawu narzędzi interfejsu wiersza polecenia platformy .NET Core, zapoznaj się z [Omówienie zestawu .NET Core SDK](../tools/index.md).

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET Core SDK 2.1](https://www.microsoft.com/net/download/core).
- Edytor tekstu lub ulubionego edytora kodu.

## <a name="hello-console-app"></a>Witaj, aplikacja Konsolowa!

Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium dotnet/samples w witrynie GitHub. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*. Przejdź do folderu, który został utworzony, a następnie wpisz następujące polecenie:

```console
dotnet new console
dotnet run
```

Zróbmy szybkiego przewodnika:

1. `dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) Tworzy aktualnej `Hello.csproj` pliku projektu z zależnościami, które są niezbędne do tworzenia aplikacji konsolowej.  Tworzy również `Program.cs`, podstawowy plik zawierający punkt wejścia dla aplikacji.

   `Hello.csproj`:

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i kompilacji programu.

   * `OutputType` Tag Określa, czy tworzymy plik wykonywalny, innymi słowy aplikację konsolową w języku.
   * `TargetFramework` Tagów Określa, jakie firma Microsoft objęci implementacja programu .NET. W zaawansowanym scenariuszu można określić wielu platform docelowych i kompilacja — przejście do wszystkich tych w ramach jednej operacji. W tym samouczku używany będzie tworzenie tylko dla platformy .NET Core 2.1.

   `Program.cs`:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   Program, który rozpoczyna się od `using System`, co oznacza, że "Przenieś wszystko `System` przestrzeni nazw do zakresu dla tego pliku". `System` Przestrzeń nazw zawiera podstawowymi konstrukcjami `string`, lub typów liczbowych.

   Następnie definiujemy przestrzeń nazwy wywołaną `Hello`. Można to zmienić, do żadnego elementu, który ma. Klasa o nazwie `Program` jest zdefiniowana w ramach tej przestrzeni nazw za pomocą `Main` metody, która przyjmuje tablicę ciągów, jako argumentem. Ta tablica zawiera listę argumentów przekazywanych do wywołanego skompilowanego programu. I nie jest używana ta tablica: wszystkie działania programu służy do zapisania "Hello World!" w konsoli. Później, wybierzemy zmiany do kodu, który będzie używać tego argumentu.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new` wywołania [ `dotnet restore` ](../tools/dotnet-restore.md) niejawnie. `dotnet restore` wywoła [NuGet](https://www.nuget.org/) (.NET package manager) w celu przywrócenia drzewo zależności. Analizuje NuGet *Hello.csproj* plików, pliki do pobrania zależności zdefiniowane w pliku (lub bierze ich z pamięci podręcznej na komputerze) i zapisuje *obj/project.assets.json* pliku, który jest konieczny do Skompiluj i uruchom aplikację przykładową.

   > [!IMPORTANT]
   > Jeśli używasz wersji 1.x platformy .NET Core SDK, musisz wywołać `dotnet restore` samodzielnie po wywołaniu `dotnet new`.

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) wywołania [ `dotnet build` ](../tools/dotnet-build.md) do upewnij się, że kompilacji, utworzone elementy docelowe, a następnie wywołania `dotnet <assembly.dll>` do uruchamiania aplikacji docelowej.

    ```console
    $ dotnet run
    Hello World!
    ```

    Alternatywnie można również wykonać [ `dotnet build` ](../tools/dotnet-build.md) skompilować kod bez konieczności uruchamiania kompilacji aplikacji konsoli. Skutkuje to skompilowaną aplikację jako plik DLL, który można uruchomić z `dotnet bin\Debug\netcoreapp2.1\Hello.dll` na Windows (Użyj `/` systemów innych niż Windows). Jak zobaczysz później tematu można też określić argumenty do aplikacji.

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    W ramach scenariusza zaawansowanego jest możliwe utworzenie aplikacji jako autonomiczny zestaw plików specyficznych dla platformy, które można wdrożyć i uruchomić na komputerze, na którym nie musi koniecznie mieć platformy .NET Core zainstalowane. Zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md) Aby uzyskać szczegółowe informacje.

### <a name="augmenting-the-program"></a>Rozszerzając program

Zmieńmy nieco program. Numery Fibonacci zabawy, Dodajmy oprócz Użyj argumentu w celu powitania osoby uruchamiania aplikacji.

1. Zastąp zawartość swojej *Program.cs* pliku następującym kodem:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. Wykonaj [ `dotnet build` ](../tools/dotnet-build.md) skompilować zmiany.

3. Uruchom program przekazywania parametru do aplikacji:

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

I to wszystko!  Można rozszerzyć `Program.cs` sposób chcesz.

## <a name="working-with-multiple-files"></a>Praca z wieloma plikami

Pojedynczych plików są w dobrym stanie, proste, jednorazowe programów, ale jeśli tworzysz bardziej złożonych aplikacji są teraz zawierają wiele plików źródłowych w projekcie najczęściej kompilacji zniżki w stosunku do poprzedniego przykładu Fibonacci przez buforowanie niektórych wartości Fibonacci i dodaj kilka cykliczne funkcje.

1. Dodaj nowy plik wewnątrz *Hello* katalog o nazwie *FibonacciGenerator.cs* następującym kodem:

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. Zmiana `Main` method in Class metoda swoje *Program.cs* plik, aby utworzyć nowe wystąpienie klasy i wywołać jej metodę jak w poniższym przykładzie:

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Wykonaj [ `dotnet build` ](../tools/dotnet-build.md) skompilować zmiany.

4. Uruchom aplikację, wykonując [ `dotnet run` ](../tools/dotnet-run.md). Poniżej przedstawiono dane wyjściowe programu:

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

I to wszystko! Teraz można uruchomić przy użyciu podstawowych pojęć w tym miejscu przedstawiono tworzenie własnych programów.

Należy pamiętać, że polecenia i kroki opisane w tym samouczku do uruchamiania aplikacji są używane tylko w czasie projektowania. Gdy wszystko będzie gotowe do wdrożenia aplikacji, należy spojrzeć na poszczególne [strategie wdrażania](../deploying/index.md) dla aplikacji platformy .NET Core i [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia.

## <a name="see-also"></a>Zobacz także

- [Organizowanie i testowanie projektów przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core](testing-with-cli.md)
