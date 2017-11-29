---
title: "Wprowadzenie do delegatów"
description: "Więcej informacji na temat delegatów w tym temacie omówienie, które wprowadzono podstawowe pojęcia i opisano cele projektowania język dla obiektów delegowanych."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: dd4c68fb4f960d0c2d5cbdc9e699650070cacaf1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="b4458-104">Wprowadzenie do delegatów</span><span class="sxs-lookup"><span data-stu-id="b4458-104">Introduction to Delegates</span></span>

[<span data-ttu-id="b4458-105">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="b4458-105">Previous</span></span>](delegates-events.md)

<span data-ttu-id="b4458-106">Podaj delegatów *późne wiązanie* mechanizmu programu .NET.</span><span class="sxs-lookup"><span data-stu-id="b4458-106">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="b4458-107">Późne wiązanie oznacza, że można utworzyć algorytmu, gdy obiekt wywołujący dostarcza co najmniej jedną metodę, która implementuje część algorytmu.</span><span class="sxs-lookup"><span data-stu-id="b4458-107">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="b4458-108">Rozważmy na przykład listę gwiazdki w aplikacji astronomii sortowania.</span><span class="sxs-lookup"><span data-stu-id="b4458-108">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="b4458-109">Można sortować tych gwiazdek przez ich odległość od ziemi lub wielkość gwiazdy lub ich postrzegana jasność.</span><span class="sxs-lookup"><span data-stu-id="b4458-109">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="b4458-110">W takich przypadkach metody Sort() jest zasadniczo samo: Rozmieszcza elementy na liście, na podstawie niektórych porównania.</span><span class="sxs-lookup"><span data-stu-id="b4458-110">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="b4458-111">Kod, który porównuje dwie gwiazdki jest różne dla każdego uporządkowania sortowania.</span><span class="sxs-lookup"><span data-stu-id="b4458-111">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="b4458-112">Tego rodzaju rozwiązań były używane w oprogramowaniu do połowy wieku.</span><span class="sxs-lookup"><span data-stu-id="b4458-112">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="b4458-113">Pojęcie delegata języka C# zapewnia obsługę języka w pierwszej klasie i bezpieczeństwo typów myślą.</span><span class="sxs-lookup"><span data-stu-id="b4458-113">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="b4458-114">Jak można zauważyć w dalszej części tej serii, tworzonego algorytmów, takich jak to kodu C# jest typu bezpieczne i korzysta z języka i kompilatora, aby upewnić się, czy typy są prawidłowe dla argumentów i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="b4458-114">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="b4458-115">Cele projektowania język dla obiektów delegowanych</span><span class="sxs-lookup"><span data-stu-id="b4458-115">Language Design Goals for Delegates</span></span>

<span data-ttu-id="b4458-116">Projektanci języka wyliczyć kilku celów dla funkcji ostatecznie stał się delegatów.</span><span class="sxs-lookup"><span data-stu-id="b4458-116">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="b4458-117">Zespół chce konstrukcję języka wspólnego można użyć dowolnego późne powiązania algorytmów.</span><span class="sxs-lookup"><span data-stu-id="b4458-117">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="b4458-118">Który umożliwia deweloperom Dowiedz się, co koncepcji i użyj tego samego pojęcia na wiele problemów z różnego oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="b4458-118">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="b4458-119">Po drugie zespół chciała obsługuje zarówno wywołania metody jedno- i multiemisji.</span><span class="sxs-lookup"><span data-stu-id="b4458-119">Second, the team wanted to support both single and multi-cast method calls.</span></span> <span data-ttu-id="b4458-120">(Obiekty delegowane multiemisji są delegatów gdzie wiele metod zostało połączonych ze sobą.</span><span class="sxs-lookup"><span data-stu-id="b4458-120">(Multicast delegates are delegates where multiple methods have been chained together.</span></span> <span data-ttu-id="b4458-121">Zobaczysz przykłady [dalej w tej serii](delegate-class.md).</span><span class="sxs-lookup"><span data-stu-id="b4458-121">You'll see examples [later in this series](delegate-class.md).</span></span> 

<span data-ttu-id="b4458-122">Zespół chce delegatów do obsługi tego samego typu bezpieczeństwa, który deweloperzy oczekuje od wszystkich konstrukcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="b4458-122">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="b4458-123">Na koniec zespołu rozpoznany, że wzorzec zdarzeń jest jedną z określonym wzorcem gdzie delegatów lub dowolny algorytm późne wiązanie) jest bardzo przydatne.</span><span class="sxs-lookup"><span data-stu-id="b4458-123">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm) is very useful.</span></span> <span data-ttu-id="b4458-124">Zespół chce upewnij się, kod delegatów stanowią podstawę dla wzorca zdarzenia platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b4458-124">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="b4458-125">Wynik wszystkich czy pracy została obsługi delegata i zdarzeń w języku C# i platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b4458-125">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="b4458-126">Pozostałe artykuły w tej sekcji opisano funkcje językowe, obsługa bibliotek i idioms wspólne, które są używane podczas pracy z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="b4458-126">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="b4458-127">Dowiesz się `delegate` generuje — słowo kluczowe i jego kodu.</span><span class="sxs-lookup"><span data-stu-id="b4458-127">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="b4458-128">Dowiesz się o funkcjach programu `System.Delegate` klasy, a także używania tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="b4458-128">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="b4458-129">Dowiesz się, jak utworzyć bezpieczne obiektów delegowanych typu i Tworzenie metody, które mogą być wywoływane za pośrednictwem obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="b4458-129">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="b4458-130">Ponadto dowiesz się, jak do pracy z delegaci i zdarzenia za pomocą wyrażenia Lambda.</span><span class="sxs-lookup"><span data-stu-id="b4458-130">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="b4458-131">Zostanie wyświetlony, gdy delegatów się jeden z bloków konstrukcyjnych dla LINQ.</span><span class="sxs-lookup"><span data-stu-id="b4458-131">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="b4458-132">Dowiesz się, jak delegatów stanowią podstawę dla wzorca zdarzenia platformy .NET i jak są różne.</span><span class="sxs-lookup"><span data-stu-id="b4458-132">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="b4458-133">Ogólne zobaczysz, jak obiekty delegowane są integralną częścią programowania w programie .NET i Praca z framework interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="b4458-133">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="b4458-134">Zacznijmy od początku.</span><span class="sxs-lookup"><span data-stu-id="b4458-134">Let's get started.</span></span>

[<span data-ttu-id="b4458-135">Dalej</span><span class="sxs-lookup"><span data-stu-id="b4458-135">Next</span></span>](delegate-class.md)
