---
title: const — słowo kluczowe — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 812aeb331b6dd333075d19076a896246ecc5b374
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713679"
---
# <a name="const-c-reference"></a><span data-ttu-id="8f79d-102">const (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8f79d-102">const (C# Reference)</span></span>

<span data-ttu-id="8f79d-103">`const` Słowo kluczowe służy do deklarowania stałego pola lub stałego lokalnego.</span><span class="sxs-lookup"><span data-stu-id="8f79d-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="8f79d-104">Stałe pola i lokalne nie są zmiennymi i nie mogą być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="8f79d-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="8f79d-105">Stałe mogą być liczbami, wartościami logicznymi, ciągami lub odwołaniem zerowym.</span><span class="sxs-lookup"><span data-stu-id="8f79d-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="8f79d-106">Nie należy tworzyć stałą do reprezentowania informacji, które można oczekiwać, aby zmienić w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="8f79d-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="8f79d-107">Na przykład nie używaj stałego pola do przechowywania ceny usługi, numeru wersji produktu ani nazwy firmy.</span><span class="sxs-lookup"><span data-stu-id="8f79d-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="8f79d-108">Wartości te mogą się zmieniać wraz z uchwale, a kompilatory propagować stałe, inny kod skompilowany z bibliotek będzie musiał zostać ponownie skompilowany, aby zobaczyć zmiany.</span><span class="sxs-lookup"><span data-stu-id="8f79d-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="8f79d-109">Zobacz też słowo kluczowe [tylko do odczytu.](./readonly.md)</span><span class="sxs-lookup"><span data-stu-id="8f79d-109">See also the [readonly](./readonly.md) keyword.</span></span> <span data-ttu-id="8f79d-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="8f79d-110">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="8f79d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f79d-111">Remarks</span></span>

<span data-ttu-id="8f79d-112">Typ stałej deklaracji określa typ elementów członkowskich, które wprowadza deklaracja.</span><span class="sxs-lookup"><span data-stu-id="8f79d-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="8f79d-113">Iinicjator stałego pola lokalnego lub stałego musi być wyrażeniem stałym, które można niejawnie przekonwertować na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="8f79d-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="8f79d-114">Wyrażenie stałe jest wyrażeniem, które można w pełni ocenić w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8f79d-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="8f79d-115">W związku z tym jedynymi możliwymi `string` wartościami dla stałych typów odwołań są i odwołanie null.</span><span class="sxs-lookup"><span data-stu-id="8f79d-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="8f79d-116">Stała deklaracja może zadeklarować wiele stałych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="8f79d-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="8f79d-117">Modyfikator `static` nie jest dozwolone w deklaracji stałej.</span><span class="sxs-lookup"><span data-stu-id="8f79d-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="8f79d-118">Stała może uczestniczyć w wyrażeniu stałym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f79d-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="8f79d-119">Słowo kluczowe tylko do `const` [odczytu](./readonly.md) różni się od słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="8f79d-119">The [readonly](./readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="8f79d-120">Pole `const` można zainicjować tylko w deklaracji pola.</span><span class="sxs-lookup"><span data-stu-id="8f79d-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="8f79d-121">Pole `readonly` można zainicjować w deklaracji lub w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="8f79d-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="8f79d-122">W `readonly` związku z tym pola mogą mieć różne wartości w zależności od konstruktora używane.</span><span class="sxs-lookup"><span data-stu-id="8f79d-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="8f79d-123">Ponadto, mimo `const` że pole jest stałą `readonly` w czasie kompilacji, pole może być używane dla stałych czasu wykonywania, jak w tym wierszu:`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="8f79d-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="8f79d-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f79d-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="8f79d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f79d-125">Example</span></span>

<span data-ttu-id="8f79d-126">W tym przykładzie pokazano, jak używać stałych jako zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="8f79d-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="8f79d-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8f79d-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8f79d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f79d-128">See also</span></span>

- [<span data-ttu-id="8f79d-129">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="8f79d-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8f79d-130">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="8f79d-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8f79d-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8f79d-131">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="8f79d-132">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="8f79d-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="8f79d-133">Readonly</span><span class="sxs-lookup"><span data-stu-id="8f79d-133">readonly</span></span>](./readonly.md)
