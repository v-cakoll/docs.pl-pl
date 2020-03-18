---
title: nowy operator — odwołanie do języka C#
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 84131bc503a106961419a27fc4e3e0f2d82306a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846236"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="06989-102">nowy operator (odwołanie do Języka C#)</span><span class="sxs-lookup"><span data-stu-id="06989-102">new operator (C# reference)</span></span>

<span data-ttu-id="06989-103">Operator `new` tworzy nowe wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="06989-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="06989-104">Można również użyć `new` słowa kluczowego jako [modyfikatora deklaracji elementów członkowskich](../keywords/new-modifier.md) lub [ograniczenia typu ogólnego](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="06989-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="06989-105">Wywołanie konstruktora</span><span class="sxs-lookup"><span data-stu-id="06989-105">Constructor invocation</span></span>

<span data-ttu-id="06989-106">Aby utworzyć nowe wystąpienie typu, zazwyczaj wywołać jeden z [konstruktorów](../../programming-guide/classes-and-structs/constructors.md) `new` tego typu przy użyciu operatora:</span><span class="sxs-lookup"><span data-stu-id="06989-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/NewOperator.cs#Constructor)]

<span data-ttu-id="06989-107">Można użyć [inicjatora](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) `new` obiektu lub kolekcji z operatorem do tworzenia wystąpienia i inicjowania obiektu w jednej instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="06989-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="06989-108">Tworzenie tablicy</span><span class="sxs-lookup"><span data-stu-id="06989-108">Array creation</span></span>

<span data-ttu-id="06989-109">Operator służy `new` również do tworzenia wystąpienia tablicy, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="06989-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/NewOperator.cs#Array)]

<span data-ttu-id="06989-110">Składnia inicjowania tablicy służy do tworzenia wystąpienia tablicy i wypełniania go elementami w jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="06989-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="06989-111">W poniższym przykładzie pokazano różne sposoby wykonywania tego działania:</span><span class="sxs-lookup"><span data-stu-id="06989-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="06989-112">Aby uzyskać więcej informacji o tablicach, zobacz [Tablice](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="06989-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="06989-113">Tworzenie wystąpienia typów anonimowych</span><span class="sxs-lookup"><span data-stu-id="06989-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="06989-114">Aby utworzyć wystąpienie [typu anonimowego,](../../programming-guide/classes-and-structs/anonymous-types.md)należy użyć składni `new` operatora i inicjatora obiektów:</span><span class="sxs-lookup"><span data-stu-id="06989-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="06989-115">Niszczenie wystąpień typu</span><span class="sxs-lookup"><span data-stu-id="06989-115">Destruction of type instances</span></span>

<span data-ttu-id="06989-116">Nie trzeba niszczyć wcześniej utworzonych wystąpień typu.</span><span class="sxs-lookup"><span data-stu-id="06989-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="06989-117">Wystąpienia typów odwołań i wartości są niszczone automatycznie.</span><span class="sxs-lookup"><span data-stu-id="06989-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="06989-118">Wystąpienia typów wartości są niszczone, gdy kontekst, który je zawiera, zostanie zniszczony.</span><span class="sxs-lookup"><span data-stu-id="06989-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="06989-119">Wystąpienia typów odwołań są niszczone przez [moduł zbierający elementy bezużyteczne](../../../standard/garbage-collection/index.md) w nieokreślonym czasie po usunięciu ostatniego odwołania do nich.</span><span class="sxs-lookup"><span data-stu-id="06989-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="06989-120">W przypadku wystąpień typu, które zawierają zasoby niezarządzane, na przykład dojście do plików, zaleca się stosowanie deterministycznego oczyszczania, aby upewnić się, że zasoby, które zawierają, są zwalniane tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="06989-120">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="06989-121">Aby uzyskać więcej <xref:System.IDisposable?displayProperty=nameWithType> informacji, zobacz odwołanie interfejsu API i [using statement](../keywords/using-statement.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="06989-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="06989-122">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="06989-122">Operator overloadability</span></span>

<span data-ttu-id="06989-123">Typ zdefiniowany przez użytkownika `new` nie może przeciążać operatora.</span><span class="sxs-lookup"><span data-stu-id="06989-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="06989-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="06989-124">C# language specification</span></span>

<span data-ttu-id="06989-125">Aby uzyskać więcej informacji, zobacz [sekcję nowy operator](~/_csharplang/spec/expressions.md#the-new-operator) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="06989-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06989-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06989-126">See also</span></span>

- [<span data-ttu-id="06989-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="06989-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="06989-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="06989-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="06989-129">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="06989-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
