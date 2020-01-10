---
title: Aplikacja konsoli
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 921c8fc7824bdb48f08e4d9f5a276bf2284f8a17
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714603"
---
# <a name="console-app"></a>Aplikacja konsolowa

W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka. W dokumencie omówiono następujące zagadnienia :

- Podstawowe informacje o interfejsie wiersza polecenia platformy .NET Core (CLI)
- Struktura aplikacji C# konsolowej
- We/wy konsoli
- Podstawy interfejsów API we/wy plików w programie .NET
- Podstawowe informacje na temat programowania asynchronicznego opartego na zadaniach w programie .NET

Utworzysz aplikację, która odczytuje plik tekstowy, i echo zawartość tego pliku tekstowego do konsoli programu. Dane wyjściowe do konsoli są w tempie zgodne z odczytem na głos. Można przyspieszyć lub spowalniać tempo, naciskając klawisze "<" (mniejsze niż) lub ">" (większe niż).

Ten samouczek zawiera wiele funkcji. Kompilujmy je po jednej.

## <a name="prerequisites"></a>Wymagania wstępne

- Skonfiguruj maszynę do uruchamiania programu .NET Core. Instrukcje instalacji można znaleźć na stronie [pliki do pobrania w programie .NET Core](https://dotnet.microsoft.com/download) . Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.

- Zainstaluj swój ulubiony Edytor kodu.

## <a name="create-the-app"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji. Upewnij się, że bieżący katalog. Wpisz `dotnet new console` polecenia w wierszu polecenia. Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world".

Przed rozpoczęciem wprowadzania zmian przejdź do kroku, aby uruchomić prostą aplikację Hello world. Po utworzeniu aplikacji wpisz `dotnet restore` w wierszu polecenia. To polecenie uruchamia proces przywracania pakietów NuGet. Pakiet NuGet jest menedżerem pakietów platformy .NET. To polecenie pobiera wszystkie brakujące zależności dla projektu. Ponieważ jest to nowy projekt, nie są stosowane żadne zależności, więc pierwsze uruchomienie spowoduje pobranie środowiska .NET Core. Po tym początkowym kroku będzie konieczne uruchomienie `dotnet restore` tylko wtedy, gdy dodasz nowe pakiety zależne lub zaktualizujesz wersje dowolnych zależności.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po przywróceniu pakietów Uruchom `dotnet build`. Spowoduje to uruchomienie aparatu kompilacji i utworzenie pliku wykonywalnego aplikacji. Na koniec należy wykonać `dotnet run`, aby uruchomić aplikację.

Prosty kod aplikacji Hello world to wszystko w Program.cs. Otwórz ten plik za pomocą ulubionego edytora tekstu. Zamierzamy wprowadzić Twoje pierwsze zmiany. W górnej części pliku Zobacz instrukcję using:

```csharp
using System;
```

Ta instrukcja informuje kompilator, że wszystkie typy z przestrzeni nazw `System` znajdują się w zakresie. Podobnie jak w przypadku innych języków zorientowanych na obiekt, C# które mogą być używane, program używa przestrzeni nazw do organizowania typów. Ten program Hello world nie jest inny. Można zobaczyć, że program jest ujęty w przestrzeń nazw o nazwie na podstawie nazwy bieżącego katalogu. Na potrzeby tego samouczka Zmieńmy nazwę przestrzeni nazw na `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Odczytywanie i echo pliku

Pierwsza funkcja do dodania to możliwość odczytywania pliku tekstowego i wyświetlania całego tekstu w konsoli programu. Najpierw Dodajmy plik tekstowy. Skopiuj plik [sampleQuotes. txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z repozytorium GitHub dla tego [przykładu](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do katalogu projektu. Będzie to skrypt aplikacji. Jeśli chcesz uzyskać informacje dotyczące sposobu pobierania przykładowej aplikacji dla tego tematu, zobacz instrukcje w temacie [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) .

Następnie Dodaj następującą metodę do klasy `Program` (bezpośrednio poniżej metody `Main`):

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

Ta metoda używa typów z dwóch nowych przestrzeni nazw. Aby można było skompilować kompilację, należy dodać dwa następujące wiersze na początku pliku:

```csharp
using System.Collections.Generic;
using System.IO;
```

Interfejs <xref:System.Collections.Generic.IEnumerable%601> jest zdefiniowany w przestrzeni nazw <xref:System.Collections.Generic>. Klasa <xref:System.IO.File> jest zdefiniowana w przestrzeni nazw <xref:System.IO>.

Ta metoda jest specjalnym typem C# metody zwanej *metodą iteratora*. Metody modułu wyliczającego zwracają sekwencje zwracające opóźnieniem. Oznacza to, że każdy element w sekwencji jest generowany w miarę żądania przez kod korzystający z sekwencji. Metody modułu wyliczającego to metody, które zawierają jedną lub więcej instrukcji [`yield return`](../language-reference/keywords/yield.md) . Obiekt zwrócony przez metodę `ReadFrom` zawiera kod generujący każdy element w sekwencji. W tym przykładzie, który obejmuje odczytywanie następnego wiersza tekstu z pliku źródłowego i zwracanie tego ciągu. Za każdym razem, gdy wywołujący kod żąda następnego elementu z sekwencji, kod odczytuje następny wiersz tekstu z pliku i zwraca go. Gdy plik jest całkowicie odczytywany, sekwencja wskazuje, że nie ma więcej elementów.

Istnieją dwa inne C# elementy składni, które mogą być nowe dla Ciebie. Instrukcja [`using`](../language-reference/keywords/using-statement.md) w tej metodzie zarządza oczyszczaniem zasobów. Zmienna, która została zainicjowana w instrukcji `using` (`reader`w tym przykładzie) musi implementować interfejs <xref:System.IDisposable>. Ten interfejs definiuje pojedynczą metodę, `Dispose`, która powinna być wywoływana, gdy zasób powinien zostać wyznaczony. Kompilator generuje to wywołanie, gdy wykonanie osiągnie zamykający nawias klamrowy instrukcji `using`. Kod wygenerowany przez kompilator zapewnia, że zasób jest wydawany nawet wtedy, gdy wyjątek jest zgłaszany z kodu w bloku zdefiniowanym przez instrukcję using.

Zmienna `reader` jest definiowana przy użyciu słowa kluczowego `var`. [`var`](../language-reference/keywords/var.md) definiuje *niejawnie wpisaną zmienną lokalną*. Oznacza to, że typ zmiennej jest określany przez typ czasu kompilacji obiektu przypisanego do zmiennej. W tym miejscu jest to wartość zwracana z metody <xref:System.IO.File.OpenText(System.String)>, która jest obiektem <xref:System.IO.StreamReader>.

Teraz uzupełnimy kod w celu odczytania pliku w `Main` metodzie:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Uruchom program (za pomocą `dotnet run`) i zobaczysz, że każdy wiersz został wydrukowany w konsoli programu.

## <a name="adding-delays-and-formatting-output"></a>Dodawanie opóźnień i formatowanie danych wyjściowych

Zawartość jest zbyt szybka, aby można ją było odczytać. Teraz musisz dodać opóźnienia w danych wyjściowych. Po rozpoczęciu będziesz kompilować część kodu podstawowego, który umożliwia przetwarzanie asynchroniczne. Jednak te pierwsze kroki będą zgodne z kilkoma wzorcami. Wzorce są podkreślane w komentarzach podczas dodawania kodu, a kod zostanie zaktualizowany w dalszych krokach.

Ta sekcja zawiera dwa kroki. Najpierw należy zaktualizować metodę iteratora w celu zwrócenia pojedynczych słów zamiast całych wierszy. Jest to wykonywane z tymi modyfikacjami. Zastąp instrukcję `yield return line;` następującym kodem:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Następnie należy zmodyfikować sposób korzystania z wierszy pliku i dodać opóźnienie po zapisaniu każdego wyrazu. Zastąp instrukcję `Console.WriteLine(line)` w metodzie `Main` następującym blokiem:

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

Klasa <xref:System.Threading.Tasks.Task> znajduje się w przestrzeni nazw <xref:System.Threading.Tasks>, dlatego należy dodać tę instrukcję `using` na początku pliku:

```csharp
using System.Threading.Tasks;
```

Uruchom przykład i sprawdź dane wyjściowe. Teraz każdy pojedynczy wyraz jest drukowany, po którym następuje opóźnienie 200 ms. Jednak wyświetlane dane wyjściowe pokazują pewne problemy, ponieważ źródłowy plik tekstowy ma kilka wierszy, które mają więcej niż 80 znaków bez przerwy w wierszu. Może to być trudne do odczytania podczas przewijania przez program. Jest to łatwe do naprawienia. Będziesz śledzić długość każdego wiersza i generować nowy wiersz zawsze, gdy długość wiersza osiągnie określony próg. Zadeklaruj zmienną lokalną po deklaracji `words` w metodzie `ReadFrom`, która posiada długość wiersza:

```csharp
var lineLength = 0;
```

Następnie Dodaj następujący kod po instrukcji `yield return word + " ";` (przed zamykającym nawiasem klamrowym):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Uruchom próbkę i będzie można odczytywać na głos ze wstępnie skonfigurowanym tempem.

## <a name="async-tasks"></a>Zadania asynchroniczne

W tym ostatnim kroku dodasz kod, aby zapisać dane wyjściowe asynchronicznie w jednym zadaniu, a jednocześnie uruchomić inne zadanie odczytujące dane wejściowe od użytkownika, jeśli chcesz przyspieszyć lub spowolnić wyświetlanie tekstu lub zatrzymać wyświetlanie tekstu. Obejmuje to kilka kroków i zakończenie, które będą potrzebne do wszystkich niezbędnych aktualizacji. Pierwszym krokiem jest utworzenie asynchronicznej metody zwracającej <xref:System.Threading.Tasks.Task>, która reprezentuje kod, który został utworzony do odczytu i wyświetlenia pliku.

Dodaj tę metodę do klasy `Program` (jest ona pobierana z treści metody `Main`):

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

Zauważysz dwie zmiany. Najpierw w treści metody zamiast wywołania <xref:System.Threading.Tasks.Task.Wait> synchronicznie poczekaj na zakończenie zadania, ta wersja używa słowa kluczowego `await`. Aby to zrobić, należy dodać modyfikator `async` do sygnatury metody. Ta metoda zwraca `Task`. Zwróć uwagę, że nie istnieją żadne instrukcje Return zwracające obiekt `Task`. Zamiast tego ten obiekt `Task` jest tworzony przez kod wygenerowany przez kompilator podczas korzystania z operatora `await`. Można Wyobraź sobie, że ta metoda zwraca, gdy osiągnie `await`. Zwrócony `Task` wskazuje, że pracę nie została ukończona. Metoda zostaje wznowiona po zakończeniu oczekiwania na zadanie. Po wykonaniu tej operacji zwrócony `Task` wskazuje, że została ukończona.
Kod wywołujący może monitorować, który zwrócił `Task`, aby określić, kiedy zakończył się.

Tę nową metodę można wywołać w metodzie `Main`:

```csharp
ShowTeleprompter().Wait();
```

W tym miejscu w `Main`kod wykonuje synchronicznie oczekiwania. Jeśli to możliwe, należy użyć operatora `await` zamiast synchronicznie czekać. Ale w metodzie `Main` aplikacji konsoli nie można użyć operatora `await`. Spowoduje to zakończenie działania aplikacji przed ukończeniem wszystkich zadań.

> [!NOTE]
> Jeśli używasz C# 7,1 lub nowszej, możesz tworzyć aplikacje konsolowe za pomocą [metody`async` `Main`](../whats-new/csharp-7-1.md#async-main).

Następnie należy napisać drugą metodę asynchroniczną w celu odczytania z konsoli i obserwowania dla "<" (mniejszej niż), ">" (większe niż) i "X" lub "x". Oto Metoda dodawana do tego zadania:

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

Spowoduje to utworzenie wyrażenia lambda do reprezentowania delegata <xref:System.Action>, który odczytuje klucz z konsoli programu i modyfikuje zmienną lokalną reprezentującą opóźnienie, gdy użytkownik naciśnie klawisz "<" (mniejsze niż) lub ">" (większe niż). Metoda Delegate kończy się, gdy użytkownik naciśnie klawisze "X" lub "x", które umożliwiają użytkownikowi zatrzymanie wyświetlania tekstu w dowolnym momencie. Ta metoda używa <xref:System.Console.ReadKey> do blokowania i poczekania na naciśnięcie klawisza przez użytkownika.

Aby zakończyć tę funkcję, należy utworzyć nową metodę zwracającą `async Task`, która uruchamia oba te zadania (`GetInput` i `ShowTeleprompter`), a także zarządza danymi udostępnionymi między tymi dwoma zadaniami.

Czas na utworzenie klasy, która może obsługiwać udostępnione dane między tymi dwoma zadaniami. Ta klasa zawiera dwie właściwości publiczne: opóźnienie i flaga `Done` wskazujące, że plik został całkowicie odczytany:

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

Umieść tę klasę w nowym pliku i umieść ją w przestrzeni nazw `TeleprompterConsole`, jak pokazano powyżej. Należy również dodać instrukcję `using static`, aby można było odwoływać się do `Min` i `Max` metod bez nazwy klasy lub przestrzeni nazw. Instrukcja [`using static`](../language-reference/keywords/using-static.md) importuje metody z jednej klasy. Jest to w przeciwieństwie do instrukcji `using` używanych do tego momentu, w którym zaimportowano wszystkie klasy z przestrzeni nazw.

```csharp
using static System.Math;
```

Następnie należy zaktualizować metody `ShowTeleprompter` i `GetInput`, aby użyć nowego obiektu `config`. Napisz jedną `Task` ostateczną zwracającą metodę `async`, aby uruchomić oba zadania i wyjść po zakończeniu pierwszego zadania:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Jedną z nowych metod jest wywołanie <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])>. Tworzy `Task`, która kończy się zaraz po zakończeniu wszystkich zadań na liście argumentów.

Następnie należy zaktualizować metody `ShowTeleprompter` i `GetInput`, aby użyć obiektu `config` dla opóźnienia:

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

Ta nowa wersja `ShowTeleprompter` wywołuje nową metodę w klasie `TeleprompterConfig`. Teraz musisz zaktualizować `Main`, aby wywołać `RunTeleprompter` zamiast `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Wniosek

W tym samouczku przedstawiono szereg funkcji dotyczących C# języka i bibliotek .NET Core związanych z pracą w aplikacjach konsolowych. Możesz utworzyć tę wiedzę, aby dowiedzieć się więcej o języku i klasach wprowadzonych w tym miejscu. Przedstawiono podstawowe informacje na temat operacji we/wy plików i konsoli, blokowania i nieblokowania użycia programowania asynchronicznego opartego na zadaniach, samouczka dotyczącego C# języka i sposobu C# organizowania programów oraz interfejsu wiersza polecenia i narzędzi .NET Core.

Aby uzyskać więcej informacji na temat operacji we/wy plików, zobacz temat [plik i strumień we/wy](../../standard/io/index.md) . Aby uzyskać więcej informacji o modelu programowania asynchronicznego używanym w tym samouczku, zapoznaj się z tematem [programowanie asynchroniczne oparte na zadaniach](../..//standard/parallel-programming/task-based-asynchronous-programming.md) i w temacie [programowanie asynchroniczne](../async.md) .
