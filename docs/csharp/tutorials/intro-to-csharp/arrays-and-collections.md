---
title: Praca z kolekcjami — wprowadzenie do samouczka języka C#
description: Dowiedz się C# eksplorując Listy kolekcji w tym samouczku.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 25d20de2eae8ad1f544fa17553c173a6141ae464
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156692"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Dowiedz się, jak zarządzać zbiorami danych przy użyciu ogólnego typu listy

Ten instruktażowy samouczek zawiera wprowadzenie do języka <xref:System.Collections.Generic.List%601> Języka C# i podstawy klasy.

Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia. Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS. Szybki przegląd poleceń, których będziesz używać, znajduje się w [obszarze Zaznajomij się z narzędziami programistycznymi](local-environment.md)z łączami do więcej szczegółów.

## <a name="a-basic-list-example"></a>Przykład listy podstawowej

Utwórz katalog o nazwie *list-tutorial*. Upewnij się, że `dotnet new console`bieżący katalog i uruchom .

Otwórz *Program.cs* w ulubionym edytorze i zastąp istniejący kod następującymi elementami:

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

Zastąp `<name>` swoim imieniem i nazwiskiem. Zapisz plik *Program.cs*. Wpisz `dotnet run` okno konsoli, aby spróbować.

Właśnie utworzono listę ciągów, dodano trzy nazwy do tej listy i wydrukowano nazwy we wszystkich caps. Używasz pojęć, które zostały nauczone we wcześniejszych samouczkach do pętli za pośrednictwem listy.

Kod do wyświetlania nazw korzysta z funkcji [interpolacji ciągów.](../../language-reference/tokens/interpolated.md)  Poprzedzić `string` znak, `$` można osadzić kod C# w deklaracji ciągu. Rzeczywisty ciąg zastępuje ten kod C# wartością, którą generuje. W tym przykładzie zastępuje `{name.ToUpper()}` z każdej nazwy, konwertowane na wielkie <xref:System.String.ToUpper%2A> litery, ponieważ nazywa się metodę.

Badajmy dalej.

## <a name="modify-list-contents"></a>Modyfikowanie zawartości listy

Kolekcja, którą utworzyłeś <xref:System.Collections.Generic.List%601> używa tego typu. Ten typ przechowuje sekwencje elementów. Typ elementów między nawiasami kątowymi.

Jednym z ważnych <xref:System.Collections.Generic.List%601> aspektów tego typu jest to, że można go rozwijać lub zmniejszać, umożliwiając dodawanie lub usuwanie elementów. Dodaj ten kod `}` przed `Main` zamknięciem w metodzie:

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

Na końcu listy dodano jeszcze dwie nazwy. Usunięto również jeden. Zapisz plik i `dotnet run` wpisz, aby go wypróbować.

Umożliwia <xref:System.Collections.Generic.List%601> odwoływanie się do poszczególnych elementów przez **indeks,** jak również. Należy umieścić indeks `[` `]` między i tokeny po nazwie listy. C# używa 0 dla pierwszego indeksu. Dodaj ten kod bezpośrednio pod dodanym kodem i spróbuj go:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nie można uzyskać dostępu do indeksu poza końcem listy. Pamiętaj, że indeksy zaczynają się od 0, więc największy prawidłowy indeks jest o jeden mniejszy niż liczba pozycji na liście. Można sprawdzić, jak długo lista <xref:System.Collections.Generic.List%601.Count%2A> jest przy użyciu właściwości. Dodaj następujący kod na końcu Metody Głównej:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Zapisz plik i `dotnet run` wpisz ponownie, aby zobaczyć wyniki.

## <a name="search-and-sort-lists"></a>Wyszukiwanie i sortowanie list

Nasze przykłady używają stosunkowo małych list, ale aplikacje często mogą tworzyć listy z wieloma innymi elementami, czasami numerowane w tysiącach. Aby znaleźć elementy w tych większych kolekcji, należy wyszukać listę różnych elementów. Metoda <xref:System.Collections.Generic.List%601.IndexOf%2A> wyszukuje element i zwraca indeks elementu. Dodaj ten kod do `Main` dołu metody:

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

Elementy na liście można również sortować. Metoda <xref:System.Collections.Generic.List%601.Sort%2A> sortuje wszystkie elementy na liście w normalnej kolejności (alfabetycznie w przypadku ciągów). Dodaj ten kod do `Main` dolnej części naszej metody:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Zapisz plik i `dotnet run` wpisz, aby wypróbować tę najnowszą wersję.

Przed rozpoczęciem następnej sekcji przenieśmy bieżący kod do osobnej metody. Ułatwia to rozpoczęcie pracy z nowym przykładem. Zmień nazwę `Main` metody `WorkingWithStrings` i napisz `Main` nową `WorkingWithStrings`metodę, która wywołuje . Po zakończeniu kod powinien wyglądać tak:

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

Do tej pory `string` używano tego typu na listach. Zróbmy <xref:System.Collections.Generic.List%601> przy użyciu innego typu. Zbudujmy zestaw liczb.

Dodaj następujące elementy do dolnej części nowej `Main` metody:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Spowoduje to utworzenie listy liczb całkowitych i ustawienie pierwszych dwóch liczb całkowitych na wartość 1. Są to dwie pierwsze wartości *sekwencji Fibonacciego*, sekwencji liczb. Każdy następny numer Fibonacciego znajduje się, biorąc sumę poprzednich dwóch liczb. Dodaj ten kod:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Zapisz plik i `dotnet run` wpisz, aby zobaczyć wyniki.

> [!TIP]
> Aby skoncentrować się tylko na tej sekcji, `WorkingWithStrings();`możesz skomentować kod, który wywołuje . Wystarczy umieścić `/` dwa znaki przed połączeniem `// WorkingWithStrings();`tak: .

## <a name="challenge"></a>Wyzwanie

Zobacz, czy możesz połączyć niektóre koncepcje z tej i wcześniejszych lekcji. Rozwiń to, co zbudowałeś do tej pory dzięki numerom Fibonacciego. Spróbuj napisać kod, aby wygenerować pierwsze 20 liczb w sekwencji. (Jako wskazówkę, 20 numer Fibonacciego jest 6765.)

## <a name="complete-challenge"></a>Ukończenie wyzwania

Możesz zobaczyć przykładowe rozwiązanie, [patrząc na gotowy przykładowy kod w usiuł github](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).

Przy każdej iteracji pętli przyjmujesz dwie ostatnie liczby całkowite na liście, sumując je i dodając tę wartość do listy. Pętla jest powtarzana, dopóki nie dodasz 20 elementów do listy.

Gratulacje, ukończyłeś samouczek listy. Można kontynuować [wprowadzenie do zajęć](introduction-to-classes.md) samouczek we własnym środowisku programistycznym.

Więcej informacji na temat `List` pracy z typem można uzyskać w temacie [przewodnika .NET](../../../standard/index.md) w [kolekcjach](../../../standard/collections/index.md). Dowiesz się również o wielu innych typach kolekcji.
