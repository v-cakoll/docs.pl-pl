---
title: Rozgałęzienia i pętle — wprowadzenie do samouczka języka C#
description: W tym samouczku dotyczącym gałęzi i pętli można napisać kod w języku C#, aby poznać składnię języka, która obsługuje gałęzie warunkowe, i pętle, aby wielokrotnie wykonywać instrukcje.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d8c10a7462b7c27c5353aee6d957732a8d161015
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135948"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Informacje o logice warunkowej przy użyciu instrukcji Branch i Loop

W tym samouczku przedstawiono sposób pisania kodu, który analizuje zmienne i zmienia ścieżkę wykonywania na podstawie tych zmiennych. Napiszesz kod w języku C# i zobaczysz wyniki kompilacji i uruchomienia. Samouczek zawiera szereg lekcji, które eksplorują gałęzie i konstrukcje zapętlenia w języku C#. Te lekcje umożliwiają poznanie podstaw języka C#.

Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania. Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS. Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.

## <a name="make-decisions-using-the-if-statement"></a>Podejmowanie decyzji przy `if` użyciu instrukcji

Utwórz katalog o nazwie *branchs — samouczek*. Upewnij się, że bieżący katalog i uruchom następujące polecenie:

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

To polecenie powoduje utworzenie nowej aplikacji konsolowej .NET Core w bieżącym katalogu.

Otwórz *program.cs* w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli. Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10". Wydrukowano w konsoli programu.

Zmodyfikuj deklarację zmiennej `b`, tak aby suma była mniejsza niż 10:

```csharp
int b = 3;
```

Wpisz `dotnet run` ponownie. Ponieważ odpowiedź jest mniejsza niż 10, nic nie zostanie wyświetlone. Testowany **warunek** ma wartość false. Nie ma żadnego kodu do wykonania, ponieważ napisano kod tylko dla jednej z możliwych gałęzi instrukcji `if`: wykonywanej dla wartości true.

> [!TIP]
> Podczas nauki języka C# (lub dowolnego języka programowania) będziesz robić błędy przy pisaniu kodu. Kompilator znajdzie i zgłosi błędy. Sprawdź blisko danych wyjściowych błędu i kod, który wygenerował błąd. Błąd kompilatora może zwykle pomóc w znalezieniu problemu.

Ten pierwszy przykład pokazuje moc `if` i typy logiczne. *Wartość logiczna* to zmienna, która może mieć jedną z dwóch wartości: `true` lub `false`. C# definiuje typ specjalny, `bool` dla zmiennych logicznych. Instrukcja `if` umożliwia sprawdzenie wartości typu `bool`. Jeśli wartość to `true`, zostanie wykonana instrukcja następująca po instrukcji `if`. W przeciwnym razie zostanie ona pominięta.

Taki proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków daje ogromne możliwości.

## <a name="make-if-and-else-work-together"></a>Łączenie działania instrukcji if i else

Aby wykonać różny kod w gałęziach dla wartości true i false, należy utworzyć gałąź `else` wykonywaną, jeśli wartość warunku to false. Wypróbuj to. Dodaj ostatnie dwa wiersze w kodzie poniżej do `Main` metody (należy mieć już pierwsze cztery):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Instrukcja po słowie kluczowym `else` jest wykonywana tylko wtedy, gdy testowany warunek ma wartość `false`. Łączenie `if` i `else` z warunkami logicznymi zapewnia wszystko, co jest potrzebne do obsługi zarówno `true` `false` warunku, jak i.

> [!IMPORTANT]
> Wcięcia pod instrukcjami `if` i `else` służą tylko do zwiększenia czytelności.
> Język C# nie traktuje wcięcia ani odstępu jako znaczącego.
> Instrukcja po słowie kluczowym `if` lub `else` zostanie wykonana w zależności od warunku. Wszystkie przykłady w tym samouczku są zgodne ze wspólną metodą tworzenia wcięć wierszy na podstawie przepływu sterowania instrukcji.

Ponieważ wcięcia nie mają znaczenia, należy użyć znaków `{` i `}` do określenia, czy do bloku wykonywanego warunkowo ma należeć więcej niż jedna instrukcja. Programiści języka C# zazwyczaj używają nawiasów klamrowych we wszystkich klauzulach `if` i `else`. Poniższy przykład jest taki sam jak właśnie utworzony. Zmodyfikuj kod powyżej, aby był zgodny z następującym kodem:

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
> W pozostałej części tego samouczka wszystkie przykłady kodu zawierają nawiasy klamrowe, po zastosowaniu zaakceptowanych praktyk.

Możesz przetestować bardziej skomplikowane warunki. Dodaj następujący kod w `Main` metodzie po kodzie, który zapisano do tej pory:

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

`==` Symbol sprawdza *równość*. Użycie `==` odróżnia test pod kątem równości przed przypisaniem `a = 5`.

Znaki `&&` określają warunek „i”. Oznacza to, że instrukcja w gałęzi dla wartości true zostanie wykonana tylko wtedy, gdy oba warunki będą mieć wartość true.  Te przykłady przedstawiają także, że można użyć wielu instrukcji w każdej gałęzi warunkowej, jeśli zostaną umieszczone między znakami `{` i `}`.

Można również użyć `||` do reprezentowania "or". Dodaj następujący kod po wykonaniu tej czynności:

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

`a`Zmodyfikuj wartości, `b`i `c` i przełączenie między `&&` i `||` do Eksploruj. Dowiesz się `&&` , jak działają operatory i `||` .

