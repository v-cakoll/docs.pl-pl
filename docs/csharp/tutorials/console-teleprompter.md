---
title: Aplikacja konsoli
description: W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: da3f8f913d452b5c3c9dcda6079067c879a678dd
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540901"
---
# <a name="console-application"></a>Aplikacja konsoli

W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#. Dowiesz się:

- Podstawowe narzędzia .NET Core interfejsu wiersza polecenia (CLI)
- Struktura aplikacji Konsolowej C#
- Konsola operacje We/Wy
- Podstawowe informacje dotyczące interfejsów API we/wy pliku w programie .NET
- Podstawy opartego na zadaniach asynchronicznej programowanie na platformie .NET

Skompiluj aplikację, która odczytuje plik tekstowy i zwraca zawartość tego pliku tekstowego do konsoli. Dane wyjściowe do konsoli jest realizowany do dopasowania wczytaniem go na głos. Można przyspieszyć lub zwolnić tempie, naciskając klawisz "<" (mniejsze niż) lub ">" (większe niż) kluczy.

Istnieje wiele funkcji, w tym samouczku. Utworzymy je jedno po drugim.

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować maszynę w taki sposób, aby uruchomić platformy .NET Core. Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony. Windows, Linux, macOS lub w kontenerze platformy Docker, mogą uruchamiać tę aplikację.
Musisz zainstalować wybrany edytor kodu.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji. Upewnij się, że sposób bieżącego katalogu. Wpisz polecenie `dotnet new console` w wierszu polecenia. Spowoduje to utworzenie plikach startowych dla podstawowych aplikacji "Hello World".

Przed rozpoczęciem wprowadzania modyfikacji, Przejdźmy przez czynności, aby uruchomić prostej aplikacji Hello World. Po utworzeniu aplikacji wpisz `dotnet restore` w wierszu polecenia. To polecenie uruchamia proces przywracania pakietów NuGet. NuGet to Menedżer pakietów .NET. To polecenie pobiera wszystkich brakujących zależności dla Twojego projektu. Jak jest to nowy projekt, żaden z zależności jest w miejscu, dzięki czemu przy pierwszym uruchomieniu pobierze platformę .NET Core. Po wykonaniu tego kroku początkowego, wystarczy uruchomić `dotnet restore` podczas dodawania nowych pakietów zależnych lub zaktualizować wersje tych zależności.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po przywróceniu pakietów, możesz uruchomić `dotnet build`. Wykonuje aparat kompilacji i tworzy pliku wykonywalnego aplikacji. Na koniec wykonaj `dotnet run` do uruchamiania aplikacji.

Prosty kod aplikacji Hello World znajduje się w pliku Program.cs. Otwórz ten plik za pomocą ulubionego edytora tekstu. Jesteśmy przeprowadzasz pierwszy zmian.
W górnej części pliku, zobacz using instrukcji:

```csharp
using System;
```

Ta instrukcja informuje kompilator, że dowolne typy z `System` przestrzeni nazw znajdują się w zakresie. Podobnie jak może być użyty innych języków obiektowo języka C# korzysta przestrzenie nazw do organizowania typów. Ten program Hello World nie różni się. Aby zobaczyć, że program jest ujęty w przestrzeni nazw o nazwie na podstawie nazwy bieżącego katalogu. W tym samouczku zmienimy nazwę przestrzeni nazw do `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Odczytywanie i wyświetlania pliku

Pierwszą funkcją do dodania jest możliwość odczytywanie pliku tekstowego i wyświetlić ten tekst do konsoli. Najpierw Dodajmy pliku tekstowego. Kopiuj [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) plik z repozytorium GitHub, w tym [przykładowe](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) w katalogu projektu. To będzie służyć jako skrypt dla aplikacji. Jeśli chcesz uzyskać informacje dotyczące sposobu pobierania przykładowej aplikacji na potrzeby tego artykułu zapoznaj się z instrukcjami w [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) tematu.

Następnie dodaj następującą metodę w swojej `Program` klasy (bezpośrednio poniżej `Main` metoda):

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

