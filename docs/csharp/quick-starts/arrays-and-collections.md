---
title: "Przewodnik Szybki Start — kolekcje - C#"
description: "Naucz się C# eksplorując kolekcji listy, w tym szybki start."
keywords: C#, wprowadzenie, samouczek, kolekcje, lista
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 44e79432c0a1970313cba21778e2bf439f8a4388
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2018
---
# <a name="c-quick-start-collections"></a>C# szybki start: kolekcje #

To szybki start zawiera wprowadzenie do języka C# i podstawy <xref:System.Collections.Generic.List%601> klasy.

To szybki start oczekuje posiadania maszynie, która służy do tworzenia aplikacji. Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux. Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.

## <a name="a-basic-list-example"></a>Przykład podstawowa lista.

Utwórz katalog o nazwie **szybkiego startu listy**. Upewnij, że bieżący katalog i uruchom `dotnet new console`.

> [!NOTE]
> Jeśli właśnie został ukończony [Rozpoczynanie pracy z platformą .NET w ciągu 10 minut](https://www.microsoft.com/net), można nadal używać aplikacji moja_aplikacja, który został właśnie utworzony.
 
Otwórz **Program.cs** ulubionego edytora i Zastąp istniejący kod następującym kodem:

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
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

Zastąp `<name>` nazwą użytkownika. Zapisz **Program.cs**. Typ `dotnet run` w oknie konsoli Wypróbuj ją.

Utworzeniu tylko listę ciągów, dodać trzy nazwy do tej listy i wydrukowane nazwy WERSALIKÓW. Używasz pojęcia, które znasz już wcześniej Szybki Start pętli na liście.

Kod, aby wyświetlić nazwy sprawia, że użycie **ciągi interpolowane**.  Gdy poprzedzać `string` z `$` kodu C# można osadzić w deklaracji ciąg znaków. Wartość, która generuje rzeczywisty ciąg zastępuje kodu C#. W tym przykładzie zastępuje `{name.ToUpper()}` z każdej nazwy przekonwertowany na wielkie litery, ponieważ wywołana <xref:System.String.ToUpper%2A> metody.

Ta funkcja pozwala zachować eksploracji.
    
## <a name="modify-list-contents"></a>Modyfikowanie listy zawartości

Kolekcja utworzona używa <xref:System.Collections.Generic.List%601> typu. Tego typu przechowuje sekwencji elementów. Należy określić typ elementów między nawiasami.
    
Jeden ważnym aspektem tej <xref:System.Collections.Generic.List%601> typ jest czy można zwiększać i zmniejszać, dzięki któremu można dodać lub usunąć elementy. Dodaj ten kod przed tagiem zamykającym `}` w `Main` metody:

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

Dodano dwa więcej nazw na końcu listy. Możesz również usunięto jedną również. Zapisz plik i typ `dotnet run` Wypróbuj ją.
    
<xref:System.Collections.Generic.List%601> Umożliwia odwoływać się do poszczególnych elementów przez **indeksu** również. Umieść wskaźnik między `[` i `]` po nazwie listy tokenów. C# używa 0 dla pierwszego indeksu. Dodaj ten kod bezpośrednio poniżej kod, który właśnie został dodany i spróbuj go:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Nie można uzyskać dostępu do indeksu poza koniec listy. Należy pamiętać, że indeksów zaczynają się od 0, dlatego największy prawidłowy indeks jest jednym mniejszy niż liczba elementów na liście. Możesz sprawdzić, jak długo używa listy <xref:System.Collections.Generic.List%601.Count%2A> właściwości. Dodaj następujący kod na końcu metody Main:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Zapisz plik i typ `dotnet run` ponownie, aby wyświetlić wyniki.    

## <a name="search-and-sort-lists"></a>Wyszukiwanie i sortowanie listy
Nasze przykłady za pomocą list stosunkowo mały, ale aplikacje często może tworzyć listy o wiele więcej elementów, czasami numerowanie tysięcy. Aby znaleźć elementy w tych kolekcjach większy, musisz Wyszukaj liście różne elementy. <xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda szuka elementu i zwraca indeks elementu. Dodaj ten kod do dolnej części Twojego `Main` metody:

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

Elementy na liście mogą być również sortowane. <xref:System.Collections.Generic.List%601.Sort%2A> Metody sortuje wszystkie elementy na liście w ich normalnym kolejność (alfabetycznie w przypadku ciągi). Dodaj ten kod do dołu naszych `Main` metody:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Zapisz plik i typ `dotnet run` próby najnowsza wersja.

Przed rozpoczęciem następnej sekcji przejdziemy bieżącego kodu w oddzielnych metodach. Który ułatwia rozpoczęcie pracy z nowego przykład. Zmień nazwę Twojej `Main` metodę `WorkingWithStrings` i zapisać nową `Main` — metoda, która wywołuje `WorkingWithStrings`. Po zakończeniu, kod powinien wyglądać następująco:

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
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

Obecnie używasz `string` typu na listach wykonanej do tej pory. Upewnijmy <xref:System.Collections.Generic.List%601> przy użyciu innego typu. Utworzymy zbioru liczb. 

Dodaj następującą wartość do dołu nowej `Main` metody:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Która tworzy listę liczb całkowitych i ustawia pierwszych dwóch liczb całkowitych na wartości 1. Są to pierwsze dwie wartości *sekwencji Fibonacci*, sekwencji liczb. Znaleziono każdej kolejny numer Fibonacci wykonując Suma poprzednich dwóch liczb. Dodaj ten kod:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Zapisz plik i typ `dotnet run` wyników. 

> [!TIP]
> Aby skoncentrować się na tylko w tej sekcji, możesz przekształcić w komentarz kod, który wywołuje `WorkingWithStrings();`. Po prostu umieść dwa `/` znaków przed wywołanie podobnie do następującej: `// WorkingWithStrings();`. 

## <a name="challenge"></a>żądanie
Zobacz, czy można utworzyć niektóre z pojęć związanych z tej i starszych wersji — lekcje. Rozwiń węzeł, na co powstanie wykonanej do tej pory numerami Fibonacci. Spróbuj napisać kod, aby wygenerować najpierw 20 cyfr w sekwencji. (Jako wskazówki, 20 numer Fibonacci jest 6765).

## <a name="complete-challenge"></a>Żądanie ukończone

Widać przykład rozwiązania przez [patrzeć Zakończono przykładowy kod w witrynie GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)

Przy każdej iteracji pętli tworzenia ostatnich dwóch liczb całkowitych na liście sumowanie je, a następnie dodanie tej wartości na liście. Pętla jest powtarzany aż 20 elementy dodane do listy.

Gratulacje, przeprowadzisz listy szybki start. Można kontynuować [wprowadzenie do klasy](introduction-to-classes.md) szybki start w środowisku projektowania.

Dowiedz się więcej o pracy z `List` wpisz [.NET przewodnik](../../standard/index.md) temat [kolekcje](../../standard/collections/index.md). Dowiesz się o innych typów kolekcji.
