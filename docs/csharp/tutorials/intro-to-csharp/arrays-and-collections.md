---
title: Praca z kolekcjami — wprowadzenie do C# samouczek
description: Dowiedz się, C# eksplorując kolekcji listy, w tym samouczku.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 9a910ccd6265011fc0e5540b461ba089dbd3e7ba
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261274"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Dowiedz się, jak zarządzać zbierania danych przy użyciu typu listy ogólnej

Ten Samouczek wprowadzający zawiera wprowadzenie do C# język oraz znasz podstawy <xref:System.Collections.Generic.List%601> klasy.

W tym samouczku oczekuje, że będziesz mieć maszyny, których można użyć do tworzenia aplikacji. Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux. Krótkie omówienie poleceń użyjesz znajduje się w [zapoznanie się z narzędziami programistycznymi](local-environment.md), wraz z łączami, aby uzyskać więcej szczegółów.

## <a name="a-basic-list-example"></a>Przykład podstawowa lista

Utwórz katalog o nazwie **samouczek**. Upewnij, że bieżącego katalogu i uruchom `dotnet new console`.

Otwórz **Program.cs** w ulubionym edytorze i Zastąp istniejący kod następującym kodem:

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

Zastąp `<name>` z Twoją nazwą. Zapisz **Program.cs**. Typ `dotnet run` w oknie konsoli do wypróbowania tej funkcji.

Została właśnie utworzona lista ciągów, dodane trzy nazwy do tej listy i drukowane nazwy w całości wielkimi. Używasz pojęcia, które wyjaśniono w samouczkach wcześniej pętli na liście.

Kod, aby wyświetlić nazwy sprawia, że użycie [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) funkcji.  Kiedy należy poprzedzić `string` z `$` kodu C# można osadzić w deklaracji ciąg znaków. Rzeczywistego ciągu zastępuje wartość, która generuje kod C#. W tym przykładzie zastępuje `{name.ToUpper()}` przy użyciu nazwy, konwertowane na wielkie litery, ponieważ wywołujesz <xref:System.String.ToUpper%2A> metody.

Możemy kontynuować Eksplorowanie.

## <a name="modify-list-contents"></a>Modyfikowanie zawartości listy

Kolekcja utworzona używa <xref:System.Collections.Generic.List%601> typu. Tego typu przechowuje elementów. Należy określić typ elementów między nawiasami.

Jednym ważnym aspektem to <xref:System.Collections.Generic.List%601> typ jest, może rosnąć lub maleć, dzięki któremu można dodawać lub usuwać elementy. Dodaj ten kod przed tagiem zamykającym `}` w `Main` metody:

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

Dwa więcej nazw zostały dodane na końcu listy. Został również usunięty jeden także. Zapisz plik i typ `dotnet run` do wypróbowania tej funkcji.

<xref:System.Collections.Generic.List%601> Umożliwia odwoływać się do pojedynczych elementów przez **indeksu** także. Umieść indeksu między `[` i `]` po nazwie listy tokenów. C#używa pierwszego indeksu 0. Dodaj następujący kod bezpośrednio poniżej kod, który właśnie został dodany, a następnie spróbuj go:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nie masz dostępu do indeksu poza koniec listy. Należy pamiętać, że indeksy rozpoczynają się od 0, dlatego największego indeksu nieprawidłowy jest jednym mniejszy niż liczba elementów na liście. Możesz sprawdzić, jak długo używa listy <xref:System.Collections.Generic.List%601.Count%2A> właściwości. Dodaj następujący kod na końcu metody Main:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Zapisz plik i typ `dotnet run` ponownie, aby zobaczyć wyniki.

## <a name="search-and-sort-lists"></a>Wyszukiwanie i sortowanie list

Nasze przykłady za pomocą list stosunkowo mały, ale aplikacje często może utworzyć listy o wiele więcej elementów, czasami numerowania w tysiącach. Aby znaleźć elementy w tych kolekcjach większe, musisz wyszukiwania na liście dla różnych elementów. <xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda wyszukuje element i zwraca indeks elementu. Dodaj następujący kod na końcu Twojej `Main` metody:

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

Można również sortować elementy na liście. <xref:System.Collections.Generic.List%601.Sort%2A> Metoda sortuje wszystkie elementy na liście w kolejności ich normalne (alfabetycznie w przypadku ciągów znaków). Dodaj następujący kod do dolnej części naszych `Main` metody:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Zapisywanie pliku i typu `dotnet run` do wypróbowania tej najnowszej wersji.

Przed rozpoczęciem następnej sekcji, Przejdźmy bieżącego kodu w oddzielnych metodach. Który sprawia, że łatwiej rozpocząć pracę z nową przykładową. Zmiana nazwy Twojego `Main` metodę, aby `WorkingWithStrings` i zapisywać nowy `Main` metodę, która wywołuje `WorkingWithStrings`. Po zakończeniu, kod powinien wyglądać następująco:

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

## <a name="lists-of-other-types"></a>Listę innych typów

Wcześniej użyto `string` typu na listach do tej pory. Upewnijmy się <xref:System.Collections.Generic.List%601> przy użyciu innego typu. Utwórzmy zbioru liczb.

Dodaj następujący kod do dolnej części nowej `Main` metody:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Który tworzy listę liczb całkowitych i ustawia pierwszych dwóch liczb całkowitych na wartości 1. Są to dwie pierwsze wartości *sekwencji Fibonacci*, sekwencji liczb. Każdy kolejny numer Fibonacci zostanie znaleziony, wykonując sumie poprzednich dwóch liczb. Dodaj następujący kod:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Zapisywanie pliku i typu `dotnet run` aby zobaczyć wyniki.

> [!TIP]
> Skoncentrować się na tylko w tej sekcji, możesz przekształcić w komentarz kod, który wywołuje `WorkingWithStrings();`. Po prostu umieść dwa `/` znaków poprzedzającymi wywołania podobnie do następującego: `// WorkingWithStrings();`.

## <a name="challenge"></a>Wyzwanie

Zobacz, można umieścić ze sobą pewne pojęcia z tego i starszych wersji lekcje. Rozwiń węzeł, na jakie dołączeniu do tej pory z międzynarodowymi numerami identyfikującymi Fibonacci. Spróbuj napisać kod, aby wygenerować pierwszych 20 cyfr w sekwencji. (Wskazówka 20 numer Fibonacci jest 6765).

## <a name="complete-challenge"></a>Ukończenie wyzwania

Przykładowe rozwiązanie, możesz zobaczyć [spojrzenie na Zakończono przykładowego kodu w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)

Z każdą iteracją pętli tworzenia ostatnich dwóch liczb całkowitych na liście sumowanie je, a następnie dodanie wartości do listy. Pętla powtarza się, aż 20 elementów zostały dodane do listy.

Gratulacje, pomyślnie ukończono samouczek listy. Możesz kontynuować [wprowadzenie do klas](introduction-to-classes.md) samouczków w środowisku projektowym.

Dowiedz się więcej o pracy z `List` wpisać [.NET — przewodnik](../../../standard/index.md) tematu [kolekcje](../../../standard/collections/index.md). Ponadto dowiesz się o innych typach kolekcji.