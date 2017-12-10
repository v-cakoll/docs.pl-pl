---
title: "Ogólne typy (Ogólne) — omówienie"
description: "Dowiedz się, jak ogólne działanie jako kod szablonów, które umożliwiają zdefiniowanie struktury danych bezpieczny, nie poświęcając na to rzeczywisty typ danych."
keywords: .NET, .NET core
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.openlocfilehash: acd6f1cc3a6200140f25fc31e4f6fb0f8da5a6e3
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="generic-types-generics-overview"></a><span data-ttu-id="d6121-104">Ogólne typy (Ogólne) — omówienie</span><span class="sxs-lookup"><span data-stu-id="d6121-104">Generic Types (Generics) Overview</span></span>

<span data-ttu-id="d6121-105">Używamy ogólne cały czas w języku C#, czy jawnie lub niejawnie.</span><span class="sxs-lookup"><span data-stu-id="d6121-105">We use generics all the time in C#, whether implicitly or explicitly.</span></span> <span data-ttu-id="d6121-106">Korzystając z LINQ w C#, kiedykolwiek Zwróć uwagę, że korzystasz z interfejsu IEnumerable<T>?</span><span class="sxs-lookup"><span data-stu-id="d6121-106">When you use LINQ in C#, did you ever notice that you are working with IEnumerable<T>?</span></span> <span data-ttu-id="d6121-107">Lub jeśli kiedykolwiek widać online próbki "repository ogólnego" do rozmowy baz danych przy użyciu programu Entity Framework, czy widoczny czy większości metod zwracać interfejs IQueryable<T>?</span><span class="sxs-lookup"><span data-stu-id="d6121-107">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="d6121-108">Użytkownik może zaawansowanych co **T** znajduje się w tych przykładach i dlaczego jest w nim?</span><span class="sxs-lookup"><span data-stu-id="d6121-108">You may have wondered what the **T** is in these examples and why is it in there?</span></span>

<span data-ttu-id="d6121-109">Po raz pierwszy wprowadzone do programu .NET Framework 2.0, ogólne zaangażowany zmiany języka C# i środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d6121-109">First introduced to the .NET Framework 2.0, generics involved changes to both the C# language and the Common Language Runtime (CLR).</span></span> <span data-ttu-id="d6121-110">**Typy ogólne** są zasadniczo "kod szablonu" który umożliwia deweloperom Zdefiniuj [bezpieczne](https://msdn.microsoft.com/library/hbzz1a9a.aspx) struktury danych, nie poświęcając na to rzeczywisty typ danych.</span><span class="sxs-lookup"><span data-stu-id="d6121-110">**Generics** are essentially a "code template" that allows developers to define [type-safe](https://msdn.microsoft.com/library/hbzz1a9a.aspx) data structures without committing to an actual data type.</span></span> <span data-ttu-id="d6121-111">Na przykład `List<T>` jest [kolekcji ogólnej](xref:System.Collections.Generic) który zadeklarowany i używane w przypadku każdego typu: `List<int>`, `List<string>`, `List<Person>`itp.</span><span class="sxs-lookup"><span data-stu-id="d6121-111">For example, `List<T>` is a [Generic Collection](xref:System.Collections.Generic) that can be declared and used with any type: `List<int>`, `List<string>`, `List<Person>`, etc.</span></span>

