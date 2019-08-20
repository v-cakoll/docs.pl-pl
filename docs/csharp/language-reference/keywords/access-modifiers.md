---
title: Modyfikatory dostępu — C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 5568d79c4a13b7b0db5a46bb4ebb2168ea66a2c9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606094"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="3499d-102">Modyfikatory dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3499d-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="3499d-103">Modyfikatory dostępu są słowami kluczowymi używanymi do określania zadeklarowanej dostępności elementu członkowskiego lub typu.</span><span class="sxs-lookup"><span data-stu-id="3499d-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="3499d-104">W tej sekcji przedstawiono cztery Modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="3499d-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="3499d-105">Za pomocą modyfikatorów dostępu można określić następujące sześć poziomów dostępności:</span><span class="sxs-lookup"><span data-stu-id="3499d-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="3499d-106">[`public`](public.md): Dostęp nie jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="3499d-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="3499d-107">[`protected`](protected.md): Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="3499d-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="3499d-108">[`internal`](internal.md): Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3499d-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="3499d-109">[`protected internal`](protected-internal.md): Dostęp jest ograniczony do bieżącego zestawu lub typów pochodzących od klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="3499d-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="3499d-110">[`private`](private.md): Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="3499d-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="3499d-111">[`private protected`](private-protected.md): Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="3499d-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="3499d-112">W tej sekcji wprowadzono również następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="3499d-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="3499d-113">[Poziomy ułatwień dostępu](./accessibility-levels.md): Użycie czterech modyfikatorów dostępu do deklarowania sześciu poziomów dostępności.</span><span class="sxs-lookup"><span data-stu-id="3499d-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="3499d-114">[Domena dostępności](./accessibility-domain.md): Określa, gdzie w sekcjach programu można odwoływać się do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3499d-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="3499d-115">[Ograniczenia dotyczące używania poziomów ułatwień dostępu](./restrictions-on-using-accessibility-levels.md): Podsumowanie ograniczeń dotyczących używania zadeklarowanych poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="3499d-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3499d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3499d-116">See also</span></span>

- [<span data-ttu-id="3499d-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3499d-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3499d-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3499d-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3499d-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3499d-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="3499d-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="3499d-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3499d-121">Słowa kluczowe dostępu</span><span class="sxs-lookup"><span data-stu-id="3499d-121">Access Keywords</span></span>](./access-keywords.md)
- [<span data-ttu-id="3499d-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="3499d-122">Modifiers</span></span>](./modifiers.md)
