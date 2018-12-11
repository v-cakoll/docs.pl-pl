---
title: Dostęp do modyfikatorów - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 0fb435a35b928cb78511d8969f1dfce9f94869eb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242025"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="b4071-102">Modyfikatory dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b4071-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="b4071-103">Modyfikatory dostępu są słowami kluczowymi, używany do określenia deklarowaną dostępność składowej lub typu.</span><span class="sxs-lookup"><span data-stu-id="b4071-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="b4071-104">Ta sekcja wprowadza modyfikatory dostępu cztery:</span><span class="sxs-lookup"><span data-stu-id="b4071-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="b4071-105">Następujące sześć poziomów ułatwień dostępu, można określić za pomocą modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="b4071-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="b4071-106">[`public`](public.md): Dostęp nie jest ograniczona.</span><span class="sxs-lookup"><span data-stu-id="b4071-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="b4071-107">[`protected`](protected.md): Dostęp jest ograniczony do zawierający klasy lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="b4071-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="b4071-108">[`internal`](internal.md): Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4071-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="b4071-109">[`protected internal`](protected-internal.md): Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="b4071-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="b4071-110">[`private`](private.md): Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="b4071-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="b4071-111">[`private protected`](private-protected.md): Dostęp jest ograniczony do zawierający klasy lub typów pochodnych typu zawierającego klasy w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="b4071-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="b4071-112">Ta sekcja wprowadza również następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b4071-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="b4071-113">[Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md): Za pomocą modyfikatorów dostępu cztery do deklarowania sześciu poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="b4071-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="b4071-114">[Domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md): Określa, gdzie, w sekcjach program członka mogą być przywoływane.</span><span class="sxs-lookup"><span data-stu-id="b4071-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="b4071-115">[Ograniczenia dotyczące używania poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Podsumowanie ograniczenia dotyczące używania zadeklarowany poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="b4071-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4071-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4071-116">See Also</span></span>  
- [<span data-ttu-id="b4071-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b4071-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b4071-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b4071-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b4071-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="b4071-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="b4071-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="b4071-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="b4071-121">Słowa kluczowe dostępu</span><span class="sxs-lookup"><span data-stu-id="b4071-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
- [<span data-ttu-id="b4071-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="b4071-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