<span data-ttu-id="d6121-112">Tak co to jest punkt?</span><span class="sxs-lookup"><span data-stu-id="d6121-112">So, what’s the point?</span></span> <span data-ttu-id="d6121-113">Typy ogólne są przydatne</span><span class="sxs-lookup"><span data-stu-id="d6121-113">Why are generics useful?</span></span> <span data-ttu-id="d6121-114">Aby to zrozumieć, należy spojrzeć na określonej klasy przed i po dodaniu typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="d6121-114">In order to understand this, we need to take a look at a specific class before and after adding generics.</span></span> <span data-ttu-id="d6121-115">Przyjrzyjmy się `ArrayList`.</span><span class="sxs-lookup"><span data-stu-id="d6121-115">Let’s look at the `ArrayList`.</span></span> <span data-ttu-id="d6121-116">W języku C# 1.0 `ArrayList` elementy zostały typu `object`.</span><span class="sxs-lookup"><span data-stu-id="d6121-116">In C# 1.0, the `ArrayList` elements were of type `object`.</span></span> <span data-ttu-id="d6121-117">Oznacza to, że dowolny element, który został dodany dyskretnie został przekonwertowany na `object`; tym samym co się dzieje na odczyt elementów na liście (ten proces jest nazywany [boxing](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md) i konwersja unboxing odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="d6121-117">This meant that any element that was added was silently converted into an `object`; same thing happens on reading the elements from the list (this process is known as [boxing](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md) and unboxing respectively).</span></span> <span data-ttu-id="d6121-118">Opakowywanie i rozpakowywanie wpływają na wydajność.</span><span class="sxs-lookup"><span data-stu-id="d6121-118">Boxing and unboxing have an impact of performance.</span></span> <span data-ttu-id="d6121-119">Więcej niż ta ponieważ nie ma można sprawdzić w czasie kompilacji, co jest rzeczywisty typ danych na liście.</span><span class="sxs-lookup"><span data-stu-id="d6121-119">More than that, however, there is no way to tell at compile time what is the actual type of the data in the list.</span></span> <span data-ttu-id="d6121-120">Dzięki temu wrażliwych kodu.</span><span class="sxs-lookup"><span data-stu-id="d6121-120">This makes for some fragile code.</span></span> <span data-ttu-id="d6121-121">Typy ogólne rozwiązać ten problem, udostępniając dodatkowe informacje typu danych, który będzie zawierać każde wystąpienie listy.</span><span class="sxs-lookup"><span data-stu-id="d6121-121">Generics solve this problem by providing additional information the type of data each instance of list will contain.</span></span> <span data-ttu-id="d6121-122">Po prostu umieść, można dodawać tylko liczb całkowitych na `List<int>` i osoby, które mają być dodawane tylko `List<Person>`itp.</span><span class="sxs-lookup"><span data-stu-id="d6121-122">Put simply, you can only add integers to `List<int>` and only add Persons to `List<Person>`, etc.</span></span>

<span data-ttu-id="d6121-123">Typy ogólne są również dostępne w czasie wykonywania, lub **reified**.</span><span class="sxs-lookup"><span data-stu-id="d6121-123">Generics are also available at runtime, or **reified**.</span></span> <span data-ttu-id="d6121-124">Oznacza to, że środowisko wykonawcze wie, jakiego rodzaju struktury danych używany i nie można przechowywać go wydajniej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d6121-124">This means the runtime knows what type of data structure you are using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="d6121-125">W tym miejscu jest mały program, który przedstawia wydajność wiedząc danych struktury typu w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="d6121-125">Here is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="d6121-126">Ten program daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d6121-126">This program yields the following output:</span></span>

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

<span data-ttu-id="d6121-127">Pierwszą czynnością, którą można zauważyć, że w tym miejscu jest sortowanie listy ogólnej jest znacznie szybsze niż listy nierodzajową.</span><span class="sxs-lookup"><span data-stu-id="d6121-127">The first thing you notice here is that sorting the generic list is significantly faster than for the non-generic list.</span></span> <span data-ttu-id="d6121-128">Można również zauważyć, że typu listy ogólnej jest różne ([System.Int32]), podczas gdy uogólniony typu listy nierodzajową.</span><span class="sxs-lookup"><span data-stu-id="d6121-128">You might also notice that the type for the generic list is distinct ([System.Int32]) whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="d6121-129">Ponieważ środowisko uruchomieniowe zna ogólnego `List<int>` jest typu int umożliwia przechowywanie listy elementów w tablicy źródłowej całkowitą w pamięci podczas nieogólnego `ArrayList` ma można rzutować każdego elementu listy jako obiekt jako przechowywane w tablicy obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d6121-129">Because the runtime knows the generic `List<int>` is of type int, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element as an object as stored in an object array in memory.</span></span> <span data-ttu-id="d6121-130">Jak widoczny w tym przykładzie, dodatkowe odlewów zajmuje czasu i spowolnić sortowanie listy.</span><span class="sxs-lookup"><span data-stu-id="d6121-130">As shown through this example, the extra castings take up time and slow down the list sort.</span></span>

<span data-ttu-id="d6121-131">Ostatnim etapem przydatne informacje o środowisku uruchomieniowym, znajomość typu zwykłego użytkownika jest działanie lepiej debugowania.</span><span class="sxs-lookup"><span data-stu-id="d6121-131">The last useful thing about the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="d6121-132">Podczas debugowania ogólnego w języku C#, wiesz, jakiego typu jest każdego elementu w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="d6121-132">When you are debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="d6121-133">Bez ogólne trzeba nie wiadomo typ każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="d6121-133">Without generics, you would have no idea what type each element was.</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="d6121-134">Dalsze informacje i zasoby</span><span class="sxs-lookup"><span data-stu-id="d6121-134">Further reading and resources</span></span>

*   [<span data-ttu-id="d6121-135">Wprowadzenie do typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="d6121-135">An Introduction to C# Generics</span></span>](https://msdn.microsoft.com/library/ms379564.aspx)
*   [<span data-ttu-id="d6121-136">C# przewodnik programowania w języku — ogólne</span><span class="sxs-lookup"><span data-stu-id="d6121-136">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
