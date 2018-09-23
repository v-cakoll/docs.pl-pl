---
title: interface (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 4adc7ba106e0044ba6aff94ea3180d9c8e3ded7b
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540112"
---
# <a name="interface-c-reference"></a><span data-ttu-id="a289e-102">interface (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a289e-102">interface (C# Reference)</span></span>

<span data-ttu-id="a289e-103">Interfejs zawiera tylko sygnatury [metody](../../programming-guide/classes-and-structs/methods.md), [właściwości](../../programming-guide/classes-and-structs/properties.md), [zdarzenia](../../programming-guide/events/index.md) lub [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="a289e-103">An interface contains only the signatures of [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [events](../../programming-guide/events/index.md) or [indexers](../../programming-guide/indexers/index.md).</span></span> <span data-ttu-id="a289e-104">Klasa lub struktura implementująca interfejs musi implementować składowych interfejsu, które są określone w definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a289e-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="a289e-105">W poniższym przykładzie klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod` , nie ma parametrów i zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="a289e-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="a289e-106">Aby uzyskać więcej informacji i przykładów, zobacz [interfejsów](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="a289e-106">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="a289e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a289e-107">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="a289e-108">Interfejs może być elementem członkowskim klasy lub przestrzeni nazw i może zawierać podpisy następujące elementy członkowskie:</span><span class="sxs-lookup"><span data-stu-id="a289e-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>

- [<span data-ttu-id="a289e-109">Metody</span><span class="sxs-lookup"><span data-stu-id="a289e-109">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="a289e-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a289e-110">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)

- [<span data-ttu-id="a289e-111">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="a289e-111">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)

- [<span data-ttu-id="a289e-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a289e-112">Events</span></span>](event.md)

<span data-ttu-id="a289e-113">Interfejs może dziedziczyć z jednego lub więcej podstawowych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="a289e-113">An interface can inherit from one or more base interfaces.</span></span>

<span data-ttu-id="a289e-114">Gdy listy Typ podstawowy zawiera klasę bazową i interfejsy, pierwszy na liście musi występować klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="a289e-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="a289e-115">Klasa, która implementuje interfejs może jawne Implementowanie elementów interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a289e-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="a289e-116">Jawnie implementowane elementu członkowskiego nie są dostępne za pośrednictwem wystąpienia klasy, ale tylko za pośrednictwem wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a289e-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>

<span data-ttu-id="a289e-117">Aby uzyskać więcej informacji i przykładów kodu w jawnej implementacji interfejsu, zobacz [jawnej implementacji interfejsu](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="a289e-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="a289e-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a289e-118">Example</span></span>

<span data-ttu-id="a289e-119">W poniższym przykładzie pokazano implementację interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a289e-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="a289e-120">W tym przykładzie interfejs zawiera deklarację właściwości, a klasa zawiera implementację.</span><span class="sxs-lookup"><span data-stu-id="a289e-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="a289e-121">Wszystkie wystąpienia klasy, która implementuje `IPoint` ma właściwości Liczba całkowita `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="a289e-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="a289e-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a289e-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a289e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a289e-123">See also</span></span>

- [<span data-ttu-id="a289e-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a289e-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a289e-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a289e-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="a289e-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a289e-126">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="a289e-127">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="a289e-127">Reference Types</span></span>](reference-types.md)  
- [<span data-ttu-id="a289e-128">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a289e-128">Interfaces</span></span>](../../programming-guide/interfaces/index.md)  
- [<span data-ttu-id="a289e-129">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="a289e-129">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)  
- [<span data-ttu-id="a289e-130">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="a289e-130">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)  
- [<span data-ttu-id="a289e-131">class</span><span class="sxs-lookup"><span data-stu-id="a289e-131">class</span></span>](class.md)  
- [<span data-ttu-id="a289e-132">struct</span><span class="sxs-lookup"><span data-stu-id="a289e-132">struct</span></span>](struct.md)  
- [<span data-ttu-id="a289e-133">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a289e-133">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
