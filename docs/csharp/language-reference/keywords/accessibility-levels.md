---
title: Poziomy ułatwień dostępu (odwołanie w C#)
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 4679fd2564454e7f1ade5cb4813729b65f433012
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787548"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="598fe-102">Poziomy ułatwień dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="598fe-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="598fe-103">Użyj modyfikatory dostępu `public`, `protected`, `internal`, lub `private`, aby określić jedną z następujących poziomów deklarowana dostępność metody dla elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="598fe-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="598fe-104">Deklarowana dostępność metody</span><span class="sxs-lookup"><span data-stu-id="598fe-104">Declared accessibility</span></span>|<span data-ttu-id="598fe-105">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="598fe-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="598fe-106">Dostęp nie jest ograniczona.</span><span class="sxs-lookup"><span data-stu-id="598fe-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="598fe-107">Dostęp jest ograniczony do zawierający klasy lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="598fe-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="598fe-108">Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="598fe-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="598fe-109">Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="598fe-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="598fe-110">Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="598fe-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="598fe-111">Dostęp jest ograniczony do zawierający klasy lub typów pochodnych typu zawierającego klasy w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="598fe-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="598fe-112">Dostępne od C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="598fe-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="598fe-113">Modyfikator dostępu tylko jeden jest dozwolona dla elementu członkowskiego lub typu, z wyjątkiem sytuacji, gdy używasz `protected internal` lub `private protected` kombinacje.</span><span class="sxs-lookup"><span data-stu-id="598fe-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="598fe-114">Modyfikatory dostępu są niedozwolone w przypadku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="598fe-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="598fe-115">Przestrzenie nazw nie ma ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="598fe-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="598fe-116">W zależności od kontekstu, w którym występuje deklaracja elementu członkowskiego dozwolone są tylko niektóre zadeklarowane możliwości dostępu do.</span><span class="sxs-lookup"><span data-stu-id="598fe-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="598fe-117">Jeśli modyfikator dostępu, nie jest określony w deklaracji elementu członkowskiego, jest używana domyślna dostępu.</span><span class="sxs-lookup"><span data-stu-id="598fe-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="598fe-118">Typy najwyższego poziomu, które nie są zagnieżdżone w innych typach, może mieć tylko `internal` lub `public` ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="598fe-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="598fe-119">Wartość domyślna dostępu dla tych typów `internal`.</span><span class="sxs-lookup"><span data-stu-id="598fe-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="598fe-120">Zagnieżdżone typy, które należą do innych typów, może zadeklarowana możliwości dostępu, zgodnie z instrukcjami w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="598fe-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="598fe-121">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="598fe-121">Members of</span></span>|<span data-ttu-id="598fe-122">Domyślny element członkowski w ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="598fe-122">Default member accessibility</span></span>|<span data-ttu-id="598fe-123">Dozwolone zadeklarowanej dostępności członka</span><span class="sxs-lookup"><span data-stu-id="598fe-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="598fe-124">Brak</span><span class="sxs-lookup"><span data-stu-id="598fe-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="598fe-125">Brak</span><span class="sxs-lookup"><span data-stu-id="598fe-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="598fe-126">Dostępność typu zagnieżdżonego zależy od jego [domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md), która jest określona przez oba deklarowana dostępność metody elementu członkowskiego i domena dostępności typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="598fe-126">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="598fe-127">Jednakże domena dostępności typu zagnieżdżonego nie może przekraczać tego dla typu zawierającej.</span><span class="sxs-lookup"><span data-stu-id="598fe-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="598fe-128">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="598fe-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="598fe-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="598fe-129">See Also</span></span>  
- [<span data-ttu-id="598fe-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="598fe-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="598fe-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="598fe-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="598fe-132">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="598fe-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="598fe-133">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="598fe-133">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="598fe-134">Domena dostępności</span><span class="sxs-lookup"><span data-stu-id="598fe-134">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
- [<span data-ttu-id="598fe-135">Ograniczenia dotyczące używania poziomów ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="598fe-135">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
- [<span data-ttu-id="598fe-136">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="598fe-136">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="598fe-137">public</span><span class="sxs-lookup"><span data-stu-id="598fe-137">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
- [<span data-ttu-id="598fe-138">private</span><span class="sxs-lookup"><span data-stu-id="598fe-138">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="598fe-139">protected</span><span class="sxs-lookup"><span data-stu-id="598fe-139">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
- [<span data-ttu-id="598fe-140">internal</span><span class="sxs-lookup"><span data-stu-id="598fe-140">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
