---
title: New operator - C# odwołania
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3d64c4805abe38c80301748ffa6b35fc87563b60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402512"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="2eba6-102">New — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="2eba6-102">new operator (C# reference)</span></span>

<span data-ttu-id="2eba6-103">`new` Operatora, tworzy nowe wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="2eba6-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="2eba6-104">Można również użyć `new` słowo kluczowe as [modyfikator deklaracji elementu członkowskiego](../keywords/new-modifier.md) lub [ograniczenie typu ogólnego](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="2eba6-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="2eba6-105">Wywołanie konstruktora</span><span class="sxs-lookup"><span data-stu-id="2eba6-105">Constructor invocation</span></span>

<span data-ttu-id="2eba6-106">Aby utworzyć nowe wystąpienie typu, zwykle wywołuje jedną z [konstruktory](../../programming-guide/classes-and-structs/constructors.md) z tego typu za pomocą `new` operator:</span><span class="sxs-lookup"><span data-stu-id="2eba6-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

<span data-ttu-id="2eba6-107">Możesz użyć [Inicjator obiektu lub kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) z `new` operator do tworzenia instancji i zainicjować obiektu w jednej instrukcji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="2eba6-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="2eba6-108">Do utworzenia tablicy</span><span class="sxs-lookup"><span data-stu-id="2eba6-108">Array creation</span></span>

<span data-ttu-id="2eba6-109">Możesz także użyć `new` operatora do utworzenia wystąpienia tablicy, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="2eba6-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

<span data-ttu-id="2eba6-110">Składnia inicjalizacji tablicy należy użyć do utworzenia instancji tablicy i wypełnić je z elementami w jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2eba6-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="2eba6-111">Poniższy przykład pokazuje różne sposoby, jak można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="2eba6-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="2eba6-112">Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="2eba6-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="2eba6-113">Podczas tworzenia wystąpienia typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="2eba6-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="2eba6-114">Aby utworzyć wystąpienie [typu anonimowego](../../programming-guide/classes-and-structs/anonymous-types.md), użyj `new` operatora i obiekt składni inicjatora:</span><span class="sxs-lookup"><span data-stu-id="2eba6-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="2eba6-115">Niszczenie wystąpień typu</span><span class="sxs-lookup"><span data-stu-id="2eba6-115">Destruction of type instances</span></span>

<span data-ttu-id="2eba6-116">Nie masz do likwidacji wcześniej utworzony typ wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2eba6-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="2eba6-117">Wystąpień typów wartości i odwołań są niszczone, automatycznie.</span><span class="sxs-lookup"><span data-stu-id="2eba6-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="2eba6-118">Wystąpienia typu wartości są niszczone, tak szybko, jak jest niszczony, kontekst, w którym się znajdują.</span><span class="sxs-lookup"><span data-stu-id="2eba6-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="2eba6-119">Wystąpienia typu referencyjnego są niszczone [modułu zbierającego elementy bezużyteczne](../../../standard/garbage-collection/index.md) na nieokreślony czas, po usunięciu ostatniego odwołania do nich.</span><span class="sxs-lookup"><span data-stu-id="2eba6-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="2eba6-120">Dla typów, które zawierają zasoby niezarządzane na przykład dojście do pliku, zaleca się stosować deterministyczne oczyszczania aby upewnić się, jak najszybciej zwolnienie zasobów, które zawierają.</span><span class="sxs-lookup"><span data-stu-id="2eba6-120">For types that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="2eba6-121">Aby uzyskać więcej informacji, zobacz <xref:System.IDisposable?displayProperty=nameWithType> dokumentacja interfejsu API i [za pomocą instrukcji](../keywords/using-statement.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="2eba6-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2eba6-122">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="2eba6-122">Operator overloadability</span></span>

<span data-ttu-id="2eba6-123">Typ zdefiniowany przez użytkownika nie mogą przeciążać `new` operatora.</span><span class="sxs-lookup"><span data-stu-id="2eba6-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2eba6-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2eba6-124">C# language specification</span></span>

<span data-ttu-id="2eba6-125">Aby uzyskać więcej informacji, zobacz [operatora new](~/_csharplang/spec/expressions.md#the-new-operator) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2eba6-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2eba6-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2eba6-126">See also</span></span>

- [<span data-ttu-id="2eba6-127">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="2eba6-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2eba6-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="2eba6-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="2eba6-129">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="2eba6-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
