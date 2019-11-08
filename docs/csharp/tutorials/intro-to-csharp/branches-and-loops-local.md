---
title: Gałęzie i pętle — C# wprowadzenie do samouczka
description: W tym samouczku dotyczącej gałęzi i pętli można C# napisać kod, aby poznać składnię języka, która obsługuje gałęzie warunkowe, i pętle do wykonywania instrukcji wielokrotnie.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 44b634e3c2120116ee7fd66770398a6b66c8ed8c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739125"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Informacje o logice warunkowej przy użyciu instrukcji Branch i Loop

W tym samouczku przedstawiono sposób pisania kodu, który analizuje zmienne i zmienia ścieżkę wykonywania na podstawie tych zmiennych. Napiszesz C# kod i zobaczysz wyniki kompilacji i uruchomienia. Samouczek zawiera szereg lekcji, które eksplorują gałęzie i konstrukcje w pętli w C#. Te lekcje uczyją się podstaw C# języka.

Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania. Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS. Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.

## <a name="make-decisions-using-the-if-statement"></a>Podejmowanie decyzji przy użyciu instrukcji `if`

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

Zmodyfikuj deklarację `b`, aby suma była mniejsza niż 10:

```csharp
int b = 3;
```

Wpisz ponownie `dotnet run`. Ponieważ odpowiedź jest mniejsza niż 10, nic nie jest drukowane. Testowany **warunek** ma wartość false. Nie masz żadnego kodu do wykonania, ponieważ Zapisano tylko jedną z możliwych gałęzi dla instrukcji `if`: gałąź true.

> [!TIP]
> Podczas eksplorowania C# (lub dowolnego języka programowania) nastąpi pomyłki podczas pisania kodu. Kompilator znajdzie i zgłosi błędy. Sprawdź blisko danych wyjściowych błędu i kod, który wygenerował błąd. Błąd kompilatora może zwykle pomóc w znalezieniu problemu.

Ten pierwszy przykład pokazuje moc `if` i typów logicznych. *Wartość logiczna* to zmienna, która może mieć jedną z dwóch wartości: `true` lub `false`. C#definiuje typ specjalny, `bool` dla zmiennych logicznych. Instrukcja `if` sprawdza wartość `bool`. Gdy wartość jest `true`, zostanie wykonana instrukcja po `if`. W przeciwnym razie zostanie pominięty.

Ten proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków jest bardzo wydajny.

## <a name="make-if-and-else-work-together"></a>Utwórz, jeśli i else współpracują ze sobą

Aby wykonać inny kod zarówno dla gałęzi prawdy, jak i fałszywych, należy utworzyć gałąź `else`, która jest wykonywana, gdy warunek ma wartość false. Wypróbuj to. Dodaj ostatnie dwa wiersze w poniższym kodzie do metody `Main` (należy mieć już pierwsze cztery):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Instrukcja po słowie kluczowym `else` wykonuje się tylko wtedy, gdy testowany warunek jest `false`. Łączenie `if` i `else` z warunkami logicznymi zapewnia wszystko, co jest potrzebne do obsługi zarówno `true`, jak i `false`.

> [!IMPORTANT]
> Wcięcia pod instrukcjami `if` i `else` są przeznaczone dla czytników ludzkich.
> C# Język nie traktuje wcięcia ani odstępu jako znaczącego.
> Instrukcja po słowie kluczowym `if` lub `else` zostanie wykonana na podstawie warunku. Wszystkie przykłady w tym samouczku są zgodne ze wspólną metodą tworzenia wcięć wierszy na podstawie przepływu sterowania instrukcji.

Ponieważ wcięcia nie są znaczące, należy użyć `{` i `}`, aby wskazać, Kiedy chcesz, aby więcej niż jedna instrukcja była częścią bloku, który jest wykonywany warunkowo. C#programiści zwykle używają tych nawiasów klamrowych we wszystkich klauzulach `if` i `else`. Poniższy przykład jest taki sam jak właśnie utworzony. Zmodyfikuj kod powyżej, aby był zgodny z następującym kodem:

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

Możesz przetestować bardziej skomplikowane warunki. Dodaj następujący kod w metodzie `Main` po kodzie, który zapisano do tej pory:

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

Symbol `==` sprawdza *równość*. Przy użyciu `==` odróżnia test pod kątem równości od przydziału, który został wyświetlony w `a = 5`.

`&&` reprezentuje "i". Oznacza to, że oba warunki muszą mieć wartość true, aby wykonać instrukcję w gałęzi prawdy.  Te przykłady pokazują również, że można mieć wiele instrukcji w każdej gałęzi warunkowej, pod warunkiem, że zostały one ujęte w `{` i `}`.

Można również użyć `||` do reprezentowania "lub". Dodaj następujący kod po wykonaniu tej czynności:

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

