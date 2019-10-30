---
title: Delegaty o jednoznacznie określonym typie
description: Dowiedz się, jak używać typów delegatów ogólnych do deklarowania typów niestandardowych podczas tworzenia funkcji wymagającej delegatów.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: efdbef39d0e6bf2f07cde2c9621cec173e921752
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037359"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="c7d7a-103">Delegaty o jednoznacznie określonym typie</span><span class="sxs-lookup"><span data-stu-id="c7d7a-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="c7d7a-104">Ubiegł</span><span class="sxs-lookup"><span data-stu-id="c7d7a-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="c7d7a-105">W poprzednim artykule przedstawiono tworzenie określonych typów delegatów za pomocą słowa kluczowego `delegate`.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="c7d7a-106">Abstrakcyjna klasa delegatów zapewnia infrastrukturę do swobodnego sprzęgania i wywoływania.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="c7d7a-107">Konkretne typy delegatów stają się znacznie bardziej przydatne poprzez stosowanie i wymuszanie bezpieczeństwa typów dla metod, które są dodawane do listy wywołań dla obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="c7d7a-108">Gdy używasz słowa kluczowego `delegate` i zdefiniujesz konkretny typ delegata, kompilator generuje te metody.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="c7d7a-109">W tej sytuacji może to spowodować utworzenie nowych typów delegatów, gdy będzie potrzebna inna sygnatura metody.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="c7d7a-110">To działanie może uzyskać żmudnym po upływie czasu.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-110">This work could get tedious after a time.</span></span> <span data-ttu-id="c7d7a-111">Każda nowa funkcja wymaga nowych typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="c7d7a-112">Thankfully, nie jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="c7d7a-113">.NET Core Framework zawiera kilka typów, których można użyć, gdy potrzebne są typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="c7d7a-114">Są to definicje [Ogólne](programming-guide/generics/index.md) , dzięki czemu można deklarować dostosowania, gdy potrzebne są nowe deklaracje metody.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="c7d7a-115">Pierwszy z tych typów jest typem <xref:System.Action> i kilka wariantów:</span><span class="sxs-lookup"><span data-stu-id="c7d7a-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="c7d7a-116">Modyfikator `in` dla argumentu typu ogólnego jest pokryty w artykule dotyczącym kowariancji.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="c7d7a-117">Istnieją różne odmiany delegata `Action`, które zawierają do 16 argumentów, takich jak <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="c7d7a-118">Ważne jest, aby te definicje używały różnych argumentów ogólnych dla każdego z argumentów delegata: zapewnia maksymalną elastyczność.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="c7d7a-119">Argumenty metody nie muszą być, ale mogą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="c7d7a-120">Użyj jednego z typów `Action` dla dowolnego typu delegata, który ma zwracany typ void.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="c7d7a-121">Struktura zawiera również kilka ogólnych typów delegatów, których można użyć dla typów delegatów, które zwracają wartości:</span><span class="sxs-lookup"><span data-stu-id="c7d7a-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="c7d7a-122">Modyfikator `out` dla argumentu typu ogólnego wyniku jest pokryty w artykule dotyczącym kowariancji.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="c7d7a-123">Istnieją różne odmiany delegata `Func` z maksymalnie 16 argumentami wejściowymi, takimi jak <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="c7d7a-124">Typ wyniku jest zawsze ostatnim parametrem typu we wszystkich deklaracjach `Func` według Konwencji.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="c7d7a-125">Użyj jednego z typów `Func` dla dowolnego typu delegata, który zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="c7d7a-126">Istnieje również wyspecjalizowana <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="c7d7a-126">There's also a specialized <xref:System.Predicate%601></span></span> 
<span data-ttu-id="c7d7a-127">typ delegata, który zwraca test dla pojedynczej wartości:</span><span class="sxs-lookup"><span data-stu-id="c7d7a-127">type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="c7d7a-128">Można zauważyć, że dla dowolnego typu `Predicate` istnieje strukturalnie odpowiedni typ `Func` na przykład:</span><span class="sxs-lookup"><span data-stu-id="c7d7a-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="c7d7a-129">Te dwa typy mogą być uważane za równoważne.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="c7d7a-130">Nie są.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-130">They are not.</span></span>
<span data-ttu-id="c7d7a-131">Te dwie zmienne nie mogą być używane zamiennie.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="c7d7a-132">Zmienna jednego typu nie może być przypisana do innego typu.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="c7d7a-133">System C# typów używa nazw zdefiniowanych typów, a nie struktury.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="c7d7a-134">Wszystkie te definicje typów delegatów w bibliotece .NET Core powinny oznaczać, że nie trzeba definiować nowego typu delegata dla każdej nowej funkcji, którą tworzysz, która wymaga delegatów.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="c7d7a-135">Te definicje ogólne powinny podawać wszystkie typy delegatów, które są potrzebne w większości sytuacji.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="c7d7a-136">Można po prostu utworzyć wystąpienie jednego z tych typów z wymaganymi parametrami typu.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="c7d7a-137">W przypadku algorytmów, które mogą być generyczne, te Delegaty mogą być używane jako typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="c7d7a-138">Powinno to zaoszczędzić czas i zminimalizować liczbę nowych typów, które należy utworzyć w celu pracy z delegatami.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="c7d7a-139">W następnym artykule zobaczysz kilka typowych wzorców do pracy z delegatami w ćwiczeniu.</span><span class="sxs-lookup"><span data-stu-id="c7d7a-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="c7d7a-140">Next</span><span class="sxs-lookup"><span data-stu-id="c7d7a-140">Next</span></span>](delegates-patterns.md)
