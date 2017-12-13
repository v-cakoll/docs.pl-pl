---
title: "Przewodnik Szybki Start - gałęzie i pętle - C#"
description: "W tym szybki start dotyczące gałęzi i pętle pisania kodu C#, aby eksplorować składni języka, obsługującego warunkowych gałęzi i pętli do wykonywania instrukcji wielokrotnie."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 7954475616b122f8bb96ad00d05b476b3beeb52c
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="branches-and-loops"></a>Gałęzie i pętli

To szybki start jest przedstawienie sposobu pisania kodu, który sprawdza zmienne i zmieniona ścieżka wykonywania na podstawie tych zmiennych. Pisanie kodu C# i wyświetlić wyniki kompilowania i uruchamiania go. Szybki start zawiera szereg lekcje, które eksplorować rozgałęzianie i zapętlenia konstrukcje w języku C#. Że wnioski uczy również podstaw programu w języku C#.

To szybki start oczekuje posiadania maszynie, która służy do tworzenia aplikacji. Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux. Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.

## <a name="make-decisions-using-the-if-statement"></a>Podejmowanie decyzji przy użyciu `if` — instrukcja

Utwórz katalog o nazwie **szybkiego startu gałęzie**. Upewnij, że bieżący katalog i uruchom `dotnet new console -n BranchesAndLoops -o .`. To polecenie tworzy nową aplikację konsolową .NET Core w bieżącym katalogu. 

Otwórz **Program.cs** ulubionego edytora i Zastąp linię `Console.Writeline("Hello World!");` następującym kodem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Spróbuj ten kod, wpisując `dotnet run` w okna konsoli. Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10". podane do konsoli.

Modyfikowanie deklaracja `b` , tak aby suma była mniejsza niż 10: 

```csharp
int b = 3;
```

Typ `dotnet run` ponownie. Ponieważ odpowiedź jest mniejsza niż 10, nic nie jest wydrukowane. **Warunku** jesteś testowania ma wartość false. Nie masz żadnych kod do wykonania, ponieważ został zapisany tylko jedną z możliwych gałęzi dla `if` instrukcji: gałąź prawdy.

> [!TIP]
> Ci poznać platformę C# (lub dowolnego języka programowania), należy podjąć błędów podczas pisania kodu. Kompilator znajdzie i raportów o błędach. Należy dokładnie przejrzeć dane wyjściowe błędów i kod, który wygenerował błąd. Błąd compler zwykle może pomóc w znalezieniu problem. 

W tym przykładzie pierwsze pokazano możliwości `if` i typów logicznych. A *logiczna* jest zmienna, która może mieć jedną z dwóch wartości: `true` lub `false`. C# definiuje specjalny typ `bool` dla zmienne typu Boolean. `if` Instrukcji sprawdza wartość `bool`. Jeśli wartość jest `true`, instrukcji następującej `if` wykonuje. W przeciwnym razie zostanie pominięte. 

Ten proces sprawdzania warunków i wykonywanie instrukcji na podstawie tych warunków jest bardzo zaawansowaną.


## <a name="make-if-and-else-work-together"></a>Upewnij się, jeśli i else współpracują ze sobą

Aby wykonać inny kod w gałęzi true i false, należy utworzyć `else` gałęzi, która wykonuje, gdy warunek ma wartość false. Skorzystaj z tej. Dodaj ostatnie dwa wiersze w poniższym kodzie do Twojej `Main` — metoda (powinna już być pierwsze cztery):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Poniższa instrukcja `else` — słowo kluczowe jest wykonywana tylko wtedy, gdy warunek testowana jest `false`. Łączenie `if` i `else` z logiczną warunki zawiera wszystkie możliwości muszą obsługiwać oba `true` i `false` warunku.

> [!IMPORTANT]
> Wcięcie w obszarze `if` i `else` jest instrukcje dla człowieka czytników.
> W języku C# nie Traktuj wcięcia lub była białym znakiem za istotne. Poniższa instrukcja `if` lub `else` — słowo kluczowe zostanie wykonana na podstawie warunku. Wszystkie przykłady w tym szybki start wykonaj popularną praktyką tworzenia wcięć oparte na przepływie sterowania instrukcji.

Ponieważ wcięcia nie ma znaczenia, należy użyć `{` i `}` wskazująca, kiedy ma więcej niż jedną instrukcję jako część bloku, która wykonuje warunkowo. C# programistów zazwyczaj używają tych nawiasów klamrowych na wszystkich `if` i `else` klauzul. Poniższy przykład jest taki sam jak ten, który został utworzony. Modyfikowanie kodu powyżej, aby dopasować następujący kod:

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> Za pomocą reszty to szybki start, wszystkie przykłady kodu zawiera nawiasy klamrowe, po zaakceptowane rozwiązania.

Można przetestować bardziej skomplikowane warunki. Dodaj następujący kod w Twojej `Main` metody po kodzie napisanych wykonanej do tej pory:

```csharp
    int c = 4;
    if ((a + b + c > 10) && (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not greater than the second");
}
```

`&&` Reprezentuje "i". Oznacza to, że oba warunki muszą być spełnione, można wykonać instrukcji w gałęzi wartość true.  Pokazują powyższe przykłady również może występować wiele instrukcji w każdym gałąź warunkowa, pod warunkiem, umieść je w `{` i `}`.

