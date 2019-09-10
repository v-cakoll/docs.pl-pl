---
title: Cyfry w C# programie — wprowadzenie C# do samouczka
description: Poznaj C# typy liczbowe, ich właściwości i metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 436e8db10f973b468458987150e1312a16103b91
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850692"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipuluj liczby całkowite i zmiennoprzecinkowe w C\#

Ten samouczek zawiera informacje o typach liczbowych w C# sposób interaktywny. Zapiszesz małe ilości kodu, a następnie utworzysz i uruchomisz ten kod. Samouczek zawiera serię lekcji, które eksplorują liczby i operacje matematyczne C#w programie. Te lekcje uczyją się podstaw C# języka.

Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania. Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego na komputerach Mac, komputerze lub Linux. Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.

## <a name="explore-integer-math"></a>Eksploruj liczbę całkowitą

Utwórz katalog o nazwie **Numbers — szybki start**. Upewnij się, że bieżący katalog jest `dotnet new console -n NumbersInCSharp -o .`uruchomiony.

Otwórz **program.cs** w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Uruchom ten kod, wpisując `dotnet run` w oknie wiersza polecenia.

Właśnie zaobserwowano jedną z podstawowych operacji matematycznych z liczbami całkowitymi. Typ reprezentuje liczbę całkowitą, dodatnią lub ujemną. `int` `+` Symbol można użyć do dodania. Inne typowe operacje matematyczne na liczbach całkowitych obejmują:

- `-`na potrzeby odejmowania
- `*`dla mnożenia
- `/`dla dzielenia

Zacznij od eksplorowania tych różnych operacji. Dodaj te wiersze po wierszu, który zapisuje wartość `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Uruchom ten kod, wpisując `dotnet run` w oknie wiersza polecenia.

Możesz również eksperymentować, wykonując wiele operacji matematycznych w tym samym wierszu, jeśli chcesz. Spróbuj `c = a + b - 12 * 17;` na przykład. Mieszanie zmiennych i liczb stałych jest dozwolone.

> [!TIP]
> Podczas eksplorowania C# (lub dowolnego języka programowania) nastąpi pomyłki podczas pisania kodu. **Kompilator** odnajdzie te błędy i zgłosi je do użytkownika. Gdy dane wyjściowe zawierają komunikaty o błędach, dokładnie zapoznaj się z przykładowym kodem i kodem w oknie, aby zobaczyć, co należy naprawić.
> To ćwiczenie pomoże Ci poznać strukturę C# kodu.

Wykonano pierwszy krok. Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę `WorkingWithIntegers` `Main` metody na i Napisz nową metodę, która wywołuje `WorkingWithIntegers`. `Main` Po zakończeniu kod powinien wyglądać następująco:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a>Eksploruj kolejność operacji

Komentarz wywołania do `WorkingWithIntegers()`. Dane wyjściowe będą mniej czytelne podczas pracy w tej sekcji:

```csharp
//WorkingWithIntegers();
```

Uruchamia komentarz w C#. `//` Komentarze są dowolnym tekstem, który chcesz zachować w kodzie źródłowym, ale nie można go wykonać jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

C# Język definiuje kolejność różnych operacji matematycznych z regułami spójnymi z regułami, które zostały uzyskane w postaci matematyki.
Mnożenie i dzielenie mają pierwszeństwo przed dodaniem i odejmowaniem.
Zbadaj, że dodając następujący kod do `Main` metody i wykonując `dotnet run`polecenie:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Dane wyjściowe pokazują, że mnożenie jest wykonywane przed dodaniem.

Można wymusić inną kolejność operacji, dodając nawiasy wokół operacji lub operacji, które chcesz wykonać jako pierwsze. Dodaj następujące wiersze i uruchom ponownie:

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Dowiedz się więcej, łącząc wiele różnych operacji. Dodaj coś tak jak w poniższych wierszach u dołu `Main` metody. Spróbuj `dotnet run` ponownie.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Być może zauważono interesujące zachowanie dla liczb całkowitych. Dzielenie liczb całkowitych zawsze generuje wynik w postaci liczby całkowitej, nawet gdy oczekuje się, że wynik będzie zawierać część dziesiętną lub ułamkową.

Jeśli takie zachowanie nie zostało obserwowane, wypróbuj następujący kod na końcu `Main` metody:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Wpisz `dotnet run` ponownie, aby zobaczyć wyniki.

Zanim zaczniesz, przyjrzyjmy się cały kod w tej sekcji i umieścisz go w nowej metodzie. Wywołaj tę nową `OrderPrecedence`metodę.
Należy się do nich zakończyć w następujący sposób:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a>Eksploruj precyzję całkowitą i limity

