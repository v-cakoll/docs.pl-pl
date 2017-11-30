---
title: "Jednoznacznie delegatów"
description: "Dowiedz się, jak użycie ogólnych typów delegata w celu zadeklarowania typów niestandardowych podczas tworzenia funkcji wymagających delegatów."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 467ba18f8e032b9b3b8f480d4b10c92d0d7ba3b9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="e004f-104">Jednoznacznie delegatów</span><span class="sxs-lookup"><span data-stu-id="e004f-104">Strongly Typed Delegates</span></span>

[<span data-ttu-id="e004f-105">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="e004f-105">Previous</span></span>](delegate-class.md)

<span data-ttu-id="e004f-106">W poprzednim artykule widać, utworzyć delegata określonych typów za pomocą `delegate` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e004f-106">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="e004f-107">Abstrakcyjna klasa delegata zapewnia infrastrukturę luźne powiązanie i wywołania.</span><span class="sxs-lookup"><span data-stu-id="e004f-107">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="e004f-108">Konkretne typy delegata staną się bardziej użyteczne obejmującego i wymuszanie bezpieczeństwa typu dla metody, które są dodawane do listy wywołania obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="e004f-108">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="e004f-109">Jeśli używasz `delegate` — słowo kluczowe i typ delegata konkretnych, kompilator generuje tych metod.</span><span class="sxs-lookup"><span data-stu-id="e004f-109">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="e004f-110">W praktyce może to prowadzić do tworzenia nowego obiektu delegowanego typów przy każdym podpisu innej metody.</span><span class="sxs-lookup"><span data-stu-id="e004f-110">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="e004f-111">Tę pracę można pobrać niewygodny po pewnym czasie.</span><span class="sxs-lookup"><span data-stu-id="e004f-111">This work could get tedious after a time.</span></span> <span data-ttu-id="e004f-112">Co nowa funkcja wymaga nowych typów delegata.</span><span class="sxs-lookup"><span data-stu-id="e004f-112">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="e004f-113">Thankfully nie jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="e004f-113">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="e004f-114">Framework .NET Core zawiera kilka typów, które można wykorzystać w każdym przypadku, gdy należy przekazać typów.</span><span class="sxs-lookup"><span data-stu-id="e004f-114">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="e004f-115">Są to [ogólnego](programming-guide/generics/index.md) definicje, mogą zadeklarować dostosowań, gdy będziesz potrzebować nowej deklaracje metody.</span><span class="sxs-lookup"><span data-stu-id="e004f-115">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="e004f-116">Pierwsza z tych typów jest <xref:System.Action> typu i kilka zmian:</span><span class="sxs-lookup"><span data-stu-id="e004f-116">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="e004f-117">`in` Modyfikator na argumentu typu ogólnego zostało opisane w artykule na KOWARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="e004f-117">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="e004f-118">Brak zmian `Action` delegata, który będzie zawierać do 16 argumenty, takich jak <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="e004f-118">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="e004f-119">Należy pamiętać, że te definicje używać różnych argumentów ogólnych dla każdego z argumentami delegata: który zapewnia elastyczność maksymalna.</span><span class="sxs-lookup"><span data-stu-id="e004f-119">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="e004f-120">Argumenty metody nie muszą być, ale może być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="e004f-120">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="e004f-121">Użyj jednej z `Action` typy dla dowolnego typu delegata, który został zwrócony typ void.</span><span class="sxs-lookup"><span data-stu-id="e004f-121">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="e004f-122">Struktura obejmuje również kilka ogólnych typów delegata używane dla typów delegowanych, które zwracają wartości:</span><span class="sxs-lookup"><span data-stu-id="e004f-122">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="e004f-123">`out` Modyfikatora w wyniku argumentu typu ogólnego zostało opisane w artykule na KOWARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="e004f-123">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="e004f-124">Brak zmian `Func` delegować z maksymalnie 16 argumenty wejściowe, takie jak <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="e004f-124">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="e004f-125">Typ wyniku jest zawsze ostatniego parametru typu we wszystkich `Func` deklaracje przez Konwencję.</span><span class="sxs-lookup"><span data-stu-id="e004f-125">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="e004f-126">Użyj jednej z `Func` typy dla dowolnego typu delegata, która zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="e004f-126">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="e004f-127">Istnieje również specjalne <xref:System.Predicate%601> typ delegata, która zwraca pojedynczą wartość testu:</span><span class="sxs-lookup"><span data-stu-id="e004f-127">There's also a specialized <xref:System.Predicate%601> type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="e004f-128">Należy zauważyć, że dla każdego `Predicate` typu, strukturę równoważne `Func` typ istnieje na przykład:</span><span class="sxs-lookup"><span data-stu-id="e004f-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="e004f-129">Wydaje się, że te dwa typy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="e004f-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="e004f-130">Nie są one.</span><span class="sxs-lookup"><span data-stu-id="e004f-130">They are not.</span></span>
<span data-ttu-id="e004f-131">Te dwie zmienne nie może być używane zamiennie.</span><span class="sxs-lookup"><span data-stu-id="e004f-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="e004f-132">Zmienna typu nie można przypisać innego typu.</span><span class="sxs-lookup"><span data-stu-id="e004f-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="e004f-133">System typów języka C# korzysta z nazw określonych typów nie struktury.</span><span class="sxs-lookup"><span data-stu-id="e004f-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="e004f-134">Wszystkie te typu delegata, który definicje w bibliotece programu .NET Core oznacza, że nie trzeba zdefiniować nowy typ delegata żadnych nowych funkcji tworzenia wymaganych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="e004f-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="e004f-135">Te definicje ogólnego powinien zawierać wszystkie delegata typy, które są potrzebne w większości sytuacji.</span><span class="sxs-lookup"><span data-stu-id="e004f-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="e004f-136">Można po prostu utworzyć wystąpienie jednego z następujących typów z parametrami typu wymagane.</span><span class="sxs-lookup"><span data-stu-id="e004f-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="e004f-137">W przypadku algorytmy, które można podjąć ogólnego te obiekty delegowane może służyć jako typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="e004f-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="e004f-138">To powinno zaoszczędzić czas i zminimalizować liczbę nowych typów, które należy utworzyć w celu zapewnienia ich współdziałania z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="e004f-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="e004f-139">W artykule pojawi się kilka typowych wzorców do pracy z delegatów w praktyce.</span><span class="sxs-lookup"><span data-stu-id="e004f-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="e004f-140">Dalej</span><span class="sxs-lookup"><span data-stu-id="e004f-140">Next</span></span>](delegates-patterns.md)
