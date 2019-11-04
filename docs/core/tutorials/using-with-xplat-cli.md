---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia
description: Samouczek krok po kroku pokazujący, jak rozpocząć pracę z platformą .NET Core w systemie Windows, Linux lub macOS przy użyciu interfejsu wiersza polecenia (CLI) platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: c7e314e9712c3b569ecc813a72670942651feda1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454738"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Rozpoczynanie pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia

W tym temacie pokazano, jak rozpocząć tworzenie aplikacji dla wielu platform na maszynie przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core.

Jeśli nie znasz zestawu narzędzi interfejs wiersza polecenia platformy .NET Core, zapoznaj się z tematem [zestaw .NET Core SDK Omówienie](../tools/index.md).

## <a name="prerequisites"></a>Wymagania wstępne

- [Zestaw .NET Core SDK 2,1](https://dotnet.microsoft.com/download) lub nowszymi wersjami.
- Edytor tekstu lub Edytor kodu.

## <a name="hello-console-app"></a>Witaj, Aplikacja konsolowa!

[Przykładowy kod można wyświetlić lub pobrać](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium usługi GitHub/przykłady Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*. Przejdź do utworzonego folderu i wpisz następujące:

```dotnetcli
dotnet new console
dotnet run
```

Wykonajmy szybkie wskazówki:

1. `dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) tworzy aktualny plik projektu *Hello. csproj* z zależnościami niezbędnymi do skompilowania aplikacji konsolowej. Tworzy również *program.cs*, podstawowy plik zawierający punkt wejścia dla aplikacji.

   *Witaj. csproj*:

   [!code-xml[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i skompilowania programu.

   - Znacznik `OutputType` określa, że tworzysz plik wykonywalny, innymi słowy aplikację konsolową.
   - Znacznik `TargetFramework` określa, która implementacja platformy .NET jest celem. W zaawansowanym scenariuszu można określić wiele platform docelowych i skompilować je do wszystkich w ramach jednej operacji. W tym samouczku dojdziemy do kompilowania tylko dla platformy .NET Core 2,1.

   *Program.cs*:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   Program jest uruchamiany przez `using System`, co oznacza, że w zakresie dla tego pliku można przenieść wszystko w przestrzeni nazw `System`. Przestrzeń nazw `System` zawiera podstawowe konstrukcje, takie jak `string`lub typy liczbowe.

   Następnie zdefiniujemy przestrzeń nazw o nazwie `Hello`. Możesz to zmienić w dowolny sposób. Klasa o nazwie `Program` jest zdefiniowana w tej przestrzeni nazw, z metodą `Main`, która pobiera tablicę ciągów jako argument. Ta tablica zawiera listę argumentów, które zostały przekazane podczas wywoływania skompilowanego programu. W takim przypadku ta tablica nie jest używana: cały program wykonuje zapis "Hello world!" do konsoli programu. Później wprowadzimy zmiany w kodzie, który będzie korzystał z tego argumentu.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   wywołania `dotnet new` [`dotnet restore`](../tools/dotnet-restore.md) niejawnie. `dotnet restore` wywołania [NuGet](https://www.nuget.org/) (Menedżer pakietów .NET) w celu przywrócenia drzewa zależności. Pakiet NuGet analizuje plik *Hello. csproj* , pobiera zależności zdefiniowane w pliku (lub zbiera je z pamięci podręcznej na maszynie) i zapisuje plik *obj/Project. assets. JSON* , który jest niezbędny do skompilowania i uruchomienia przykładu.

   > [!IMPORTANT]
   > Jeśli używasz wersji programu .NET Core 1. x zestawu SDK, musisz wywołać `dotnet restore` siebie po wywołaniu `dotnet new`.

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) wywołań [`dotnet build`](../tools/dotnet-build.md) , aby upewnić się, że cele kompilacji zostały skompilowane, a następnie wywoła `dotnet <assembly.dll>`, aby uruchomić aplikację docelową.

    ```console
    $ dotnet run
    Hello World!
    ```

    Alternatywnie można również wykonać [`dotnet build`](../tools/dotnet-build.md) , aby skompilować kod bez uruchamiania aplikacji konsolowej kompilacji. Powoduje to skompilowaną aplikację jako plik DLL, który można uruchomić za pomocą `dotnet bin\Debug\netcoreapp2.1\Hello.dll` w systemie Windows (Użyj `/` dla systemów innych niż Windows). Możesz również określić argumenty dla aplikacji, jak widać w dalszej części tematu.

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    Zaawansowanym scenariuszem jest możliwość tworzenia aplikacji jako samodzielnego zestawu plików specyficznych dla platformy, które można wdrożyć i uruchomić na komputerze, na którym nie jest zainstalowany program .NET Core. Aby uzyskać szczegółowe informacje, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) .

### <a name="augmenting-the-program"></a>Rozszerzanie programu

Zmieńmy program na bit. Liczby Fibonacci są przyjemne, więc Dodajmy ten dodatek, a także użyjesz argumentu, aby powitać osobę, która uruchamia aplikację.

1. Zastąp zawartość pliku *program.cs* następującym kodem:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. Wykonaj [`dotnet build`](../tools/dotnet-build.md) , aby skompilować zmiany.

3. Uruchom program, przekazując do aplikacji parametr:

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

I to wszystko!  Możesz rozszerzyć `Program.cs` w dowolny sposób.

## <a name="working-with-multiple-files"></a>Praca z wieloma plikami

Pojedyncze pliki są ograniczone do prostych programów jednostronnych, ale jeśli tworzysz bardziej złożoną aplikację, prawdopodobnie będziesz mieć wiele plików źródłowych w projekcie.
Utwórzmy od poprzedniego przykładu Fibonacci przez buforowanie niektórych wartości Fibonacci i dodanie niektórych funkcji cyklicznych.

1. Dodaj nowy plik w katalogu *Hello* o nazwie *FibonacciGenerator.cs* przy użyciu następującego kodu:

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. Zmień metodę `Main` w pliku *program.cs* , aby utworzyć wystąpienie nowej klasy i wywołać jej metodę, tak jak w poniższym przykładzie:

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Wykonaj [`dotnet build`](../tools/dotnet-build.md) , aby skompilować zmiany.

4. Uruchom aplikację, wykonując [`dotnet run`](../tools/dotnet-run.md). Poniżej przedstawiono dane wyjściowe programu:

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

Gdy wszystko będzie gotowe do dystrybucji swojej aplikacji, użyj polecenia [`dotnet publish`](../tools/dotnet-publish.md) , aby wygenerować folder _publikowania_ w polu _bin\\Debuguj\\netcoreapp 2.1\\Publish\\_ (Użyj `/` dla systemów innych niż Windows). Zawartość folderu _publikowania_ można dystrybuować na inne platformy, o ile już zainstalowano środowisko uruchomieniowe dotnet.

Opublikowaną aplikację można uruchomić za pomocą polecenia [dotnet](../tools/dotnet.md) :

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a>Wniosek

I to wszystko! Teraz możesz zacząć korzystać z podstawowych pojęć zamieszczonych w tym miejscu, aby utworzyć własne programy.

## <a name="see-also"></a>Zobacz także

- [Organizowanie i testowanie projektów przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core](testing-with-cli.md)
- [Publikowanie aplikacji platformy .NET Core za pomocą interfejsu wiersza polecenia](../deploying/deploy-with-cli.md)
- [Dowiedz się więcej o wdrażaniu aplikacji](../deploying/index.md)
