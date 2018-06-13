---
title: Modyfikatory dostępu (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 9629b1727fc210025256724db8db82b13b63b7db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217171"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="87319-102">Modyfikatory dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="87319-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="87319-103">Modyfikatory dostępu są używany do określenia dostępności zadeklarowany element członkowski lub typ słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="87319-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="87319-104">W tej sekcji przedstawiono Modyfikatory cztery dostępu:</span><span class="sxs-lookup"><span data-stu-id="87319-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="87319-105">Można określić następujące sześć poziomów ułatwień dostępu, używając modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="87319-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="87319-106">[`public`](public.md): Dostępu nie jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="87319-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="87319-107">[`protected`](protected.md): Dostęp jest ograniczony do zawierający klasy lub typy pochodzące od klasy zawierającego.</span><span class="sxs-lookup"><span data-stu-id="87319-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="87319-108">[`internal`](internal.md): Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="87319-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="87319-109">[`protected internal`](protected-internal.md): Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące od klasy zawierającego.</span><span class="sxs-lookup"><span data-stu-id="87319-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="87319-110">[`private`](private.md): Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="87319-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="87319-111">[`private protected`](private-protected.md): Dostęp jest ograniczony do zawierającego klasę lub typy pochodzące od klasy zawierające w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="87319-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="87319-112">W tej sekcji przedstawiono również następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="87319-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="87319-113">[Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md): za pomocą modyfikatorów dostępu cztery Aby zadeklarować sześciu poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="87319-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="87319-114">[Domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md): Określa, gdzie w sekcjach program elementem członkowskim można odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="87319-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="87319-115">[Ograniczenia dotyczące poziomów ułatwień dostępu przy użyciu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Podsumowanie ograniczenia dotyczące używania zadeklarowany poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="87319-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87319-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87319-116">See Also</span></span>  
 [<span data-ttu-id="87319-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="87319-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="87319-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="87319-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="87319-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="87319-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="87319-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="87319-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="87319-121">Słowa kluczowe dostępu</span><span class="sxs-lookup"><span data-stu-id="87319-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="87319-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="87319-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
