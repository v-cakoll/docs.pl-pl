---
title: Modyfikatory dostępu — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 754949e42771de30cc2dce7e4e610f70ada6dfd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713843"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="0a790-102">Modyfikatory dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0a790-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="0a790-103">Modyfikatory dostępu to słowa kluczowe używane do określania zadeklarowanej dostępności elementu członkowskiego lub typu.</span><span class="sxs-lookup"><span data-stu-id="0a790-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="0a790-104">W tej sekcji przedstawiono cztery modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="0a790-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="0a790-105">Za pomocą modyfikatorów dostępu można określić następujące sześć poziomów ułatwień dostępu:</span><span class="sxs-lookup"><span data-stu-id="0a790-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="0a790-106">[`public`](public.md): Dostęp nie jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="0a790-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="0a790-107">[`protected`](protected.md): Dostęp jest ograniczony do klasy zawierającej lub typów pochodzących z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="0a790-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="0a790-108">[`internal`](internal.md): Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0a790-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="0a790-109">[`protected internal`](protected-internal.md): Dostęp jest ograniczony do bieżącego zestawu lub typów pochodzących z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="0a790-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="0a790-110">[`private`](private.md): Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="0a790-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="0a790-111">[`private protected`](private-protected.md): Dostęp jest ograniczony do klasy zawierającej lub typów pochodzących z klasy zawierającej w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="0a790-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="0a790-112">W tej sekcji przedstawiono również następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0a790-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="0a790-113">[Poziomy ułatwień dostępu:](./accessibility-levels.md)Korzystanie z czterech modyfikatorów dostępu do deklarowania sześciu poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="0a790-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="0a790-114">[Domena ułatwień dostępu](./accessibility-domain.md): określa, gdzie w sekcjach programu można odwoływać się do członka.</span><span class="sxs-lookup"><span data-stu-id="0a790-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="0a790-115">[Ograniczenia dotyczące korzystania z poziomów ułatwień dostępu:](./restrictions-on-using-accessibility-levels.md)Podsumowanie ograniczeń dotyczących korzystania z zadeklarowanych poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="0a790-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a790-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a790-116">See also</span></span>

- [<span data-ttu-id="0a790-117">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="0a790-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0a790-118">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="0a790-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0a790-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0a790-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="0a790-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="0a790-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="0a790-121">Słowa kluczowe dostępu</span><span class="sxs-lookup"><span data-stu-id="0a790-121">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="0a790-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="0a790-122">Modifiers</span></span>](index.md)