Ta metoda używa typów z dwa nowe przestrzenie nazw. W tym można skompilować należy dodać następujące dwa wiersze na początku pliku:

```csharp
using System.Collections.Generic;
using System.IO;
```

<xref:System.Collections.Generic.IEnumerable%601> Interfejsu jest zdefiniowany w <xref:System.Collections.Generic> przestrzeni nazw. <xref:System.IO.File> Klasa jest zdefiniowana w <xref:System.IO> przestrzeni nazw.

Ta metoda jest specjalnym typem metodę języka C# o nazwie *metody iteratora*. Moduł wyliczający metody zwracają sekwencji, które zostaną ocenione opóźnieniem. Oznacza to, że każdy element w sekwencji jest generowany, zgodnie z żądaniem kodu korzystanie z sekwencji. Moduł wyliczający metody są metodami, które zawierają co najmniej jeden [ `yield return` ](../language-reference/keywords/yield.md) instrukcji. Obiekt zwrócony przez `ReadFrom` metoda zawiera kod, aby wygenerować każdego elementu w sekwencji. W tym przykładzie, który obejmuje odczytywanie kolejny wiersz tekstu z pliku źródłowego i zwraca ciąg. Za każdym żądaniem kod wywołujący następnego elementu w sekwencji, kod odczytuje następny wiersz tekstu z pliku i zwraca go. Gdy plik jest całkowicie do odczytu, sekwencja oznacza, że brak elementów.

Istnieją dwa inne C# składni elementy, które mogą być dla Ciebie nowe. [ `using` ](../language-reference/keywords/using-statement.md) Poufności informacji w tej metodzie zarządza czyszczenie zasobów. Zmienna, która jest inicjowana w `using` — instrukcja (`reader`, w tym przykładzie) należy zaimplementować <xref:System.IDisposable> interfejsu. Ten interfejs definiuje jedną metodę `Dispose`, która powinna być wywoływana, gdy zasobu powinny zostać opublikowane. Kompilator generuje to wywołanie, gdy wykonywanie osiągnie zamykającym nawiasem klamrowym `using` instrukcji. Kod wygenerowany przez kompilator zapewnia, jest zwolnienie zasobów nawet wtedy, gdy wyjątek jest generowany z kodu w bloku zdefiniowane za pomocą instrukcji.

`reader` Zmienna jest zdefiniowana za pomocą `var` — słowo kluczowe. [`var`](../language-reference/keywords/var.md) definiuje *niejawnie typizowanej zmiennej lokalnej*. Oznacza to, że typ zmiennej jest określana przez typ kompilacji, przypisana do zmiennej obiektu. Tutaj, która jest wartością zwracaną z <xref:System.IO.File.OpenText(System.String)> metoda, która jest <xref:System.IO.StreamReader> obiektu.

Teraz możemy wypełnienie kodu, który można odczytać pliku w `Main` metody:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Uruchom program (przy użyciu `dotnet run`) i zobaczyć wszystkich wierszy drukowane do konsoli.

## <a name="adding-delays-and-formatting-output"></a>Dodawanie opóźnień i formatowanie danych wyjściowych

Posiadane zasoby są wyświetlane w zbyt szybko, aby odczytywać. Teraz należy dodać opóźnienia w danych wyjściowych. Po rozpoczęciu, tworzyć część kodu core, która umożliwia przetwarzanie asynchroniczne. Jednak te pierwsze kroki są zgodne z kilku niezalecane wzorce. Niezalecane wzorce są wskazano w komentarzach, Dodaj kod, a kod zostanie zaktualizowany w kolejnych krokach.

Istnieją dwa kroki, aby w tej sekcji. Po pierwsze zostaną zaktualizowane metody iteratora, aby zwrócić pojedynczego słowa zamiast całego wierszy. Zostanie to zrobione za pomocą tych zmian. Zastąp `yield return line;` instrukcję, używając następującego kodu:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Następnie należy zmodyfikować, jak używać wiersze pliku i dodawanie opóźnienia po zapisaniu każdego wyrazu. Zastąp `Console.WriteLine(line)` instrukcji w `Main` metody z następujący blok:

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