Można również użyć `||` do reprezentowania "lub". Dodaj następujący kod, po czym napisanych wykonanej do tej pory:

```csharp
if ((a + b + c > 10) || (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not greater than the second");
}
```

Po zakończeniu pierwszym krokiem. Przed rozpoczęciem następnej sekcji przejdziemy bieżącego kodu w oddzielnych metodach. Który ułatwia rozpoczęcie pracy z nowego przykład. Zmień nazwę Twojej `Main` metodę `ExploreIf` i zapisać nową `Main` — metoda, która wywołuje `ExploreIf`. Po zakończeniu, kod powinien wyglądać następująco:

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }            
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

Komentarz wywołanie `ExploreIf()`. Spowoduje to, że dane wyjściowe mniej elementów pracy w tej sekcji:

```csharp
//ExploreIf();
```

`//` Uruchamia **komentarz** w języku C#. Komentarze mogą zawierać dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie wykonują jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

## <a name="use-loops-to-repeat-operations"></a>Powtórz operacji za pomocą pętli

W tej sekcji użyjesz **pętle** powtórzeń instrukcje. Spróbuj ten kod w Twojej `Main` metody:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` Instrukcji sprawdza warunek i wykonuje instrukcji lub bloku instrukcji po `while`. Wciąż sprawdza warunek i wykonywania tych instrukcji, dopóki nie jest spełniony warunek.

W tym przykładzie znajduje się jeden operator new. `++` Po `counter` zmienna jest **przyrostu** operatora. Dodaje do wartości 1 `counter` i zapisuje tę wartość w `counter` zmiennej.

> [!IMPORTANT]
> Upewnij się, że `while` wykonać kod w pętli zmiany stanu na wartość false. W przeciwnym razie utwórz **nieskończoną pętlę** gdzie program nigdy nie kończy. Który nie jest prezentowana w tym przykładzie, ponieważ trzeba wymusić programu, aby zrezygnować z używania **CTRL-C** lub w inny sposób.

`while` Pętli sprawdza warunek przed wykonaniem poniższy kod `while`. `do` ... `while` pętli wykonuje kod najpierw, a następnie sprawdza warunek. Czy podczas pętli przedstawiono w poniższym kodzie:

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

To `do` pętli i wcześniej `while` pętli tworzenia tych samych danych wyjściowych.

## <a name="work-with-the-for-loop"></a>Praca z pętli for

**Dla** pętli jest powszechnie używany w języku C#. Spróbuj wykonać ten kod w wybranej metody Main():

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

Wykonuje ten sam pracę jako `while` pętli i `do` pętli, które zostały już użyte. `for` Instrukcji ma trzy części, które kontrolują sposób działania. 

Pierwsza część **dla inicjatora**: `for index = 0;` deklaruje, że `index` jest zmienna pętli i ustawia swojej wartości początkowej `0`.

Jest środka **warunku**: `index < 10` deklaruje tego `for` pętli kontynuuje wykonywanie tak długo, jak wartość licznika jest mniejsza niż 10.

Ostatnim etapem jest **dla iterator**: `index++` określa sposób modyfikowania zmienna pętli for po wykonaniu następujących bloku `for` instrukcji. Określa ona, że w tym miejscu `index` powinny być zwiększana o 1 zawsze wykonuje bloku.

Wypróbuj te samodzielnie. Spróbuj wykonać następujące czynniki:

- Zmień inicjatora można uruchomić na inną wartość.
- Zmiany tego warunku można zatrzymać na inną wartość.

Gdy wszystko będzie gotowe, Przyjrzyjmy się do zapisu niektóre kod samodzielnie do użycia, zostały rozpoznane.

## <a name="combine-branches-and-loops"></a>Połączenia oddziałów i pętle

Teraz, w tym samouczku `if` instrukcji i konstrukcji pętli w języku C#, zobacz, czy można napisać kod C#, aby znaleźć sumę wszystkich liczb całkowitych od 1 do 20, które są podzielnych przez 3.  Poniżej przedstawiono kilka wskazówek:

- `%` Operatora daje reszta z operacji dzielenia.
- `if` Instrukcja zawiera warunek, aby zobaczyć, jeśli liczba powinna być częścią suma.
- `for` Pętli mogą pomóc w serie kroków należy powtórzyć dla wszystkich liczb od 1 do 20.

Wypróbuj ją samodzielnie. Następnie sprawdź, jak Ty. Należy pobrać 63 dla odpowiedzi. Zobaczysz jednego możliwe odpowiedzi przez [wyświetlanie kompletny kod w serwisie GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).

Zakończono szybki start "gałęzi i pętlę".

Można kontynuować [kolekcji i tablic](arrays-and-collections.md) szybki start w środowisku projektowania.

Użytkownik może dowiedzieć się więcej o tych pojęć w tych tematach:

[Jeśli i else — instrukcja](../language-reference/keywords/if-else.md)   
[While — instrukcja](../language-reference/keywords/while.md)   
[— Instrukcja](../language-reference/keywords/do.md)   
[For — instrukcja](../language-reference/keywords/for.md)   
