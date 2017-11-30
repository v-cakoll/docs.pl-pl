---
title: "Poziomy ułatwień dostępu (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="d9ab1-102">Poziomy ułatwień dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d9ab1-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="d9ab1-103">Używać modyfikatorów dostępu [publicznego](../../../csharp/language-reference/keywords/public.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), lub [prywatnej](../../../csharp/language-reference/keywords/private.md), aby określić jedną z następujących zadeklarowana poziomy ułatwień dostępu dla członków.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="d9ab1-104">Zadeklarowane ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="d9ab1-104">Declared accessibility</span></span>|<span data-ttu-id="d9ab1-105">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="d9ab1-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="d9ab1-106">Dostęp nie jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="d9ab1-107">Dostęp jest ograniczony do zawierający klasy lub typy pochodzące od klasy zawierającego.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="d9ab1-108">Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="d9ab1-109">Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące od klasy zawierającego.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="d9ab1-110">Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="d9ab1-111">Dostęp jest ograniczony do zawierającego klasę lub typy pochodzące od klasy zawierające w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>|  
  
 <span data-ttu-id="d9ab1-112">Modyfikator dostępu tylko jeden jest dozwolone dla elementu członkowskiego lub typu, z wyjątkiem, korzystając z `protected internal` lub `private protected` kombinacji.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-112">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="d9ab1-113">Modyfikatory dostępu są niedozwolone w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-113">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="d9ab1-114">Przestrzenie nazw nie ma ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-114">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="d9ab1-115">W zależności od kontekstu, w którym występuje deklaracji elementu członkowskiego dozwolone są tylko niektórych zadeklarowane dostępności.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-115">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="d9ab1-116">Jeśli nie modyfikator dostępu został określony w deklaracji elementu członkowskiego, dostępność domyślny jest używany.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-116">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="d9ab1-117">Typy najwyższego poziomu, które nie są zagnieżdżone w innych typów, może mieć tylko `internal` lub `public` ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-117">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="d9ab1-118">Dostępność domyślne dla tych typów jest `internal`.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-118">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="d9ab1-119">Zagnieżdżone typy, które są członkami innych typów, można zadeklarować dostępności, opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-119">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="d9ab1-120">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d9ab1-120">Members of</span></span>|<span data-ttu-id="d9ab1-121">Domyślny element członkowski dostępności</span><span class="sxs-lookup"><span data-stu-id="d9ab1-121">Default member accessibility</span></span>|<span data-ttu-id="d9ab1-122">Dozwolone zadeklarowane dostępność elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="d9ab1-122">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="d9ab1-123">Brak</span><span class="sxs-lookup"><span data-stu-id="d9ab1-123">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="d9ab1-124">Brak</span><span class="sxs-lookup"><span data-stu-id="d9ab1-124">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="d9ab1-125">Zależy od dostępności typu zagnieżdżonego jego [domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md), który jest określany przez oba zadeklarowane dostępność elementu członkowskiego i domena dostępności typu natychmiast zawierającego.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-125">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="d9ab1-126">Jednak domena dostępności typu zagnieżdżonego nie może przekraczać, który typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="d9ab1-126">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d9ab1-127">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d9ab1-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9ab1-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9ab1-128">See Also</span></span>  
 [<span data-ttu-id="d9ab1-129">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d9ab1-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d9ab1-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d9ab1-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d9ab1-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d9ab1-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d9ab1-132">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="d9ab1-132">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="d9ab1-133">Domena dostępności</span><span class="sxs-lookup"><span data-stu-id="d9ab1-133">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="d9ab1-134">Ograniczenia dotyczące używania poziomów ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="d9ab1-134">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="d9ab1-135">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="d9ab1-135">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="d9ab1-136">publiczny</span><span class="sxs-lookup"><span data-stu-id="d9ab1-136">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="d9ab1-137">prywatne</span><span class="sxs-lookup"><span data-stu-id="d9ab1-137">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="d9ab1-138">chronione</span><span class="sxs-lookup"><span data-stu-id="d9ab1-138">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="d9ab1-139">wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="d9ab1-139">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
