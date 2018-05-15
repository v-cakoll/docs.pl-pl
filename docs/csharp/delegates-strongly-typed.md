---
title: Jednoznacznie delegatów
description: Dowiedz się, jak użycie ogólnych typów delegata w celu zadeklarowania typów niestandardowych podczas tworzenia funkcji wymagających delegatów.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="bfcb3-103">Jednoznacznie delegatów</span><span class="sxs-lookup"><span data-stu-id="bfcb3-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="bfcb3-104">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="bfcb3-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="bfcb3-105">W poprzednim artykule widać, utworzyć delegata określonych typów za pomocą `delegate` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="bfcb3-106">Abstrakcyjna klasa delegata zapewnia infrastrukturę luźne powiązanie i wywołania.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="bfcb3-107">Konkretne typy delegata staną się bardziej użyteczne obejmującego i wymuszanie bezpieczeństwa typu dla metody, które są dodawane do listy wywołania obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="bfcb3-108">Jeśli używasz `delegate` — słowo kluczowe i typ delegata konkretnych, kompilator generuje tych metod.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="bfcb3-109">W praktyce może to prowadzić do tworzenia nowego obiektu delegowanego typów przy każdym podpisu innej metody.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="bfcb3-110">Tę pracę można pobrać niewygodny po pewnym czasie.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-110">This work could get tedious after a time.</span></span> <span data-ttu-id="bfcb3-111">Co nowa funkcja wymaga nowych typów delegata.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="bfcb3-112">Thankfully nie jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="bfcb3-113">Framework .NET Core zawiera kilka typów, które można wykorzystać w każdym przypadku, gdy należy przekazać typów.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="bfcb3-114">Są to [ogólnego](programming-guide/generics/index.md) definicje, mogą zadeklarować dostosowań, gdy będziesz potrzebować nowej deklaracje metody.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="bfcb3-115">Pierwsza z tych typów jest <xref:System.Action> typu i kilka zmian:</span><span class="sxs-lookup"><span data-stu-id="bfcb3-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="bfcb3-116">`in` Modyfikator na argumentu typu ogólnego zostało opisane w artykule na KOWARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="bfcb3-117">Brak zmian `Action` delegata, który będzie zawierać do 16 argumenty, takich jak <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="bfcb3-118">Należy pamiętać, że te definicje używać różnych argumentów ogólnych dla każdego z argumentami delegata: który zapewnia elastyczność maksymalna.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="bfcb3-119">Argumenty metody nie muszą być, ale może być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="bfcb3-120">Użyj jednej z `Action` typy dla dowolnego typu delegata, który został zwrócony typ void.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="bfcb3-121">Struktura obejmuje również kilka ogólnych typów delegata używane dla typów delegowanych, które zwracają wartości:</span><span class="sxs-lookup"><span data-stu-id="bfcb3-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="bfcb3-122">`out` Modyfikatora w wyniku argumentu typu ogólnego zostało opisane w artykule na KOWARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="bfcb3-123">Brak zmian `Func` delegować z maksymalnie 16 argumenty wejściowe, takie jak <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="bfcb3-124">Typ wyniku jest zawsze ostatniego parametru typu we wszystkich `Func` deklaracje przez Konwencję.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="bfcb3-125">Użyj jednej z `Func` typy dla dowolnego typu delegata, która zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="bfcb3-126">Istnieje również specjalne <xref:System.Predicate%601> typ delegata, która zwraca pojedynczą wartość testu:</span><span class="sxs-lookup"><span data-stu-id="bfcb3-126">There's also a specialized <xref:System.Predicate%601> type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="bfcb3-127">Należy zauważyć, że dla każdego `Predicate` typu, strukturę równoważne `Func` typ istnieje na przykład:</span><span class="sxs-lookup"><span data-stu-id="bfcb3-127">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="bfcb3-128">Wydaje się, że te dwa typy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-128">You might think these two types are equivalent.</span></span> <span data-ttu-id="bfcb3-129">Nie są one.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-129">They are not.</span></span>
<span data-ttu-id="bfcb3-130">Te dwie zmienne nie może być używane zamiennie.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-130">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="bfcb3-131">Zmienna typu nie można przypisać innego typu.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-131">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="bfcb3-132">System typów języka C# korzysta z nazw określonych typów nie struktury.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-132">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="bfcb3-133">Wszystkie te typu delegata, który definicje w bibliotece programu .NET Core oznacza, że nie trzeba zdefiniować nowy typ delegata żadnych nowych funkcji tworzenia wymaganych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-133">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="bfcb3-134">Te definicje ogólnego powinien zawierać wszystkie delegata typy, które są potrzebne w większości sytuacji.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-134">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="bfcb3-135">Można po prostu utworzyć wystąpienie jednego z następujących typów z parametrami typu wymagane.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-135">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="bfcb3-136">W przypadku algorytmy, które można podjąć ogólnego te obiekty delegowane może służyć jako typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-136">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="bfcb3-137">To powinno zaoszczędzić czas i zminimalizować liczbę nowych typów, które należy utworzyć w celu zapewnienia ich współdziałania z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-137">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="bfcb3-138">W artykule pojawi się kilka typowych wzorców do pracy z delegatów w praktyce.</span><span class="sxs-lookup"><span data-stu-id="bfcb3-138">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="bfcb3-139">Next</span><span class="sxs-lookup"><span data-stu-id="bfcb3-139">Next</span></span>](delegates-patterns.md)
