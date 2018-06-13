---
title: interface (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 0320b1e287f8c7a3eb7751b68b40120f74e8f61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266545"
---
# <a name="interface-c-reference"></a><span data-ttu-id="42660-102">interface (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="42660-102">interface (C# Reference)</span></span>
<span data-ttu-id="42660-103">Interfejs zawiera tylko sygnatur [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [zdarzenia](../../../csharp/programming-guide/events/index.md) lub [indeksatory](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="42660-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="42660-104">Klasy lub struktury, która implementuje interfejs musi implementować członków interfejsu, które są określone w definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="42660-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="42660-105">W poniższym przykładzie klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod` czy nie ma parametrów i zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="42660-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="42660-106">Aby uzyskać dodatkowe informacje i przykłady, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="42660-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42660-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="42660-107">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 <span data-ttu-id="42660-108">Interfejs może być elementem członkowskim przestrzeni nazw lub klasy i może zawierać podpisów następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="42660-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="42660-109">Metody</span><span class="sxs-lookup"><span data-stu-id="42660-109">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="42660-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="42660-110">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="42660-111">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="42660-111">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="42660-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="42660-112">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="42660-113">Interfejs może dziedziczyć z jednego lub więcej interfejsach podstawowych.</span><span class="sxs-lookup"><span data-stu-id="42660-113">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="42660-114">Gdy listy Typ podstawowy zawiera klasę podstawową i interfejsy, klasy podstawowej musi występować pierwsze na liście.</span><span class="sxs-lookup"><span data-stu-id="42660-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="42660-115">Klasy, która implementuje interfejs jawnie można implementować członków interfejsu.</span><span class="sxs-lookup"><span data-stu-id="42660-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="42660-116">Jawnie implementowane elementu członkowskiego nie jest dostępny za pośrednictwem wystąpienia klasy, ale tylko za pośrednictwem wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="42660-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="42660-117">Aby uzyskać bardziej szczegółowe informacje i przykłady kodu w jawnej implementacji interfejsu, zobacz [jawnej implementacji interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="42660-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42660-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="42660-118">Example</span></span>  
 <span data-ttu-id="42660-119">W poniższym przykładzie pokazano implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="42660-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="42660-120">W tym przykładzie interfejs zawiera deklaracji właściwości i klasa zawiera implementację.</span><span class="sxs-lookup"><span data-stu-id="42660-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="42660-121">Wszystkie wystąpienia klasy, która implementuje `IPoint` ma właściwości całkowitą `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="42660-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="42660-122">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="42660-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="42660-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42660-123">See Also</span></span>  
 [<span data-ttu-id="42660-124">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="42660-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="42660-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="42660-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="42660-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="42660-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="42660-127">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="42660-127">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="42660-128">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="42660-128">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="42660-129">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="42660-129">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="42660-130">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="42660-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [<span data-ttu-id="42660-131">class</span><span class="sxs-lookup"><span data-stu-id="42660-131">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="42660-132">struct</span><span class="sxs-lookup"><span data-stu-id="42660-132">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="42660-133">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="42660-133">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
