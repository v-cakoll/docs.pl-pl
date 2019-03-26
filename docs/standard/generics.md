---
title: Ogólne typy (Ogólne) — omówienie
description: Dowiedz się, jak ogólne działają jako szablony kodu, które umożliwiają zdefiniowanie struktury danych bezpiecznego typu nie poświęcając na to rzeczywisty typ danych.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 3c1181f5be717f328ae906c6009fc8a34b904c89
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465428"
---
# <a name="generic-types-overview"></a>Przegląd typów ogólnych

Deweloperzy używaj typów ogólnych przez cały czas na platformie .NET, czy jawnie lub niejawnie. Korzystając z programu LINQ na platformie .NET, nigdy nie Zwróć uwagę, że pracujesz z <xref:System.Collections.Generic.IEnumerable%601>? Lub Jeśli nigdy nie był wyświetlany próbki online "ogólnego repozytorium" do rozmowy baz danych przy użyciu platformy Entity Framework, czy zobaczysz, że większość metod zwracają IQueryable\<T >? Użytkownik może być bardziej co **T** znajduje się w tych przykładach i dlaczego jest tam.

Po raz pierwszy wprowadzone w programie .NET Framework 2.0 **ogólne** są zasadniczo "kodu szablon", umożliwia deweloperom definiowanie [bezpieczny](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) struktur danych, nie poświęcając na to rzeczywisty typ danych. Na przykład <xref:System.Collections.Generic.List%601> jest [kolekcji generycznej](xref:System.Collections.Generic) , zadeklarowany i używać z dowolnego typu, takie jak `List<int>`, `List<string>`, lub `List<Person>`.

Aby zrozumieć, dlaczego typy ogólne są przydatne, Przyjrzyjmy się w określonej klasie przed i po dodaniu ogólne: <xref:System.Collections.ArrayList>. W programie .NET Framework 1.0 `ArrayList` elementy były typu <xref:System.Object>. Oznacza to, że dowolny element dodany został dyskretnie konwertowane na `Object`. Taka sama sytuacja może mieć miejsce podczas odczytywania elementów z listy. Ten proces jest nazywany [opakowywanie i rozpakowywanie](../csharp/programming-guide/types/boxing-and-unboxing.md), i ma wpływ na wydajność. Więcej niż ten jednak nie ma możliwości można ustalić typu danych na liście w czasie kompilacji. To sprawia, że niektóre słabe kodu. Typy ogólne rozwiązują ten problem przez zdefiniowanie typu danych, który będzie zawarty w każde wystąpienie listy. Na przykład, można dodawać tylko liczb całkowitych na `List<int>` i dodawać tylko osoby, które mają `List<Person>`.

Typy ogólne są również dostępne w czasie wykonywania. Oznacza to, że środowisko uruchomieniowe wie, jakiego rodzaju strukturę danych używasz i będą przechowywane jego efektywniej w pamięci.

Poniższy przykład jest mały program, który przedstawia wydajność, wiedząc, dane struktury typu w czasie wykonywania:

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

Ten program tworzy dane wyjściowe podobne do następujących:

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

Pierwszą rzeczą, jaką można zauważyć, że w tym miejscu jest sortowanie listy ogólnej jest znacznie szybsze niż sortowanie listy nieogólnego. Można też zauważyć typu listy ogólnej to odrębne ([System.Int32]), natomiast typ listy nieogólnego jest uogólniona. Ponieważ środowisko uruchomieniowe wie ogólnego `List<int>` typu <xref:System.Int32>, może ona przechowywać elementy listy w podstawowej tablicę liczb całkowitych w pamięci podczas niepodstawowy `ArrayList` ma rzutowanie każdego elementu listy do obiektu. Jak pokazano w tym przykładzie dodatkowe rzutowania zajmuje czasu i spowolnić sortowanie listy.

Dodatkową zaletą środowiska uruchomieniowego, wiedząc, typ ogólny usługi jest to lepszy proces debugowania. Podczas debugowania zwykłego w języku C#, wiadomo, jakiego typu każdy element jest w strukturze danych. Bez ogólne czy nie masz jakiego typu została każdego elementu.

## <a name="see-also"></a>Zobacz także

- [C# Programming Guide - ogólne](../../docs/csharp/programming-guide/generics/index.md)