<xref:System.Threading.Tasks.Task> Klasa się zebrała <xref:System.Threading.Tasks> przestrzeni nazw, dlatego należy go dodać `using` instrukcji w górnej części pliku:

```csharp
using System.Threading.Tasks;
```

Uruchamianie aplikacji przykładowej i sprawdź dane wyjściowe. Teraz każdego pojedynczego wyrazu drukowania, a następnie z opóźnieniem 200 ms. Jednak wyświetlane dane wyjściowe pokazują niektóre problemy, ponieważ źródłowy plik tekstowy zawiera kilka wierszy, które mają więcej niż 80 znaków bez podziału wiersza. Który może być trudny do odczytania, podczas gdy przewijanie jest przez. To łatwe rozwiązać problem. Można będzie po prostu śledzić długość każdego wiersza i wygenerować nowy wiersz, w każdym przypadku, gdy długość wiersza osiągnie określony próg. Zadeklaruj zmienną lokalnej po zadeklarowaniu `words` w `ReadFrom` metodę, która zawiera długość wiersza:

```csharp
var lineLength = 0;
```

Następnie należy dodać następujący kod po `yield return word + " ";` — instrukcja (przed zamykający nawias klamrowy):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Uruchom aplikację przykładową, a będzie można odczytywać w jej wstępnie skonfigurowanych tempie.

## <a name="async-tasks"></a>Zadań asynchronicznych

W tym ostatnim kroku dodasz kod, aby zapisywać dane wyjściowe asynchronicznie w ramach jednego zadania podczas również działa inne zadanie, które można odczytać danych wejściowych od użytkownika, jeśli chcesz przyspieszyć lub zwolnić wyświetlania tekstu. Ma kilka kroków i do końca, będziesz mieć wszystkie aktualizacje, które są potrzebne.
Pierwszym krokiem jest utworzenie asynchronicznego <xref:System.Threading.Tasks.Task> zwracania metody, która przedstawia kod do tej pory utworzono do odczytywania i wyświetlić plik.

Dodaj tę metodę, aby Twoje `Program` klasy (jest zajęta z treści usługi `Main` metody):

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

Można zauważyć dwie zmiany. Po pierwsze, w treści metody, zamiast wywoływać metodę <xref:System.Threading.Tasks.Task.Wait> synchronicznie oczekiwania na zakończenie zadania, ta wersja wykorzystuje `await` — słowo kluczowe. Aby to zrobić, należy dodać `async` modyfikatora podpis metody. Ta metoda zwraca `Task`. Należy zauważyć, że nie istnieją żadne instrukcjach return, które zwracają `Task` obiektu. Zamiast tego, który `Task` obiekt jest tworzony przez kod, kompilator generuje, gdy używasz `await` operatora. Można sobie wyobrazić, że ta metoda zwraca po osiągnięciu `await`. Zwrócony `Task` wskazuje, że nie zakończył pracy.
Metoda zostanie wznowione, gdy zakończy się oczekiwane zadanie. Kiedy zostało wykonane do zakończenia zwracanego `Task` wskazuje, że została zakończona.
Wywoływanie kodu, można monitorować zwróconą `Task` ustalenie, kiedy zostało ono ukończone.

Ta nowa metoda można wywołać w swojej `Main` metody:

```csharp
ShowTeleprompter().Wait();
```

W tym miejscu, w `Main`, kod synchronicznie oczekiwania. Należy używać `await` operatora, zamiast czekać synchronicznie, jeśli to możliwe. Jednak w aplikacji konsoli `Main` metody, nie można użyć `await` operatora. Które mogłyby spowodować zamykania aplikacji, zanim wszystkie zadania zostały ukończone.

> [!NOTE]
> Jeśli używasz języka C# 7.1 lub nowszy, możesz tworzyć aplikacje konsoli przy użyciu [ `async` `Main` metoda](../whats-new/csharp-7-1.md#async-main).

