---
title: Aplikacja konsolowa
description: W tym samouczku nauczy Cię wiele funkcji w .NET Core i języku C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 09ce36e7a61f576dc4449976ce676701dc57c9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76921124"
---
# <a name="console-app"></a>Aplikacja konsolowa

W tym samouczku nauczy Cię wiele funkcji w .NET Core i języku C#. Dowiesz się:

- Podstawy cli .NET Core
- Struktura aplikacji konsoli C#
- Konsola We/Wy
- Podstawy interfejsów API we/wy plików w .NET
- Podstawy programowania asynchronicznego opartego na zadaniach w programie .NET

Stworzysz aplikację, która odczytuje plik tekstowy i nawiązuje do konsoli zawartość tego pliku tekstowego. Wyjście do konsoli jest w tempie, aby dopasować czytanie na głos. Możesz przyspieszyć lub spowolnić tempo, naciskając klawisze "<" (mniej niż) lub ">" (większe niż).

Istnieje wiele funkcji w tym samouczku. Budujmy je jeden po drugim.

## <a name="prerequisites"></a>Wymagania wstępne

- Skonfiguruj komputer do uruchamiania .NET Core. Instrukcje instalacji można znaleźć na stronie [pobierania .NET Core.](https://dotnet.microsoft.com/download) Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.

- Zainstaluj swój ulubiony edytor kodów.

## <a name="create-the-app"></a>Tworzymy aplikację.

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i utwórz nowy katalog dla aplikacji. Upewnij się, że bieżący katalog. Wpisz `dotnet new console` polecenie w wierszu polecenia. Spowoduje to utworzenie plików startowych dla podstawowej aplikacji "Hello World".

Przed rozpoczęciem wprowadzania modyfikacji przejdźmy przez kroki, aby uruchomić prostą aplikację Hello World. Po utworzeniu aplikacji `dotnet restore` wpisz wiersz polecenia. To polecenie uruchamia proces przywracania pakietów NuGet. NuGet jest menedżerem pakietów .NET. To polecenie pobiera dowolną z brakujących zależności dla projektu. Ponieważ jest to nowy projekt, żadna z zależności nie są na miejscu, więc pierwsze uruchomienie pobierze .NET Core framework. Po tym początkowym kroku należy `dotnet restore` uruchomić tylko podczas dodawania nowych pakietów zależnych lub zaktualizować wersje dowolnej z zależności.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po przywróceniu pakietów `dotnet build`uruchomisz . Spowoduje to wykonanie aparatu kompilacji i tworzy plik wykonywalny aplikacji. Na koniec `dotnet run` można wykonać, aby uruchomić aplikację.

Prosty kod aplikacji Hello World jest w Program.cs. Otwórz ten plik za pomocą ulubionego edytora tekstu. Nieszywniemy pierwsze zmiany. U góry pliku zobacz using instrukcji:

```csharp
using System;
```

Ta instrukcja informuje kompilator, że wszystkie typy z obszaru `System` nazw są w zakresie. Podobnie jak inne języki zorientowane na obiekty, które mogły być używane, C# używa przestrzeni nazw do organizowania typów. Ten program Hello World nie różni się. Widać, że program jest ujęty w obszarze nazw nazwą o nazwie opartej na nazwie bieżącego katalogu. W tym samouczku zmieńmy nazwę obszaru nazw `TeleprompterConsole`na :

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Odczytywanie i powtarzanie pliku

Pierwszą funkcją do dodania jest możliwość odczytu pliku tekstowego i wyświetlenia całego tekstu w konsoli. Najpierw dodajmy plik tekstowy. Skopiuj [plik sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z repozytorium GitHub dla tego [przykładu](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do katalogu projektu. Będzie to służyć jako skrypt dla aplikacji. Jeśli chcesz uzyskać informacje na temat pobierania przykładowej aplikacji dla tego tematu, zapoznaj się z instrukcjami w temacie [Przykłady i samouczki.](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)

Następnie dodaj następującą `Program` metodę w klasie `Main` (tuż poniżej metody):

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

Ta metoda używa typów z dwóch nowych obszarów nazw. Aby to skompilować, musisz dodać następujące dwa wiersze do górnej części pliku:

```csharp
using System.Collections.Generic;
using System.IO;
```

Interfejs <xref:System.Collections.Generic.IEnumerable%601> jest zdefiniowany <xref:System.Collections.Generic> w obszarze nazw. Klasa <xref:System.IO.File> jest zdefiniowana <xref:System.IO> w obszarze nazw.

Ta metoda jest specjalnym typem metody Języka C# o nazwie *Iterator method*. Metody wyliczania zwracają sekwencje, które są oceniane leniwie. Oznacza to, że każdy element w sekwencji jest generowany, ponieważ jest wymagane przez kod korzystających sekwencji. Metody wyliczania są metody, które [`yield return`](../language-reference/keywords/yield.md) zawierają co najmniej jedną instrukcję. Obiekt zwrócony przez `ReadFrom` metodę zawiera kod do generowania każdego elementu w sekwencji. W tym przykładzie, który obejmuje odczytywanie następnego wiersza tekstu z pliku źródłowego i zwracanie tego ciągu. Za każdym razem, gdy kod wywołujący żąda następnego elementu z sekwencji, kod odczytuje następny wiersz tekstu z pliku i zwraca go. Gdy plik jest całkowicie odczytywany, sekwencja wskazuje, że nie ma więcej elementów.

Istnieją dwa inne elementy składni Języka C#, które mogą być dla Ciebie nowe. Instrukcja [`using`](../language-reference/keywords/using-statement.md) w tej metodzie zarządza oczyszczania zasobów. Zmienna, która jest `using` inicjowana`reader`w instrukcji ( , <xref:System.IDisposable> w tym przykładzie) musi implementować interfejs. Ten interfejs definiuje jedną `Dispose`metodę, która powinna być wywoływana, gdy zasób powinien zostać zwolniony. Kompilator generuje to wywołanie, gdy wykonanie `using` osiągnie nawias zamykający instrukcji. Kod wygenerowany przez kompilator zapewnia, że zasób jest zwalniany, nawet jeśli wyjątek jest zgłaszany z kodu w bloku zdefiniowane przez using instrukcji.

Zmienna `reader` jest definiowana `var` przy użyciu słowa kluczowego. [`var`](../language-reference/keywords/var.md)definiuje *niejawnie wpisaną zmienną lokalną*. Oznacza to, że typ zmiennej jest określana przez typ czasu kompilacji obiektu przypisanego do zmiennej. W tym miejscu jest to <xref:System.IO.File.OpenText(System.String)> wartość zwracana <xref:System.IO.StreamReader> z metody, która jest obiektem.

Teraz wypełnijmy kod, aby odczytać plik `Main` w metodzie:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Uruchom program (za pomocą `dotnet run`) i możesz zobaczyć każdy wiersz wydrukowany na konsoli.

## <a name="adding-delays-and-formatting-output"></a>Dodawanie opóźnień i danych wyjściowych formatowania

To, co masz, jest wyświetlane zbyt szybko, aby przeczytać na głos. Teraz musisz dodać opóźnienia w danych wyjściowych. Po uruchomieniu będziesz budować niektóre z podstawowych kodu, który umożliwia przetwarzanie asynchroniczne. Jednak te pierwsze kroki będą zgodne z kilkoma anty-wzorców. Anti-wzorce są wskazywane w komentarzach podczas dodawania kodu, a kod zostanie zaktualizowany w kolejnych krokach.

Istnieją dwa kroki do tej sekcji. Najpierw zaktualizujesz metodę iteratorego, aby zwrócić pojedyncze wyrazy zamiast całych wierszy. Tak jest z tymi modyfikacjami. Zastąp instrukcję `yield return line;` następującym kodem:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Następnie należy zmodyfikować sposób korzystania z wierszy pliku i dodać opóźnienie po zapisaniu każdego wyrazu. Zamień instrukcję `Console.WriteLine(line)` w metodzie `Main` na następujący blok:

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

Klasa <xref:System.Threading.Tasks.Task> znajduje się <xref:System.Threading.Tasks> w obszarze nazw, więc `using` należy dodać tę instrukcję u góry pliku:

```csharp
using System.Threading.Tasks;
```

Uruchom przykład i sprawdź dane wyjściowe. Teraz każde pojedyncze słowo jest drukowane, a następnie 200 ms opóźnienie. Jednak wyświetlane dane wyjściowe pokazują pewne problemy, ponieważ źródłowy plik tekstowy ma kilka wierszy, które mają więcej niż 80 znaków bez podziału wiersza. To może być trudne do odczytania podczas przewijania przez. To jest łatwe do naprawienia. Po prostu będziesz śledzić długość każdego wiersza i generować nowy wiersz, gdy długość linii osiągnie określony próg. Zadeklarować zmienną lokalną `words` po `ReadFrom` deklaracji w metodzie, która przechowuje długość wiersza:

```csharp
var lineLength = 0;
```

Następnie dodaj następujący kod `yield return word + " ";` po instrukcji (przed nawiasem klamrowym zamknięcia):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Uruchom przykład, a będziesz mógł czytać na głos w jego wstępnie skonfigurowanym tempie.

## <a name="async-tasks"></a>Zadania asynchroniczne

W tym ostatnim kroku dodasz kod do zapisu danych wyjściowych asynchronicznie w jednym zadaniu, a także uruchamiasz inne zadanie do odczytu danych wejściowych od użytkownika, jeśli chcesz przyspieszyć lub spowolnić wyświetlanie tekstu lub całkowicie zatrzymać wyświetlanie tekstu. Ma to kilka kroków w nim i na koniec będziesz miał wszystkie aktualizacje, które są potrzebne. Pierwszym krokiem jest utworzenie asynchronicznej <xref:System.Threading.Tasks.Task> metody zwracania, która reprezentuje kod utworzony do tej pory do odczytu i wyświetlania pliku.

Dodaj tę metodę `Program` do swojej klasy (jest pobierana z treści metody): `Main`

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

Zauważysz dwie zmiany. Po pierwsze, w treści metody, <xref:System.Threading.Tasks.Task.Wait> zamiast wywoływania synchronicznie czekać na zakończenie `await` zadania, ta wersja używa słowa kluczowego. Aby to zrobić, należy dodać `async` modyfikator do podpisu metody. Ta metoda `Task`zwraca wartość . Należy zauważyć, że nie ma `Task` żadnych instrukcji zwrotnych, które zwracają obiekt. Zamiast tego `Task` ten obiekt jest tworzony przez kod kompilator generuje podczas korzystania z `await` operatora. Można sobie wyobrazić, że ta metoda `await`zwraca, gdy osiągnie . Zwrócony `Task` wskazuje, że praca nie została ukończona. Metoda zostanie wznowiona po zakończeniu oczekiwanego zadania. Po wykonaniu do zakończenia, zwrócony `Task` wskazuje, że jest zakończona.
Kod wywołujący można `Task` monitorować, który powrócił, aby określić, kiedy została ukończona.

Możesz wywołać tę nową `Main` metodę w metodzie:

```csharp
ShowTeleprompter().Wait();
```

W tym `Main`miejscu , w , kod nie synchronicznie czekać. Należy użyć `await` operatora zamiast synchronicznie oczekiwania, gdy jest to możliwe. Jednak w `Main` metodzie aplikacji konsoli nie można `await` użyć operatora. Spowodowałoby to zamknięcie aplikacji przed zakończeniem wszystkich zadań.

> [!NOTE]
> Jeśli używasz języka C# 7.1 lub nowszego, możesz tworzyć aplikacje konsoli za pomocą [ `async` `Main` metody](../whats-new/csharp-7-1.md#async-main).

Następnie należy napisać drugą metodę asynchroniczną, aby odczytać z Konsoli i obserwować klawisze "<" (mniej niż), ">" (większa niż) i "X" lub "x". Oto metoda dodania dla tego zadania:

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

Spowoduje to utworzenie wyrażenia lambda do reprezentowania delegata, <xref:System.Action> który odczytuje klucz z konsoli i modyfikuje zmienną lokalną reprezentującą opóźnienie, gdy użytkownik naciśnie klucze "<" (mniej niż) lub ">" (większe niż). Metoda delegowania kończy się, gdy użytkownik naciśnie klawisze "X" lub "x", co pozwala użytkownikowi zatrzymać wyświetlanie tekstu w dowolnym momencie. Ta metoda <xref:System.Console.ReadKey> służy do blokowania i oczekiwania na użytkownika, aby nacisnąć klawisz.

Aby zakończyć tę funkcję, należy `async Task` utworzyć nową metodę zwracania,`GetInput` która `ShowTeleprompter`uruchamia oba te zadania ( i ), a także zarządza udostępnionymi danymi między tymi dwoma zadaniami.

Nadszedł czas, aby utworzyć klasę, która może obsługiwać udostępnione dane między tymi dwoma zadaniami. Ta klasa zawiera dwie właściwości publiczne: opóźnienie `Done` i flagę wskazującą, że plik został całkowicie odczytany:

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

Umieść tę klasę w nowym pliku i ująć tę klasę w obszarze `TeleprompterConsole` nazw, jak pokazano powyżej. Należy również dodać instrukcję, `using static` aby można było `Min` `Max` odwoływać się do i metod bez otaczających nazw klasy lub obszaru nazw. Instrukcja [`using static`](../language-reference/keywords/using-static.md) importuje metody z jednej klasy. Jest to w `using` przeciwieństwie do instrukcji używanych do tego momentu, które zaimportowały wszystkie klasy z obszaru nazw.

```csharp
using static System.Math;
```

Następnie należy zaktualizować `ShowTeleprompter` i `GetInput` metody, aby `config` użyć nowego obiektu. Zapisz jedną `Task` ostateczną metodę zwracania, `async` aby uruchomić oba zadania i zakończyć po zakończeniu pierwszego zadania:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Jedną z nowych metod <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> jest tutaj wywołanie. Spowoduje to `Task` utworzenie, które kończy się tak szybko, jak każde z zadań na liście argumentów zostanie zakończone.

Następnie należy zaktualizować zarówno `ShowTeleprompter` `GetInput` metody, jak `config` i metody, aby użyć obiektu dla opóźnienia:

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

Ta nowa `ShowTeleprompter` wersja wywołuje nową `TeleprompterConfig` metodę w klasie. Teraz musisz zaktualizować, `Main` `RunTeleprompter` aby `ShowTeleprompter`zadzwonić, a nie:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Podsumowanie

W tym samouczku pokazano szereg funkcji wokół języka C# i bibliotek .NET Core związanych z pracą w aplikacjach konsoli. Można wykorzystać tę wiedzę, aby dowiedzieć się więcej o języku i klas wprowadzonych tutaj. Widzieliście podstawy we/wy pliku i konsoli, blokowanie i nieblokowanie użycia programowania asynchronicznego opartego na zadaniach, przewodnik po języku C# i sposób organizowania programów C#oraz interfejs cli .NET Core.

Aby uzyskać więcej informacji na temat we/wy pliku, zobacz [temat We/Wy plik i strumień.](../../standard/io/index.md) Aby uzyskać więcej informacji na temat asynchronicznego modelu programowania używanego w tym samouczku, zobacz temat [Programowania asynchronicznego opartego na zadaniach](../..//standard/parallel-programming/task-based-asynchronous-programming.md) i temat [programowania asynchronicznego.](../async.md)