Zmodyfikuj wartości `a`, `b` i `c` i przełączenie między `&&` i `||` do eksplorowania. Dowiesz się, jak działają operatory `&&` i `||`.

Wykonano pierwszy krok. Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę metody `Main`, aby `ExploreIf` i napisać nową metodę `Main`, która wywoła `ExploreIf`. Po zakończeniu kod powinien wyglądać następująco:

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

Dodaj komentarz do wywołania `ExploreIf()`. Dane wyjściowe będą mniej czytelne podczas pracy w tej sekcji:

```csharp
//ExploreIf();
```

`//` uruchamia **komentarz** w C#. Komentarze są dowolnym tekstem, który chcesz zachować w kodzie źródłowym, ale nie można go wykonać jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

## <a name="use-loops-to-repeat-operations"></a>Używanie pętli do powtarzania operacji

W tej sekcji Użyj **pętli** do powtarzania instrukcji. Wypróbuj ten kod w metodzie `Main`:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

Instrukcja `while` sprawdza warunek i wykonuje instrukcję lub blok instrukcji po `while`. Wielokrotnie sprawdza warunek i wykonuje te instrukcje do momentu, gdy warunek nie ma wartości false.

W tym przykładzie istnieje jeden inny operator new. `++` po zmiennej `counter` jest operatorem **przyrostu** . Dodaje 1 do wartości `counter` i zapisuje tę wartość w zmiennej `counter`.

> [!IMPORTANT]
> Upewnij się, że warunek pętli `while` zmieni się na FAŁSZ podczas wykonywania kodu. W przeciwnym razie utworzysz **nieskończoną pętlę** , w której program nigdy się nie skończy. Nie jest to pokazane w tym przykładzie, ponieważ trzeba wymusić zamknięcie programu przy użyciu **klawiszy CTRL-C** lub innych.

Pętla `while` sprawdza warunek przed wykonaniem kodu następującego po `while`. Pętla `do`... `while` wykonuje najpierw kod, a następnie sprawdza warunek. Pętla do while jest pokazana w poniższym kodzie:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Ta pętla `do` i wcześniejsza pętla `while` tworzą te same dane wyjściowe.

## <a name="work-with-the-for-loop"></a>Pracuj z pętlą for

Pętla **for** jest często używana w C#. Wypróbuj ten kod w metodzie Main ():

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

To działa tak samo jak w przypadku pętli `while` i pętli `do`, która została już użyta. Instrukcja `for` zawiera trzy części, które kontrolują sposób działania.

Pierwsza część to **inicjator for**: `int index = 0;` deklaruje, że `index` jest zmienną Loop i ustawia jej wartość początkową na `0`.

Częścią średnią jest **warunek dla**: `index < 10` deklaruje, że ta pętla `for` będzie działać tak długo, jak wartość licznika jest mniejsza niż 10.

Ostatnia część to **iterator for**: `index++` określa, jak zmodyfikować zmienną pętli po wykonaniu bloku po instrukcji `for`. W tym miejscu określa, że wartość `index` powinna być zwiększana o 1 przy każdym uruchomieniu bloku.

Wypróbuj je samodzielnie. Spróbuj wykonać następujące czynności:

- Zmień inicjator tak, aby był uruchamiany z inną wartością.
- Zmień warunek, aby zatrzymać z inną wartością.

Gdy skończysz, przyjrzyjmy się, aby samodzielnie napisać kod, aby użyć informacji, które znasz.

## <a name="combine-branches-and-loops"></a>Połącz gałęzie i pętle

Po zapoznaniu się z instrukcją `if` i konstrukcjami pętli w C# języku Sprawdź, czy można napisać C# kod, aby znaleźć sumę wszystkich liczb całkowitych od 1 do 20, które są podzielne przez 3.  Oto kilka wskazówek:

- Operator `%` zapewnia pozostałą część operacji dzielenia.
- Instrukcja `if` zapewnia warunek, aby sprawdzić, czy liczba powinna być częścią sumy.
- Pętla `for` może pomóc powtórzyć serię kroków dla wszystkich liczb od 1 do 20.

Wypróbuj siebie. Następnie sprawdź, jak to się stało. Należy uzyskać 63 na odpowiedź. Możesz wyświetlić jedną możliwą odpowiedź, [wyświetlając kod ukończony w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Samouczek "gałęzie i pętle" został ukończony.

Możesz kontynuować samouczek dotyczący [tablic i kolekcji](arrays-and-collections.md) w Twoim środowisku programistycznym.

Więcej informacji na temat tych pojęć można znaleźć w następujących tematach:

- [Instrukcja if i else](../../language-reference/keywords/if-else.md)
- [While, instrukcja](../../language-reference/keywords/while.md)
- [Do — instrukcja](../../language-reference/keywords/do.md)
- [For — instrukcja](../../language-reference/keywords/for.md)
