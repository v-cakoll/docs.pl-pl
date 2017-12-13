---
title: "Przewodnik Szybki Start - numery w języku C# - C#"
description: "Naucz się C# eksplorując typy liczbowe, ich właściwości i metody."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: f275f157d9a9e41407be0beac83c337c7706a95d
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="numbers-in-c-quick-start"></a>Liczby w języku C# — szybki start #

To szybki start zawiera informacje na temat typu liczbowego w języku C# interaktywnie. Przedstawiono tworzenie niewielkich ilości kodu, a następnie będzie można skompilować i uruchomić ten kod. Szybki start zawiera szereg — lekcje przedstawiających operacji matematycznych w języku C# i cyfry. Że wnioski uczy również podstaw programu w języku C#.

To szybki start oczekuje posiadania maszynie, która służy do tworzenia aplikacji. Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux. Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.

## <a name="explore-integer-math"></a>Eksploruj matematyczne liczba całkowita

Utwórz katalog o nazwie **szybkiego startu numery**. Upewnij, że bieżący katalog i uruchom `dotnet new console -n NumbersInCSharp -o .`.

Otwórz **Program.cs** ulubionego edytora i Zastąp linię `Console.Writeline("Hello World!");` następującym kodem:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Uruchom ten kod, wpisując `dotnet run` w oknie polecenia. 

Po prostu przedstawiono jednej z operacji matematycznych podstawowych z liczbami całkowitymi. `int` Wpisz reprezentuje **całkowitą**, liczbą całkowitą liczbą dodatnią lub ujemną. Możesz użyć `+` symbol do dodania. Inne typowe operacji matematycznych liczb całkowitych obejmują:

- `-`dla odejmowania
- `*`dla mnożenia
- `/`podziału

Rozpocznij od eksploracji tych różnych operacji. Dodaj następujące wiersze po wierszu, który zapisuje wartość `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Uruchom ten kod, wpisując `dotnet run` w oknie polecenia. 
    
Poeksperymentuj przez wykonanie wielu operacji matematyce w tej samej linii, jeśli chcesz. Spróbuj `c = a + b - 12 * 17;` np. Mieszanie zmienne i stałe numery jest dozwolone.

> [!TIP]
> Ci poznać platformę C# (lub dowolnego języka programowania), należy podjąć błędów podczas pisania kodu. **Kompilatora** znajdzie te błędy i raportuj je użytkownikowi. Jeśli dane wyjściowe zawiera komunikaty o błędach, należy dokładnie przejrzeć przykładowy kod i kod w oknie, aby zobaczyć rozwiązać problem.
> Tym ćwiczeniu zostanie zapoznawania się struktury kodu C#.     

Po zakończeniu pierwszym krokiem. Przed rozpoczęciem następnej sekcji przejdziemy bieżącego kodu w oddzielnych metodach. Który ułatwia rozpoczęcie pracy z nowego przykład. Zmień nazwę Twojej `Main` metodę `WorkingWithIntegers` i zapisać nową `Main` — metoda, która wywołuje `WorkingWithIntegers`. Po zakończeniu, kod powinien wyglądać następująco:

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

Komentarz wywołanie `WorkingWithIntegers()`. Spowoduje to, że dane wyjściowe mniej elementów pracy w tej sekcji:

```csharp
//WorkingWithIntegers();
```

`//` Uruchamia **komentarz** w języku C#. Komentarze mogą zawierać dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie wykonują jako kod. Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.

