---
title: Operatory konwersji zdefiniowane przez użytkownika — odwołanie do języka C#
description: Dowiedz się, jak zdefiniować niestandardowe konwersje typów niejawnych i jawnych w języku C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: b6061492cc1a4f756196fb8a9050b68651431e38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847273"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="2c50f-103">Operatory konwersji zdefiniowane przez użytkownika (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="2c50f-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="2c50f-104">Typ zdefiniowany przez użytkownika można zdefiniować niestandardowe niejawne konwersji lub jawne z lub do innego typu.</span><span class="sxs-lookup"><span data-stu-id="2c50f-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="2c50f-105">Konwersje niejawne nie wymagają specjalnej składni do wywołania i mogą występować w różnych sytuacjach, na przykład w przypisaniach i wywołaniach metod.</span><span class="sxs-lookup"><span data-stu-id="2c50f-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="2c50f-106">Wstępnie zdefiniowane konwersje niejawne C# zawsze się powiedzie i nigdy nie zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2c50f-106">Predefined C# implicit conversions always succeed and never throw an exception.</span></span> <span data-ttu-id="2c50f-107">Konwersje niejawne zdefiniowane przez użytkownika powinny również zachowywać się w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="2c50f-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="2c50f-108">Jeśli konwersja niestandardowa może zgłosić wyjątek lub utracić informacje, zdefiniuj je jako jawną konwersję.</span><span class="sxs-lookup"><span data-stu-id="2c50f-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="2c50f-109">Konwersje zdefiniowane przez użytkownika nie są brane pod uwagę przez [is](type-testing-and-cast.md#is-operator) i [jako](type-testing-and-cast.md#as-operator) operatory.</span><span class="sxs-lookup"><span data-stu-id="2c50f-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="2c50f-110">Użyj [operatora rzutowania ()](type-testing-and-cast.md#cast-operator-) do wywołania konwersji jawnej zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2c50f-110">Use the [cast operator ()](type-testing-and-cast.md#cast-operator-) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="2c50f-111">Użyj `operator` i `implicit` `explicit` lub słowa kluczowego, aby zdefiniować konwersję niejawną lub jawną, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="2c50f-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="2c50f-112">Typ definiujący konwersję musi być typem źródłowym lub docelowym tej konwersji.</span><span class="sxs-lookup"><span data-stu-id="2c50f-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="2c50f-113">Konwersję między dwoma typami zdefiniowanymi przez użytkownika można zdefiniować w jednym z dwóch typów.</span><span class="sxs-lookup"><span data-stu-id="2c50f-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="2c50f-114">W poniższym przykładzie pokazano, jak zdefiniować konwersję niejawną i jawną:</span><span class="sxs-lookup"><span data-stu-id="2c50f-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

<span data-ttu-id="2c50f-115">Słowo `operator` kluczowe służy również do przeciążenia wstępnie zdefiniowanego operatora Języka C#.</span><span class="sxs-lookup"><span data-stu-id="2c50f-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="2c50f-116">Aby uzyskać więcej informacji, zobacz [Przeciążenie operatora](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="2c50f-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2c50f-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2c50f-117">C# language specification</span></span>

<span data-ttu-id="2c50f-118">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="2c50f-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2c50f-119">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="2c50f-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="2c50f-120">Konwersje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="2c50f-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="2c50f-121">Konwersje niejawne</span><span class="sxs-lookup"><span data-stu-id="2c50f-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="2c50f-122">Jawne konwersje</span><span class="sxs-lookup"><span data-stu-id="2c50f-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="2c50f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c50f-123">See also</span></span>

- [<span data-ttu-id="2c50f-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2c50f-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2c50f-125">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="2c50f-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="2c50f-126">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="2c50f-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="2c50f-127">Operatory testowania typu i rzutowania</span><span class="sxs-lookup"><span data-stu-id="2c50f-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="2c50f-128">Casting i konwersja typu</span><span class="sxs-lookup"><span data-stu-id="2c50f-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="2c50f-129">Wytyczne projektowe - Operatorzy konwersji</span><span class="sxs-lookup"><span data-stu-id="2c50f-129">Design guidelines - Conversion operators</span></span>](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [<span data-ttu-id="2c50f-130">Konwersje jawne zdefiniowane przez użytkownika w łańcuchu w C #</span><span class="sxs-lookup"><span data-stu-id="2c50f-130">Chained user-defined explicit conversions in C#</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
