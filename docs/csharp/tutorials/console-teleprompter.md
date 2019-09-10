---
title: Aplikacja konsoli
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 4324b25daa253b3d2446955ad9ca57c2f0294f0c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851019"
---
# <a name="console-application"></a>Aplikacja konsoli

W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka. Dowiesz się:

- Podstawowe informacje o interfejsie wiersza polecenia platformy .NET Core (CLI)
- Struktura aplikacji C# konsolowej
- We/wy konsoli
- Podstawy interfejsów API we/wy plików w programie .NET
- Podstawowe informacje na temat programowania asynchronicznego opartego na zadaniach w programie .NET

Utworzysz aplikację, która odczytuje plik tekstowy, i echo zawartość tego pliku tekstowego do konsoli programu. Dane wyjściowe do konsoli są w tempie zgodne z odczytem na głos. Można przyspieszyć lub spowalniać tempo, naciskając klawisze "<" (mniejsze niż) lub ">" (większe niż).

Ten samouczek zawiera wiele funkcji. Kompilujmy je po jednej.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core. Instrukcje instalacji można znaleźć na stronie [pliki do pobrania w programie .NET Core](https://dotnet.microsoft.com/download) . Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.
Musisz zainstalować swój ulubiony Edytor kodu.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji. Upewnij się, że bieżący katalog. Wpisz polecenie `dotnet new console` w wierszu polecenia. Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world".

Przed rozpoczęciem wprowadzania zmian przejdź do kroku, aby uruchomić prostą aplikację Hello world. Po utworzeniu aplikacji wpisz `dotnet restore` w wierszu polecenia. To polecenie uruchamia proces przywracania pakietów NuGet. Pakiet NuGet jest menedżerem pakietów platformy .NET. To polecenie pobiera wszystkie brakujące zależności dla projektu. Ponieważ jest to nowy projekt, nie są stosowane żadne zależności, więc pierwsze uruchomienie spowoduje pobranie środowiska .NET Core. Po tym początkowym kroku będziesz mieć możliwość uruchamiania `dotnet restore` tylko wtedy, gdy dodasz nowe pakiety zależne lub zaktualizujesz wersje dowolnych zależności.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po przywróceniu pakietów zostanie uruchomione `dotnet build`polecenie. Spowoduje to uruchomienie aparatu kompilacji i utworzenie pliku wykonywalnego aplikacji. `dotnet run` Na koniec uruchamiasz aplikację.

Prosty kod aplikacji Hello world to wszystko w Program.cs. Otwórz ten plik za pomocą ulubionego edytora tekstu. Zamierzamy wprowadzić Twoje pierwsze zmiany.
W górnej części pliku Zobacz instrukcję using:

```csharp
using System;
```

Ta instrukcja informuje kompilator, że wszystkie typy z `System` przestrzeni nazw znajdują się w zakresie. Podobnie jak w przypadku innych języków zorientowanych na obiekt, C# które mogą być używane, program używa przestrzeni nazw do organizowania typów. Ten program Hello world nie jest inny. Można zobaczyć, że program jest ujęty w przestrzeń nazw o nazwie na podstawie nazwy bieżącego katalogu. Na potrzeby tego samouczka Zmieńmy nazwę przestrzeni nazw na `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Odczytywanie i echo pliku

Pierwsza funkcja do dodania to możliwość odczytywania pliku tekstowego i wyświetlania całego tekstu w konsoli programu. Najpierw Dodajmy plik tekstowy. Skopiuj plik [sampleQuotes. txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z repozytorium GitHub dla tego [przykładu](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do katalogu projektu. Będzie to skrypt aplikacji. Jeśli chcesz uzyskać informacje dotyczące sposobu pobierania przykładowej aplikacji dla tego tematu, zobacz instrukcje w temacie [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) .

Następnie Dodaj następującą metodę do `Program` klasy (bezpośrednio `Main` poniżej metody):

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

Interfejs jest zdefiniowany <xref:System.Collections.Generic> w przestrzeni nazw. <xref:System.Collections.Generic.IEnumerable%601> Klasa jest zdefiniowana <xref:System.IO> w przestrzeni nazw. <xref:System.IO.File>

Ta metoda jest specjalnym typem C# metody zwanej *metodą iteratora*. Metody modułu wyliczającego zwracają sekwencje zwracające opóźnieniem. Oznacza to, że każdy element w sekwencji jest generowany w miarę żądania przez kod korzystający z sekwencji. Metody modułu wyliczającego to metody, które [`yield return`](../language-reference/keywords/yield.md) zawierają jedną lub więcej instrukcji. Obiekt zwrócony przez `ReadFrom` metodę zawiera kod generujący każdy element w sekwencji. W tym przykładzie, który obejmuje odczytywanie następnego wiersza tekstu z pliku źródłowego i zwracanie tego ciągu. Za każdym razem, gdy wywołujący kod żąda następnego elementu z sekwencji, kod odczytuje następny wiersz tekstu z pliku i zwraca go. Gdy plik jest całkowicie odczytywany, sekwencja wskazuje, że nie ma więcej elementów.

Istnieją dwa inne C# elementy składni, które mogą być nowe dla Ciebie. [`using`](../language-reference/keywords/using-statement.md) Instrukcja w tej metodzie zarządza oczyszczaniem zasobów. Zmienna, która została zainicjowana `using` w instrukcji`reader`(w tym <xref:System.IDisposable> przykładzie) musi implementować interfejs. Ten interfejs definiuje pojedynczą metodę `Dispose`, która powinna być wywoływana, gdy zasób powinien zostać wyznaczony. Kompilator generuje to wywołanie, gdy wykonanie osiągnie zamykający nawias klamrowy `using` instrukcji. Kod wygenerowany przez kompilator zapewnia, że zasób jest wydawany nawet wtedy, gdy wyjątek jest zgłaszany z kodu w bloku zdefiniowanym przez instrukcję using.

Zmienna jest definiowana `var` przy użyciu słowa kluczowego. `reader` [`var`](../language-reference/keywords/var.md)definiuje *niejawnie wpisaną zmienną lokalną*. Oznacza to, że typ zmiennej jest określany przez typ czasu kompilacji obiektu przypisanego do zmiennej. Tutaj jest to wartość zwracana z <xref:System.IO.File.OpenText(System.String)> metody, która <xref:System.IO.StreamReader> jest obiektem.

Teraz uzupełnimy kod w celu odczytania pliku w `Main` metodzie:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Uruchom program (za pomocą `dotnet run`programu) i zobaczysz, że każdy wiersz został wydrukowany w konsoli programu.

## <a name="adding-delays-and-formatting-output"></a>Dodawanie opóźnień i formatowanie danych wyjściowych

Zawartość jest zbyt szybka, aby można ją było odczytać. Teraz musisz dodać opóźnienia w danych wyjściowych. Po rozpoczęciu będziesz kompilować część kodu podstawowego, który umożliwia przetwarzanie asynchroniczne. Jednak te pierwsze kroki będą zgodne z kilkoma wzorcami. Wzorce są podkreślane w komentarzach podczas dodawania kodu, a kod zostanie zaktualizowany w dalszych krokach.

Ta sekcja zawiera dwa kroki. Najpierw należy zaktualizować metodę iteratora w celu zwrócenia pojedynczych słów zamiast całych wierszy. Jest to wykonywane z tymi modyfikacjami. Zastąp `yield return line;` instrukcję następującym kodem:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Następnie należy zmodyfikować sposób korzystania z wierszy pliku i dodać opóźnienie po zapisaniu każdego wyrazu. `Console.WriteLine(line)` Zamień instrukcję `Main` w metodzie na następujący blok:

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

Klasa znajduje się <xref:System.Threading.Tasks> w przestrzeni nazw, dlatego należy dodać tę `using` instrukcję na początku pliku: <xref:System.Threading.Tasks.Task>

```csharp
using System.Threading.Tasks;
```

Uruchom przykład i sprawdź dane wyjściowe. Teraz każdy pojedynczy wyraz jest drukowany, po którym następuje opóźnienie 200 ms. Jednak wyświetlane dane wyjściowe pokazują pewne problemy, ponieważ źródłowy plik tekstowy ma kilka wierszy, które mają więcej niż 80 znaków bez przerwy w wierszu. Może to być trudne do odczytania podczas przewijania przez program. Jest to łatwe do naprawienia. Będziesz śledzić długość każdego wiersza i generować nowy wiersz zawsze, gdy długość wiersza osiągnie określony próg. Zadeklaruj zmienną lokalną po deklaracji `words` `ReadFrom` metody, która posiada długość wiersza:

```csharp
var lineLength = 0;
```

Następnie Dodaj następujący kod po `yield return word + " ";` instrukcji (przed zamykającym nawiasem klamrowym):

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

W tym ostatnim kroku dodasz kod, aby zapisać dane wyjściowe asynchronicznie w jednym zadaniu, a jednocześnie uruchomić inne zadanie odczytujące dane wejściowe od użytkownika, jeśli chcesz przyspieszyć lub spowolnić wyświetlanie tekstu lub zatrzymać wyświetlanie tekstu. Obejmuje to kilka kroków i zakończenie, które będą potrzebne do wszystkich niezbędnych aktualizacji.
Pierwszym krokiem jest utworzenie asynchronicznej <xref:System.Threading.Tasks.Task> metody zwracającej, która reprezentuje kod, który został utworzony do odczytu i wyświetlenia pliku.

Dodaj tę metodę do `Program` klasy (jest ona pobierana z treści `Main` metody):

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

Zauważysz dwie zmiany. Po pierwsze, w treści metody, zamiast wywołania <xref:System.Threading.Tasks.Task.Wait> synchronicznie oczekiwanie na zakończenie zadania, ta wersja `await` używa słowa kluczowego. Aby to zrobić, należy dodać `async` modyfikator do sygnatury metody. Ta metoda zwraca `Task`. Zwróć uwagę, że nie ma instrukcji return zwracających `Task` obiekt. Zamiast tego ten `Task` obiekt jest tworzony przez kod, który kompilator generuje podczas korzystania z `await` operatora. Można Wyobraź sobie, że ta metoda zwraca, gdy osiągnie `await`. Zwracana `Task` wartość wskazuje, że pracę nie została ukończona.
Metoda zostaje wznowiona po zakończeniu oczekiwania na zadanie. Po wykonaniu tej operacji zwrócona `Task` wartość wskazuje, że została zakończona.
Wywoływanie kodu może monitorować, `Task` który zwraca, aby określić, kiedy został ukończony.

Tę nową metodę można wywołać w `Main` metodzie:

```csharp
ShowTeleprompter().Wait();
```

W `Main`tym miejscu kod wykonuje synchronicznie oczekiwania. Jeśli to możliwe, `await` należy użyć operatora zamiast synchronicznego oczekiwania. Ale w `Main` metodzie aplikacji konsolowej nie można `await` używać operatora. Spowoduje to zakończenie działania aplikacji przed ukończeniem wszystkich zadań.

> [!NOTE]
> Jeśli używasz C# 7,1 lub nowszej, możesz utworzyć aplikacje konsolowe za pomocą [ `async` `Main` metody](../whats-new/csharp-7-1.md#async-main).

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

Spowoduje to utworzenie wyrażenia lambda do reprezentowania <xref:System.Action> delegata, który odczytuje klucz z konsoli programu i modyfikuje zmienną lokalną reprezentującą opóźnienie, gdy użytkownik naciśnie klawisz "<" (mniej niż) lub ">" (większy niż). Metoda Delegate kończy się, gdy użytkownik naciśnie klawisze "X" lub "x", które umożliwiają użytkownikowi zatrzymanie wyświetlania tekstu w dowolnym momencie.
Ta metoda używa <xref:System.Console.ReadKey> do blokowania i poczekania użytkownika o naciśnięcie klawisza.

Aby zakończyć tę funkcję, należy utworzyć nową `async Task` metodę zwracającą, która uruchamia oba te zadania (`GetInput` i `ShowTeleprompter`), a także zarządza danymi udostępnionymi między tymi dwoma zadaniami.

Czas na utworzenie klasy, która może obsługiwać udostępnione dane między tymi dwoma zadaniami. Ta klasa zawiera dwie właściwości publiczne: opóźnienie i flagę `Done` wskazującą, że plik został całkowicie odczytany:

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

Umieść tę klasę w nowym pliku i umieść ją w `TeleprompterConsole` przestrzeni nazw, jak pokazano powyżej. Należy również dodać `using static` instrukcję, aby można było odwoływać się `Min` do metod i `Max` bez nazwy klasy lub przestrzeni nazw. [`using static`](../language-reference/keywords/using-static.md) Instrukcja importuje metody z jednej klasy. Jest to w przeciwieństwie `using` do instrukcji używanych do tego punktu, który zaimportował wszystkie klasy z przestrzeni nazw.

```csharp
using static System.Math;
```

Następnie należy zaktualizować `ShowTeleprompter` metody i `GetInput` , aby użyć nowego `config` obiektu. Napisz jedną ostateczną `Task` metodę `async` zwracającą, aby uruchomić oba zadania i wyjść po zakończeniu pierwszego zadania:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Ta nowa metoda to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> wywołanie. Spowoduje to utworzenie `Task` , który zakończy się zaraz po zakończeniu wszystkich zadań na liście argumentów.

Następnie należy zaktualizować `ShowTeleprompter` metody i `GetInput` , aby użyć `config` obiektu dla opóźnienia:

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

Ta nowa wersja `ShowTeleprompter` wywołuje nową metodę `TeleprompterConfig` w klasie. Teraz musisz zaktualizować `Main` do wywołania `RunTeleprompter` zamiast `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Wniosek

W tym samouczku przedstawiono szereg funkcji dotyczących C# języka i bibliotek .NET Core związanych z pracą w aplikacjach konsolowych.
Możesz utworzyć tę wiedzę, aby dowiedzieć się więcej o języku i klasach wprowadzonych w tym miejscu. Przedstawiono podstawowe informacje na temat operacji we/wy plików i konsoli, blokowania i nieblokowania użycia programowania asynchronicznego opartego na zadaniach, samouczka dotyczącego C# języka i sposobu C# organizowania programów oraz interfejsu wiersza polecenia i narzędzi .NET Core.

Aby uzyskać więcej informacji na temat operacji we/wy plików, zobacz temat [plik i strumień we/wy](../../standard/io/index.md) . Aby uzyskać więcej informacji o modelu programowania asynchronicznego używanym w tym samouczku, zapoznaj się z tematem [programowanie asynchroniczne oparte na zadaniach](../..//standard/parallel-programming/task-based-asynchronous-programming.md) i w temacie [programowanie asynchroniczne](../async.md) .
