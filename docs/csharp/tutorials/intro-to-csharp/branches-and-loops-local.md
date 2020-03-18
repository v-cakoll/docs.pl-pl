---
title: Gałęzie i pętle — wprowadzenie do samouczka języka C#
description: W tym samouczku o gałęziach i pętlach piszesz kod Języka C#, aby eksplorować składnię języka, która obsługuje gałęzie warunkowe i pętle do wielokrotnego wykonywania instrukcji.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 44b634e3c2120116ee7fd66770398a6b66c8ed8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73739125"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Poznaj logikę warunkową za pomocą instrukcji gałęzi i pętli

W tym samouczku nauczy cię, jak napisać kod, który sprawdza zmienne i zmienia ścieżkę wykonywania na podstawie tych zmiennych. Piszesz kod C# i zobaczyć wyniki kompilacji i uruchamiania go. Samouczek zawiera serię lekcji, które eksplorują rozgałęzienia i pętli konstrukcje w języku C#. Te lekcje umożliwiają poznanie podstaw języka C#.

Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia. Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS. Szybki przegląd poleceń, których będziesz używać, znajduje się w [obszarze Zaznajomij się z narzędziami programistycznymi](local-environment.md) z łączami do szczegółowych informacji.

## <a name="make-decisions-using-the-if-statement"></a>Podejmuj `if` decyzje za pomocą instrukcji

Utwórz katalog o nazwie *branches-tutorial*. Upewnij się, że bieżący katalog i uruchom następujące polecenie:

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.

Otwórz *Program.cs* w ulubionym edytorze `Console.WriteLine("Hello World!");` i zastąp wiersz następującym kodem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Wypróbuj `dotnet run` ten kod, wpisując w oknie konsoli. Powinien zostać wyświetlony komunikat "Odpowiedź jest większa niż 10". wydrukowane na konsoli.

Zmodyfikuj deklarację zmiennej `b`, tak aby suma była mniejsza niż 10:

```csharp
int b = 3;
```

Wpisz `dotnet run` ponownie. Ponieważ odpowiedź jest mniejsza niż 10, nic nie zostanie wyświetlone. Testowany **warunek** ma wartość false. Nie ma żadnego kodu do wykonania, ponieważ napisano kod tylko dla jednej z możliwych gałęzi instrukcji `if`: wykonywanej dla wartości true.

> [!TIP]
> Podczas nauki języka C# (lub dowolnego języka programowania) będziesz robić błędy przy pisaniu kodu. Kompilator znajdzie i zgłosi błędy. Przyjrzyj się uważnie danych wyjściowych błędu i kod, który wygenerował błąd. Błąd kompilatora zazwyczaj może pomóc w znalezieniu problemu.

W tym pierwszym przykładzie `if` przedstawiono moc i typy logiczne. *Wartość logiczna* jest zmienną, która może `true` `false`mieć jedną z dwóch wartości: lub . C# definiuje typ specjalny `bool` dla zmiennych logicznych. Instrukcja `if` umożliwia sprawdzenie wartości typu `bool`. Jeśli wartość to `true`, zostanie wykonana instrukcja następująca po instrukcji `if`. W przeciwnym razie zostanie ona pominięta.

Taki proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków daje ogromne możliwości.

## <a name="make-if-and-else-work-together"></a>Łączenie działania instrukcji if i else

Aby wykonać różny kod w gałęziach dla wartości true i false, należy utworzyć gałąź `else` wykonywaną, jeśli wartość warunku to false. Spróbuj tego. Dodaj dwa ostatnie wiersze w `Main` kodzie poniżej do metody (powinieneś mieć już pierwsze cztery):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Instrukcja po słowie kluczowym `else` jest wykonywana tylko wtedy, gdy testowany warunek ma wartość `false`. Połączenie `if` i `else` warunki logiczne zapewnia całą moc potrzebną `true` do `false` obsługi zarówno a, jak i warunek.

> [!IMPORTANT]
> Wcięcia pod instrukcjami `if` i `else` służą tylko do zwiększenia czytelności.
> Język Języka C# nie traktuje wcięcia lub biały znak jako znaczące.
> Instrukcja po słowie kluczowym `if` lub `else` zostanie wykonana w zależności od warunku. Wszystkie przykłady w tym samouczku postępuj zgodnie z powszechną praktyką wcięcia wierszy na podstawie przepływu sterowania instrukcji.

Ponieważ wcięcia nie mają znaczenia, należy użyć znaków `{` i `}` do określenia, czy do bloku wykonywanego warunkowo ma należeć więcej niż jedna instrukcja. Programiści języka C# zazwyczaj używają nawiasów klamrowych we wszystkich klauzulach `if` i `else`. Poniższy przykład jest taki sam jak ten, który właśnie został utworzony. Zmodyfikuj powyższy kod, aby dopasować go do następującego kodu:

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
> W pozostałej części tego samouczka przykłady kodu zawierają nawiasy klamrowe, zgodnie z przyjętymi praktykami.

Możesz przetestować bardziej skomplikowane warunki. Dodaj następujący kod `Main` w metodzie po kodzie, który został napisany do tej pory:

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

Symbol `==` testuje *na rzecz równości*. Za `==` pomocą odróżnia test równości od przypisania, który został odnotowywana w . `a = 5`

