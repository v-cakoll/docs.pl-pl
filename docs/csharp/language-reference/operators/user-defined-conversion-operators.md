---
title: Operatory konwersji zdefiniowane przez użytkownika — odwołanie do języka C#
description: Dowiedz się, jak zdefiniować niestandardowe konwersje typu niejawnego i jawnego w języku C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: b59fc27be31f1a38e2a6c3cabd82598933b5ed53
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121406"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="c9338-103">Operatory konwersji zdefiniowane przez użytkownika (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="c9338-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="c9338-104">Typ zdefiniowany przez użytkownika można zdefiniować niestandardowe niejawne lub jawne konwersji z lub do innego typu.</span><span class="sxs-lookup"><span data-stu-id="c9338-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="c9338-105">Konwersje niejawne nie wymagają specjalnej składni do wywoływania i mogą wystąpić w różnych sytuacjach, na przykład w przypisaniach i wywołaniach metod.</span><span class="sxs-lookup"><span data-stu-id="c9338-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="c9338-106">Wstępnie zdefiniowane konwersje niejawne języka C# zawsze powiedzie się i nigdy nie zgłaszają wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c9338-106">Predefined C# implicit conversions always succeed and never throw an exception.</span></span> <span data-ttu-id="c9338-107">Konwersje niejawne zdefiniowane przez użytkownika powinny zachowywać się również w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="c9338-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="c9338-108">Jeśli konwersja niestandardowa może zgłosić wyjątek lub utracić informacje, zdefiniuj ją jako konwersję jawną.</span><span class="sxs-lookup"><span data-stu-id="c9338-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="c9338-109">Konwersje zdefiniowane przez użytkownika nie są uwzględniane przez [operatorów is](type-testing-and-cast.md#is-operator) i [as.](type-testing-and-cast.md#as-operator)</span><span class="sxs-lookup"><span data-stu-id="c9338-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="c9338-110">Użyj [wyrażenia rzutowego,](type-testing-and-cast.md#cast-expression) aby wywołać konwersję jawną zdefiniowaną przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c9338-110">Use a [cast expression](type-testing-and-cast.md#cast-expression) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="c9338-111">Użyj `operator` i `implicit` `explicit` lub słowa kluczowe, aby zdefiniować konwersji niejawnej lub jawnej, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c9338-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="c9338-112">Typ definiujący konwersję musi być typem źródłowym lub typem docelowym tej konwersji.</span><span class="sxs-lookup"><span data-stu-id="c9338-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="c9338-113">Konwersja między dwoma typami zdefiniowanymi przez użytkownika może być zdefiniowana w jednym z dwóch typów.</span><span class="sxs-lookup"><span data-stu-id="c9338-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="c9338-114">W poniższym przykładzie pokazano, jak zdefiniować konwersję niejawną i jawną:</span><span class="sxs-lookup"><span data-stu-id="c9338-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

<span data-ttu-id="c9338-115">Służy również `operator` słowo kluczowe przeciążenie wstępnie zdefiniowanego operatora języka C#.</span><span class="sxs-lookup"><span data-stu-id="c9338-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="c9338-116">Aby uzyskać więcej informacji, zobacz [Przeciążanie operatora](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="c9338-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c9338-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c9338-117">C# language specification</span></span>

<span data-ttu-id="c9338-118">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="c9338-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c9338-119">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="c9338-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="c9338-120">Konwersje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="c9338-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="c9338-121">Konwersje niejawne</span><span class="sxs-lookup"><span data-stu-id="c9338-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="c9338-122">Konwersje jawne</span><span class="sxs-lookup"><span data-stu-id="c9338-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="c9338-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9338-123">See also</span></span>

- [<span data-ttu-id="c9338-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c9338-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c9338-125">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c9338-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="c9338-126">Przeładowanie operatora</span><span class="sxs-lookup"><span data-stu-id="c9338-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="c9338-127">Operatory testowania typu i rzutowania</span><span class="sxs-lookup"><span data-stu-id="c9338-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="c9338-128">Odlewanie i konwersja typu</span><span class="sxs-lookup"><span data-stu-id="c9338-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="c9338-129">Wytyczne dotyczące projektowania — operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="c9338-129">Design guidelines - Conversion operators</span></span>](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [<span data-ttu-id="c9338-130">Konwersje jawne zdefiniowane przez użytkownika w łańcuchu w języku C #</span><span class="sxs-lookup"><span data-stu-id="c9338-130">Chained user-defined explicit conversions in C#</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
