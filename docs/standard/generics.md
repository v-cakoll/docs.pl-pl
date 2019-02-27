---
title: Ogólne typy (Ogólne) — omówienie
description: Dowiedz się, jak ogólne działają jako szablony kodu, które umożliwiają zdefiniowanie struktury danych bezpiecznego typu nie poświęcając na to rzeczywisty typ danych.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 991e3800e1302843db0dc1c57ed3a7e4becd298e
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835294"
---
# <a name="generic-types-overview"></a><span data-ttu-id="e480f-103">Przegląd typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="e480f-103">Generic types overview</span></span>

<span data-ttu-id="e480f-104">Deweloperzy używaj typów ogólnych przez cały czas na platformie .NET, czy jawnie lub niejawnie.</span><span class="sxs-lookup"><span data-stu-id="e480f-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="e480f-105">Korzystając z programu LINQ na platformie .NET, nigdy nie Zwróć uwagę, że pracujesz z <xref:System.Collections.Generic.IEnumerable%601>?</span><span class="sxs-lookup"><span data-stu-id="e480f-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="e480f-106">Lub Jeśli nigdy nie był wyświetlany próbki online "ogólnego repozytorium" do rozmowy baz danych przy użyciu platformy Entity Framework, czy zobaczysz, że większość metod zwracają IQueryable<T>?</span><span class="sxs-lookup"><span data-stu-id="e480f-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="e480f-107">Użytkownik może być bardziej co **T** znajduje się w tych przykładach i dlaczego jest tam.</span><span class="sxs-lookup"><span data-stu-id="e480f-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="e480f-108">Po raz pierwszy wprowadzone w programie .NET Framework 2.0 **ogólne** są zasadniczo "kodu szablon", umożliwia deweloperom definiowanie [bezpieczny](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) struktur danych, nie poświęcając na to rzeczywisty typ danych.</span><span class="sxs-lookup"><span data-stu-id="e480f-108">First introduced in the .NET Framework 2.0, **generics** are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="e480f-109">Na przykład <xref:System.Collections.Generic.List%601> jest [kolekcji generycznej](xref:System.Collections.Generic) , zadeklarowany i używać z dowolnego typu, takie jak `List<int>`, `List<string>`, lub `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="e480f-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="e480f-110">Aby zrozumieć, dlaczego typy ogólne są przydatne, Przyjrzyjmy się w określonej klasie przed i po dodaniu ogólne: <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="e480f-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="e480f-111">W programie .NET Framework 1.0 `ArrayList` elementy były typu <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="e480f-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="e480f-112">Oznacza to, że dowolny element dodany został dyskretnie konwertowane na `Object`.</span><span class="sxs-lookup"><span data-stu-id="e480f-112">This meant that any element added was silently converted into an `Object`.</span></span> <span data-ttu-id="e480f-113">Taka sama sytuacja może mieć miejsce podczas odczytywania elementów z listy.</span><span class="sxs-lookup"><span data-stu-id="e480f-113">The same would happen when reading the elements from the list.</span></span> <span data-ttu-id="e480f-114">Ten proces jest nazywany [opakowywanie i rozpakowywanie](../csharp/programming-guide/types/boxing-and-unboxing.md), i ma wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="e480f-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="e480f-115">Więcej niż ten jednak nie ma możliwości można ustalić typu danych na liście w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e480f-115">More than that, however, there's no way to determine the type of data in the list at compile time.</span></span> <span data-ttu-id="e480f-116">To sprawia, że niektóre słabe kodu.</span><span class="sxs-lookup"><span data-stu-id="e480f-116">This makes for some fragile code.</span></span> <span data-ttu-id="e480f-117">Typy ogólne rozwiązują ten problem przez zdefiniowanie typu danych, który będzie zawarty w każde wystąpienie listy.</span><span class="sxs-lookup"><span data-stu-id="e480f-117">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="e480f-118">Na przykład, można dodawać tylko liczb całkowitych na `List<int>` i dodawać tylko osoby, które mają `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="e480f-118">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="e480f-119">Typy ogólne są również dostępne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e480f-119">Generics are also available at runtime.</span></span> <span data-ttu-id="e480f-120">Oznacza to, że środowisko uruchomieniowe wie, jakiego rodzaju strukturę danych używasz i będą przechowywane jego efektywniej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e480f-120">This means the runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="e480f-121">Poniższy przykład jest mały program, który przedstawia wydajność, wiedząc, dane struktury typu w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="e480f-121">The following example is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="e480f-122">Ten program tworzy dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="e480f-122">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="e480f-123">Pierwszą rzeczą, jaką można zauważyć, że w tym miejscu jest sortowanie listy ogólnej jest znacznie szybsze niż sortowanie listy nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="e480f-123">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="e480f-124">Można też zauważyć typu listy ogólnej to odrębne ([System.Int32]), natomiast typ listy nieogólnego jest uogólniona.</span><span class="sxs-lookup"><span data-stu-id="e480f-124">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="e480f-125">Ponieważ środowisko uruchomieniowe wie ogólnego `List<int>` typu <xref:System.Int32>, może ona przechowywać elementy listy w podstawowej tablicę liczb całkowitych w pamięci podczas niepodstawowy `ArrayList` ma rzutowanie każdego elementu listy do obiektu.</span><span class="sxs-lookup"><span data-stu-id="e480f-125">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="e480f-126">Jak pokazano w tym przykładzie dodatkowe rzutowania zajmuje czasu i spowolnić sortowanie listy.</span><span class="sxs-lookup"><span data-stu-id="e480f-126">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="e480f-127">Dodatkową zaletą środowiska uruchomieniowego, wiedząc, typ ogólny usługi jest to lepszy proces debugowania.</span><span class="sxs-lookup"><span data-stu-id="e480f-127">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="e480f-128">Podczas debugowania zwykłego w języku C#, wiadomo, jakiego typu każdy element jest w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="e480f-128">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="e480f-129">Bez ogólne czy nie masz jakiego typu została każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="e480f-129">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="e480f-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e480f-130">See also</span></span>

- [<span data-ttu-id="e480f-131">C# Programming Guide - ogólne</span><span class="sxs-lookup"><span data-stu-id="e480f-131">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
