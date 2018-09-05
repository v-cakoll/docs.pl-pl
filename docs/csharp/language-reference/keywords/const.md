---
title: Const — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: f586b6d097a8592fd74e92df7886b519d623e478
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513387"
---
# <a name="const-c-reference"></a><span data-ttu-id="018bb-102">const (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="018bb-102">const (C# Reference)</span></span>

<span data-ttu-id="018bb-103">Możesz użyć `const` — słowo kluczowe, aby zadeklarować pole stałe lub stałą lokalną.</span><span class="sxs-lookup"><span data-stu-id="018bb-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="018bb-104">Stałe pola i zmienne lokalne są zmienne i nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="018bb-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="018bb-105">Stałe może być liczb, wartości logicznych, ciągi lub odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="018bb-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="018bb-106">Nie należy tworzyć stałą do reprezentowania informacje, które chcą zmienić w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="018bb-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="018bb-107">Na przykład nie używaj pole stałe do przechowywania ceny usługi, numer wersji produktu lub nazwa marki firmy.</span><span class="sxs-lookup"><span data-stu-id="018bb-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="018bb-108">Te wartości mogą ulec zmianie, a ponieważ kompilatory propagację stałych, inny kod skompilowany przy użyciu bibliotek musi być ponownie kompilowane, aby zobaczyć zmiany.</span><span class="sxs-lookup"><span data-stu-id="018bb-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="018bb-109">Zobacz też [tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="018bb-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="018bb-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="018bb-110">For example:</span></span>

```csharp
const int x = 0;
public const double gravitationalConstant = 6.673e-11;
private const string productName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="018bb-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="018bb-111">Remarks</span></span>

<span data-ttu-id="018bb-112">Typ deklaracji stałej Określa typ elementów członkowskich, które wprowadza deklaracja.</span><span class="sxs-lookup"><span data-stu-id="018bb-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="018bb-113">Inicjator stałą lokalne lub pola stałego musi być wyrażeniem stałym, które mogą być niejawnie konwertowane na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="018bb-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="018bb-114">Wyrażenie stałe jest wyrażeniem, które mogą zostać w pełni oszacowane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="018bb-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="018bb-115">Dlatego jedyne możliwe wartości dla stałych o typach odwołania to `string` i odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="018bb-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="018bb-116">W deklaracji stałej można zadeklarować kilka stałych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="018bb-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double x = 1.0, y = 2.0, z = 3.0;
```

<span data-ttu-id="018bb-117">`static` Modyfikator nie jest dozwolony w deklaracji stałej.</span><span class="sxs-lookup"><span data-stu-id="018bb-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="018bb-118">Stała może brać udział w wyrażeniu stałym, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="018bb-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int c1 = 5;
public const int c2 = c1 + 100;
```

> [!NOTE]
> <span data-ttu-id="018bb-119">[Tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md) — słowo kluczowe różni się od `const` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="018bb-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="018bb-120">A `const` pola mogą być inicjowane tylko na deklarację pola.</span><span class="sxs-lookup"><span data-stu-id="018bb-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="018bb-121">A `readonly` pola mogą być inicjowane w deklaracji lub w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="018bb-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="018bb-122">W związku z tym `readonly` pola mogą mieć różne wartości w zależności od używanego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="018bb-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="018bb-123">Ponadto mimo że `const` pole jest stałą czasu kompilacji `readonly` pole może być używane dla stałych run-time, jak w tym wierszu: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="018bb-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="018bb-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="018bb-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="018bb-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="018bb-125">Example</span></span>

<span data-ttu-id="018bb-126">W tym przykładzie przedstawiono sposób użycia stałych jako zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="018bb-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="018bb-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="018bb-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="018bb-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="018bb-128">See also</span></span>

- [<span data-ttu-id="018bb-129">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="018bb-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="018bb-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="018bb-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="018bb-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="018bb-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="018bb-132">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="018bb-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="018bb-133">readonly</span><span class="sxs-lookup"><span data-stu-id="018bb-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
