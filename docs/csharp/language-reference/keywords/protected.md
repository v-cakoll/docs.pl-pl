---
title: "protected (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 18278ed28f899d9030d6056eca9bbe83ebec04c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="protected-c-reference"></a><span data-ttu-id="0fc3d-102">protected (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0fc3d-102">protected (C# Reference)</span></span>
<span data-ttu-id="0fc3d-103">`protected` — Słowo kluczowe jest modyfikator dostępu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0fc3d-103">The `protected` keyword is a member access modifier.</span></span> 

 > <span data-ttu-id="0fc3d-104">Ta strona zawiera `protected` dostępu.</span><span class="sxs-lookup"><span data-stu-id="0fc3d-104">This page covers `protected` access.</span></span> <span data-ttu-id="0fc3d-105">`protected` — Słowo kluczowe jest również częścią [ `protected internal` ](./protected-internal.md) i [ `private protected` ](./private-protected.md) modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="0fc3d-105">The `protected` keyword is also part of the [`protected internal`](./protected-internal.md) and [`private protected`](./private-protected.md) access modifiers.</span></span> 

<span data-ttu-id="0fc3d-106">Chroniony element członkowski jest dostępny w swojej klasie i wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="0fc3d-106">A protected member is accessible within its class and by derived class instances.</span></span> 

<span data-ttu-id="0fc3d-107">Porównanie `protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0fc3d-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
  
## <a name="example"></a><span data-ttu-id="0fc3d-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fc3d-108">Example</span></span>  
 <span data-ttu-id="0fc3d-109">Chroniony element członkowski klasy podstawowej jest dostępna w klasie pochodnej, tylko wtedy, gdy występuje dostęp za pośrednictwem typu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="0fc3d-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="0fc3d-110">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="0fc3d-110">For example, consider the following code segment:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 <span data-ttu-id="0fc3d-111">Instrukcja `a.x = 10` generuje błąd, ponieważ jest on w statycznej metody Main, a nie jest wystąpieniem klasy B.</span><span class="sxs-lookup"><span data-stu-id="0fc3d-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="0fc3d-112">Elementy członkowskie struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="0fc3d-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fc3d-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fc3d-113">Example</span></span>  
 <span data-ttu-id="0fc3d-114">W tym przykładzie klasa `DerivedPoint` jest pochodną `Point`.</span><span class="sxs-lookup"><span data-stu-id="0fc3d-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="0fc3d-115">W związku z tym dostępne chronionych elementów członkowskich klasy podstawowej bezpośrednio z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="0fc3d-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 <span data-ttu-id="0fc3d-116">Zmiana poziomów dostępu `x` i `y` do [prywatnej](../../../csharp/language-reference/keywords/private.md), kompilator będzie wystawiać komunikaty o błędach:</span><span class="sxs-lookup"><span data-stu-id="0fc3d-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="0fc3d-117">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0fc3d-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0fc3d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fc3d-118">See Also</span></span>  
 [<span data-ttu-id="0fc3d-119">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="0fc3d-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0fc3d-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0fc3d-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0fc3d-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0fc3d-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0fc3d-122">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="0fc3d-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="0fc3d-123">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="0fc3d-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="0fc3d-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="0fc3d-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="0fc3d-125">publiczny</span><span class="sxs-lookup"><span data-stu-id="0fc3d-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="0fc3d-126">prywatne</span><span class="sxs-lookup"><span data-stu-id="0fc3d-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="0fc3d-127">wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="0fc3d-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="0fc3d-128">[Problemy z zabezpieczeniami dla wewnętrznego wirtualnego słowa kluczowe](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="0fc3d-128">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>