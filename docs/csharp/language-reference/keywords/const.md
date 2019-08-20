---
title: const — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 2a2e4bb45d21708ea3971d2f5b784280b9d13d0d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605900"
---
# <a name="const-c-reference"></a><span data-ttu-id="c73c9-102">const (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c73c9-102">const (C# Reference)</span></span>

<span data-ttu-id="c73c9-103">Użyj słowa kluczowego, `const` aby zadeklarować pole stałe lub stałą lokalną.</span><span class="sxs-lookup"><span data-stu-id="c73c9-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="c73c9-104">Pola stałe i zmienne lokalne nie są zmiennymi i nie mogą być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="c73c9-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="c73c9-105">Stałe mogą być liczbami, wartościami logicznymi, ciągami lub odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="c73c9-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="c73c9-106">Nie należy tworzyć stałej do reprezentowania informacji, które można zmienić w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="c73c9-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="c73c9-107">Na przykład nie należy używać pola stałego do przechowywania ceny usługi, numeru wersji produktu ani nazwy marki firmy.</span><span class="sxs-lookup"><span data-stu-id="c73c9-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="c73c9-108">Te wartości mogą ulec zmianie z upływem czasu, a ponieważ kompilatory propagują stałe, inne kod skompilowane z bibliotekami będzie musiały zostać ponownie skompilowane w celu wyświetlenia zmian.</span><span class="sxs-lookup"><span data-stu-id="c73c9-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="c73c9-109">Zobacz również słowo kluczowe [ReadOnly](./readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="c73c9-109">See also the [readonly](./readonly.md) keyword.</span></span> <span data-ttu-id="c73c9-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c73c9-110">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="c73c9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c73c9-111">Remarks</span></span>

<span data-ttu-id="c73c9-112">Typ deklaracji stałej określa typ elementów członkowskich, które wprowadza deklaracja.</span><span class="sxs-lookup"><span data-stu-id="c73c9-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="c73c9-113">Inicjator stałego lokalnego lub stałego pola musi być wyrażeniem stałym, które może być niejawnie konwertowane na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="c73c9-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="c73c9-114">Wyrażenie stałe jest wyrażeniem, które może być w pełni oceniane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c73c9-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="c73c9-115">W związku z tym jedynymi możliwymi wartościami dla stałych typów `string` odwołań są i odwołania o wartości null.</span><span class="sxs-lookup"><span data-stu-id="c73c9-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="c73c9-116">Deklaracja stałej może deklarować wiele stałych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="c73c9-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="c73c9-117">`static` Modyfikator nie jest dozwolony w deklaracji stałej.</span><span class="sxs-lookup"><span data-stu-id="c73c9-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="c73c9-118">Stała może uczestniczyć w wyrażeniu stałym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c73c9-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="c73c9-119">Słowo kluczowe [ReadOnly](./readonly.md) różni się `const` od słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="c73c9-119">The [readonly](./readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="c73c9-120">`const` Pole może być inicjowane tylko w deklaracji pola.</span><span class="sxs-lookup"><span data-stu-id="c73c9-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="c73c9-121">`readonly` Pole może być inicjowane w deklaracji lub w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="c73c9-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="c73c9-122">W `readonly` związku z tym pola mogą mieć różne wartości w zależności od użytego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c73c9-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="c73c9-123">Ponadto mimo że `const` pole jest stałą czasu kompilacji `readonly` , pole może być używane dla stałych czasu wykonywania, jak w tym wierszu:`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="c73c9-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="c73c9-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="c73c9-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="c73c9-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="c73c9-125">Example</span></span>

<span data-ttu-id="c73c9-126">W tym przykładzie pokazano, jak używać stałych jako zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="c73c9-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="c73c9-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c73c9-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c73c9-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c73c9-128">See also</span></span>

- [<span data-ttu-id="c73c9-129">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c73c9-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c73c9-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c73c9-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c73c9-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c73c9-131">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c73c9-132">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="c73c9-132">Modifiers</span></span>](./modifiers.md)
- [<span data-ttu-id="c73c9-133">readonly</span><span class="sxs-lookup"><span data-stu-id="c73c9-133">readonly</span></span>](./readonly.md)
