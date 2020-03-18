---
title: Delegaty o jednoznacznie określonym typie
description: Dowiedz się, jak używać ogólnych typów delegatów do deklarowania typów niestandardowych podczas tworzenia funkcji wymagającej delegatów.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 798e8b597389bc99d10e587ec417a4e717f28abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146206"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="dcd67-103">Delegaty o jednoznacznie określonym typie</span><span class="sxs-lookup"><span data-stu-id="dcd67-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="dcd67-104">Wstecz</span><span class="sxs-lookup"><span data-stu-id="dcd67-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="dcd67-105">W poprzednim artykule widać, że tworzysz określone `delegate` typy delegatów przy użyciu słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="dcd67-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span>

<span data-ttu-id="dcd67-106">Abstrakcyjne Delegate klasy zapewniają infrastrukturę dla luźne sprzężenia i wywołania.</span><span class="sxs-lookup"><span data-stu-id="dcd67-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="dcd67-107">Konkretne typy delegatów stają się znacznie bardziej przydatne, obejmując i wymuszając bezpieczeństwo typów dla metod, które są dodawane do listy wywołania dla obiektu delegata.</span><span class="sxs-lookup"><span data-stu-id="dcd67-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="dcd67-108">Korzystając ze `delegate` słowa kluczowego i zdefiniować konkretny typ delegata, kompilator generuje te metody.</span><span class="sxs-lookup"><span data-stu-id="dcd67-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="dcd67-109">W praktyce prowadzi to do tworzenia nowych typów delegatów, gdy potrzebujesz podpisu innej metody.</span><span class="sxs-lookup"><span data-stu-id="dcd67-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="dcd67-110">Ta praca może stać się nużące po jakauroku.</span><span class="sxs-lookup"><span data-stu-id="dcd67-110">This work could get tedious after a time.</span></span> <span data-ttu-id="dcd67-111">Każda nowa funkcja wymaga nowych typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="dcd67-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="dcd67-112">Na szczęście nie jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="dcd67-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="dcd67-113">Struktura .NET Core zawiera kilka typów, które można ponownie użyć, gdy potrzebujesz typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="dcd67-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="dcd67-114">Są to definicje [ogólne,](programming-guide/generics/index.md) dzięki czemu można zadeklarować dostosowania, gdy potrzebujesz deklaracji nowych metod.</span><span class="sxs-lookup"><span data-stu-id="dcd67-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span>

<span data-ttu-id="dcd67-115">Pierwszym z tych typów <xref:System.Action> jest typ i kilka odmian:</span><span class="sxs-lookup"><span data-stu-id="dcd67-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="dcd67-116">Modyfikator `in` na argument typu ogólnego jest omówione w artykule na kowariancji.</span><span class="sxs-lookup"><span data-stu-id="dcd67-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="dcd67-117">Istnieją odmiany delegata, `Action` które zawierają do 16 <xref:System.Action%6016>argumentów, takich jak .</span><span class="sxs-lookup"><span data-stu-id="dcd67-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="dcd67-118">Ważne jest, aby te definicje używać różnych argumentów ogólnych dla każdego z argumentów delegata: To daje maksymalną elastyczność.</span><span class="sxs-lookup"><span data-stu-id="dcd67-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="dcd67-119">Argumenty metody nie muszą być, ale mogą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="dcd67-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="dcd67-120">Użyj jednego `Action` z typów dla dowolnego typu delegata, który ma typ zwracany unieważnienia.</span><span class="sxs-lookup"><span data-stu-id="dcd67-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="dcd67-121">Struktura zawiera również kilka typów delegatów ogólnych, które można użyć dla typów delegatów, które zwracają wartości:</span><span class="sxs-lookup"><span data-stu-id="dcd67-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="dcd67-122">Modyfikator `out` argumentu wynikowego typu ogólnego jest omówiony w artykule na kowariancję.</span><span class="sxs-lookup"><span data-stu-id="dcd67-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="dcd67-123">Istnieją odmiany delegata `Func` z maksymalnie 16 argumentami <xref:System.Func%6017>wejściowymi, takimi jak .</span><span class="sxs-lookup"><span data-stu-id="dcd67-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="dcd67-124">Typ wyniku jest zawsze ostatni parametr typu `Func` we wszystkich deklaracjach, zgodnie z konwencją.</span><span class="sxs-lookup"><span data-stu-id="dcd67-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="dcd67-125">Użyj jednego `Func` z typów dla dowolnego typu delegata, który zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="dcd67-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="dcd67-126">Istnieje również wyspecjalizowana<xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="dcd67-126">There's also a specialized <xref:System.Predicate%601></span></span>
<span data-ttu-id="dcd67-127">typ pełnomocnika, który zwraca test na pojedynczą wartość:</span><span class="sxs-lookup"><span data-stu-id="dcd67-127">type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="dcd67-128">Można zauważyć, że `Predicate` dla każdego typu `Func` istnieje typ strukturalnie równoważny Na przykład:</span><span class="sxs-lookup"><span data-stu-id="dcd67-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="dcd67-129">Można by pomyśleć, że te dwa typy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="dcd67-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="dcd67-130">Nie są.</span><span class="sxs-lookup"><span data-stu-id="dcd67-130">They are not.</span></span>
<span data-ttu-id="dcd67-131">Te dwie zmienne nie mogą być używane zamiennie.</span><span class="sxs-lookup"><span data-stu-id="dcd67-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="dcd67-132">Zmiennej jednego typu nie można przypisać drugiego typu.</span><span class="sxs-lookup"><span data-stu-id="dcd67-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="dcd67-133">System typu C# używa nazw zdefiniowanych typów, a nie struktury.</span><span class="sxs-lookup"><span data-stu-id="dcd67-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="dcd67-134">Wszystkie te definicje typów delegatów w bibliotece .NET Core powinny oznaczać, że nie trzeba definiować nowego typu delegata dla każdej nowej funkcji, która wymaga delegatów.</span><span class="sxs-lookup"><span data-stu-id="dcd67-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="dcd67-135">Te definicje ogólne powinny zawierać wszystkie typy delegatów, których potrzebujesz w większości sytuacji.</span><span class="sxs-lookup"><span data-stu-id="dcd67-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="dcd67-136">Można po prostu utworzyć wystąpienia jednego z tych typów z wymaganymi parametrami typu.</span><span class="sxs-lookup"><span data-stu-id="dcd67-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="dcd67-137">W przypadku algorytmów, które mogą być ogólne, tych delegatów mogą służyć jako typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="dcd67-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span>

<span data-ttu-id="dcd67-138">Powinno to zaoszczędzić czas i zminimalizować liczbę nowych typów, które należy utworzyć w celu pracy z delegatów.</span><span class="sxs-lookup"><span data-stu-id="dcd67-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="dcd67-139">W następnym artykule zobaczysz kilka typowych wzorców do pracy z delegatami w praktyce.</span><span class="sxs-lookup"><span data-stu-id="dcd67-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="dcd67-140">Dalej</span><span class="sxs-lookup"><span data-stu-id="dcd67-140">Next</span></span>](delegates-patterns.md)
