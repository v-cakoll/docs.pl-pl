---
title: Współpraca z kolekcjami — wprowadzenie C# do samouczka
description: Poznaj C# kolekcję list w tym samouczku.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: b80225cf1614a7c25ac9011acd39e74032465ca3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834146"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Dowiedz się, jak zarządzać kolekcjami danych przy użyciu typu listy ogólnej

Ten samouczek wprowadzający zawiera wprowadzenie do C# języka i podstawowe informacje dotyczące klasy <xref:System.Collections.Generic.List%601>.

Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania. Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS. Szybki przegląd poleceń, które będą używane, jest [znany z narzędziami programistycznymi](local-environment.md)z linkami do dodatkowych informacji.

## <a name="a-basic-list-example"></a>Przykład listy podstawowej

Utwórz katalog o nazwie *list-samouczek*. Upewnij się, że bieżący katalog i uruchomiono `dotnet new console`.

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

Zastąp `<name>` nazwą użytkownika. Zapisz plik *Program.cs*. Wpisz `dotnet run` w oknie konsoli, aby go wypróbować.

Właśnie utworzono listę ciągów, dodano trzy nazwy do tej listy i wydrukowanych nazw we wszystkich WERSALIKach. Są używane koncepcje, które zostały uzyskane we wcześniejszych samouczkach, aby przepętlać listę.

Kod do wyświetlania nazw korzysta z funkcji [interpolacji ciągów](../../language-reference/tokens/interpolated.md) .  Gdy poprzedzasz `string` znakiem `$`, możesz osadzić C# kod w deklaracji ciągu. Rzeczywisty ciąg zastępuje ten C# kod wartością, którą generuje. W tym przykładzie zastępuje `{name.ToUpper()}` z każdą nazwą, konwertowana na wielkie litery, ponieważ wywołana została Metoda <xref:System.String.ToUpper%2A>.

Kontynuujmy Eksplorowanie.

## <a name="modify-list-contents"></a>Modyfikuj zawartość listy

Utworzona kolekcja używa typu <xref:System.Collections.Generic.List%601>. Ten typ przechowuje sekwencje elementów. Należy określić typ elementów między nawiasami kątowymi.

Jednym ważnym aspektem tego typu <xref:System.Collections.Generic.List%601> jest to, że można go zwiększyć lub zmniejszyć, umożliwiając dodawanie lub usuwanie elementów. Dodaj ten kod przed zamykaniem `}` w metodzie `Main`:

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

Dodano dwie więcej nazw na końcu listy. Również został także usunięty. Zapisz plik i wpisz `dotnet run`, aby go wypróbować.

@No__t-0 umożliwia odwoływanie się do poszczególnych elementów według **indeksu** . Indeks między tokenami `[` i `]` należy umieścić po nazwie listy. C#używa wartości 0 dla pierwszego indeksu. Dodaj ten kod bezpośrednio poniżej kodu, który właśnie został dodany, i wypróbuj go:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nie można uzyskać dostępu do indeksu poza końcem listy. Pamiętaj, że indeksy zaczynają się od 0, więc największy prawidłowy indeks jest mniejszy od liczby elementów na liście. Możesz sprawdzić, jak długo lista używa właściwości <xref:System.Collections.Generic.List%601.Count%2A>. Dodaj następujący kod na końcu metody Main:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Zapisz plik, a następnie wpisz `dotnet run` ponownie, aby wyświetlić wyniki.

## <a name="search-and-sort-lists"></a>Wyszukiwanie i sortowanie list

Nasze przykłady używają stosunkowo małych list, ale aplikacje mogą często tworzyć listy z wieloma elementami, czasami numerowania w tysiącach. Aby znaleźć elementy w tych większych kolekcjach, należy przeszukać listę pod kątem różnych elementów. Metoda <xref:System.Collections.Generic.List%601.IndexOf%2A> wyszukuje element i zwraca indeks elementu. Dodaj ten kod na końcu metody `Main`:

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

Elementy na liście można także sortować. Metoda <xref:System.Collections.Generic.List%601.Sort%2A> sortuje wszystkie elementy na liście w ich normalnej kolejności (alfabetycznie w przypadku ciągów). Dodaj ten kod na końcu metody `Main`:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Zapisz plik i wpisz `dotnet run`, aby wypróbować tę najnowszą wersję.

Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę metody `Main` na `WorkingWithStrings` i Napisz nową metodę `Main`, która wywołuje `WorkingWithStrings`. Po zakończeniu kod powinien wyglądać następująco:

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

        public static void WorkingWithStrings()
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
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

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

W tej chwili używasz typu `string` na listach. Przyjrzyjmy się <xref:System.Collections.Generic.List%601> przy użyciu innego typu. Utwórzmy zestaw numerów.

Dodaj następujący wiersz na końcu nowej metody `Main`:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Tworzy listę liczb całkowitych i ustawia pierwsze dwie liczby całkowite na wartość 1. Są to dwie pierwsze wartości *sekwencji Fibonacci*, sekwencja liczb. Każdy kolejny numer Fibonacci można znaleźć, pobierając sumę poprzednich dwóch liczb. Dodaj następujący kod:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Zapisz plik i wpisz `dotnet run`, aby wyświetlić wyniki.

> [!TIP]
> Aby skoncentrować się na tej sekcji, można skomentować kod, który wywołuje `WorkingWithStrings();`. Po prostu umieść dwa znaki `/` przed wywołaniem takim jak: `// WorkingWithStrings();`.

## <a name="challenge"></a>Sprawdz

Sprawdź, czy możesz połączyć niektóre koncepcje z tej i wcześniejszych lekcji. Rozwiń elementy, które zostały już skompilowane z użyciem numerów Fibonacci. Spróbuj napisać kod w celu wygenerowania pierwszych 20 cyfr w sekwencji. (Jako wskazówkę 20 Fibonacci numer jest 6765).

## <a name="complete-challenge"></a>Ukończ wyzwanie

Przykładowe rozwiązanie można zobaczyć, [przeglądając gotowy przykładowy kod w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).

Każda iteracja pętli polega na wykorzystaniu ostatnich dwóch liczb całkowitych na liście, sumowaniu ich i dodawania tej wartości do listy. Pętla jest powtarzana do momentu dodania 20 elementów do listy.

Gratulacje, ukończono samouczek z listą. Możesz przejść do samouczka [wprowadzenie do klas](introduction-to-classes.md) w Twoim środowisku programistycznym.

Więcej informacji o pracy z typem `List` można znaleźć w temacie [Przewodnik po platformie .NET](../../../standard/index.md) na stronie [kolekcje](../../../standard/collections/index.md). Zapoznaj się również z wieloma innymi typami kolekcji.
