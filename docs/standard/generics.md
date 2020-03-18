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
# <a name="generic-types-overview"></a><span data-ttu-id="cc18f-103">Omówienie typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="cc18f-103">Generic types overview</span></span>

<span data-ttu-id="cc18f-104">Deweloperzy używają typów ogólnych przez cały czas w .NET, czy niejawnie lub jawnie.</span><span class="sxs-lookup"><span data-stu-id="cc18f-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="cc18f-105">Czy podczas korzystania z linq w .NET kiedykolwiek zauważyłeś, że pracujesz z <xref:System.Collections.Generic.IEnumerable%601>?</span><span class="sxs-lookup"><span data-stu-id="cc18f-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="cc18f-106">Lub jeśli kiedykolwiek widziałeś online próbki "ogólne repozytorium" do rozmowy z bazami danych przy użyciu entity\<framework, czy widzisz, że większość metod zwraca IQueryable T>?</span><span class="sxs-lookup"><span data-stu-id="cc18f-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable\<T>?</span></span> <span data-ttu-id="cc18f-107">Być może zastanawialiście się, co **T** jest w tych przykładach i dlaczego tam jest.</span><span class="sxs-lookup"><span data-stu-id="cc18f-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="cc18f-108">Po raz pierwszy wprowadzony w .NET Framework 2.0, **generyki** są zasadniczo "szablon kodu", który umożliwia deweloperom definiowanie struktur danych [bezpieczne dla typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) bez zatwierdzania do rzeczywistego typu danych.</span><span class="sxs-lookup"><span data-stu-id="cc18f-108">First introduced in the .NET Framework 2.0, **generics** are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="cc18f-109">Na przykład <xref:System.Collections.Generic.List%601> jest [zbiorem ogólnym,](xref:System.Collections.Generic) który może być zadeklarowany i używany z dowolnym typem, takim jak `List<int>`, `List<string>`lub `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="cc18f-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="cc18f-110">Aby zrozumieć, dlaczego leki ogólne są przydatne, przyjrzyjmy się określonej <xref:System.Collections.ArrayList>klasie przed i po dodaniu leków generycznych: .</span><span class="sxs-lookup"><span data-stu-id="cc18f-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="cc18f-111">W programie .NET Framework `ArrayList` 1.0 <xref:System.Object>elementy były typu .</span><span class="sxs-lookup"><span data-stu-id="cc18f-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="cc18f-112">Oznaczało to, że każdy dodany `Object`element został po cichu przekształcony w plik .</span><span class="sxs-lookup"><span data-stu-id="cc18f-112">This meant that any element added was silently converted into an `Object`.</span></span> <span data-ttu-id="cc18f-113">To samo stanie się podczas odczytywania elementów z listy.</span><span class="sxs-lookup"><span data-stu-id="cc18f-113">The same would happen when reading the elements from the list.</span></span> <span data-ttu-id="cc18f-114">Proces ten jest znany jako [boks i rozpakowywanie](../csharp/programming-guide/types/boxing-and-unboxing.md), i to wpływa na wydajność.</span><span class="sxs-lookup"><span data-stu-id="cc18f-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="cc18f-115">Co więcej, jednak nie ma sposobu, aby określić typ danych na liście w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cc18f-115">More than that, however, there's no way to determine the type of data in the list at compile time.</span></span> <span data-ttu-id="cc18f-116">To sprawia, że niektóre kruche kodu.</span><span class="sxs-lookup"><span data-stu-id="cc18f-116">This makes for some fragile code.</span></span> <span data-ttu-id="cc18f-117">Rodzajowe rozwiązać ten problem, definiując typ danych każde wystąpienie listy będzie zawierać.</span><span class="sxs-lookup"><span data-stu-id="cc18f-117">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="cc18f-118">Na przykład można dodawać tylko liczby `List<int>` całkowite do i `List<Person>`dodawać tylko osoby do .</span><span class="sxs-lookup"><span data-stu-id="cc18f-118">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="cc18f-119">Rodzajowe są również dostępne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cc18f-119">Generics are also available at runtime.</span></span> <span data-ttu-id="cc18f-120">Oznacza to, że czas wykonywania wie, jakiego typu struktury danych używasz i można przechowywać go w pamięci bardziej efektywnie.</span><span class="sxs-lookup"><span data-stu-id="cc18f-120">This means the runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="cc18f-121">W poniższym przykładzie przedstawiono mały program, który ilustruje wydajność znajomości typu struktury danych w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="cc18f-121">The following example is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="cc18f-122">Ten program generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="cc18f-122">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="cc18f-123">Pierwszą rzeczą, którą można zauważyć w tym miejscu jest to, że sortowanie listy ogólnej jest znacznie szybsze niż sortowanie listy nierodzajowej.</span><span class="sxs-lookup"><span data-stu-id="cc18f-123">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="cc18f-124">Można również zauważyć, że typ dla listy ogólnej jest odrębny ([System.Int32]), podczas gdy typ dla listy nierodzajowej jest uogólniony.</span><span class="sxs-lookup"><span data-stu-id="cc18f-124">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="cc18f-125">Ponieważ czas wykonywania `List<int>` wie, <xref:System.Int32>że rodzajowy jest typu , można przechowywać elementy listy w `ArrayList` podstawowej tablicy całkowitej w pamięci, podczas gdy nierodzajowy musi oddać każdy element listy do obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc18f-125">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="cc18f-126">Jak pokazano w tym przykładzie, dodatkowe rzuty zajmują czas i spowalniają sortowanie listy.</span><span class="sxs-lookup"><span data-stu-id="cc18f-126">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="cc18f-127">Dodatkową zaletą środowiska uruchomieniowego znając typ ogólnego jest lepsze środowisko debugowania.</span><span class="sxs-lookup"><span data-stu-id="cc18f-127">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="cc18f-128">Podczas debugowania ogólne w języku C#, wiesz, jaki typ każdego elementu jest w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="cc18f-128">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="cc18f-129">Bez leków ogólnych, nie masz pojęcia, jaki typ był każdy element.</span><span class="sxs-lookup"><span data-stu-id="cc18f-129">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc18f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc18f-130">See also</span></span>

- [<span data-ttu-id="cc18f-131">Przewodnik programowania Języka C# — leki ogólne</span><span class="sxs-lookup"><span data-stu-id="cc18f-131">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
