---
title: interface (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 4adc7ba106e0044ba6aff94ea3180d9c8e3ded7b
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700732"
---
# <a name="interface-c-reference"></a><span data-ttu-id="2361f-102">interface (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2361f-102">interface (C# Reference)</span></span>

<span data-ttu-id="2361f-103">Interfejs zawiera tylko sygnatury [metody](../../programming-guide/classes-and-structs/methods.md), [właściwości](../../programming-guide/classes-and-structs/properties.md), [zdarzenia](../../programming-guide/events/index.md) lub [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="2361f-103">An interface contains only the signatures of [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [events](../../programming-guide/events/index.md) or [indexers](../../programming-guide/indexers/index.md).</span></span> <span data-ttu-id="2361f-104">Klasa lub struktura implementująca interfejs musi implementować składowych interfejsu, które są określone w definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2361f-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="2361f-105">W poniższym przykładzie klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod` , nie ma parametrów i zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="2361f-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="2361f-106">Aby uzyskać więcej informacji i przykładów, zobacz [interfejsów](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="2361f-106">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="2361f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2361f-107">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="2361f-108">Interfejs może być elementem członkowskim klasy lub przestrzeni nazw i może zawierać podpisy następujące elementy członkowskie:</span><span class="sxs-lookup"><span data-stu-id="2361f-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>

- [<span data-ttu-id="2361f-109">Metody</span><span class="sxs-lookup"><span data-stu-id="2361f-109">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="2361f-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2361f-110">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)

- [<span data-ttu-id="2361f-111">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="2361f-111">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)

- [<span data-ttu-id="2361f-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="2361f-112">Events</span></span>](event.md)

<span data-ttu-id="2361f-113">Interfejs może dziedziczyć z jednego lub więcej podstawowych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2361f-113">An interface can inherit from one or more base interfaces.</span></span>

<span data-ttu-id="2361f-114">Gdy listy Typ podstawowy zawiera klasę bazową i interfejsy, pierwszy na liście musi występować klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="2361f-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="2361f-115">Klasa, która implementuje interfejs może jawne Implementowanie elementów interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2361f-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="2361f-116">Jawnie implementowane elementu członkowskiego nie są dostępne za pośrednictwem wystąpienia klasy, ale tylko za pośrednictwem wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2361f-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>

<span data-ttu-id="2361f-117">Aby uzyskać więcej informacji i przykładów kodu w jawnej implementacji interfejsu, zobacz [jawnej implementacji interfejsu](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="2361f-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="2361f-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2361f-118">Example</span></span>

<span data-ttu-id="2361f-119">W poniższym przykładzie pokazano implementację interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2361f-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="2361f-120">W tym przykładzie interfejs zawiera deklarację właściwości, a klasa zawiera implementację.</span><span class="sxs-lookup"><span data-stu-id="2361f-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="2361f-121">Wszystkie wystąpienia klasy, która implementuje `IPoint` ma właściwości Liczba całkowita `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="2361f-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="2361f-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2361f-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2361f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2361f-123">See also</span></span>

- [<span data-ttu-id="2361f-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2361f-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2361f-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2361f-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="2361f-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2361f-126">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="2361f-127">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="2361f-127">Reference Types</span></span>](reference-types.md)  
- [<span data-ttu-id="2361f-128">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="2361f-128">Interfaces</span></span>](../../programming-guide/interfaces/index.md)  
- [<span data-ttu-id="2361f-129">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="2361f-129">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)  
- [<span data-ttu-id="2361f-130">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="2361f-130">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)  
- [<span data-ttu-id="2361f-131">class</span><span class="sxs-lookup"><span data-stu-id="2361f-131">class</span></span>](class.md)  
- [<span data-ttu-id="2361f-132">struct</span><span class="sxs-lookup"><span data-stu-id="2361f-132">struct</span></span>](struct.md)  
- [<span data-ttu-id="2361f-133">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="2361f-133">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
