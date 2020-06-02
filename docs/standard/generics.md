---
title: Typy ogólne (ogólne) — Omówienie
description: Dowiedz się, w jaki sposób typy ogólne działają jako szablony kodu, które umożliwiają definiowanie bezpiecznych dla typu struktur danych bez przekazywania ich do rzeczywistego typu danych.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 99e3b589cd67c9d7026966d3d48d0e06a91fcc86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287548"
---
# <a name="generic-types-overview"></a>Przegląd typów ogólnych

Deweloperzy używają typów ogólnych przez cały czas w programie .NET, niezależnie od tego, czy jest to jawnie, czy niejawnie. Kiedy używasz LINQ w programie .NET, czy wiesz, że pracujesz z <xref:System.Collections.Generic.IEnumerable%601> ? Lub jeśli kiedykolwiek zdarzyło Ci się korzystać z przykładu online "ogólnego repozytorium" do nawiązywania komunikacji z bazami danych przy użyciu Entity Framework, zobaczysz, że większość metod zwraca `IQueryable<T>` ? Być może zastanawiasz się, co znajduje się w tych przykładach i dlaczego znajduje się **w tym miejscu** .

Po raz pierwszy wprowadzona w .NET Framework 2,0, typy ogólne są zasadniczo "szablonem kodu", dzięki czemu deweloperzy mogą definiować [bezpieczne dla typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) struktury danych bez przekazywania ich do rzeczywistego typu danych. Na przykład <xref:System.Collections.Generic.List%601> to [Ogólna kolekcja](xref:System.Collections.Generic) , która może być zadeklarowana i używana z dowolnym typem, takim jak `List<int>` , `List<string>` lub `List<Person>` .

Aby zrozumieć, dlaczego typy ogólne są przydatne, przyjrzyjmy się określonej klasie przed i po dodaniu typów ogólnych: <xref:System.Collections.ArrayList> . W .NET Framework 1,0 `ArrayList` elementy były typu <xref:System.Object> . Każdy element dodany do kolekcji został dyskretnie przekonwertowany na `Object` . Taka sytuacja miałaby miejsce podczas odczytywania elementów z listy. Ten proces jest nazywany [opakowaniem i rozpakowywaniem](../csharp/programming-guide/types/boxing-and-unboxing.md)i ma wpływ na wydajność. Poza wydajnością nie ma jednak możliwości określenia typu danych na liście w czasie kompilacji, co sprawia, że jest to niedelikatny kod. Typy ogólne rozwiązują ten problem przez zdefiniowanie typu danych, które będą zawierać każde wystąpienie listy. Na przykład można dodawać tylko liczby całkowite do `List<int>` i dodawać tylko osoby do `List<Person>` .

Typy ogólne są również dostępne w czasie wykonywania. Środowisko uruchomieniowe wie, jakiego typu struktura danych używasz i może być bardziej wydajnie przechowywana w pamięci.

Poniższy przykład jest małym programem, który ilustruje efektywność znajomości typu struktury danych w czasie wykonywania:

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

Ten program generuje dane wyjściowe podobne do następujących:

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

W pierwszej kolejności można zauważyć, że sortowanie listy ogólnej jest znacznie szybsze niż sortowanie listy nieogólnej. Można również zauważyć, że typ listy ogólnej to DISTINCT ([System. Int32]), podczas gdy typ dla listy nieogólnej jest uogólniony. Ponieważ środowisko uruchomieniowe wie, że ogólny `List<int>` jest typu <xref:System.Int32> , może przechowywać elementy listy w źródłowej tablicy liczb całkowitych w pamięci, podczas gdy nieogólny `ArrayList` musi rzutować każdy element listy na obiekt. Jak pokazano w tym przykładzie, dodatkowe rzuty zajmują czas i spowalniają sortowanie listy.

Dodatkową zaletą środowiska uruchomieniowego, wiedząc, że typ ogólny jest lepszym rozwiązaniem debugowania. Gdy debugujesz ogólne w języku C#, wiesz, jaki typ każdy element znajduje się w strukturze danych. Bez typów ogólnych nie ma żadnego pomysłu na to, co typ każdy element był.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C# — typy ogólne](../csharp/programming-guide/generics/index.md)
