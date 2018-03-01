---
title: "interface (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aba9ee66a90216066a47f22e251182caad465818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="interface-c-reference"></a><span data-ttu-id="adbe4-102">interface (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="adbe4-102">interface (C# Reference)</span></span>
<span data-ttu-id="adbe4-103">Interfejs zawiera tylko sygnatur [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [zdarzenia](../../../csharp/programming-guide/events/index.md) lub [indeksatory](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="adbe4-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="adbe4-104">Klasy lub struktury, która implementuje interfejs musi implementować członków interfejsu, które są określone w definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="adbe4-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="adbe4-105">W poniższym przykładzie klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod` czy nie ma parametrów i zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="adbe4-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="adbe4-106">Aby uzyskać dodatkowe informacje i przykłady, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="adbe4-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="adbe4-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="adbe4-107">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 <span data-ttu-id="adbe4-108">Interfejs może być elementem członkowskim przestrzeni nazw lub klasy i może zawierać podpisów następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="adbe4-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="adbe4-109">Metody</span><span class="sxs-lookup"><span data-stu-id="adbe4-109">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="adbe4-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="adbe4-110">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="adbe4-111">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="adbe4-111">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="adbe4-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="adbe4-112">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="adbe4-113">Interfejs może dziedziczyć z jednego lub więcej interfejsach podstawowych.</span><span class="sxs-lookup"><span data-stu-id="adbe4-113">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="adbe4-114">Gdy listy Typ podstawowy zawiera klasę podstawową i interfejsy, klasy podstawowej musi występować pierwsze na liście.</span><span class="sxs-lookup"><span data-stu-id="adbe4-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="adbe4-115">Klasy, która implementuje interfejs jawnie można implementować członków interfejsu.</span><span class="sxs-lookup"><span data-stu-id="adbe4-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="adbe4-116">Jawnie implementowane elementu członkowskiego nie jest dostępny za pośrednictwem wystąpienia klasy, ale tylko za pośrednictwem wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="adbe4-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="adbe4-117">Aby uzyskać bardziej szczegółowe informacje i przykłady kodu w jawnej implementacji interfejsu, zobacz [jawnej implementacji interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="adbe4-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="adbe4-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="adbe4-118">Example</span></span>  
 <span data-ttu-id="adbe4-119">W poniższym przykładzie pokazano implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="adbe4-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="adbe4-120">W tym przykładzie interfejs zawiera deklaracji właściwości i klasa zawiera implementację.</span><span class="sxs-lookup"><span data-stu-id="adbe4-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="adbe4-121">Wszystkie wystąpienia klasy, która implementuje `IPoint` ma właściwości całkowitą `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="adbe4-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="adbe4-122">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="adbe4-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="adbe4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adbe4-123">See Also</span></span>  
 [<span data-ttu-id="adbe4-124">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="adbe4-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="adbe4-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="adbe4-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="adbe4-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="adbe4-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="adbe4-127">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="adbe4-127">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="adbe4-128">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="adbe4-128">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="adbe4-129">Przy użyciu właściwości</span><span class="sxs-lookup"><span data-stu-id="adbe4-129">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="adbe4-130">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="adbe4-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [<span data-ttu-id="adbe4-131">klasy</span><span class="sxs-lookup"><span data-stu-id="adbe4-131">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="adbe4-132">— Struktura</span><span class="sxs-lookup"><span data-stu-id="adbe4-132">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="adbe4-133">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="adbe4-133">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
