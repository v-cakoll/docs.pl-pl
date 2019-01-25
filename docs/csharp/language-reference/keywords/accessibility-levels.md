---
title: Poziomy ułatwień dostępu — C# odwołania
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: ca7bef8bf68b80015128619336db9fc6a8f5c237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661832"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="0f4be-102">Poziomy ułatwień dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0f4be-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="0f4be-103">Użyj modyfikatory dostępu `public`, `protected`, `internal`, lub `private`, aby określić jedną z następujących poziomów deklarowana dostępność metody dla elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="0f4be-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="0f4be-104">Deklarowana dostępność metody</span><span class="sxs-lookup"><span data-stu-id="0f4be-104">Declared accessibility</span></span>|<span data-ttu-id="0f4be-105">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="0f4be-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="0f4be-106">Dostęp nie jest ograniczona.</span><span class="sxs-lookup"><span data-stu-id="0f4be-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="0f4be-107">Dostęp jest ograniczony do zawierający klasy lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="0f4be-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="0f4be-108">Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0f4be-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="0f4be-109">Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="0f4be-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="0f4be-110">Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="0f4be-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="0f4be-111">Dostęp jest ograniczony do zawierający klasy lub typów pochodnych typu zawierającego klasy w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="0f4be-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="0f4be-112">Dostępne od C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="0f4be-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="0f4be-113">Modyfikator dostępu tylko jeden jest dozwolona dla elementu członkowskiego lub typu, z wyjątkiem sytuacji, gdy używasz `protected internal` lub `private protected` kombinacje.</span><span class="sxs-lookup"><span data-stu-id="0f4be-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="0f4be-114">Modyfikatory dostępu są niedozwolone w przypadku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0f4be-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="0f4be-115">Przestrzenie nazw nie ma ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="0f4be-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="0f4be-116">W zależności od kontekstu, w którym występuje deklaracja elementu członkowskiego dozwolone są tylko niektóre zadeklarowane możliwości dostępu do.</span><span class="sxs-lookup"><span data-stu-id="0f4be-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="0f4be-117">Jeśli modyfikator dostępu, nie jest określony w deklaracji elementu członkowskiego, jest używana domyślna dostępu.</span><span class="sxs-lookup"><span data-stu-id="0f4be-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="0f4be-118">Typy najwyższego poziomu, które nie są zagnieżdżone w innych typach, może mieć tylko `internal` lub `public` ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="0f4be-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="0f4be-119">Wartość domyślna dostępu dla tych typów `internal`.</span><span class="sxs-lookup"><span data-stu-id="0f4be-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="0f4be-120">Zagnieżdżone typy, które należą do innych typów, może zadeklarowana możliwości dostępu, zgodnie z instrukcjami w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0f4be-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="0f4be-121">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0f4be-121">Members of</span></span>|<span data-ttu-id="0f4be-122">Domyślny element członkowski w ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="0f4be-122">Default member accessibility</span></span>|<span data-ttu-id="0f4be-123">Dozwolone zadeklarowanej dostępności członka</span><span class="sxs-lookup"><span data-stu-id="0f4be-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="0f4be-124">Brak</span><span class="sxs-lookup"><span data-stu-id="0f4be-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="0f4be-125">Brak</span><span class="sxs-lookup"><span data-stu-id="0f4be-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="0f4be-126">Dostępność typu zagnieżdżonego zależy od jego [domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md), która jest określona przez oba deklarowana dostępność metody elementu członkowskiego i domena dostępności typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="0f4be-126">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="0f4be-127">Jednakże domena dostępności typu zagnieżdżonego nie może przekraczać tego dla typu zawierającej.</span><span class="sxs-lookup"><span data-stu-id="0f4be-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0f4be-128">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0f4be-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0f4be-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f4be-129">See also</span></span>
- [<span data-ttu-id="0f4be-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0f4be-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="0f4be-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0f4be-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0f4be-132">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0f4be-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="0f4be-133">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="0f4be-133">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="0f4be-134">Domena dostępności</span><span class="sxs-lookup"><span data-stu-id="0f4be-134">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="0f4be-135">Ograniczenia dotyczące używania poziomów ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="0f4be-135">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="0f4be-136">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="0f4be-136">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="0f4be-137">public</span><span class="sxs-lookup"><span data-stu-id="0f4be-137">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="0f4be-138">private</span><span class="sxs-lookup"><span data-stu-id="0f4be-138">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="0f4be-139">protected</span><span class="sxs-lookup"><span data-stu-id="0f4be-139">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
- [<span data-ttu-id="0f4be-140">internal</span><span class="sxs-lookup"><span data-stu-id="0f4be-140">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
