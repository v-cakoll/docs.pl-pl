---
title: Modyfikatory dostępu (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d63cf724a2364059e5f3327254a9ec95f7493e5e
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="0df63-102">Modyfikatory dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0df63-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="0df63-103">Modyfikatory dostępu są używany do określenia dostępności zadeklarowany element członkowski lub typ słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="0df63-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="0df63-104">W tej sekcji przedstawiono Modyfikatory cztery dostępu:</span><span class="sxs-lookup"><span data-stu-id="0df63-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="0df63-105">Można określić następujące sześć poziomów ułatwień dostępu, używając modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="0df63-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="0df63-106">[`public`](public.md): Dostępu nie jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="0df63-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="0df63-107">[`protected`](protected.md): Dostęp jest ograniczony do zawierający klasy lub typy pochodzące od klasy zawierającego.</span><span class="sxs-lookup"><span data-stu-id="0df63-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="0df63-108">[`internal`](internal.md): Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0df63-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="0df63-109">[`protected internal`](protected-internal.md): Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące od klasy zawierającego.</span><span class="sxs-lookup"><span data-stu-id="0df63-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="0df63-110">[`private`](private.md): Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="0df63-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="0df63-111">[`private protected`](private-protected.md): Dostęp jest ograniczony do zawierającego klasę lub typy pochodzące od klasy zawierające w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="0df63-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="0df63-112">W tej sekcji przedstawiono również następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0df63-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="0df63-113">[Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md): za pomocą modyfikatorów dostępu cztery Aby zadeklarować sześciu poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="0df63-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="0df63-114">[Domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md): Określa, gdzie w sekcjach program elementem członkowskim można odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="0df63-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="0df63-115">[Ograniczenia dotyczące poziomów ułatwień dostępu przy użyciu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Podsumowanie ograniczenia dotyczące używania zadeklarowany poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="0df63-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df63-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0df63-116">See Also</span></span>  
 [<span data-ttu-id="0df63-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="0df63-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0df63-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0df63-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0df63-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0df63-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0df63-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="0df63-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="0df63-121">Słowa kluczowe dostępu</span><span class="sxs-lookup"><span data-stu-id="0df63-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="0df63-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="0df63-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
