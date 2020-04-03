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
# <a name="generic-types-overview"></a><span data-ttu-id="769e6-103">Omówienie typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="769e6-103">Generic types overview</span></span>

<span data-ttu-id="769e6-104">Deweloperzy używają generycznych cały czas w .NET, czy niejawnie lub jawnie.</span><span class="sxs-lookup"><span data-stu-id="769e6-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="769e6-105">Kiedy używasz LINQ w .NET, czy kiedykolwiek zauważyłeś, że pracujesz z? <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="769e6-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="769e6-106">Lub jeśli kiedykolwiek widziałeś online próbki "ogólnego repozytorium" do rozmowy z bazami danych `IQueryable<T>`za pomocą Entity Framework, czy widzisz, że większość metod powrót?</span><span class="sxs-lookup"><span data-stu-id="769e6-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return `IQueryable<T>`?</span></span> <span data-ttu-id="769e6-107">Być może zastanawialiście się, co **T** jest w tych przykładach i dlaczego tam jest.</span><span class="sxs-lookup"><span data-stu-id="769e6-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="769e6-108">Po raz pierwszy wprowadzone w .NET Framework 2.0, ogólne są zasadniczo "szablon kodu", który pozwala deweloperom zdefiniować struktury danych [bezpieczne dla typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) bez pojmowania rzeczywistego typu danych.</span><span class="sxs-lookup"><span data-stu-id="769e6-108">First introduced in the .NET Framework 2.0, generics are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="769e6-109">Na przykład <xref:System.Collections.Generic.List%601> jest [ogólną kolekcją,](xref:System.Collections.Generic) która może być `List<int>`zadeklarowana i używana z dowolnym typem, takim jak , `List<string>`lub `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="769e6-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="769e6-110">Aby zrozumieć, dlaczego leki generyczne są przydatne, przyjrzyjmy <xref:System.Collections.ArrayList>się określonej klasie przed i po dodaniu leków generycznych: .</span><span class="sxs-lookup"><span data-stu-id="769e6-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="769e6-111">W programie .NET Framework 1.0 `ArrayList` <xref:System.Object>elementy były typu .</span><span class="sxs-lookup"><span data-stu-id="769e6-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="769e6-112">Każdy element dodany do kolekcji został `Object`po cichu przekształcony w plik .</span><span class="sxs-lookup"><span data-stu-id="769e6-112">Any element added to the collection was silently converted into an `Object`.</span></span> <span data-ttu-id="769e6-113">To samo miałoby miejsce podczas czytania elementów z listy.</span><span class="sxs-lookup"><span data-stu-id="769e6-113">The same would happen when reading elements from the list.</span></span> <span data-ttu-id="769e6-114">Proces ten jest znany jako [boks i unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), i to wpływa na wydajność.</span><span class="sxs-lookup"><span data-stu-id="769e6-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="769e6-115">Oprócz wydajności, jednak nie ma sposobu, aby określić typ danych na liście w czasie kompilacji, co sprawia, że dla niektórych delikatny kod.</span><span class="sxs-lookup"><span data-stu-id="769e6-115">Aside from performance, however, there's no way to determine the type of data in the list at compile time, which makes for some fragile code.</span></span> <span data-ttu-id="769e6-116">Ogólne rozwiązać ten problem, definiując typ danych każde wystąpienie listy będzie zawierać.</span><span class="sxs-lookup"><span data-stu-id="769e6-116">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="769e6-117">Na przykład można dodawać liczby całkowite `List<int>` tylko do i `List<Person>`tylko dodawać osoby do .</span><span class="sxs-lookup"><span data-stu-id="769e6-117">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="769e6-118">Generyki są również dostępne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="769e6-118">Generics are also available at run time.</span></span> <span data-ttu-id="769e6-119">Środowisko wykonawcze wie, jakiego typu struktury danych używasz i można przechowywać go w pamięci bardziej efektywnie.</span><span class="sxs-lookup"><span data-stu-id="769e6-119">The runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="769e6-120">Poniższy przykład jest mały program, który ilustruje wydajność znając typ struktury danych w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="769e6-120">The following example is a small program that illustrates the efficiency of knowing the data structure type at run time:</span></span>

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

<span data-ttu-id="769e6-121">Ten program generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="769e6-121">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="769e6-122">Pierwszą rzeczą, którą można zauważyć w tym miejscu jest to, że sortowanie listy rodzajowej jest znacznie szybsze niż sortowanie listy nierodzgonej.</span><span class="sxs-lookup"><span data-stu-id="769e6-122">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="769e6-123">Można również zauważyć, że typ dla listy rodzajowej jest odrębny ([System.Int32]), podczas gdy typ listy nieogólnej jest uogólniony.</span><span class="sxs-lookup"><span data-stu-id="769e6-123">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="769e6-124">Ponieważ środowisko wykonawcze `List<int>` wie, <xref:System.Int32>że rodzajowy jest typu, może przechowywać elementy listy w podstawowej tablicy liczby całkowitej w pamięci, podczas gdy niegeneryczne `ArrayList` musi rzutować każdy element listy do obiektu.</span><span class="sxs-lookup"><span data-stu-id="769e6-124">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory, while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="769e6-125">Jak pokazano w tym przykładzie, dodatkowe rzutowania zajmują czas i spowalniają sortowanie listy.</span><span class="sxs-lookup"><span data-stu-id="769e6-125">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="769e6-126">Dodatkową zaletą środowiska wykonawczego znając typ ogólnego jest lepsze środowisko debugowania.</span><span class="sxs-lookup"><span data-stu-id="769e6-126">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="769e6-127">Podczas debugowania ogólnego w języku C#, wiesz, jaki typ każdego elementu jest w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="769e6-127">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="769e6-128">Bez generycznych, nie masz pojęcia, jaki typ każdego elementu był.</span><span class="sxs-lookup"><span data-stu-id="769e6-128">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="769e6-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="769e6-129">See also</span></span>

- [<span data-ttu-id="769e6-130">C# Przewodnik programowania - Generyki</span><span class="sxs-lookup"><span data-stu-id="769e6-130">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