Ten ostatni przykład wskazuje, że dzielenie liczby całkowitej obcina wynik.
**Resztę** można uzyskać za pomocą `%` operatora **modulo** , znaku. Wypróbuj następujący kod w `Main` metodzie:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Typ C# Integer różni się od matematycznych liczb całkowitych w jeden inny sposób `int` : typ ma minimalne i maksymalne limity. Dodaj ten kod do `Main` metody, aby zobaczyć te limity:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Jeśli obliczenie generuje wartość, która przekracza te limity, istnieje warunek **niedopełnienia** **lub** przeciążenia. Odpowiedź wydaje się być zawijana z jednego limitu do drugiego. Dodaj te dwa wiersze do `Main` metody, aby zobaczyć przykład:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Zwróć uwagę, że odpowiedź jest bardzo bliska minimalnej (ujemnej) liczbie całkowitej. Jest taka sama jak `min + 2`.
Operacja dodawania **spowodowała przepełnienie** dozwolonych wartości liczb całkowitych.
Odpowiedź to bardzo duża liczba ujemna, ponieważ przepełnienie "zawija" z największej możliwej wartości całkowitej do najmniejszej.

Istnieją inne typy liczbowe z różnymi limitami i dokładnością, których można użyć, `int` gdy typ nie spełnia Twoich potrzeb. Eksplorujmy te informacje dalej.

Teraz Przenieśmy kod napisany w tej sekcji do oddzielnej metody. Nadaj mu `TestLimits`nazwę.

## <a name="work-with-the-double-type"></a>Pracuj z typem Double

Typ `double` liczbowy reprezentuje liczbę zmiennoprzecinkową o podwójnej precyzji. Te warunki mogą być nowe dla Ciebie. Liczba **zmiennoprzecinkowa** jest przydatna do reprezentowania numerów niecałkowitych, które mogą być bardzo duże lub małe. **Podwójne precyzja** oznacza, że te liczby są przechowywane z większą dokładnością niż **Pojedyncza precyzja**. Na nowoczesnych komputerach, bardziej powszechne jest użycie podwójnej precyzji niż pojedyncze numery precyzji.
Eksplorujmy. Dodaj następujący kod i zobacz wynik:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Należy zauważyć, że odpowiedź zawiera część dziesiętną ilorazu. Wypróbuj nieco bardziej skomplikowane wyrażenie z podwajaniem:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Zakres wartości podwójnej jest znacznie większy niż wartości całkowite. Wypróbuj Poniższy kod poniżej tego, co zostało wcześniej zrobione:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Te wartości są drukowane w notacji wykładniczej. Liczba po lewej stronie `E` to mantysę. Liczba po prawej stronie jest wykładnikiem potęgi od 10.

Podobnie jak w przypadku liczb dziesiętnych w zapisie matematycznym, podwaja w C# może mieć błędy zaokrągleń. Wypróbuj następujący kod:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Wiadomo, że `0.3` powtarzanie nie jest dokładnie takie samo `1/3`jak.

***Sprawdz***

Wypróbuj inne obliczenia z dużymi liczbami, małymi liczbami, mnożeniem i dzieleniem przy użyciu `double` typu.  Wypróbuj bardziej skomplikowane obliczenia.

Po pewnym czasie z wezwaniem Zrób wpisany kod i umieść go w nowej metodzie. Nadaj nazwę nowej metodzie `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Pracuj z stałymi typami punktów

Wykorzystano podstawowe typy liczbowe w C#: liczby całkowite i podwaja.  Istnieje jeden inny typ do poznania: `decimal` typ. Typ ma mniejszy zakres, ale większą precyzję niż `double`. `decimal` Termin " **stała** " oznacza, że punkt dziesiętny (lub punkt binarny) nie jest przenoszony. Przyjrzyjmy się:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Zauważ, że zakres jest mniejszy niż `double` typ. Większą precyzję typu dziesiętnego można zobaczyć, próbując wykonać następujący kod:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Sufiks na liczbie wskazuje, że należy `decimal` użyć typu. `M`

Zauważ, że zapis matematyczny przy użyciu typu dziesiętnego ma więcej cyfr po prawej stronie przecinka dziesiętnego.

***Sprawdz***

Teraz, gdy widzisz różne typy liczbowe, napisz kod, który oblicza obszar okręgu, którego promień to 2,50 cm. Należy pamiętać, że obszar okręgu to promień kwadratowy pomnożony przez PI. Jedna Wskazówka: .NET zawiera stałą dla liczby pi, <xref:System.Math.PI?displayProperty=nameWithType> której można użyć dla tej wartości.

Należy uzyskać odpowiedź między 19 a 20.
Odpowiedź możesz sprawdzić, [przeglądając przykładowy kod w usłudze GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)

Wypróbuj inne formuły, jeśli chcesz.

Ukończono Przewodnik Szybki Start dotyczący liczb C#. Możesz kontynuować pracę z [gałęziami i pętle](branches-and-loops-local.md) szybkiego startu w swoim środowisku programistycznym.

Więcej informacji na temat numerów C# można znaleźć w następujących tematach:

- [Typy całkowite](../../language-reference/builtin-types/integral-numeric-types.md)
- [Tabela typów zmiennoprzecinkowych](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Tabela typów wbudowanych](../../language-reference/keywords/built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](../../language-reference/keywords/explicit-numeric-conversions-table.md)
