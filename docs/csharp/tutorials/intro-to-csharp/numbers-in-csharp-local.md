---
title: Liczby w języku C# — wprowadzenie do samouczka języka C#
description: Poznaj język C#, wyszukując typy liczbowe, ich zastosowania, właściwości i metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 3dc2a5afc6321da45351525a632f586cb84bf7fe
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794614"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipuluj liczby całkowite i zmiennoprzecinkowe w C\#

W tym samouczku przedstawiono informacje o typach liczbowych w języku C# interaktywnie. Zapiszesz małe ilości kodu, a następnie utworzysz i uruchomisz ten kod. Samouczek zawiera serię lekcji, które eksplorują liczby i operacje matematyczne w języku C#. Te lekcje umożliwiają poznanie podstaw języka C#.

Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania. Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS. Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.

## <a name="explore-integer-math"></a>Poznawanie matematyki całkowitoliczbowej

Utwórz katalog o nazwie *Numbers — szybki start*. Upewnij się, że bieżący katalog i uruchom następujące polecenie:

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

Otwórz *program.cs* w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Uruchom ten kod, wpisując `dotnet run` w oknie wiersza polecenia.

Zaobserwowano jedną z podstawowych operacji matematycznych z liczbami całkowitymi. `int` Typ reprezentuje liczbę **całkowitą**, zero, dodatnią lub ujemną. Symbol `+` umożliwia dodawanie. Inne typowe operacje matematyczne na liczbach całkowitych obejmują:

- odejmowanie — `-`
- mnożenie — `*`
- dzielenie — `/`

Rozpocznij od wypróbowania różnych operacji. Dodaj te wiersze po wierszu, który zapisuje wartość `c`:

```csharp

// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

Uruchom ten kod, wpisując `dotnet run` w oknie wiersza polecenia.

Możesz również eksperymentować, pisząc wiele operacji matematycznych w tym samym wierszu, jeśli chcesz. Spróbuj `c = a + b - 12 * 17;` na przykład. Mieszanie zmiennych i liczb stałych jest dozwolone.

> [!TIP]
> Podczas nauki języka C# (lub dowolnego języka programowania) będziesz robić błędy przy pisaniu kodu. **Kompilator** znajdzie te błędy i zgłosi je. Gdy dane wyjściowe zawierają komunikaty o błędach, dokładnie zapoznaj się z przykładowym kodem i kodem w oknie, aby zobaczyć, co należy naprawić.
> To ćwiczenie pomoże Ci poznać strukturę kodu w języku C#.

Wykonano pierwszy krok. Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę `Main` metody na `WorkingWithIntegers` i Napisz nową `Main` metodę, która wywołuje `WorkingWithIntegers`. Po zakończeniu kod powinien wyglądać następująco:

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

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
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

## <a name="explore-order-of-operations"></a>Poznawanie kolejności operacji

Komentarz wywołania do `WorkingWithIntegers()`. Dane wyjściowe będą mniej czytelne podczas pracy w tej sekcji:

```csharp
//WorkingWithIntegers();
```

W `//` języku C# jest uruchamiany **komentarz** . Komentarze są dowolnym tekstem, który chcesz zachować w kodzie źródłowym, ale nie można go wykonać jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

Język C# definiuje kolejność wykonywania różnych operacji matematycznych zgodnie z regułami spójnymi z regułami przedstawianymi na lekcjach matematyki.
Mnożenie i dzielenie ma priorytet przed dodawaniem i odejmowaniem.
Zbadaj, że dodając następujący kod do `Main` metody i wykonując `dotnet run`polecenie:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Dane wyjściowe świadczą, że mnożenie jest wykonywane przed dodawaniem.

Można wymusić inną kolejność operacji, dodając nawiasy wokół operacji lub operacji, które chcesz wykonać jako pierwsze. Dodaj następujące wiersze i uruchom ponownie:

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Dowiedz się więcej, łącząc wiele różnych operacji. Dodaj coś tak jak w poniższych wierszach u dołu `Main` metody. Spróbuj ponownie użyć narzędzia `dotnet run`.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Być może zwróciło Twoją uwagę interesujące zachowanie liczb całkowitych. Dzielenie całkowitoliczbowe zawsze daje w wyniku liczbę całkowitą, nawet jeśli oczekiwało się części dziesiętnej lub ułamkowej.

Jeśli takie zachowanie nie zostało obserwowane, wypróbuj następujący kod na końcu `Main` metody:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Wpisz `dotnet run` ponownie, aby zobaczyć wyniki.

Zanim zaczniesz, przyjrzyjmy się cały kod w tej sekcji i umieścisz go w nowej metodzie. Wywołaj tę nową `OrderPrecedence`metodę.
Należy napisać coś w następujący sposób:

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

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
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

            d = (a + b) * c;
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

## <a name="explore-integer-precision-and-limits"></a>Poznawanie precyzji i limitów liczb całkowitych

Ostatni przykład pokazuje, że dzielenie całkowitoliczbowe obcina wynik.
**Resztę** można uzyskać za pomocą operatora **modulo** , `%` znaku. Wypróbuj następujący kod w `Main` metodzie:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Typ całkowitoliczbowy języka C# różni się od matematycznych liczb całkowitych jeszcze tym, że typ `int` ma limit maksimum i minimum. Dodaj ten kod do `Main` metody, aby zobaczyć te limity:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Jeśli obliczenia generują wartość, która przekracza te limity, występuje warunek **niedopełnienia** lub **przepełnienia**. Odpowiedź wydaje się zawijać między limitami. Dodaj te dwa wiersze do `Main` metody, aby zobaczyć przykład:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Zwróć uwagę, że odpowiedź jest bardzo zbliżona do minimalnej (ujemnej) liczby całkowitej. Jej wartość jest równa `min + 2`.
Operacja dodawania spowodowała **przepełnienie** wartości dozwolonych dla liczb całkowitych.
Odpowiedź to bardzo duża liczba ujemna, ponieważ przepełnienie powoduje „zawinięcie” z największej możliwej liczby całkowitej do najmniejszej.