W języku C# określa priorytet matematyce różne operacje przy użyciu reguły zgodnych z zasadami, które przedstawiono w matematyce.
Mnożenia i dzielenia pierwszeństwo Dodawanie i odejmowanie.
Eksploruj który, dodając następujący kod, aby Twoje `Main` — metoda i execuing `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Dane wyjściowe pokazuje, że mnożenia odbywa się przed dodaniem.

Operacje, które mają przeprowadzić najpierw lub innej kolejności operacji można wymusić przez dodanie nawiasów wokół operacji. Dodaj następujące wiersze i uruchom ponownie:

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Poznaj więcej, łącząc wiele różnych operacji. Dodaj przypominać następujące wiersze w dolnej części Twojego `Main` metody. Spróbuj `dotnet run` ponownie.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Można zauważyć interesujące zachowanie liczb całkowitych. Dzielenie liczby całkowitej zawsze daje wynik liczba całkowita, nawet wtedy, gdy oczekiwany wynik, który ma zawierać dziesiętną lub ułamkową część.

Jeśli jeszcze tego nie pokazano tego zachowania, spróbuj następujący kod na końcu Twojej `Main` metody:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Typ `dotnet run` ponownie, aby wyświetlić wyniki.

Przed kontynuowaniem, Przyjrzyjmy się cały kod został napisany w tej sekcji i umieszcza je w nowej metody. Wywołanie tej nowej metody `OrderPrecedence`.
Należy na końcu podobny do następującego:

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

## <a name="explore-integer-precision-and-limits"></a>Eksploruj całkowitą dokładność i limity
Tej ostatniej próbki wykazały, że dzielenie liczby całkowitej obcina wynik.
Możesz uzyskać **pozostałej** za pomocą **modulo** operatora `%` znaków. Spróbuj następujący kod w Twojej `Main` metody:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# całkowitą różni się od matematyczne liczb całkowitych w inny sposób: `int` typ ma limity minimalną i maksymalną. Dodaj ten kod do Twojej `Main` metody, aby wyświetlić te limity:
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Jeśli obliczeń daje wartość, która przekracza te limity, masz **niedopełnienie** lub **przepełnienie** warunku. Odpowiedź zostanie wyświetlona opakowywać z limitu jednego do drugiego. Dodaj następujące dwa wiersze do Twojej `Main` metody, na przykład:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
Zwróć uwagę, że odpowiedź jest bliski minimalną liczbę całkowitą (ujemne). Jest taka sama jak `min + 2`. Operacja dodawania **nastąpiło przepełnienie** dozwolone wartości liczb całkowitych.
Odpowiedzią jest bardzo dużą liczbą ujemną, ponieważ przepełnienie "zawija się wokół" z największą wartość całkowita możliwych do najmniejszej.

Istnieją inne typy liczbowe z różnych limitów i dokładność, że będą używane podczas `int` typu nie odpowiadają Twoim potrzebom. Przyjrzyjmy się tych dalej.

Jeszcze raz przejdziemy kodu zapisanego w tej sekcji w oddzielnych metodach. Nadaj mu nazwę `TestLimits`. 

## <a name="work-with-the-double-type"></a>Praca z typu double

`double` Podwójnej precyzji liczba zmiennoprzecinkowa reprezentuje typ liczbowy. Te warunki mogą być nowe dla Ciebie. A **zmiennoprzecinkowa** numer przydaje się do wyświetlania niecałkowity liczb, które mogą być bardzo duże lub małe wielkości. **Podwójnej precyzji** oznacza, że numery te są przechowywane przy użyciu większą dokładność niż **pojedynczej precyzji**. W nowych komputerów jest najczęściej używać podwójnej precyzji niż liczby o pojedynczej precyzji.
Przyjrzyjmy się. Dodaj następujący kod i wyświetlić wyniki:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Zwróć uwagę, że odpowiedź zawiera część iloraz. Spróbuj wyrażenia nieco bardziej skomplikowane z symulacyjnych:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Zakres wartości typu double jest większa niż wartości będące liczbami całkowitymi. Wykonaj następujący kod poniżej co napisanych wykonanej do tej pory:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Te wartości są drukowany w notacji wykładniczej. Liczba z lewej strony `E` jest mantysy. Liczba po prawej stronie jest wykładnik, jako potęgi liczby 10. 

Podobnie jak liczbami dziesiętnymi matematyczne symulacyjnych w języku C# mogą mieć błędów zaokrąglania. Spróbuj wykonać ten kod:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Należy pamiętać, że `0.3` powtarzające się nie jest dokładnie taka sama jak `1/3`.

***Żądanie***

Spróbuj inne obliczenia z dużą liczbą, małej liczby, mnożenia i dzielenia przy użyciu `double` typu.  Spróbuj bardziej skomplikowane obliczenia.

Po po długiej pracy z żądaniem, należy przenieść kod napisanych i umieścić go w nowej metody. Nazwa tej nowej metody `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Praca z typami stałego punktu

W tym samouczku podstawowe typy liczbowe w języku C#: liczb całkowitych i na symulacyjnych.  Istnieje jeden inny typ, aby dowiedzieć się więcej: `decimal` typu. `decimal` Typ ma mniejszy zakres, ale większą dokładność niż `double`. Termin **stały punkt** oznacza, że punkt dziesiętny (lub punktu binarnego) nie jest przenoszony. Spójrzmy:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Należy zauważyć, że zakres jest mniejszy niż `double` typu. Możesz zobaczyć większą dokładność typu decimal podejmując następujący kod:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

`M` Sufiks na numery jest sposób oznacza, że stałą powinien używać `decimal` typu.

Należy zauważyć, że obliczenia przy użyciu typu decimal zawiera więcej cyfr z prawej strony punktu dziesiętnego. 

***Żądanie***

Skoro już znasz różne typy liczbowe pisania kodu, który oblicza obszaru koło którego radius jest 2,50 cala. Należy pamiętać, że obszar koła jest radius kwadrat pomnożona przez PI. Jedną wskazówkę: .NET zawiera stałą Pi, <xref:System.Math.PI?displayProperty=nameWithType> używanego dla tej wartości. 

Należy uzyskać odpowiedzi od 19 do 20.
Można sprawdzić odpowiedzi przez [patrzeć Zakończono przykładowy kod w witrynie GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)

Jeśli chcesz, spróbuj niektóre inne formuły. 

Zakończono szybki start "numery w języku C#". Można kontynuować [gałęzie i pętli](branches-and-loops-local.md) szybki start w środowisku projektowania.

Użytkownik może dowiedzieć się więcej o numery w języku C# w następujących tematach:

[Tabela typów całkowitych](../language-reference/keywords/integral-types-table.md)   
[Tabela typów zmiennoprzecinkowych](../language-reference/keywords/floating-point-types-table.md)   
[Tabela typów wbudowanych](../language-reference/keywords/built-in-types-table.md)   
[Tabela niejawnych konwersji liczbowych](../language-reference/keywords/implicit-numeric-conversions-table.md)   
[Tabela jawnych konwersji liczbowych](../language-reference/keywords/explicit-numeric-conversions-table.md)

