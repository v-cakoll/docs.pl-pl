---
title: Modyfikatory dostępu — C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 7dfbc103b3fd0ebf8c349bd36dc54915782eb807
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422934"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="9d684-102">Modyfikatory dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9d684-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="9d684-103">Modyfikatory dostępu są słowami kluczowymi używanymi do określania zadeklarowanej dostępności elementu członkowskiego lub typu.</span><span class="sxs-lookup"><span data-stu-id="9d684-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="9d684-104">W tej sekcji przedstawiono cztery Modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="9d684-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="9d684-105">Za pomocą modyfikatorów dostępu można określić następujące sześć poziomów dostępności:</span><span class="sxs-lookup"><span data-stu-id="9d684-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="9d684-106">[`public`](public.md): dostęp nie jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="9d684-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="9d684-107">[`protected`](protected.md): dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="9d684-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="9d684-108">[`internal`](internal.md): dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9d684-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="9d684-109">[`protected internal`](protected-internal.md): dostęp jest ograniczony do bieżącego zestawu lub typów pochodzących od klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="9d684-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="9d684-110">[`private`](private.md): dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="9d684-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="9d684-111">[`private protected`](private-protected.md): dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="9d684-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="9d684-112">W tej sekcji wprowadzono również następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9d684-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="9d684-113">[Poziomy ułatwień](./accessibility-levels.md)dostępu: aby zadeklarować sześć poziomów dostępności, użyj czterech modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="9d684-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="9d684-114">[Domena dostępności](./accessibility-domain.md): określa, gdzie w sekcjach programu można odwoływać się do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9d684-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="9d684-115">[Ograniczenia dotyczące używania poziomów ułatwień dostępu](./restrictions-on-using-accessibility-levels.md): Podsumowanie ograniczeń dotyczących używania zadeklarowanych poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="9d684-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d684-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d684-116">See also</span></span>

- [<span data-ttu-id="9d684-117">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="9d684-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9d684-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9d684-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9d684-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9d684-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="9d684-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="9d684-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="9d684-121">Słowa kluczowe dostępu</span><span class="sxs-lookup"><span data-stu-id="9d684-121">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="9d684-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="9d684-122">Modifiers</span></span>](index.md)
