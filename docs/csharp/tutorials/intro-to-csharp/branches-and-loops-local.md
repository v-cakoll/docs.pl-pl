---
title: Gałęzie i pętle — C# wprowadzenie do samouczka
description: W tym samouczku dotyczącej gałęzi i pętli można C# napisać kod, aby poznać składnię języka, która obsługuje gałęzie warunkowe, i pętle do wykonywania instrukcji wielokrotnie.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 0da446a71f5d7a7183a8323c470087c8726bc02f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587214"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Informacje o logice warunkowej przy użyciu instrukcji Branch i Loop

W tym samouczku przedstawiono sposób pisania kodu, który analizuje zmienne i zmienia ścieżkę wykonywania na podstawie tych zmiennych. Napiszesz C# kod i zobaczysz wyniki kompilacji i uruchomienia. Samouczek zawiera szereg lekcji, które eksplorują gałęzie i konstrukcje w pętli w C#. Te lekcje uczyją się podstaw C# języka.

Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania. Temat .NET — [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego na komputerach Mac, komputerze lub Linux. Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.

## <a name="make-decisions-using-the-if-statement"></a>Podejmowanie decyzji przy `if` użyciu instrukcji

Utwórz katalog o nazwie **branchs — samouczek**. Upewnij się, że bieżący katalog jest `dotnet new console -n BranchesAndLoops -o .`uruchomiony. To polecenie powoduje utworzenie nowej aplikacji konsolowej .NET Core w bieżącym katalogu.

Otwórz **program.cs** w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli. Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10". Wydrukowano w konsoli programu.

Zmodyfikuj deklarację `b` , tak aby suma była mniejsza niż 10:

```csharp
int b = 3;
```

Wpisz `dotnet run` ponownie. Ponieważ odpowiedź jest mniejsza niż 10, nic nie jest drukowane. Testowany **warunek** ma wartość false. Nie masz żadnego kodu do wykonania, ponieważ Zapisano tylko jedną z możliwych gałęzi `if` instrukcji: wartość true.

> [!TIP]
> Podczas eksplorowania C# (lub dowolnego języka programowania) nastąpi pomyłki podczas pisania kodu. Kompilator znajdzie i zgłosi błędy. Sprawdź blisko danych wyjściowych błędu i kod, który wygenerował błąd. Błąd kompilatora może zwykle pomóc w znalezieniu problemu.

Ten pierwszy przykład pokazuje moc `if` i typy logiczne. *Wartość logiczna* to zmienna, która może mieć jedną z dwóch wartości: `true` lub `false`. C#definiuje typ specjalny, `bool` dla zmiennych logicznych. Instrukcja sprawdza wartość elementu `bool`. `if` Gdy wartość jest `true`, instrukcja `if` po instrukcji wykonywanej. W przeciwnym razie zostanie pominięty.

Ten proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków jest bardzo wydajny.

## <a name="make-if-and-else-work-together"></a>Utwórz, jeśli i else współpracują ze sobą

Aby wykonać inny kod zarówno dla gałęzi prawdy, jak i fałszywych, należy utworzyć `else` gałąź, która jest wykonywana, gdy warunek ma wartość false. Wypróbuj to. Dodaj ostatnie dwa wiersze w kodzie poniżej do `Main` metody (należy mieć już pierwsze cztery):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Instrukcja po `else` słowie kluczowym jest wykonywana tylko wtedy, gdy testowany `false`warunek to. Łączenie `if` `true` `false` i `else` z warunkami logicznymi zapewnia wszystko, co jest potrzebne do obsługi zarówno warunku, jak i.

> [!IMPORTANT]
> Wcięcia pod `if` instrukcjami i `else` są przeznaczone dla czytników ludzkich.
> C# Język nie traktuje wcięcia ani odstępu jako znaczącego.
> Instrukcja po `if` słowie kluczowym or `else` zostanie wykonana na podstawie warunku. Wszystkie przykłady w tym samouczku są zgodne ze wspólną metodą tworzenia wcięć wierszy na podstawie przepływu sterowania instrukcji.

Ponieważ wcięcia nie są znaczące, należy użyć `{` i, `}` aby wskazać, Kiedy chcesz, aby więcej niż jedna instrukcja była częścią bloku, który jest wykonywany warunkowo. C#Programiści zazwyczaj używają tych nawiasów klamrowych `if` we `else` wszystkich klauzulach i. Poniższy przykład jest taki sam jak właśnie utworzony. Zmodyfikuj kod powyżej, aby był zgodny z następującym kodem:

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

Symbol sprawdza równość. `==` Użycie `==` odróżnia test pod kątem równości przed przypisaniem `a = 5`.

`&&` Reprezentuje "i". Oznacza to, że oba warunki muszą mieć wartość true, aby wykonać instrukcję w gałęzi prawdy.  Te przykłady pokazują również, że można mieć wiele instrukcji w każdej gałęzi warunkowej, pod warunkiem, że `{` zostały `}`one ujęte w i.

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

`a`Zmodyfikuj wartości `||` , `b`i `c` i przełączenie między `&&` i do Eksploruj. Dowiesz się `&&` , jak działają operatory i `||` .

Wykonano pierwszy krok. Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę `ExploreIf` `Main` metody na i Napisz nową metodę, która wywołuje `ExploreIf`. `Main` Po zakończeniu kod powinien wyglądać następująco:

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

Uruchamia komentarz w C#. `//` Komentarze są dowolnym tekstem, który chcesz zachować w kodzie źródłowym, ale nie można go wykonać jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

## <a name="use-loops-to-repeat-operations"></a>Używanie pętli do powtarzania operacji

W tej sekcji Użyj **pętli** do powtarzania instrukcji. Wypróbuj ten kod w `Main` metodzie:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

Instrukcja sprawdza warunek i wykonuje instrukcję lub blok instrukcji `while`po. `while` Wielokrotnie sprawdza warunek i wykonuje te instrukcje do momentu, gdy warunek nie ma wartości false.

W tym przykładzie istnieje jeden inny operator new. Gdy zmienna jest operatorem przyrostu. `++` `counter` Dodaje 1 do wartości `counter` i zapisuje tę wartość `counter` w zmiennej.

> [!IMPORTANT]
> Upewnij się, że `while` warunek pętli zmieni się na FAŁSZ podczas wykonywania kodu. W przeciwnym razie utworzysz **nieskończoną pętlę** , w której program nigdy się nie skończy. Nie jest to pokazane w tym przykładzie, ponieważ trzeba wymusić zamknięcie programu przy użyciu **klawiszy CTRL-C** lub innych.

Pętla sprawdza warunek przed wykonaniem kodu `while`po. `while` `do` ... `while` pętla wykonuje najpierw kod, a następnie sprawdza warunek. Pętla do while jest pokazana w poniższym kodzie:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Ta `do` pętla i wcześniejsza `while` pętla tworzą te same dane wyjściowe.

## <a name="work-with-the-for-loop"></a>Pracuj z pętlą for

Pętla **for** jest często używana w C#. Wypróbuj ten kod w metodzie Main ():

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Działa to tak samo jak w `while` przypadku pętli `do` i pętli, która została już użyta. `for` Instrukcja ma trzy części, które kontrolują sposób działania.

Pierwsza część to **inicjator for**: `int index = 0;` deklaruje, że `index` jest to zmienna pętli, i ustawia jej wartość początkową `0`na.

Częścią średnią jest **warunek dla**: `index < 10` deklaruje, `for` że ta pętla będzie działać tak długo, jak wartość licznika jest mniejsza niż 10.

Ostatnia część to **iterator**: `index++` określa, jak zmodyfikować zmienną pętli po wykonaniu bloku `for` po instrukcji. W tym miejscu określa, `index` że powinny być zwiększane o 1 za każdym razem, gdy blok jest wykonywany.

Wypróbuj je samodzielnie. Spróbuj wykonać następujące czynności:

- Zmień inicjator tak, aby był uruchamiany z inną wartością.
- Zmień warunek, aby zatrzymać z inną wartością.

Gdy skończysz, przyjrzyjmy się, aby samodzielnie napisać kod, aby użyć informacji, które znasz.

## <a name="combine-branches-and-loops"></a>Połącz gałęzie i pętle

Po zapoznaniu się z `if` instrukcją i konstrukcjami pętli w C# języku Sprawdź, czy można napisać C# kod, aby znaleźć sumę wszystkich liczb całkowitych od 1 do 20, które są podzielne przez 3.  Oto kilka wskazówek:

- `%` Operator podaje pozostałą część operacji dzielenia.
- `if` Instrukcja zapewnia warunek, aby sprawdzić, czy liczba powinna być częścią sumy.
- `for` Pętla może pomóc powtórzyć serię kroków dla wszystkich liczb od 1 do 20.

Wypróbuj siebie. Następnie sprawdź, jak to się stało. Należy uzyskać 63 na odpowiedź. Możesz wyświetlić jedną możliwą odpowiedź, [wyświetlając kod ukończony w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Samouczek "gałęzie i pętle" został ukończony.

Możesz kontynuować samouczek dotyczący [tablic i kolekcji](arrays-and-collections.md) w Twoim środowisku programistycznym.

Więcej informacji na temat tych pojęć można znaleźć w następujących tematach:

- [Instrukcja if i else](../../language-reference/keywords/if-else.md)
- [While, instrukcja](../../language-reference/keywords/while.md)
- [Do — instrukcja](../../language-reference/keywords/do.md)
- [For — instrukcja](../../language-reference/keywords/for.md)
