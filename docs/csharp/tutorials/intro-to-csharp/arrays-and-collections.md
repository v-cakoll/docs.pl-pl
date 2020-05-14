---
title: Współpraca z kolekcjami — wprowadzenie do samouczka języka C#
description: Poznaj język C#, eksplorując kolekcję list w tym samouczku.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: c99f5582702120db238de1206de42d964837cdbd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396895"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Dowiedz się, jak zarządzać kolekcjami danych przy użyciu typu listy ogólnej

Ten samouczek wprowadzający zawiera wprowadzenie do języka C# i podstawowe informacje o <xref:System.Collections.Generic.List%601> klasie.

Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania. Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS. Szybki przegląd poleceń, które będą używane, jest [znany z narzędziami programistycznymi](local-environment.md)z linkami do dodatkowych informacji.

## <a name="a-basic-list-example"></a>Przykład listy podstawowej

Utwórz katalog o nazwie *list-samouczek*. Upewnij się, że bieżący katalog jest uruchomiony `dotnet new console` .

Otwórz *program.cs* w ulubionym edytorze i Zastąp istniejący kod następującym:

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

Zamień `<name>` na nazwę użytkownika. Zapisz plik *Program.cs*. Wpisz `dotnet run` w oknie konsoli, aby ją wypróbować.

Utworzono listę ciągów, dodano trzy nazwy do tej listy i wydrukowanych nazw we wszystkich WERSALIKach. Są używane koncepcje, które zostały uzyskane we wcześniejszych samouczkach, aby przepętlać listę.

Kod do wyświetlania nazw korzysta z funkcji [interpolacji ciągów](../../language-reference/tokens/interpolated.md) .  Gdy poprzedzasz `string` `$` znak, możesz osadzić kod w języku C# w deklaracji ciągu. Rzeczywisty ciąg zastępuje ten kod C# wartością, którą generuje. W tym przykładzie zastępuje on `{name.ToUpper()}` każdą nazwę, przekonwertowane na wielkie litery, ponieważ wywołano <xref:System.String.ToUpper%2A> metodę.

Kontynuujmy Eksplorowanie.

## <a name="modify-list-contents"></a>Modyfikuj zawartość listy

Utworzona kolekcja używa <xref:System.Collections.Generic.List%601> typu. Ten typ przechowuje sekwencje elementów. Należy określić typ elementów między nawiasami kątowymi.

Jednym z ważnych aspektów tego <xref:System.Collections.Generic.List%601> typu jest to, że można go zwiększyć lub zmniejszyć, umożliwiając dodawanie lub usuwanie elementów. Dodaj ten kod przed zamknięciem `}` `Main` metody:

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Dodano dwie więcej nazw na końcu listy. Również został także usunięty. Zapisz plik i wpisz, `dotnet run` Aby go wypróbować.

<xref:System.Collections.Generic.List%601>Umożliwia także odwoływanie się do poszczególnych elementów według **indeksu** . Indeks między `[` i `]` tokenami należy umieścić po nazwie listy. Język C# używa wartości 0 jako pierwszego indeksu. Dodaj ten kod bezpośrednio poniżej kodu, który właśnie został dodany, i wypróbuj go:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nie można uzyskać dostępu do indeksu poza końcem listy. Pamiętaj, że indeksy zaczynają się od 0, więc największy prawidłowy indeks jest mniejszy od liczby elementów na liście. Możesz sprawdzić, jak długo lista używa <xref:System.Collections.Generic.List%601.Count%2A> właściwości. Dodaj następujący kod na końcu metody Main:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Zapisz plik i wpisz ponownie, `dotnet run` Aby zobaczyć wyniki.

## <a name="search-and-sort-lists"></a>Wyszukiwanie i sortowanie list

Nasze przykłady używają stosunkowo małych list, ale aplikacje mogą często tworzyć listy z wieloma elementami, czasami numerowania w tysiącach. Aby znaleźć elementy w tych większych kolekcjach, należy przeszukać listę pod kątem różnych elementów. <xref:System.Collections.Generic.List%601.IndexOf%2A>Metoda wyszukuje element i zwraca indeks elementu. Jeśli element nie znajduje się na liście, `IndexOf` zwraca `-1` . Dodaj ten kod na końcu `Main` metody:

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

Elementy na liście można także sortować. <xref:System.Collections.Generic.List%601.Sort%2A>Metoda sortuje wszystkie elementy na liście w ich normalnej kolejności (alfabetycznie w przypadku ciągów). Dodaj ten kod na końcu naszej `Main` metody:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Zapisz plik i wpisz, `dotnet run` Aby wypróbować tę najnowszą wersję.

Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę `Main` metody na `WorkingWithStrings` i Napisz nową `Main` metodę, która wywołuje `WorkingWithStrings` . Po zakończeniu kod powinien wyglądać następująco:

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");
            }

            index = names.IndexOf("Not Found");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");

            }

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a>Listy innych typów

Używasz `string` typu na listach do tej pory. Użyjmy <xref:System.Collections.Generic.List%601> innego typu. Utwórzmy zestaw numerów.

Dodaj następujący wiersz na końcu nowej `Main` metody:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Tworzy listę liczb całkowitych i ustawia pierwsze dwie liczby całkowite na wartość 1. Są to dwie pierwsze wartości *sekwencji Fibonacci*, sekwencja liczb. Każdy kolejny numer Fibonacci można znaleźć, pobierając sumę poprzednich dwóch liczb. Dodaj ten kod:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Zapisz plik i wpisz `dotnet run` , aby zobaczyć wyniki.

> [!TIP]
> Aby skoncentrować się na tej sekcji, można skomentować kod, który wywołuje `WorkingWithStrings();` . Po prostu umieść dwa `/` znaki przed wywołaniem podobnym do tego: `// WorkingWithStrings();` .

## <a name="challenge"></a>Wyzwanie

Sprawdź, czy możesz połączyć niektóre koncepcje z tej i wcześniejszych lekcji. Rozwiń elementy, które zostały już skompilowane z użyciem numerów Fibonacci. Spróbuj napisać kod w celu wygenerowania pierwszych 20 cyfr w sekwencji. (Jako wskazówkę 20 Fibonacci numer jest 6765).

## <a name="complete-challenge"></a>Ukończenie wyzwania

Przykładowe rozwiązanie można zobaczyć, [przeglądając gotowy przykładowy kod w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).

Każda iteracja pętli polega na wykorzystaniu ostatnich dwóch liczb całkowitych na liście, sumowaniu ich i dodawania tej wartości do listy. Pętla jest powtarzana do momentu dodania 20 elementów do listy.

Gratulacje, ukończono samouczek z listą. Możesz przejść do samouczka [wprowadzenie do klas](introduction-to-classes.md) w Twoim środowisku programistycznym.

Aby dowiedzieć się więcej na temat pracy z `List` typem w artykule [Przewodnik .NET](../../../standard/index.yml) w [kolekcji](../../../standard/collections/index.md). Zapoznaj się również z wieloma innymi typami kolekcji.
