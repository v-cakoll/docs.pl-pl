---
title: Ogólny omówienie typów ogólnych (ogólnych)
description: Dowiedz się, jak leki ogólne działają jako szablony kodu, które umożliwiają definiowanie struktur danych bezpiecznych dla typu bez zatwierdzania rzeczywistego typu danych.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 3c1181f5be717f328ae906c6009fc8a34b904c89
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "61923854"
---
# <a name="generic-types-overview"></a>Omówienie typów ogólnych

Deweloperzy używają typów ogólnych przez cały czas w .NET, czy niejawnie lub jawnie. Czy podczas korzystania z linq w .NET kiedykolwiek zauważyłeś, że pracujesz z <xref:System.Collections.Generic.IEnumerable%601>? Lub jeśli kiedykolwiek widziałeś online próbki "ogólne repozytorium" do rozmowy z bazami danych przy użyciu entity\<framework, czy widzisz, że większość metod zwraca IQueryable T>? Być może zastanawialiście się, co **T** jest w tych przykładach i dlaczego tam jest.

Po raz pierwszy wprowadzony w .NET Framework 2.0, **generyki** są zasadniczo "szablon kodu", który umożliwia deweloperom definiowanie struktur danych [bezpieczne dla typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) bez zatwierdzania do rzeczywistego typu danych. Na przykład <xref:System.Collections.Generic.List%601> jest [zbiorem ogólnym,](xref:System.Collections.Generic) który może być zadeklarowany i używany z dowolnym typem, takim jak `List<int>`, `List<string>`lub `List<Person>`.

Aby zrozumieć, dlaczego leki ogólne są przydatne, przyjrzyjmy się określonej <xref:System.Collections.ArrayList>klasie przed i po dodaniu leków generycznych: . W programie .NET Framework `ArrayList` 1.0 <xref:System.Object>elementy były typu . Oznaczało to, że każdy dodany `Object`element został po cichu przekształcony w plik . To samo stanie się podczas odczytywania elementów z listy. Proces ten jest znany jako [boks i rozpakowywanie](../csharp/programming-guide/types/boxing-and-unboxing.md), i to wpływa na wydajność. Co więcej, jednak nie ma sposobu, aby określić typ danych na liście w czasie kompilacji. To sprawia, że niektóre kruche kodu. Rodzajowe rozwiązać ten problem, definiując typ danych każde wystąpienie listy będzie zawierać. Na przykład można dodawać tylko liczby `List<int>` całkowite do i `List<Person>`dodawać tylko osoby do .

Rodzajowe są również dostępne w czasie wykonywania. Oznacza to, że czas wykonywania wie, jakiego typu struktury danych używasz i można przechowywać go w pamięci bardziej efektywnie.

W poniższym przykładzie przedstawiono mały program, który ilustruje wydajność znajomości typu struktury danych w czasie wykonywania:

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

Pierwszą rzeczą, którą można zauważyć w tym miejscu jest to, że sortowanie listy ogólnej jest znacznie szybsze niż sortowanie listy nierodzajowej. Można również zauważyć, że typ dla listy ogólnej jest odrębny ([System.Int32]), podczas gdy typ dla listy nierodzajowej jest uogólniony. Ponieważ czas wykonywania `List<int>` wie, <xref:System.Int32>że rodzajowy jest typu , można przechowywać elementy listy w `ArrayList` podstawowej tablicy całkowitej w pamięci, podczas gdy nierodzajowy musi oddać każdy element listy do obiektu. Jak pokazano w tym przykładzie, dodatkowe rzuty zajmują czas i spowalniają sortowanie listy.

Dodatkową zaletą środowiska uruchomieniowego znając typ ogólnego jest lepsze środowisko debugowania. Podczas debugowania ogólne w języku C#, wiesz, jaki typ każdego elementu jest w strukturze danych. Bez leków ogólnych, nie masz pojęcia, jaki typ był każdy element.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania Języka C# — leki ogólne](../../docs/csharp/programming-guide/generics/index.md)
