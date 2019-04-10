---
title: Gałęzie i pętle — wprowadzenie do C# samouczek
description: W tym samouczku omawiającym gałęzie i pętle zapisu C# kodu, aby poznać składnię języka, obsługującego warunkowych gałęzi i pętli, aby wykonać instrukcje wielokrotnie.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 4a116ae5294915770dec742c147cf2ba1bf6e284
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427256"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Dowiedz się, logikę warunkową instrukcji gałęzi i pętli

Ten samouczek omawia sposób pisanie kodu badającego zmienne i wybierającego ścieżkę wykonania na podstawie tych zmiennych. Możesz pisać kod w języku C# i zobaczyć wyniki kompilowania i uruchamiania ich. Samouczek zawiera serię lekcji przedstawiających konstrukcje w gałęzi i pętli C#. Te lekcje umożliwiają poznanie podstaw języka C#.

W tym samouczku oczekuje, że będziesz mieć maszyny, których można użyć do tworzenia aplikacji. Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux. Krótkie omówienie poleceń użyjesz znajduje się w [zapoznanie się z narzędziami programistycznymi](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.

## <a name="make-decisions-using-the-if-statement"></a>Podejmowanie decyzji za pomocą `if` — instrukcja

Utwórz katalog o nazwie **samouczek dotyczący gałęzi**. Upewnij, że bieżącego katalogu i uruchom `dotnet new console -n BranchesAndLoops -o .`. To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.

Otwórz **Program.cs** w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli. Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10". drukowane do konsoli.

Zmodyfikuj deklarację zmiennej `b` , tak aby suma była mniejsza niż 10:

```csharp
int b = 3;
```

Typ `dotnet run` ponownie. Ponieważ odpowiedź jest mniejsza niż 10, nic nie zostanie wyświetlone. **Warunek** jesteś testowania ma wartość false. Nie masz żadnego kodu do wykonania, ponieważ zostały zapisane wyłącznie jedną z możliwych gałęzi dla `if` instrukcji: gałęzi dla wartości true.

> [!TIP]
> Gdy eksplorujesz C# (lub dowolnego języka programowania), będziesz robić błędy podczas pisania kodu. Kompilator znajdzie i raportowania błędów. Przyjrzyj się blisko dane wyjściowe błędu i kod, który wygenerował błąd. Błąd kompilatora zazwyczaj mogą pomóc w znalezieniu problem.

Pierwszy przykład przedstawia możliwości `if` i typów logicznych. A *logiczna* jest zmienną, która może mieć jedną z dwóch wartości: `true` lub `false`. C#definiuje specjalny typ `bool` dla zmiennych logicznych. `if` Instrukcji sprawdza wartość `bool`. Jeśli wartość to `true`, instrukcji następującej `if` wykonuje. W przeciwnym razie zostanie ona pominięta.

Ten proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków są ogromne.

## <a name="make-if-and-else-work-together"></a>Upewnij się, jeśli i inne współpracują ze sobą

Aby wykonać różny kod w gałęzie true i false, należy utworzyć `else` gałęzi, która wykonuje, gdy warunek jest fałszywy. Wypróbuj to. Dodaj ostatnie dwa wiersze w poniższym kodzie, aby Twoje `Main` — metoda (konto powinno mieć już pierwsze cztery):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Instrukcja po słowie `else` — słowo kluczowe jest wykonywany tylko wtedy, gdy testowany warunek jest `false`. Łącząc `if` i `else` atrybut typu wartość logiczna warunki zapewnia wszystkich możliwości muszą obsługiwać oba modele `true` i `false` warunku.

> [!IMPORTANT]
> Wcięcia pod `if` i `else` instrukcji jest czytelności.
> W języku C# nie mają wcięcia ani białe miejsca znaczenia.
> Instrukcja po słowie `if` lub `else` — słowo kluczowe zostanie wykonana w zależności od warunku. Wszystkie przykłady w tym samouczku wykonaj jest stosowana powszechna praktyka wcięć odpowiadających przepływowi sterowania instrukcji.

Ponieważ wcięcia nie ma znaczenia, należy użyć `{` i `}` wskazać, kiedy ma więcej niż jedna instrukcja jako część bloku wykonywanego warunkowo. Programiści języka C# zazwyczaj używają nawiasów klamrowych we wszystkich `if` i `else` klauzul. Poniższy przykład jest taka sama jak właśnie utworzony. Zmodyfikuj kod powyżej, aby dopasować następujący kod:

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
> Za pomocą pozostałej części tego samouczka, wszystkie przykłady kodu zawierają nawiasy klamrowe, zgodnie z przyjętą.

Możesz przetestować bardziej skomplikowanych warunków. Dodaj następujący kod w swojej `Main` metoda po kodzie napisanych do tej pory:

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

`==` Symboli testów dla *równości*. Za pomocą `==` wyróżnia testowanie równości z przypisania, które zostały użyte w `a = 5`.

`&&` Reprezentuje "i". Oznacza to, że oba warunki muszą być spełnione, aby wykonać tę instrukcję w gałęzi dla wartości true.  Te przykłady przedstawiają także, może mieć wielu instrukcji w każdej gałęzi warunkowej, pod warunkiem, należy ująć je w `{` i `}`.

Można również użyć `||` do reprezentowania "or". Dodaj następujący kod, po czym napisanych do tej pory:

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

Zmodyfikuj wartości `a`, `b`, i `c` i przełączać się między `&&` i `||` do zbadania. Uzyskasz więcej zrozumieć sposób, w jaki `&&` i `||` pracy operatorów.

Pierwszym krokiem zostały ukończone. Przed rozpoczęciem następnej sekcji, Przejdźmy bieżącego kodu w oddzielnych metodach. Który sprawia, że łatwiej rozpocząć pracę z nową przykładową. Zmiana nazwy Twojego `Main` metodę, aby `ExploreIf` i zapisywać nowy `Main` metodę, która wywołuje `ExploreIf`. Po zakończeniu, kod powinien wyglądać następująco:

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

Komentarz wywołanie `ExploreIf()`. Spowoduje to, że dane wyjściowe, które mniej "zatłoczony" podczas pracy w tej sekcji:

```csharp
//ExploreIf();
```

`//` Uruchamia **komentarz** w C#. Komentarze są dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie jest wykonywane jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

## <a name="use-loops-to-repeat-operations"></a>Użycie pętli do powtarzania operacji

W tej sekcji użyjesz **pętli** do powtarzania instrukcji. Wypróbuj ten kod w swojej `Main` metody:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` Instrukcji sprawdza warunek i wykonuje instrukcję lub blok instrukcji po `while`. Wielokrotnie sprawdza warunek i wykonywanie instrukcji, dopóki warunek jest fałszywy.

W tym przykładzie jest jeszcze jeden nowy operator. `++` Po `counter` zmienna jest **przyrostu** operatora. Dodaje do wartości 1 `counter` i zapisuje wynikową wartość w `counter` zmiennej.

> [!IMPORTANT]
> Upewnij się, że `while` pętli warunek zmiany na wartość false podczas wykonywania kodu. W przeciwnym razie utwórz **Pętla nieskończona** gdzie programu nigdy się nie skończy. Który nie jest pokazana w tym przykładzie, ponieważ trzeba wymusić program, aby zrezygnować z używania **CTRL-C** lub w inny sposób.

`while` Pętli testuje warunek przed wykonaniem kodu po `while`. `do` ... `while` pętli najpierw wykonuje kod, a następnie sprawdza warunek. Czy podczas pętli jest wyświetlany w poniższym kodzie:

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

To `do` pętli i wcześniej `while` pętli generuje ten sam wynik.

## <a name="work-with-the-for-loop"></a>Praca z pętli for

**Dla** pętli jest często używana w C#. Wypróbuj ten kod w metodzie Main():

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

To działa ten sam jako `while` pętli i `do` pętli został już użyty. `for` Instrukcja składa się z trzech części, które sterują jej pracą.

Pierwsza część to **dla inicjatora**: `int index = 0;` oświadcza, że `index` jako zmienną pętli i ustawia jej wartość początkową `0`.

Środkowa część to **warunku**: `index < 10` oświadcza, że `for` pętli kontynuuje wykonywanie dopóki wartość licznika jest mniejsza niż 10.

Ostatnia część to **dla iteratora**: `index++` określa sposób modyfikowana zmienna pętli po wykonaniu bloku występującego `for` instrukcji. Określa ona, że w tym miejscu `index` należy zwiększyć o 1 po każdym wykonaniu bloku.

Wypróbuj te samodzielnie. Wypróbuj następujące czynniki:

- Zmień inicjator, tak aby można było uruchomić na inną wartość.
- Zmień warunek, którego chcesz zatrzymać miał inną wartość.

Gdy skończysz, przejdziemy pisania kodu, co wykorzystasz zdobyte umiejętności do samodzielnego.

## <a name="combine-branches-and-loops"></a>Łączenie gałęzi i pętli

Teraz, gdy wiesz `if` instrukcji i konstrukcje pętli w języku C#, zobacz, jeśli można napisać kod C# obliczający sumę wszystkich liczb całkowitych od 1 do 20 podzielnych przez 3.  Poniżej przedstawiono kilka wskazówek:

- `%` Operator umożliwia obliczenie reszty z operacji dzielenia.
- `if` Instrukcji zapewnia warunku określającego, jeśli liczba powinna być częścią sumy.
- `for` Pętli ułatwia powtórzenie serii kroków dla wszystkich liczb od 1 do 20.

Wypróbuj ją samodzielnie. Sprawdź, jak Ci poszło. Odpowiedź powinna wynosić 63. Możesz zobaczyć jeden możliwa odpowiedź przez [wyświetlanie kompletny kod w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Pomyślnie ukończono samouczek "gałęzi i pętli".

Możesz kontynuować [tablice i kolekcje](arrays-and-collections.md) samouczków w środowisku projektowym.

Możesz dowiedzieć się więcej na temat tych pojęć w następujących tematach:

- [Jeśli i else, instrukcja](../../language-reference/keywords/if-else.md)
- [While — Instrukcja](../../language-reference/keywords/while.md)
- [Do — Instrukcja](../../language-reference/keywords/do.md)
- [For — Instrukcja](../../language-reference/keywords/for.md)
