---
title: Omówienie typów ogólnych (generycznych)
description: Dowiedz się, jak ogólne działają jako szablony kodu, które umożliwiają definiowanie struktur danych bezpiecznych dla typu bez powiązania rzeczywistego typu danych.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: f51d69088b0d5c798f3aa3a6c1f5b62b3ea81d39
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635281"
---
# <a name="generic-types-overview"></a>Omówienie typów ogólnych

Deweloperzy używają generycznych cały czas w .NET, czy niejawnie lub jawnie. Kiedy używasz LINQ w .NET, czy kiedykolwiek zauważyłeś, że pracujesz z? <xref:System.Collections.Generic.IEnumerable%601> Lub jeśli kiedykolwiek widziałeś online próbki "ogólnego repozytorium" do rozmowy z bazami danych `IQueryable<T>`za pomocą Entity Framework, czy widzisz, że większość metod powrót? Być może zastanawialiście się, co **T** jest w tych przykładach i dlaczego tam jest.

Po raz pierwszy wprowadzone w .NET Framework 2.0, ogólne są zasadniczo "szablon kodu", który pozwala deweloperom zdefiniować struktury danych [bezpieczne dla typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) bez pojmowania rzeczywistego typu danych. Na przykład <xref:System.Collections.Generic.List%601> jest [ogólną kolekcją,](xref:System.Collections.Generic) która może być `List<int>`zadeklarowana i używana z dowolnym typem, takim jak , `List<string>`lub `List<Person>`.

Aby zrozumieć, dlaczego leki generyczne są przydatne, przyjrzyjmy <xref:System.Collections.ArrayList>się określonej klasie przed i po dodaniu leków generycznych: . W programie .NET Framework 1.0 `ArrayList` <xref:System.Object>elementy były typu . Każdy element dodany do kolekcji został `Object`po cichu przekształcony w plik . To samo miałoby miejsce podczas czytania elementów z listy. Proces ten jest znany jako [boks i unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), i to wpływa na wydajność. Oprócz wydajności, jednak nie ma sposobu, aby określić typ danych na liście w czasie kompilacji, co sprawia, że dla niektórych delikatny kod. Ogólne rozwiązać ten problem, definiując typ danych każde wystąpienie listy będzie zawierać. Na przykład można dodawać liczby całkowite `List<int>` tylko do i `List<Person>`tylko dodawać osoby do .

Generyki są również dostępne w czasie wykonywania. Środowisko wykonawcze wie, jakiego typu struktury danych używasz i można przechowywać go w pamięci bardziej efektywnie.

Poniższy przykład jest mały program, który ilustruje wydajność znając typ struktury danych w czasie wykonywania:

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

Pierwszą rzeczą, którą można zauważyć w tym miejscu jest to, że sortowanie listy rodzajowej jest znacznie szybsze niż sortowanie listy nierodzgonej. Można również zauważyć, że typ dla listy rodzajowej jest odrębny ([System.Int32]), podczas gdy typ listy nieogólnej jest uogólniony. Ponieważ środowisko wykonawcze `List<int>` wie, <xref:System.Int32>że rodzajowy jest typu, może przechowywać elementy listy w podstawowej tablicy liczby całkowitej w pamięci, podczas gdy niegeneryczne `ArrayList` musi rzutować każdy element listy do obiektu. Jak pokazano w tym przykładzie, dodatkowe rzutowania zajmują czas i spowalniają sortowanie listy.

Dodatkową zaletą środowiska wykonawczego znając typ ogólnego jest lepsze środowisko debugowania. Podczas debugowania ogólnego w języku C#, wiesz, jaki typ każdego elementu jest w strukturze danych. Bez generycznych, nie masz pojęcia, jaki typ każdego elementu był.

## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania - Generyki](../../docs/csharp/programming-guide/generics/index.md)
