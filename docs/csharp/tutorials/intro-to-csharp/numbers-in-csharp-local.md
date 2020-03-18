---
title: Liczby w języku C# — wprowadzenie do samouczka języka C#
description: Dowiedz się C# eksplorując typy liczbowe, ich właściwości i metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 7e9af4b3b859f74d7e92ff10b3964ddd59d2473b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156548"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipulowanie liczbami integralnymi i zmiennoprzecinkowymi w C\#

Ten samouczek uczy o typach liczbowych w języku C# interaktywnie. Napiszesz niewielkie ilości kodu, a następnie skompiluj i uruchomisz ten kod. Samouczek zawiera serię lekcji, które eksplorują liczby i operacje matematyczne w języku C#. Te lekcje umożliwiają poznanie podstaw języka C#.

Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia. Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS. Szybki przegląd poleceń, których będziesz używać, znajduje się w [obszarze Zaznajomij się z narzędziami programistycznymi](local-environment.md) z łączami do szczegółowych informacji.

## <a name="explore-integer-math"></a>Poznawanie matematyki całkowitoliczbowej

Utwórz katalog o nazwie *numery szybki start*. Upewnij się, że bieżący katalog i uruchom następujące polecenie:

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

Otwórz *Program.cs* w ulubionym edytorze `Console.WriteLine("Hello World!");` i zastąp wiersz następującymi elementami:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Uruchom ten kod, `dotnet run` wpisując w oknie polecenia.

Właśnie została przedstawiona jedna z podstawowych operacji matematycznych na liczbach całkowitych. Typ `int` reprezentuje **liczbę całkowitą**, zero, dodatnią lub ujemną liczbę całkowitą. Symbol `+` umożliwia dodawanie. Inne typowe operacje matematyczne na liczbach całkowitych obejmują:

- odejmowanie — `-`
- mnożenie — `*`
- dzielenie — `/`

Rozpocznij od wypróbowania różnych operacji. Dodaj te wiersze po wierszu, `c`który zapisuje wartość:

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

Uruchom ten kod, `dotnet run` wpisując w oknie polecenia.

Jeśli chcesz, możesz także eksperymentować, wykonując wiele operacji matematycznych w jednym wierszu. Spróbuj `c = a + b - 12 * 17;` na przykład. Mieszanie zmiennych i stałych liczb jest dozwolone.

> [!TIP]
> Podczas nauki języka C# (lub dowolnego języka programowania) będziesz robić błędy przy pisaniu kodu. **Kompilator** znajdzie te błędy i zgłosi je. Gdy dane wyjściowe zawierają komunikaty o błędach, przyjrzyj się uważnie przykładowemu kodowi i kodowi w oknie, aby zobaczyć, co naprawić.
> To ćwiczenie pomoże Ci poznać strukturę kodu w języku C#.

Ukończono pierwszy krok. Przed rozpoczęciem następnej sekcji przenieśmy bieżący kod do osobnej metody. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę `Main` metody `WorkingWithIntegers` i napisz `Main` nową `WorkingWithIntegers`metodę, która wywołuje . Po zakończeniu kod powinien wyglądać tak:

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

Skomentuj wezwanie `WorkingWithIntegers()`do . To sprawi, że dane wyjściowe mniej zaśmiecone podczas pracy w tej sekcji:

```csharp
//WorkingWithIntegers();
```

Rozpoczyna `//` **komentarz** w języku C#. Komentarze to dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie są wykonywane jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

Język C# definiuje kolejność wykonywania różnych operacji matematycznych zgodnie z regułami spójnymi z regułami przedstawianymi na lekcjach matematyki.
Mnożenie i dzielenie ma priorytet przed dodawaniem i odejmowaniem.
Eksploruj to, `Main` dodając następujący `dotnet run`kod do metody i wykonując:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Dane wyjściowe świadczą, że mnożenie jest wykonywane przed dodawaniem.

Można wymusić inną kolejność operacji, dodając nawiasy wokół operacji lub operacji, które mają być wykonywane jako pierwsze. Dodaj następujące wiersze i uruchom ponownie:

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Dowiedz się więcej, łącząc wiele różnych operacji. Dodaj coś takiego jak następujące wiersze na dole metody. `Main` Spróbuj ponownie użyć narzędzia `dotnet run`.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Być może zwróciło Twoją uwagę interesujące zachowanie liczb całkowitych. Dzielenie całkowitoliczbowe zawsze daje w wyniku liczbę całkowitą, nawet jeśli oczekiwało się części dziesiętnej lub ułamkowej.

Jeśli nie widzieliście tego zachowania, spróbuj wykonać następujący `Main` kod na końcu metody:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Wpisz `dotnet run` ponownie, aby zobaczyć wyniki.