Znaki `&&` określają warunek „i”. Oznacza to, że instrukcja w gałęzi dla wartości true zostanie wykonana tylko wtedy, gdy oba warunki będą mieć wartość true.  Te przykłady przedstawiają także, że można użyć wielu instrukcji w każdej gałęzi warunkowej, jeśli zostaną umieszczone między znakami `{` i `}`.

Można również `||` użyć do reprezentowania "lub". Dodaj następujący kod po tym, co do tej pory napisałeś:

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

`a`Zmodyfikuj `b`wartości `c` , `&&` i `||` przełączaj się między i do eksplorowania. Zyskasz więcej zrozumienia, `&&` `||` jak działają operatorzy i operatorzy.

Ukończono pierwszy krok. Przed rozpoczęciem następnej sekcji przenieśmy bieżący kod do osobnej metody. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę `Main` metody `ExploreIf` i napisz `Main` nową `ExploreIf`metodę, która wywołuje . Po zakończeniu kod powinien wyglądać tak:

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

Skomentuj wezwanie `ExploreIf()`do . To sprawi, że dane wyjściowe mniej zaśmiecone podczas pracy w tej sekcji:

```csharp
//ExploreIf();
```

Rozpoczyna `//` **komentarz** w języku C#. Komentarze to dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie są wykonywane jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

## <a name="use-loops-to-repeat-operations"></a>Użycie pętli do powtarzania operacji

W tej sekcji używasz **pętli** do powtarzania instrukcji. Wypróbuj `Main` ten kod w swojej metodzie:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

Instrukcja `while` sprawdza warunek i wykonuje instrukcję `while`lub blok instrukcji po . Wielokrotnie sprawdza warunek i wykonywanie tych instrukcji, dopóki warunek jest false.

Ten przykład zawiera jeszcze jeden nowy operator. Znaki `++` po zmiennej `counter` oznaczają operator **inkrementacji**. Dodaje 1 do wartości `counter` i przechowuje tę `counter` wartość w zmiennej.

> [!IMPORTANT]
> Upewnij się, `while` że warunek pętli zmienia się na false podczas wykonywania kodu. W przeciwnym razie wystąpi **pętla nieskończona**, czyli wykonywanie programu nigdy się nie skończy. Nie jest to wykazane w tym przykładzie, ponieważ musisz wymusić zamknięcie programu przy użyciu **klawisza CTRL-C** lub innych środków.

Pętla `while` testuje warunek przed wykonaniem kodu po instrukcji `while`. Pętla `do`...`while` najpierw wykonuje kod, a następnie sprawdza warunek. Pętla do while jest pokazana w następującym kodzie:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Ta `do` pętla i `while` wcześniejsza pętla wytwarzają to samo wyjście.

## <a name="work-with-the-for-loop"></a>Praca z pętlą for

For **for** pętli jest powszechnie używany w Języku C#. Wypróbuj ten kod w metodzie Main():

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Działa on tak samo jak już przedstawione pętle `while` i `do`. Instrukcja `for` składa się z trzech części, które sterują jej pracą.

Pierwsza część jest **dla inicjatora:** `int index = 0;` deklaruje, że `index` jest zmienna pętli i ustawia jego wartość początkową . `0`

Środkowa część jest **warunek for:** `index < 10` deklaruje, że ta `for` pętla kontynuuje wykonywanie tak długo, jak wartość licznika jest mniejsza niż 10.

Ostatnia część jest **dla iterator:** `index++` określa sposób modyfikowania zmiennej pętli `for` po wykonaniu bloku po instrukcji. Tutaj zdefiniowano, że zmienną `index` należy zwiększyć o 1 po każdym wykonaniu bloku.

Poeksperymentuj samodzielnie z tymi elementami. Wypróbuj poniższe modyfikacje:

- Zmień inicjator, tak aby miał inną wartość początkową.
- Zmień warunek, tak aby zatrzymanie pętli nastąpiło przy innej wartości.

Gdy skończysz, przejdziemy do samodzielnego pisania kodu, gdzie wykorzystasz zdobyte umiejętności.

## <a name="combine-branches-and-loops"></a>Łączenie gałęzi i pętli

Teraz, gdy znasz już instrukcję `if` i konstrukcje pętli w języku C#, sprawdź, czy potrafisz napisać kod C# obliczający sumę wszystkich liczb całkowitych z zakresu 1-20 podzielnych przez 3.  Oto kilka wskazówek:

- Operator `%` umożliwia obliczenie reszty z operacji dzielenia.
- Instrukcja `if` umożliwia zdefiniowanie warunku określającego, czy liczba powinna być częścią sumy.
- Pętla `for` ułatwia powtórzenie serii kroków dla wszystkich liczb z zakresu 1-20.

Spróbuj napisać kod. Następnie wykonaj go, aby dowiedzieć się, jak Ci poszło. Powinieneś dostać 63 za odpowiedź. Możesz zobaczyć jedną możliwą [odpowiedź, wyświetlając wypełniony kod w witrynie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Ukończono samouczek "gałęzie i pętle".

Można kontynuować [samouczek Tablice i kolekcje](arrays-and-collections.md) we własnym środowisku programistycznym.

Więcej na temat tych pojęć możesz dowiedzieć się w następujących tematach:

- [if i else, instrukcje](../../language-reference/keywords/if-else.md)
- [Podczas gdy oświadczenie](../../language-reference/keywords/while.md)
- [do, instrukcja](../../language-reference/keywords/do.md)
- [Dla instrukcji](../../language-reference/keywords/for.md)
