---
title: Wprowadzenie do delegatów
description: Dowiedz się więcej o pełnomocnikach w tym temacie przeglądu, który wprowadza podstawowe pojęcia i omawia cele projektowania języka dla pełnomocników.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: fd594f77c034533a1d5aee1d8279e9b727284311
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146232"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="ab91a-103">Wprowadzenie do delegatów</span><span class="sxs-lookup"><span data-stu-id="ab91a-103">Introduction to Delegates</span></span>

<span data-ttu-id="ab91a-104">Delegaci zapewniają mechanizm *późnego wiązania* w .NET.</span><span class="sxs-lookup"><span data-stu-id="ab91a-104">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="ab91a-105">Późne wiązanie oznacza, że można utworzyć algorytm, w którym obiekt wywołujący dostarcza również co najmniej jedną metodę, która implementuje część algorytmu.</span><span class="sxs-lookup"><span data-stu-id="ab91a-105">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="ab91a-106">Rozważmy na przykład sortowanie listy gwiazd w aplikacji astronomicznej.</span><span class="sxs-lookup"><span data-stu-id="ab91a-106">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="ab91a-107">Możesz posortować te gwiazdy według ich odległości od ziemi, wielkości gwiazdy lub ich postrzeganej jasności.</span><span class="sxs-lookup"><span data-stu-id="ab91a-107">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="ab91a-108">We wszystkich tych przypadkach Sort() Metoda zasadniczo to samo: rozmieszcza elementy na liście na podstawie porównania.</span><span class="sxs-lookup"><span data-stu-id="ab91a-108">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="ab91a-109">Kod, który porównuje dwie gwiazdki jest inny dla każdego z kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="ab91a-109">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="ab91a-110">Tego rodzaju rozwiązania są stosowane w oprogramowaniu od pół wieku.</span><span class="sxs-lookup"><span data-stu-id="ab91a-110">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="ab91a-111">Koncepcja delegata języka Języka C# zapewnia obsługę języka pierwszej klasy i bezpieczeństwo typu wokół koncepcji.</span><span class="sxs-lookup"><span data-stu-id="ab91a-111">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="ab91a-112">Jak zobaczysz w dalszej części tej serii, kod C# piszesz dla algorytmów, takich jak ten jest typ bezpieczny i wykorzystuje język i kompilator, aby upewnić się, że typy są zgodne dla argumentów i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="ab91a-112">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="ab91a-113">Cele projektowania języka dla delegatów</span><span class="sxs-lookup"><span data-stu-id="ab91a-113">Language Design Goals for Delegates</span></span>

<span data-ttu-id="ab91a-114">Projektanci języka wyliczono kilka celów dla funkcji, która ostatecznie stała się delegatów.</span><span class="sxs-lookup"><span data-stu-id="ab91a-114">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="ab91a-115">Zespół chciał wspólnej konstrukcji języka, który może być używany dla wszelkich algorytmów późnego wiązania.</span><span class="sxs-lookup"><span data-stu-id="ab91a-115">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="ab91a-116">Dzięki temu deweloperzy mogą nauczyć się jednej koncepcji i używać tej samej koncepcji w wielu różnych problemach z oprogramowaniem.</span><span class="sxs-lookup"><span data-stu-id="ab91a-116">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="ab91a-117">Po drugie, zespół chciał obsługiwać wywołania metodą pojedynczej i multiemisji.</span><span class="sxs-lookup"><span data-stu-id="ab91a-117">Second, the team wanted to support both single and multicast method calls.</span></span> <span data-ttu-id="ab91a-118">(Delegatów multiemisji są delegatów, które łańcuch razem wiele wywołań metody.</span><span class="sxs-lookup"><span data-stu-id="ab91a-118">(Multicast delegates are delegates that chain together multiple method calls.</span></span>
<span data-ttu-id="ab91a-119">Przykłady w [dalszej części tej serii](delegate-class.md).)</span><span class="sxs-lookup"><span data-stu-id="ab91a-119">You'll see examples [later in this series](delegate-class.md).)</span></span>

<span data-ttu-id="ab91a-120">Zespół chciał delegatów do obsługi tego samego typu bezpieczeństwa, które deweloperzy oczekują od wszystkich konstrukcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="ab91a-120">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span>

<span data-ttu-id="ab91a-121">Na koniec zespół rozpoznał, że wzorzec zdarzenia jest jeden wzorzec, w którym delegatów lub wszelkie algorytmy późnego wiązania, jest bardzo przydatne.</span><span class="sxs-lookup"><span data-stu-id="ab91a-121">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm, is very useful.</span></span> <span data-ttu-id="ab91a-122">Zespół chciał upewnić się, że kod dla delegatów może stanowić podstawę wzorca zdarzenia .NET.</span><span class="sxs-lookup"><span data-stu-id="ab91a-122">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="ab91a-123">Wynikiem całej tej pracy był pełnomocnik i obsługa zdarzeń w językach C# i .NET.</span><span class="sxs-lookup"><span data-stu-id="ab91a-123">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="ab91a-124">Pozostałe artykuły w tej sekcji omówi funkcje języka, obsługę biblioteki i wspólne idiomy, które są używane podczas pracy z delegatami.</span><span class="sxs-lookup"><span data-stu-id="ab91a-124">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="ab91a-125">Dowiesz się o `delegate` sutece kluczowej i o tym, jaki kod generuje.</span><span class="sxs-lookup"><span data-stu-id="ab91a-125">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="ab91a-126">Dowiesz się o funkcjach `System.Delegate` w klasie i jak te funkcje są używane.</span><span class="sxs-lookup"><span data-stu-id="ab91a-126">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="ab91a-127">Dowiesz się, jak utworzyć typ bezpiecznych delegatów i jak utworzyć metody, które mogą być wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="ab91a-127">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="ab91a-128">Dowiesz się również, jak pracować z delegatów i zdarzeń przy użyciu wyrażeń Lambda.</span><span class="sxs-lookup"><span data-stu-id="ab91a-128">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="ab91a-129">Zobaczysz, gdzie delegaci stają się jednym z bloków konstrukcyjnych dla LINQ.</span><span class="sxs-lookup"><span data-stu-id="ab91a-129">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="ab91a-130">Dowiesz się, jak delegaci są podstawą wzorca zdarzenia .NET i jak są one różne.</span><span class="sxs-lookup"><span data-stu-id="ab91a-130">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="ab91a-131">Ogólnie rzecz biorąc, zobaczysz, jak delegaci są integralną częścią programowania w .NET i pracy z ramowych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="ab91a-131">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="ab91a-132">Zacznijmy.</span><span class="sxs-lookup"><span data-stu-id="ab91a-132">Let's get started.</span></span>

[<span data-ttu-id="ab91a-133">Dalej</span><span class="sxs-lookup"><span data-stu-id="ab91a-133">Next</span></span>](delegate-class.md)