Przed przejściem dalej, weźmy cały kod, który został napisany w tej sekcji i umieścić go w nowej metodzie. Wywołaj tę `OrderPrecedence`nową metodę .
Powinieneś skończyć z czymś takim:

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
**Resztę** można uzyskać za pomocą operatora **modulo,** `%` znak. Wypróbuj `Main` następujący kod w metodzie:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Typ całkowitoliczbowy języka C# różni się od matematycznych liczb całkowitych jeszcze tym, że typ `int` ma limit maksimum i minimum. Dodaj ten kod `Main` do metody, aby zobaczyć te limity:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Jeśli obliczenia generują wartość, która przekracza te limity, występuje warunek **niedopełnienia** lub **przepełnienia**. Odpowiedź wydaje się zawijać między limitami. Dodaj te dwa `Main` wiersze do metody, aby zobaczyć przykład:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Zwróć uwagę, że odpowiedź jest bardzo zbliżona do minimalnej (ujemnej) liczby całkowitej. Jej wartość jest równa `min + 2`.
Operacja dodawania spowodowała **przepełnienie** wartości dozwolonych dla liczb całkowitych.
Odpowiedź to bardzo duża liczba ujemna, ponieważ przepełnienie powoduje „zawinięcie” z największej możliwej liczby całkowitej do najmniejszej.

Istnieją inne typy liczbowe z innymi limitami i precyzją, których możesz użyć, jeśli typ `int` nie spełnia wymagań. Zapoznajmy się z nimi w następnej kolejności.

Po raz kolejny przenieśmy kod, który napisałeś w tej sekcji, do osobnej metody. Nadaj jej nazwę `TestLimits`.

## <a name="work-with-the-double-type"></a>Praca z typem double

Typ liczbowy `double` reprezentuje liczbę zmiennoprzecinkową o podwójnej precyzji. Te pojęcia mogą być dla Ciebie nowe. Liczby **zmiennoprzecinkowe** są przydatne do reprezentowania bardzo małych lub bardzo dużych liczb innych niż liczby całkowite. **Podwójna precyzja** oznacza, że liczby są przechowywane z większą dokładnością niż liczby **pojedynczej precyzji**. W przypadku współczesnych komputerów częściej są używane liczby podwójnej precyzji niż pojedynczej precyzji.
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

Zakres wartości liczb podwójnej precyzji jest dużo większy niż liczb całkowitych. Wypróbuj poniższy kod, który napisałeś do tej pory:

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

Wiesz, że ułamek okresowy `0.3` to nie dokładnie to samo co `1/3`.

***Wyzwanie***

Spróbuj innych obliczeń z dużymi liczbami, małymi liczbami, mnożeniem i dzieleniem za pomocą typu `double`. Spróbuj bardziej skomplikowanych obliczeń.

Po spędzeniu trochę czasu z wyzwaniem, weź kod, który napisałeś i umieść go w nowej metodzie. Nazwij `WorkWithDoubles`tę nową metodę .

## <a name="work-with-fixed-point-types"></a>Praca ze stałoprzecinkowymi typami danych

Przedstawiono podstawowe typy danych liczbowych w języku C#: typ całkowitoliczbowy i typ podwójnej precyzji.  Istnieje jeszcze jeden typ, który należy poznać: typ `decimal`. Typ `decimal` ma mniejszy zakres, lecz większą precyzję niż typ `double`. Określenie **stałoprzecinkowy** oznacza, że przecinek dziesiętny (lub binarny) nie zmienia pozycji. Spójrzmy:

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

Sufiks `M` liczb wskazuje, że stałe powinny używać typu `decimal`.

Zwróć uwagę na to, że operacje matematyczne wykonywane na liczbach typu dziesiętnego mają więcej cyfr po prawej stronie przecinka dziesiętnego.

***Wyzwanie***

Teraz, gdy różne typy liczbowe zostały już przedstawione, napisz kod obliczający pole koła o promieniu 2,5 cm. Pole koła to promień pomnożony przez liczbę pi do kwadratu. Wskazówka: platforma .NET zawiera stałą dla liczby pi — <xref:System.Math.PI?displayProperty=nameWithType> — której możesz użyć.

Odpowiedź powinna należeć do zakresu 19-20.
Możesz sprawdzić swoją odpowiedź, [patrząc na gotowy przykładowy kod w witrynie GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).

Wypróbuj także inne wzory, jeśli chcesz.

Przewodnik szybki start "Liczby w języku C#". Można kontynuować [z gałęzi e-start i pętli](branches-and-loops-local.md) we własnym środowisku programistycznym.

Następujące tematy zawierają więcej informacji na temat liczb w języku C#:

- [Typy liczb całkowitych](../../language-reference/builtin-types/integral-numeric-types.md)
- [Zmiennoprzecinkowe rodzaje wartości numerycznych](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Wbudowane konwersje liczbowe](../../language-reference/builtin-types/numeric-conversions.md)