Wykonano pierwszy krok. Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę `Main` metody na `ExploreIf` i Napisz nową `Main` metodę, która wywołuje `ExploreIf`. Po zakończeniu kod powinien wyglądać następująco:

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

Komentarz wywołania do `ExploreIf()`. Dane wyjściowe będą mniej czytelne podczas pracy w tej sekcji:

```csharp
//ExploreIf();
```

W `//` języku C# jest uruchamiany **komentarz** . Komentarze są dowolnym tekstem, który chcesz zachować w kodzie źródłowym, ale nie można go wykonać jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

## <a name="use-loops-to-repeat-operations"></a>Użycie pętli do powtarzania operacji

W tej sekcji Użyj **pętli** do powtarzania instrukcji. Wypróbuj ten kod w `Main` metodzie:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` Instrukcja sprawdza warunek i wykonuje instrukcję lub blok instrukcji po `while`. Wielokrotnie sprawdza warunek i wykonuje te instrukcje do momentu, gdy warunek nie ma wartości false.

Ten przykład zawiera jeszcze jeden nowy operator. Znaki `++` po zmiennej `counter` oznaczają operator **inkrementacji**. Dodaje 1 do wartości `counter` i zapisuje tę wartość w `counter` zmiennej.

> [!IMPORTANT]
> Upewnij się, że `while` warunek pętli zmieni się na FAŁSZ podczas wykonywania kodu. W przeciwnym razie wystąpi **pętla nieskończona**, czyli wykonywanie programu nigdy się nie skończy. Nie jest to pokazane w tym przykładzie, ponieważ trzeba wymusić zamknięcie programu przy użyciu **klawiszy CTRL-C** lub innych.

Pętla `while` testuje warunek przed wykonaniem kodu po instrukcji `while`. Pętla `do`...`while` najpierw wykonuje kod, a następnie sprawdza warunek. Pętla do while jest pokazana w poniższym kodzie:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Ta `do` pętla i wcześniejsza `while` pętla tworzą te same dane wyjściowe.

## <a name="work-with-the-for-loop"></a>Praca z pętlą for

Pętla **for** jest często używana w języku C#. Wypróbuj ten kod w metodzie Main ():

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Działa on tak samo jak już przedstawione pętle `while` i `do`. Instrukcja `for` składa się z trzech części, które sterują jej pracą.

Pierwsza część to **inicjator for**: `int index = 0;` deklaruje, że `index` jest to zmienna pętli, i ustawia jej wartość początkową `0`na.

Częścią średnią jest **warunek dla**: `index < 10` deklaruje, `for` że ta pętla będzie działać tak długo, jak wartość licznika jest mniejsza niż 10.

Ostatnia część to **iterator**: `index++` określa, jak zmodyfikować zmienną pętli po wykonaniu bloku po `for` instrukcji. Tutaj zdefiniowano, że zmienną `index` należy zwiększyć o 1 po każdym wykonaniu bloku.

Poeksperymentuj samodzielnie z tymi elementami. Wypróbuj poniższe modyfikacje:

- Zmień inicjator, tak aby miał inną wartość początkową.
- Zmień warunek, tak aby zatrzymanie pętli nastąpiło przy innej wartości.

Gdy skończysz, przejdziemy do samodzielnego pisania kodu, gdzie wykorzystasz zdobyte umiejętności.

## <a name="created-nested-loops"></a>Utworzone Pętle zagnieżdżone

Pętla `do` lub `for` może być zagnieżdżona w innej pętli `while`, aby utworzyć macierz przy użyciu kombinacji każdego elementu w pętli zewnętrznej z każdym elementem w wewnętrznej pętli. Zróbmy to, aby utworzyć zestaw par alfanumerycznych do reprezentowania wierszy i kolumn.

Jedna `for` pętla może generować wiersze:

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

Inna pętla może generować kolumny:

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

Można zagnieździć jedną pętlę wewnątrz par:

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

Można zobaczyć, że pętla zewnętrzna przyrostowo rośnie dla każdego pełnego przebiegu pętli wewnętrznej. Wycofaj zagnieżdżanie wierszy i kolumn i zobacz zmiany dla siebie.

## <a name="combine-branches-and-loops"></a>Łączenie gałęzi i pętli

Teraz, gdy znasz już instrukcję `if` i konstrukcje pętli w języku C#, sprawdź, czy potrafisz napisać kod C# obliczający sumę wszystkich liczb całkowitych z zakresu 1-20 podzielnych przez 3.  Oto kilka wskazówek:

- Operator `%` umożliwia obliczenie reszty z operacji dzielenia.
- Instrukcja `if` umożliwia zdefiniowanie warunku określającego, czy liczba powinna być częścią sumy.
- Pętla `for` ułatwia powtórzenie serii kroków dla wszystkich liczb z zakresu 1-20.

Spróbuj napisać kod. Następnie wykonaj go, aby dowiedzieć się, jak Ci poszło. Należy uzyskać 63 na odpowiedź. Możesz wyświetlić jedną możliwą odpowiedź, [wyświetlając kod ukończony w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Samouczek "gałęzie i pętle" został ukończony.

Możesz kontynuować samouczek dotyczący [tablic i kolekcji](arrays-and-collections.md) w Twoim środowisku programistycznym.

Więcej na temat tych pojęć możesz dowiedzieć się w następujących tematach:

- [if i else, instrukcje](../../language-reference/keywords/if-else.md)
- [While, instrukcja](../../language-reference/keywords/while.md)
- [do, instrukcja](../../language-reference/keywords/do.md)
- [For — instrukcja](../../language-reference/keywords/for.md)
