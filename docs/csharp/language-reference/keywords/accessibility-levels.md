---
title: Poziomy ułatwień dostępu — odwołanie do języka C#
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26fbc2a6d86aead537465c304146630f8bcd3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713819"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="b6742-102">Poziomy ułatwień dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b6742-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="b6742-103">Użyj modyfikatorów `public`dostępu `protected` `internal`, `private`, , lub , aby określić jeden z następujących zadeklarowanych poziomów dostępności dla członków.</span><span class="sxs-lookup"><span data-stu-id="b6742-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="b6742-104">Deklarowana dostępność</span><span class="sxs-lookup"><span data-stu-id="b6742-104">Declared accessibility</span></span>|<span data-ttu-id="b6742-105">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="b6742-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="b6742-106">Dostęp nie jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="b6742-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="b6742-107">Dostęp jest ograniczony do zawierająceklasy lub typów pochodzących z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="b6742-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="b6742-108">Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6742-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="b6742-109">Dostęp jest ograniczony do bieżącego zestawu lub typów pochodzących z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="b6742-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="b6742-110">Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="b6742-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="b6742-111">Dostęp jest ograniczony do klasy zawierającej lub typów pochodzących z klasy zawierającej w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="b6742-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="b6742-112">Dostępne od języka C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="b6742-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="b6742-113">Tylko jeden modyfikator dostępu jest dozwolony dla elementu `protected internal` `private protected` członkowskiego lub typu, z wyjątkiem przypadków użycia lub kombinacji.</span><span class="sxs-lookup"><span data-stu-id="b6742-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="b6742-114">Modyfikatory dostępu nie są dozwolone w przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="b6742-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="b6742-115">Przestrzenie nazw nie mają ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="b6742-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="b6742-116">W zależności od kontekstu, w którym występuje deklaracja elementu członkowskiego, dozwolone są tylko niektóre zadeklarowane accessibilities.</span><span class="sxs-lookup"><span data-stu-id="b6742-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="b6742-117">Jeśli w deklaracji elementów członkowskich nie określono modyfikatora dostępu, używana jest domyślna dostępność.</span><span class="sxs-lookup"><span data-stu-id="b6742-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="b6742-118">Typy najwyższego poziomu, które nie są zagnieżdżone w innych typach, mogą mieć `internal` tylko lub `public` ułatwienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="b6742-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="b6742-119">Domyślną dostępnością dla `internal`tych typów jest .</span><span class="sxs-lookup"><span data-stu-id="b6742-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="b6742-120">Zagnieżdżone typy, które są członkami innych typów, mogą mieć zadeklarowane accessibilities jak wskazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b6742-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="b6742-121">Członkowie</span><span class="sxs-lookup"><span data-stu-id="b6742-121">Members of</span></span>|<span data-ttu-id="b6742-122">Domyślna dostępność elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="b6742-122">Default member accessibility</span></span>|<span data-ttu-id="b6742-123">Dozwolona zadeklarowana dostępność elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="b6742-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="b6742-124">Brak</span><span class="sxs-lookup"><span data-stu-id="b6742-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="b6742-125">Brak</span><span class="sxs-lookup"><span data-stu-id="b6742-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="b6742-126">Dostępność typu zagnieżdżonego zależy od jego [domeny ułatwień dostępu](./accessibility-domain.md), która jest określana zarówno przez zadeklarowaną dostępność elementu członkowskiego, jak i domenę ułatwień dostępu typu bezpośrednio zawierającego.</span><span class="sxs-lookup"><span data-stu-id="b6742-126">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="b6742-127">Jednak domena ułatwień dostępu typu zagnieżdżonego nie może przekraczać domeny zawierającej.</span><span class="sxs-lookup"><span data-stu-id="b6742-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b6742-128">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b6742-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b6742-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6742-129">See also</span></span>

- [<span data-ttu-id="b6742-130">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="b6742-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b6742-131">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="b6742-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b6742-132">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="b6742-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b6742-133">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="b6742-133">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="b6742-134">Domena dostępności</span><span class="sxs-lookup"><span data-stu-id="b6742-134">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="b6742-135">Ograniczenia dotyczące używania poziomów ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="b6742-135">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="b6742-136">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="b6742-136">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="b6742-137">Publicznego</span><span class="sxs-lookup"><span data-stu-id="b6742-137">public</span></span>](./public.md)
- [<span data-ttu-id="b6742-138">Prywatny</span><span class="sxs-lookup"><span data-stu-id="b6742-138">private</span></span>](./private.md)
- [<span data-ttu-id="b6742-139">protected</span><span class="sxs-lookup"><span data-stu-id="b6742-139">protected</span></span>](./protected.md)
- [<span data-ttu-id="b6742-140">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="b6742-140">internal</span></span>](./internal.md)