Następnie należy napisać drugiej metodzie asynchronicznej odczytywany z konsoli, zwracając uwagę na "<" (mniejsze niż) i ">" (większe niż) kluczy. Poniżej przedstawiono metodę, którą możesz dodać do tego zadania:

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
        } while (true);
    };
    await Task.Run(work);
}
```

Spowoduje to utworzenie wyrażenia lambda do reprezentowania <xref:System.Action> delegat, który odczytuje klucz z konsoli i modyfikuje zmienną lokalną, reprezentujący opóźnienie w przypadku, gdy użytkownik naciśnie "<" (mniejsze niż) lub ">" (większe niż) kluczy. Ta metoda używa <xref:System.Console.ReadKey> do blokowania i poczekać na użytkownika poprzez naciśnięcie klawisza.

Aby zakończyć tę funkcję, musisz utworzyć nowy `async Task` metodę, która rozpoczyna się w obu tych zadań zwracającą (`GetInput` i `ShowTeleprompter`), a także zarządza udostępnionych danych między te dwa zadania.

Nadszedł czas, aby utworzyć klasę, która może obsłużyć udostępnionych danych między te dwa zadania. Ta klasa zawiera dwie właściwości publiczne: opóźnienie i flagi `Done` aby potwierdzić, że plik został całkowicie przeczytane:

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

Umieść tej klasy w nowym pliku a następnie zamieścić tej klasy w `TeleprompterConsole` przestrzeni nazw, jak pokazano powyżej. Należy także dodać `using static` instrukcji, dzięki czemu możesz odwoływać się do `Min` i `Max` metody bez otaczającej nazwy klasy lub obszaru nazw. A [ `using static` ](../language-reference/keywords/using-static.md) instrukcji imports metody z jednej klasy. Jest to w przeciwieństwie `using` instrukcji używany do tej pory, które zostały zaimportowane wszystkie klasy z przestrzeni nazw.

```csharp
using static System.Math;
```

Z innych funkcji języka, co nowego jest [ `lock` ](../language-reference/keywords/lock-statement.md) instrukcji. Niniejszych gwarantuje, że tylko jednego wątku może należeć ten kod w dowolnym momencie. Jeśli jeden wątek znajduje się w sekcji zablokowane, inne wątki musi czekać na pierwszym wątku zakończyć tę sekcję. `lock` Instrukcja używa obiektu, który chroni sekcji blokady. Ta klasa jest zgodna standardowa idiom można zablokować obiektu prywatnego w klasie.

Następnie należy zaktualizować `ShowTeleprompter` i `GetInput` metody, aby użyć nowego `config` obiektu. Zapis jeden końcowy `Task` zwracanie `async` metodę, aby uruchomić zarówno do zadań i Zakończ po zakończeniu pierwszego zadania:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Jeden nowa metoda w tym miejscu jest <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> wywołania. Tworząca `Task` który zakończy się zaraz po zakończeniu wszystkich zadań na liście argumentów.

Następnie należy zaktualizować obydwa `ShowTeleprompter` i `GetInput` metod do zastosowania `config` obiektu opóźnienia:

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
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

Nowa wersja `ShowTeleprompter` wywołuje nową metodę `TeleprompterConfig` klasy. Teraz, musisz zaktualizować `Main` do wywołania `RunTeleprompter` zamiast `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Wniosek

W tym samouczku pokazano, że możesz pewną liczbę funkcji wokół języka C# i biblioteki .NET Core związanych z pracą w aplikacjach konsoli.
Możesz utworzyć na tej wiedzy do Dowiedz się więcej o języku, klas i wprowadzone w tym miejscu. Przedstawiono podstawowe informacje dotyczące plików i we/wy konsoli, blokowania i bez blokowania użycia asynchronicznego programowania opartego na zadaniach, samouczek języka C# oraz jak C# programy są uporządkowane i interfejs wiersza polecenia programu .NET Core oraz narzędzia.

Aby uzyskać więcej informacji na temat operacji We/Wy w pliku zobacz [plików i we/wy Stream](../../standard/io/index.md) tematu. Aby uzyskać więcej informacji na temat asynchronicznego modelu programowania, w tym samouczku używane zobacz [opartego na zadaniach Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) tematu i [programowania asynchronicznego](../async.md) tematu.
