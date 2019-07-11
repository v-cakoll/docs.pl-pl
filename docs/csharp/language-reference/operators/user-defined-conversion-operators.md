---
title: Operatory konwersji zdefiniowane przez użytkownika — C# odwołania
description: Dowiedz się, jak zdefiniować niestandardowe jawne i niejawne konwersje plików w C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 5d1882048b2af12c29a3771055cbeba9565b7dab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67788499"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="8e8d1-103">Operatory konwersji zdefiniowane przez użytkownika (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="8e8d1-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="8e8d1-104">Typ zdefiniowany przez użytkownika można zdefiniować niestandardowe jawnych lub niejawnych konwersji z lub do innego typu.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="8e8d1-105">Niejawne konwersje nie wymagają specjalnej składni wywoływanej i mogą występować w wielu sytuacjach, na przykład w wywołania zadania i metody.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="8e8d1-106">Wstępnie zdefiniowane C# niejawne konwersje zawsze powiedzie się i nigdy nie zgłoszą wyjątek lub utratę informacji.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-106">Predefined C# implicit conversions always succeed and never throw an exception or lose information.</span></span> <span data-ttu-id="8e8d1-107">Niejawne konwersje zdefiniowane przez użytkownika, powinny zachowywać się w ten sposób, jak również.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="8e8d1-108">Jeśli konwersja niestandardowych mogą zgłosić wyjątek lub utratę informacji, zdefiniuj je jako jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="8e8d1-109">Konwersje zdefiniowane przez użytkownika nie są uwzględniane przy [jest](type-testing-and-conversion-operators.md#is-operator) i [jako](type-testing-and-conversion-operators.md#as-operator) operatorów.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-109">User-defined conversions are not considered by the [is](type-testing-and-conversion-operators.md#is-operator) and [as](type-testing-and-conversion-operators.md#as-operator) operators.</span></span> <span data-ttu-id="8e8d1-110">Użyj [rzutowania (operatora)](type-testing-and-conversion-operators.md#cast-operator-) do wywoływania jawnej konwersji zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-110">Use the [cast operator ()](type-testing-and-conversion-operators.md#cast-operator-) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="8e8d1-111">Użyj `operator` i `implicit` lub `explicit` słów kluczowych, aby zdefiniować jawnych lub niejawnych konwersji, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="8e8d1-112">Typ, który definiuje konwersja musi być typ źródła lub elementu docelowego typu tej konwersji.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="8e8d1-113">Konwersja między dwoma typami zdefiniowanych przez użytkownika można zdefiniować w jednym z dwóch typów.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="8e8d1-114">Poniższy przykład pokazuje jak zdefiniować niejawne i jawne konwersji:</span><span class="sxs-lookup"><span data-stu-id="8e8d1-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

<span data-ttu-id="8e8d1-115">Możesz także użyć `operator` — słowo kluczowe próby przeciążania wstępnie zdefiniowanej C# operatora.</span><span class="sxs-lookup"><span data-stu-id="8e8d1-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="8e8d1-116">Aby uzyskać więcej informacji, zobacz [przeciążania operatora](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="8e8d1-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8e8d1-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8e8d1-117">C# language specification</span></span>

<span data-ttu-id="8e8d1-118">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="8e8d1-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8e8d1-119">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="8e8d1-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="8e8d1-120">Konwersje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="8e8d1-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="8e8d1-121">Niejawne konwersje</span><span class="sxs-lookup"><span data-stu-id="8e8d1-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="8e8d1-122">Konwersje jawne</span><span class="sxs-lookup"><span data-stu-id="8e8d1-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="8e8d1-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e8d1-123">See also</span></span>

- [<span data-ttu-id="8e8d1-124">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="8e8d1-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8e8d1-125">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="8e8d1-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="8e8d1-126">Przeładowanie operatora</span><span class="sxs-lookup"><span data-stu-id="8e8d1-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="8e8d1-127">Operatory badania typu i konwersji</span><span class="sxs-lookup"><span data-stu-id="8e8d1-127">Type-testing and conversion operators</span></span>](type-testing-and-conversion-operators.md)
- [<span data-ttu-id="8e8d1-128">Rzutowanie i typ konwersji</span><span class="sxs-lookup"><span data-stu-id="8e8d1-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="8e8d1-129">Tworzenie łańcucha zdefiniowanych przez użytkownika Konwersje jawne w języku C#</span><span class="sxs-lookup"><span data-stu-id="8e8d1-129">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
