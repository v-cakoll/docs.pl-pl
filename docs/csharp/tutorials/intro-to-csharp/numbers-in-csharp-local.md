---
title: Liczby w elemencie C# — wprowadzenie do C# samouczek
description: Dowiedz się, C# eksplorując typy liczbowe, ich właściwości i metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 009c737297c331b1aa4dcad058ac6bfdf05ac037
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978621"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipulowanie liczb całkowitych i zmiennoprzecinkowych w języku C\#

Ten samouczek zawiera informacje na temat typów liczbowych w C# interaktywnie. Napiszesz niewielką ilość kodu, a następnie będzie skompilować i uruchomić ten kod. Samouczek zawiera serię lekcji dotyczących liczb i operacji matematycznych w C#. Te lekcje umożliwiają poznanie podstaw języka C#.

W tym samouczku oczekuje, że będziesz mieć maszyny, których można użyć do tworzenia aplikacji. Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux. Krótkie omówienie poleceń użyjesz znajduje się w [zapoznanie się z narzędziami programistycznymi](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.

## <a name="explore-integer-math"></a>Poznawanie matematyki całkowitoliczbowej

Utwórz katalog o nazwie **numery — Szybki Start**. Upewnij, że bieżącego katalogu i uruchom `dotnet new console -n NumbersInCSharp -o .`.

Otwórz **Program.cs** w ulubionym edytorze i Zastąp wiersz `Console.Writeline("Hello World!");` następującym kodem:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Uruchom ten kod, wpisując `dotnet run` w oknie polecenia. 

Po prostu przedstawiono jedną z podstawowych operacji matematycznych na liczbach całkowitych. `int` Wpisz reprezentuje **całkowitą**, dodatnią lub ujemną liczbę całkowitą. Możesz użyć `+` symbol do dodania. Inne typowe operacje matematyczne dla liczb całkowitych obejmują:

- `-` odejmowanie
- `*` mnożenie
- `/` dzielenie

Rozpocznij od wypróbowania różnych operacji. Dodaj następujące wiersze po wierszu, który zapisuje wartość `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Uruchom ten kod, wpisując `dotnet run` w oknie polecenia. 
    
Możesz także eksperymentować, wykonując wiele operacji matematycznych w jednym wierszu, jeśli chcesz. Spróbuj `c = a + b - 12 * 17;` na przykład. Mieszanie zmiennych i stałych liczb jest dozwolone.

> [!TIP]
> Gdy eksplorujesz C# (lub dowolnego języka programowania), będziesz robić błędy podczas pisania kodu. **Kompilatora** znajdzie te błędy i zgłosi je. Gdy dane wyjściowe zawierają komunikaty o błędach, Przyjrzyj się blisko przykładowy kod i kod w oknie w taki sposób, aby zobaczyć, co należy naprawić.
> To ćwiczenie pomoże Ci poznać strukturę kodu C#.     

Pierwszym krokiem zostały ukończone. Przed rozpoczęciem następnej sekcji, Przejdźmy bieżącego kodu w oddzielnych metodach. Który sprawia, że łatwiej rozpocząć pracę z nową przykładową. Zmiana nazwy Twojego `Main` metodę, aby `WorkingWithIntegers` i zapisywać nowy `Main` metodę, która wywołuje `WorkingWithIntegers`. Po zakończeniu, kod powinien wyglądać następująco:

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

## <a name="explore-order-of-operations"></a>Poznawanie kolejności operacji

Komentarz wywołanie `WorkingWithIntegers()`. Spowoduje to, że dane wyjściowe, które mniej "zatłoczony" podczas pracy w tej sekcji:

```csharp
//WorkingWithIntegers();
```

`//` Uruchamia **komentarz** w C#. Komentarze są dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie jest wykonywane jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

W języku C# definiuje kolejność wykonywania różnych operacji matematycznych zgodnie z regułami spójnymi z regułami przedstawianymi na lekcjach matematyki.
Mnożenie i dzielenie pierwszeństwo dodawania i odejmowania.
Zaobserwuj to, dodając następujący kod, aby Twoje `Main` metody i wykonywania `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Dane wyjściowe pokazuje, że mnożenie jest wykonywane przed dodawaniem.

Operacje, które chcesz przeprowadzić najpierw lub inną kolejność operacji można wymusić, dodając nawiasy wokół operacji. Dodaj następujące wiersze, a następnie ponownie uruchom:

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Dowiedz się więcej, łącząc wiele różnych operacji. Dodaj coś następujące wiersze na końcu Twojej `Main` metody. Spróbuj `dotnet run` ponownie.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Być może zauważono, interesujące zachowanie liczb całkowitych. Dzielenie całkowitoliczbowe zawsze daje wyniku liczby całkowitej, nawet wtedy, gdy oczekiwany wynik, który ma zawierać części dziesiętnej lub ułamkowej.

Jeśli nie dostrzegasz tego zachowania, wypróbuj następujący kod na końcu Twojej `Main` metody:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Typ `dotnet run` ponownie, aby zobaczyć wyniki.

Przed kontynuowaniem, Przyjrzyjmy się cały kod został napisany w tej sekcji i umieścić go w nowej metody. Wywołanie tej nowej metody `OrderPrecedence`.
Użytkownik powinien kończyć podobny do poniższego:

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

## <a name="explore-integer-precision-and-limits"></a>Zapoznaj się z liczbą całkowitą precyzji i limitów
Ostatni przykład pokazuje, że dzielenie całkowitoliczbowe obcina wynik.
Możesz uzyskać **resztę** przy użyciu **modulo** operatora `%` znaków. Wypróbuj poniższy kod w swojej `Main` metody:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Typ liczby całkowitej C# różni się od matematycznych liczb całkowitych w inny sposób: `int` typ ma limit maksimum i minimum. Dodaj następujący kod do Twojego `Main` metodę, aby zobaczyć te limity:
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Jeśli obliczenia generują wartość, która przekracza te limity, masz **niedopełnienie** lub **przepełnienie** warunku. Odpowiedź wydaje się zawijać między do drugiego. Dodaj następujące dwa wiersze do Twojej `Main` metodę, aby zobaczyć przykład:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
Należy zauważyć, że odpowiedź jest bardzo zbliżona minimalnej (ujemnej) liczby całkowitej. Jest taka sama jak `min + 2`. Operacja dodawania **przepełnienie** dozwolone wartości liczb całkowitych.
Odpowiedzią jest bardzo duża liczba ujemna, ponieważ przepełnienie "zawinięcie" z największej możliwej liczby całkowitej do najmniejszej.

Istnieją inne typy liczbowe z innymi limitami i precyzją, których możesz użyć, gdy `int` typu nie odpowiada Twoim potrzebom. Przyjrzyjmy się nimi w następnej kolejności.

Jeszcze raz Przejdźmy kod, który napisał w tej sekcji w oddzielnych metodach. Nadaj mu nazwę `TestLimits`. 

## <a name="work-with-the-double-type"></a>Praca z typem double

`double` Typu numerycznego reprezentuje liczbę zmiennoprzecinkową podwójnej precyzji. Te pojęcia mogą być dla Ciebie nowe. A **zmiennoprzecinkowa** numer jest przydatne do reprezentowania liczb niecałkowitoliczbowego, które mogą być bardzo małych lub dużych. **Podwójnej precyzji** oznacza, że te liczby są przechowywane z większą dokładnością niż **pojedynczej precyzji**. W przypadku współczesnych komputerów jest bardziej powszechne, aby użyć podwójnej precyzji niż pojedynczej precyzji liczb.
Przyjrzyjmy się. Dodaj następujący kod i zobacz wynik:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Należy zauważyć, że odpowiedź obejmuje część dziesiętną ilorazu. Spróbuj nieco bardziej skomplikowanego wyrażenia z liczbami podwójnej precyzji:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Zakres liczb podwójnej precyzji jest dużo większy niż liczb całkowitych. Wypróbuj poniższy kod poniżej co napisanych do tej pory:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Te wartości są drukowane w notacji naukowej. Liczba po lewej stronie `E` to mantysa. Liczba po prawej stronie to wykładnik jako potęga 10. 

Podobnie jak liczb dziesiętnych w matematyce wartości podwójnej precyzji w języku C# mogą wystąpić błędy zaokrąglania. Wypróbuj ten kod:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Należy pamiętać, że `0.3` powtarzanie nie jest dokładnie taka sama jak `1/3`.

***Challenge***

Spróbuj innych obliczeń z dużą liczbą, małymi liczbami, mnożeniem i dzieleniem za pomocą `double` typu.  Spróbuj bardziej skomplikowanych obliczeń.

Po przez pewien czas z żądaniem zająć kodu zostały zapisane i umieść go w nowej metody. Nazwa tej nowej metody `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Praca ze stałoprzecinkowymi typami

W tym samouczku podstawowe typy danych liczbowych w języku C#: liczby całkowite i typ podwójnej precyzji.  Istnieje jeszcze jeden typ, aby dowiedzieć się więcej: `decimal` typu. `decimal` Typ ma mniejszy zakres, lecz większą precyzję niż `double`. Termin **Stałoprzecinkowy** oznacza, że punkt dziesiętny (lub binarny) nie jest przenoszony. Przyjrzyjmy się:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Należy zauważyć, że zakres jest mniejszy niż `double` typu. Możesz zobaczyć większą precyzję typu dziesiętnego, wykonując następujący kod:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

`M` Sufiks liczby jest wskazuje, że stałe powinny używać `decimal` typu.

Należy zauważyć, że matematyczne liczbach typu dziesiętnego ma więcej cyfr po prawej stronie przecinka dziesiętnego. 

***Challenge***

Teraz, gdy różne typy liczbowe, należy napisać kod obliczający pole koła o promieniu jest kosztuje 2,50 cm. Należy pamiętać, że pole koła to promień pomnożony pomnożonej przez PI. Wskazówka: platforma .NET zawiera stałą dla liczby PI — <xref:System.Math.PI?displayProperty=nameWithType> używanego dla tej wartości. 

Powinna pojawić się odpowiedź zakresu 19-20.
Możesz sprawdzić odpowiedzi przez [spojrzenie na Zakończono przykładowego kodu w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)

Wypróbuj także inne wzory, jeśli chcesz. 

Ukończono "liczby w elemencie C#" Szybki Start. Możesz kontynuować [gałęzie i pętle](branches-and-loops-local.md) Szybki Start w środowisku projektowym.

Możesz dowiedzieć się więcej na temat liczb w języku C# w następujących tematach:

[Tabela typów całkowitych](../../language-reference/keywords/integral-types-table.md)   
[Tabela typów zmiennoprzecinkowych](../../language-reference/keywords/floating-point-types-table.md)   
[Tabela typów wbudowanych](../../language-reference/keywords/built-in-types-table.md)   
[Tabela niejawnych konwersji liczbowych](../../language-reference/keywords/implicit-numeric-conversions-table.md)   
[Tabela jawnych konwersji liczbowych](../../language-reference/keywords/explicit-numeric-conversions-table.md)