Istnieją inne typy liczbowe z innymi limitami i precyzją, których możesz użyć, jeśli typ `int` nie spełnia wymagań. Zapoznajmy się z innymi typami dalej.

Teraz Przenieśmy kod napisany w tej sekcji do oddzielnej metody. Nadaj jej nazwę `TestLimits`.

## <a name="work-with-the-double-type"></a>Praca z typem double

Typ liczbowy `double` reprezentuje liczbę zmiennoprzecinkową o podwójnej precyzji. Te pojęcia mogą być dla Ciebie nowe. Liczby **zmiennoprzecinkowe** są przydatne do reprezentowania bardzo małych lub bardzo dużych liczb innych niż liczby całkowite. **Podwójna precyzja** jest terminem względnym opisującym liczbę cyfr binarnych używanych do przechowywania wartości. Liczby **podwójnej precyzji** mają dwukrotnie liczbę cyfr binarnych jako **pojedynczą precyzję**. Na nowoczesnych komputerach, bardziej powszechne jest użycie podwójnej precyzji niż pojedyncze numery precyzji. Liczby o **pojedynczej precyzji** są `float` deklarowane za pomocą słowa kluczowego.
Przyjrzyjmy się im. Dodaj następujący kod i zobacz wynik:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

Zwróć uwagę, że odpowiedź obejmuje część dziesiętną ilorazu. Spróbuj nieco bardziej skomplikowanego wyrażenia z liczbami podwójnej precyzji:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

Zakres wartości liczb podwójnej precyzji jest dużo większy niż liczb całkowitych. Wypróbuj Poniższy kod poniżej tego, co zostało wcześniej zrobione:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Wartości zostaną wyświetlone za pomocą notacji naukowej. Liczba po lewej stronie znaku `E` to mantysa. Liczba po jego prawej stronie to wykładnik jako potęga 10.

Podobnie jak w przypadku liczb dziesiętnych w matematyce, przy używaniu liczb podwójnej precyzji w języku C# mogą wystąpić błędy zaokrąglania. Wypróbuj ten kod:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Wiadomo, że `0.3` powtarzające się nie są dokładnie `1/3`takie same, co.

***Wyzwanie***

Wypróbuj inne obliczenia z dużymi liczbami, małymi liczbami, mnożeniem i dzieleniem `double` przy użyciu typu. Spróbuj bardziej skomplikowanych obliczeń.

Po pewnym czasie z wezwaniem Zrób wpisany kod i umieść go w nowej metodzie. Nadaj nazwę nowej metodzie `WorkWithDoubles`.

## <a name="work-with-decimal-types"></a>Pracuj z typami dziesiętnymi

Przedstawiono podstawowe typy danych liczbowych w języku C#: typ całkowitoliczbowy i typ podwójnej precyzji.  Istnieje jeden inny typ do poznania: `decimal` typ. Typ `decimal` ma mniejszy zakres, lecz większą precyzję niż typ `double`. Spójrzmy:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Zwróć uwagę, że zakres jest mniejszy niż w przypadku typu `double`. Większą precyzję typu dziesiętnego możesz zobaczyć, uruchamiając następujący kod:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Sufiks `M` liczb wskazuje, że stałe powinny używać typu `decimal`. W przeciwnym razie kompilator przyjmuje `double` typ.

> [!NOTE]
> Litera `M` została wybrana jako najbardziej wizualnie odrębna litera między słowami `double` kluczowymi i `decimal` .

Zwróć uwagę na to, że operacje matematyczne wykonywane na liczbach typu dziesiętnego mają więcej cyfr po prawej stronie przecinka dziesiętnego.

***Wyzwanie***

Teraz, gdy różne typy liczbowe zostały już przedstawione, napisz kod obliczający pole koła o promieniu 2,5 cm. Pole koła to promień pomnożony przez liczbę pi do kwadratu. Wskazówka: platforma .NET zawiera stałą dla liczby pi — <xref:System.Math.PI?displayProperty=nameWithType> — której możesz użyć. <xref:System.Math.PI?displayProperty=nameWithType>, podobnie jak wszystkie stałe zadeklarowane `System.Math` w przestrzeni nazw, `double` jest wartością. Z tego powodu należy użyć `double` zamiast `decimal` wartości dla tego wyzwania.

Odpowiedź powinna należeć do zakresu 19-20.
Odpowiedź możesz sprawdzić, [przeglądając przykładowy kod zakończono w witrynie GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).

Wypróbuj także inne wzory, jeśli chcesz.

Ukończono Przewodnik Szybki Start dotyczący liczb w języku C#. Możesz kontynuować pracę z [gałęziami i pętle](branches-and-loops-local.md) szybkiego startu w swoim środowisku programistycznym.

Więcej informacji na temat liczb w języku C# można znaleźć w następujących artykułach:

- [Typy liczb całkowitych](../../language-reference/builtin-types/integral-numeric-types.md)
- [Zmiennoprzecinkowe rodzaje wartości numerycznych](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Wbudowane konwersje liczbowe](../../language-reference/builtin-types/numeric-conversions.md)
