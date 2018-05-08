---
title: Ogólne typy (Ogólne) — omówienie
description: Dowiedz się, jak ogólne działanie jako kod szablonów, które umożliwiają zdefiniowanie struktury danych bezpieczny, nie poświęcając na to rzeczywisty typ danych.
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.openlocfilehash: ad6216998dff70ca7e36b52b374c5ffb9fd0cd45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generic-types-generics-overview"></a>Ogólne typy (Ogólne) — omówienie

Używamy ogólne cały czas w języku C#, czy jawnie lub niejawnie. Korzystając z LINQ w C#, kiedykolwiek Zwróć uwagę, że korzystasz z interfejsu IEnumerable<T>? Lub jeśli kiedykolwiek widać online próbki "repository ogólnego" do rozmowy baz danych przy użyciu programu Entity Framework, czy widoczny czy większości metod zwracać interfejs IQueryable<T>? Użytkownik może zaawansowanych co **T** znajduje się w tych przykładach i dlaczego jest w nim?

Po raz pierwszy wprowadzone do programu .NET Framework 2.0, ogólne zaangażowany zmiany języka C# i środowiska uruchomieniowego języka wspólnego (CLR). **Typy ogólne** są zasadniczo "kod szablonu" który umożliwia deweloperom Zdefiniuj [bezpieczne](https://msdn.microsoft.com/library/hbzz1a9a.aspx) struktury danych, nie poświęcając na to rzeczywisty typ danych. Na przykład `List<T>` jest [kolekcji ogólnej](xref:System.Collections.Generic) który zadeklarowany i używane w przypadku każdego typu: `List<int>`, `List<string>`, `List<Person>`itp.

Tak co to jest punkt? Typy ogólne są przydatne Aby to zrozumieć, należy spojrzeć na określonej klasy przed i po dodaniu typów ogólnych. Przyjrzyjmy się `ArrayList`. W języku C# 1.0 `ArrayList` elementy zostały typu `object`. Oznacza to, że dowolny element, który został dodany dyskretnie został przekonwertowany na `object`; tym samym co się dzieje na odczyt elementów na liście (ten proces jest nazywany [boxing](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md) i konwersja unboxing odpowiednio). Opakowywanie i rozpakowywanie wpływają na wydajność. Więcej niż ta ponieważ nie ma można sprawdzić w czasie kompilacji, co jest rzeczywisty typ danych na liście. Dzięki temu wrażliwych kodu. Typy ogólne rozwiązać ten problem, udostępniając dodatkowe informacje typu danych, który będzie zawierać każde wystąpienie listy. Po prostu umieść, można dodawać tylko liczb całkowitych na `List<int>` i osoby, które mają być dodawane tylko `List<Person>`itp.

Typy ogólne są również dostępne w czasie wykonywania, lub **reified**. Oznacza to, że środowisko wykonawcze wie, jakiego rodzaju struktury danych używany i nie można przechowywać go wydajniej w pamięci.

W tym miejscu jest mały program, który przedstawia wydajność wiedząc danych struktury typu w czasie wykonywania:

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

Ten program daje następujące dane wyjściowe:

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

Pierwszą czynnością, którą można zauważyć, że w tym miejscu jest sortowanie listy ogólnej jest znacznie szybsze niż listy nierodzajową. Można również zauważyć, że typu listy ogólnej jest różne ([System.Int32]), podczas gdy uogólniony typu listy nierodzajową. Ponieważ środowisko uruchomieniowe zna ogólnego `List<int>` jest typu int umożliwia przechowywanie listy elementów w tablicy źródłowej całkowitą w pamięci podczas nieogólnego `ArrayList` ma można rzutować każdego elementu listy jako obiekt jako przechowywane w tablicy obiektów w pamięci. Jak widoczny w tym przykładzie, dodatkowe odlewów zajmuje czasu i spowolnić sortowanie listy.

Ostatnim etapem przydatne informacje o środowisku uruchomieniowym, znajomość typu zwykłego użytkownika jest działanie lepiej debugowania. Podczas debugowania ogólnego w języku C#, wiesz, jakiego typu jest każdego elementu w strukturze danych. Bez ogólne trzeba nie wiadomo typ każdego elementu.

## <a name="further-reading-and-resources"></a>Dalsze informacje i zasoby

*   [Wprowadzenie do typami ogólnymi C#](https://msdn.microsoft.com/library/ms379564.aspx)
*   [C# przewodnik programowania w języku — ogólne](../../docs/csharp/programming-guide/generics/index.md)
