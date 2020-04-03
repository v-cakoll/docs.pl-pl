---
title: Praca z kolekcjami — wprowadzenie do samouczka C#
description: Dowiedz się C# eksplorując List kolekcji w tym samouczku.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 554a4601157a7d4b873c22a46ee72b6601fc36d7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635653"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Dowiedz się, jak zarządzać zbieraniem danych przy użyciu typu listy ogólnej

Ten samouczek wprowadzający zawiera wprowadzenie do języka C# <xref:System.Collections.Generic.List%601> i podstawy klasy.

W tym samouczku oczekuje się, że masz komputer, którego można użyć do tworzenia. W samouczku .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) są instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemach Windows, Linux lub macOS. Szybki przegląd poleceń, których będziesz używać, znajduje się w [części Zapoznaj się z narzędziami programistycznymi](local-environment.md), z łączami do więcej szczegółów.

## <a name="a-basic-list-example"></a>Przykład listy podstawowej

Tworzenie katalogu o nazwie *lista-samouczek*. Zrób bieżący katalog i `dotnet new console`uruchom program .

Otwórz *Program.cs* w ulubionym edytorze i zastąp istniejący kod następującymi:

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

Zamień `<name>` swoje imię i nazwisko. Zapisz plik *Program.cs*. Wpisz `dotnet run` w oknie konsoli, aby spróbować.

Właśnie utworzono listę ciągów, dodano trzy nazwy do tej listy i wydrukowano nazwy we wszystkich caps. Używasz pojęć, które zostały nauczone we wcześniejszych samouczkach, aby zapętlać listę.

Kod do wyświetlania nazw korzysta z funkcji [interpolacji ciągu.](../../language-reference/tokens/interpolated.md)  Po poprzedzić `string` `$` znak, można osadzić kod C# w deklaracji ciągu. Rzeczywisty ciąg zastępuje ten kod Języka C# wartością, którą generuje. W tym przykładzie zastępuje `{name.ToUpper()}` z każdej nazwy, konwertowane na <xref:System.String.ToUpper%2A> wielkie litery, ponieważ metoda została wywołana.

Kontynuujmy odkrywanie.

## <a name="modify-list-contents"></a>Modyfikowanie zawartości listy

Utworzona kolekcja używa <xref:System.Collections.Generic.List%601> tego typu. Ten typ przechowuje sekwencje elementów. Należy określić typ elementów między nawiasami kątowymi.

Jednym z ważnych <xref:System.Collections.Generic.List%601> aspektów tego typu jest to, że może rosnąć lub zmniejszać, umożliwiając dodawanie lub usuwanie elementów. Dodaj ten kod `}` przed `Main` zamknięciem w metodzie:

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

Dodano jeszcze dwie nazwy na końcu listy. Usunięto również jeden. Zapisz plik i `dotnet run` wpisz, aby go wypróbować.

Umożliwia <xref:System.Collections.Generic.List%601> odwoływanie się do poszczególnych elementów przez **indeks,** jak również. Umieść indeks między `[` `]` i tokenów po nazwie listy. C# używa 0 dla pierwszego indeksu. Dodaj ten kod bezpośrednio pod kodem, który właśnie dodałeś i wypróbuj go:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nie można uzyskać dostępu do indeksu poza końcem listy. Pamiętaj, że indeksy zaczynają się od 0, więc największy prawidłowy indeks jest o jeden mniejszy niż liczba elementów na liście. Można sprawdzić, jak długo lista <xref:System.Collections.Generic.List%601.Count%2A> jest przy użyciu właściwości. Dodaj następujący kod na końcu Main metody:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Zapisz plik i `dotnet run` wpisz ponownie, aby wyświetlić wyniki.

## <a name="search-and-sort-lists"></a>Wyszukiwanie i sortowanie list

Nasze przykłady używają stosunkowo małych list, ale aplikacje często mogą tworzyć listy z wieloma innymi elementami, czasami numerując w tysiącach. Aby znaleźć elementy w tych większych kolekcjach, należy przeszukać listę różnych elementów. Metoda <xref:System.Collections.Generic.List%601.IndexOf%2A> wyszukuje towar i zwraca indeks towaru. Dodaj ten kod na `Main` dole metody:

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

Elementy na liście można również sortować. Metoda <xref:System.Collections.Generic.List%601.Sort%2A> sortuje wszystkie elementy na liście w normalnej kolejności (alfabetycznie w przypadku ciągów). Dodaj ten kod na `Main` dole naszej metody:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Zapisz plik i `dotnet run` wpisz, aby wypróbować tę najnowszą wersję.

Przed rozpoczęciem następnej sekcji przenieśmy bieżący kod do osobnej metody. To ułatwia rozpoczęcie pracy z nowym przykładem. Zmień nazwę `Main` metody `WorkingWithStrings` i napisz `Main` nową `WorkingWithStrings`metodę, która wywołuje . Po zakończeniu kod powinien wyglądać następująco:

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

Do tej pory `string` używałeś tego typu na listach. Zróbmy <xref:System.Collections.Generic.List%601> przy użyciu innego typu. Zbudujmy zestaw liczb.

Dodaj następujące elementy na dole `Main` nowej metody:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Tworzy listę liczby całkowite i ustawia dwie pierwsze liczby całkowite na wartość 1. Są to dwie pierwsze wartości *sekwencji Fibonacciego*, sekwencja liczb. Każdy następny numer Fibonacciego znajduje się, biorąc sumę poprzednich dwóch liczb. Dodaj ten kod:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Zapisz plik i `dotnet run` wpisz, aby zobaczyć wyniki.

> [!TIP]
> Aby skupić się tylko na tej sekcji, `WorkingWithStrings();`możesz skomentować kod, który wywołuje . Wystarczy umieścić `/` dwa znaki przed wezwaniem `// WorkingWithStrings();`w ten sposób: .

## <a name="challenge"></a>Wyzwanie

Sprawdź, czy możesz połączyć niektóre z pojęć z tej i wcześniejszych lekcji. Rozwiń to, co zbudowałeś do tej pory dzięki Liczbom Fibonacciego. Spróbuj napisać kod, aby wygenerować pierwsze 20 liczb w sekwencji. (Jako wskazówka, 20 numer Fibonacciego jest 6765.)

## <a name="complete-challenge"></a>Ukończenie wyzwania

Możesz zobaczyć przykładowe [rozwiązanie, patrząc na gotowy przykładowy kod na GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).

Przy każdej iteracji pętli bierzesz dwie ostatnie liczby całkowite na liście, sumując je i dodając tę wartość do listy. Pętla powtarza się, dopóki nie dodasz 20 elementów do listy.

Gratulacje, ukończyłeś samouczek listy. Możesz kontynuować wprowadzenie [do zajęć](introduction-to-classes.md) samouczek w swoim własnym środowisku programistycznym.

Więcej informacji na temat `List` pracy z typem można uzyskać w artykule [przewodnika .NET](../../../standard/index.yml) dotyczącymi [kolekcji](../../../standard/collections/index.md). Dowiesz się również o wielu innych typach kolekcji.
