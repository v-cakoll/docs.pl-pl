---
title: const (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f54b686b170622ca1ead736a9f614c9bbef52dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="const-c-reference"></a><span data-ttu-id="05fc8-102">const (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="05fc8-102">const (C# Reference)</span></span>
<span data-ttu-id="05fc8-103">Możesz użyć `const` — słowo kluczowe, aby zadeklarować pole stałej lub stałej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="05fc8-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="05fc8-104">Pola stałych i zmiennych lokalnych nie są zmienne i nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="05fc8-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="05fc8-105">Stałe można liczb, wartości logiczna, ciągi lub odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="05fc8-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="05fc8-106">Nie należy tworzyć stała do reprezentowania informacji, który będzie można zmienić w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="05fc8-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="05fc8-107">Na przykład nie używaj pola stałej do przechowywania ceny usługi, numer wersji produktu lub nazwę firmy.</span><span class="sxs-lookup"><span data-stu-id="05fc8-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="05fc8-108">Te wartości mogą ulec zmianie, a ponieważ kompilatory propagowane stałe, innych kodu skompilowanego za pomocą bibliotek będzie musiał ponownie skompilowana, aby zobaczyć zmiany.</span><span class="sxs-lookup"><span data-stu-id="05fc8-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="05fc8-109">Zobacz też [tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="05fc8-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="05fc8-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="05fc8-110">For example:</span></span>  
  
```csharp
const int x = 0;  
public const double gravitationalConstant = 6.673e-11;  
private const string productName = "Visual C#";  
```  
  
## <a name="remarks"></a><span data-ttu-id="05fc8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05fc8-111">Remarks</span></span>  
 <span data-ttu-id="05fc8-112">Typ deklaracji stałej Określa typ elementów członkowskich, które wprowadza deklaracji.</span><span class="sxs-lookup"><span data-stu-id="05fc8-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="05fc8-113">Inicjatora stałej lokalne lub pola stałej musi być wyrażenie stałe, który można niejawnie przekonwertować na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="05fc8-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>  
  
 <span data-ttu-id="05fc8-114">Wyrażenie stałe jest wyrażenie, które może przyjąć pełni w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="05fc8-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="05fc8-115">W związku z tym tylko to możliwe wartości to stałe typów referencyjnych `string` i odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="05fc8-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>  
  
 <span data-ttu-id="05fc8-116">Deklaracja stałej można zadeklarować wiele stałych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="05fc8-116">The constant declaration can declare multiple constants, such as:</span></span>  
  
```csharp
public const double x = 1.0, y = 2.0, z = 3.0;  
```  
  
 <span data-ttu-id="05fc8-117">`static` Modyfikator nie jest dozwolony w deklaracji stałej.</span><span class="sxs-lookup"><span data-stu-id="05fc8-117">The `static` modifier is not allowed in a constant declaration.</span></span>  
  
 <span data-ttu-id="05fc8-118">Stała mogą uczestniczyć w wyrażeniu stałym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="05fc8-118">A constant can participate in a constant expression, as follows:</span></span>  
  
```csharp
public const int c1 = 5;  
public const int c2 = c1 + 100;  
```  
  
> [!NOTE]
>  <span data-ttu-id="05fc8-119">[Tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md) — słowo kluczowe różni się od `const` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="05fc8-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="05fc8-120">A `const` pól mogą być inicjowane tylko w deklaracji pola.</span><span class="sxs-lookup"><span data-stu-id="05fc8-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="05fc8-121">A `readonly` pól mogą być inicjowane w deklaracji lub w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="05fc8-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="05fc8-122">W związku z tym `readonly` pola mogą mieć różne wartości w zależności od Konstruktor używany.</span><span class="sxs-lookup"><span data-stu-id="05fc8-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="05fc8-123">Ponadto mimo że `const` pole jest stałą czasu kompilacji `readonly` pole może być używane dla środowiska wykonawczego stałe, tak jak ten wiersz:`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="05fc8-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>  
  
## <a name="example"></a><span data-ttu-id="05fc8-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="05fc8-124">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="05fc8-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="05fc8-125">Example</span></span>  
 <span data-ttu-id="05fc8-126">W tym przykładzie pokazano, jak używać stałych jako zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="05fc8-126">This example demonstrates how to use constants as local variables.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="05fc8-127">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="05fc8-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="05fc8-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05fc8-128">See Also</span></span>  
 [<span data-ttu-id="05fc8-129">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="05fc8-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="05fc8-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="05fc8-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="05fc8-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="05fc8-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="05fc8-132">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="05fc8-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="05fc8-133">tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="05fc8-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
