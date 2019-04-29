---
title: Silnie Typizowanych obiektów delegowanych
description: Dowiedz się, jak korzystać z ogólnymi typami delegatów do deklarowania typów niestandardowych podczas tworzenia funkcji wymagających delegatów.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646663"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="52bdf-103">Silnie Typizowanych obiektów delegowanych</span><span class="sxs-lookup"><span data-stu-id="52bdf-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="52bdf-104">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="52bdf-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="52bdf-105">W poprzednim artykule pokazano, Utwórz delegata określonych typów przy użyciu `delegate` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="52bdf-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="52bdf-106">Klasa abstrakcyjna delegata zapewnienia infrastruktury dla luźne powiązania i wywołania.</span><span class="sxs-lookup"><span data-stu-id="52bdf-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="52bdf-107">Konkretne typy delegatów stać się bardziej użyteczne założeń i wymuszanie bezpieczeństwa typu dla metody, które są dodawane do listy wywołań obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="52bdf-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="52bdf-108">Kiedy używasz `delegate` — słowo kluczowe i określić typ delegata konkretnych, kompilator generuje tych metod.</span><span class="sxs-lookup"><span data-stu-id="52bdf-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="52bdf-109">W praktyce może to prowadzić do tworzenie typów nowe delegowanie, zawsze, gdy potrzebujesz podpisu inną metodę.</span><span class="sxs-lookup"><span data-stu-id="52bdf-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="52bdf-110">Tej pracy można pobrać tedious po pewnym czasie.</span><span class="sxs-lookup"><span data-stu-id="52bdf-110">This work could get tedious after a time.</span></span> <span data-ttu-id="52bdf-111">Każdej nowej funkcji wymaga nowych typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="52bdf-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="52bdf-112">Na szczęście nie jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="52bdf-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="52bdf-113">Framework .NET Core zawiera kilka typów, które można wykorzystać w każdym przypadku, gdy potrzebujesz przekazać typów.</span><span class="sxs-lookup"><span data-stu-id="52bdf-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="52bdf-114">Są to [ogólny](programming-guide/generics/index.md) definicji, dzięki czemu można zadeklarować dostosowań, gdy będziesz potrzebować nowego deklaracje metody.</span><span class="sxs-lookup"><span data-stu-id="52bdf-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="52bdf-115">Jest to pierwsza z tych typów <xref:System.Action> typu i kilka zmian:</span><span class="sxs-lookup"><span data-stu-id="52bdf-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="52bdf-116">`in` Modyfikator na argument typu ogólnego zostało omówione w artykule na KOWARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="52bdf-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="52bdf-117">Brak odmian `Action` delegata, które zawierają argumenty do 16, takie jak <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="52bdf-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="52bdf-118">Jest ważne, że te definicje używać różnych argumenty ogólne dla każdego z podanych argumentów delegata: Który zapewnia maksymalną elastyczność.</span><span class="sxs-lookup"><span data-stu-id="52bdf-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="52bdf-119">Argumenty metody nie muszą być jednak może być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="52bdf-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="52bdf-120">Użyj jednej z `Action` typów dla dowolnego typu delegata, który ma zwracać typ void.</span><span class="sxs-lookup"><span data-stu-id="52bdf-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="52bdf-121">Środowisko zawiera także kilka ogólnymi typami delegatów, które umożliwiają typami delegatów, które zwracają wartości:</span><span class="sxs-lookup"><span data-stu-id="52bdf-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="52bdf-122">`out` Modyfikatora w wyniku argument typu ogólnego zostało omówione w artykule na KOWARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="52bdf-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="52bdf-123">Brak odmian `Func` delegowanie z maksymalnie 16 argumenty wejściowe, takie jak <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="52bdf-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="52bdf-124">Typ wyniku jest zawsze ostatnim parametrze typu we wszystkich `Func` deklaracji, zgodnie z Konwencją.</span><span class="sxs-lookup"><span data-stu-id="52bdf-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="52bdf-125">Użyj jednej z `Func` typów dla dowolnego typu delegata, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="52bdf-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="52bdf-126">Istnieje również specjalne <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="52bdf-126">There's also a specialized <xref:System.Predicate%601></span></span> 
<span data-ttu-id="52bdf-127">Typ dla pełnomocnika, który zwraca wartość typu single testu:</span><span class="sxs-lookup"><span data-stu-id="52bdf-127">type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="52bdf-128">Należy zauważyć, że dla każdego `Predicate` typ, strukturalnie równoważne `Func` typ istnieje na przykład:</span><span class="sxs-lookup"><span data-stu-id="52bdf-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="52bdf-129">Myślisz, że te dwa typy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="52bdf-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="52bdf-130">Nie są one.</span><span class="sxs-lookup"><span data-stu-id="52bdf-130">They are not.</span></span>
<span data-ttu-id="52bdf-131">Te dwie zmienne nie mogą być używane zamiennie.</span><span class="sxs-lookup"><span data-stu-id="52bdf-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="52bdf-132">Zmienna typu nie można przypisać innego typu.</span><span class="sxs-lookup"><span data-stu-id="52bdf-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="52bdf-133">C# Typu system używa nazwy zdefiniowanych typów, nie struktury.</span><span class="sxs-lookup"><span data-stu-id="52bdf-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="52bdf-134">Wszystkie te typ delegata, który definicje w bibliotece programu .NET Core oznacza, że nie musisz zdefiniować nowy typ delegata dla żadnych nowych funkcji możesz utworzyć, których wymaga delegatów.</span><span class="sxs-lookup"><span data-stu-id="52bdf-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="52bdf-135">Te definicje ogólny powinien zapewnić wszystkich delegata typów, które są potrzebne w większości sytuacji.</span><span class="sxs-lookup"><span data-stu-id="52bdf-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="52bdf-136">Można po prostu utworzyć wystąpienie jednego z następujących typów z parametrami typu wymagane.</span><span class="sxs-lookup"><span data-stu-id="52bdf-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="52bdf-137">W przypadku algorytmów, które mogą być wykonane na ogólny te delegaty może służyć jako typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="52bdf-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="52bdf-138">To powinno zaoszczędzić czas i zminimalizować liczbę nowych typów, które należy utworzyć, aby pracować z delegatów.</span><span class="sxs-lookup"><span data-stu-id="52bdf-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="52bdf-139">W następnym artykule przedstawimy kilka typowych wzorców do pracy z delegatów w praktyce.</span><span class="sxs-lookup"><span data-stu-id="52bdf-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="52bdf-140">Next</span><span class="sxs-lookup"><span data-stu-id="52bdf-140">Next</span></span>](delegates-patterns.md)
