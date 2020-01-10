---
title: C# informacje o interfejsie
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 19ca4b8a490dc85de0d0e2be6d3ca8fa7982fc14
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713439"
---
# <a name="interface-c-reference"></a><span data-ttu-id="5c5ff-102">interface (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5c5ff-102">interface (C# Reference)</span></span>

<span data-ttu-id="5c5ff-103">Interfejs zawiera tylko sygnatury [metod](../../programming-guide/classes-and-structs/methods.md), [Właściwości](../../programming-guide/classes-and-structs/properties.md), [zdarzeń](../../programming-guide/events/index.md) i [indeksatorów](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="5c5ff-103">An interface contains only the signatures of [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [events](../../programming-guide/events/index.md) or [indexers](../../programming-guide/indexers/index.md).</span></span> <span data-ttu-id="5c5ff-104">Klasa lub struktura implementująca interfejs musi implementować elementy członkowskie interfejsu, które są określone w definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5c5ff-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="5c5ff-105">W poniższym przykładzie Klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod`, która nie ma parametrów i zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="5c5ff-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="5c5ff-106">Aby uzyskać więcej informacji i przykładów, zobacz [interfejsy](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="5c5ff-106">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="5c5ff-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c5ff-107">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="5c5ff-108">Interfejs może być elementem członkowskim przestrzeni nazw lub klasy i może zawierać podpisy następujących elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="5c5ff-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>

- [<span data-ttu-id="5c5ff-109">Metody</span><span class="sxs-lookup"><span data-stu-id="5c5ff-109">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="5c5ff-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5c5ff-110">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)

- [<span data-ttu-id="5c5ff-111">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="5c5ff-111">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)

- [<span data-ttu-id="5c5ff-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5c5ff-112">Events</span></span>](event.md)

<span data-ttu-id="5c5ff-113">Interfejs może dziedziczyć z jednego lub kilku interfejsów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="5c5ff-113">An interface can inherit from one or more base interfaces.</span></span>

<span data-ttu-id="5c5ff-114">Gdy lista typów podstawowych zawiera klasę bazową i interfejsy, Klasa bazowa musi znajdować się na liście.</span><span class="sxs-lookup"><span data-stu-id="5c5ff-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="5c5ff-115">Klasa implementująca interfejs może jawnie implementować elementy członkowskie tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5c5ff-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="5c5ff-116">Nie można uzyskać dostępu do jawnie zaimplementowanego elementu członkowskiego za pomocą wystąpienia klasy, ale tylko za pomocą wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5c5ff-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>

<span data-ttu-id="5c5ff-117">Aby uzyskać szczegółowe informacje i przykłady kodu w przypadku jawnej implementacji interfejsu, zobacz [jawną implementację interfejsu](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="5c5ff-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="5c5ff-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c5ff-118">Example</span></span>

<span data-ttu-id="5c5ff-119">Poniższy przykład ilustruje implementację interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5c5ff-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="5c5ff-120">W tym przykładzie interfejs zawiera deklarację właściwości, a Klasa zawiera implementację.</span><span class="sxs-lookup"><span data-stu-id="5c5ff-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="5c5ff-121">Każde wystąpienie klasy implementującej `IPoint` ma właściwości całkowite `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="5c5ff-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="5c5ff-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5c5ff-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5c5ff-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c5ff-123">See also</span></span>

- [<span data-ttu-id="5c5ff-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5c5ff-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5c5ff-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5c5ff-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5c5ff-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5c5ff-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5c5ff-127">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="5c5ff-127">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="5c5ff-128">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5c5ff-128">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="5c5ff-129">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="5c5ff-129">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="5c5ff-130">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="5c5ff-130">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="5c5ff-131">class</span><span class="sxs-lookup"><span data-stu-id="5c5ff-131">class</span></span>](class.md)
- [<span data-ttu-id="5c5ff-132">struct</span><span class="sxs-lookup"><span data-stu-id="5c5ff-132">struct</span></span>](struct.md)
- [<span data-ttu-id="5c5ff-133">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5c5ff-133">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
