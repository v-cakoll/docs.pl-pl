---
title: Modyfikatory dostępu (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: ff313df9683dbc76bab684ff484b746ad05e065a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137035"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="8334c-102">Modyfikatory dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8334c-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="8334c-103">Modyfikatory dostępu są słowami kluczowymi, używany do określenia deklarowaną dostępność składowej lub typu.</span><span class="sxs-lookup"><span data-stu-id="8334c-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="8334c-104">Ta sekcja wprowadza modyfikatory dostępu cztery:</span><span class="sxs-lookup"><span data-stu-id="8334c-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="8334c-105">Następujące sześć poziomów ułatwień dostępu, można określić za pomocą modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="8334c-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="8334c-106">[`public`](public.md): Dostęp nie jest ograniczona.</span><span class="sxs-lookup"><span data-stu-id="8334c-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="8334c-107">[`protected`](protected.md): Dostęp jest ograniczony do zawierający klasy lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="8334c-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="8334c-108">[`internal`](internal.md): Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8334c-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="8334c-109">[`protected internal`](protected-internal.md): Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="8334c-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="8334c-110">[`private`](private.md): Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="8334c-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="8334c-111">[`private protected`](private-protected.md): Dostęp jest ograniczony do zawierający klasy lub typów pochodnych typu zawierającego klasy w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="8334c-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="8334c-112">Ta sekcja wprowadza również następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8334c-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="8334c-113">[Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md): za pomocą modyfikatorów dostępu cztery do deklarowania sześciu poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="8334c-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="8334c-114">[Domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md): Określa, gdzie, w sekcjach program członka mogą być przywoływane.</span><span class="sxs-lookup"><span data-stu-id="8334c-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="8334c-115">[Ograniczenia dotyczące poziomów ułatwień dostępu przy użyciu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Podsumowanie ograniczenia dotyczące używania zadeklarowana poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="8334c-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8334c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8334c-116">See Also</span></span>  
- [<span data-ttu-id="8334c-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8334c-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8334c-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8334c-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8334c-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8334c-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="8334c-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="8334c-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="8334c-121">Słowa kluczowe dostępu</span><span class="sxs-lookup"><span data-stu-id="8334c-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
- [<span data-ttu-id="8334c-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="8334c-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
