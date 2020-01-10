---
title: Poziomy ułatwień C# dostępu — odwołanie
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26fbc2a6d86aead537465c304146630f8bcd3ad4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713819"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="c09a2-102">Poziomy ułatwień dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c09a2-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="c09a2-103">Użyj modyfikatorów dostępu, `public`, `protected`, `internal`lub `private`, aby określić jeden z następujących zadeklarowanych poziomów dostępności dla elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c09a2-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="c09a2-104">Zadeklarowane ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="c09a2-104">Declared accessibility</span></span>|<span data-ttu-id="c09a2-105">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="c09a2-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="c09a2-106">Dostęp nie jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="c09a2-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="c09a2-107">Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="c09a2-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="c09a2-108">Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c09a2-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="c09a2-109">Dostęp jest ograniczony do bieżącego zestawu lub typów pochodzących od klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="c09a2-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="c09a2-110">Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="c09a2-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="c09a2-111">Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="c09a2-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="c09a2-112">Dostępne od C# 7,2.</span><span class="sxs-lookup"><span data-stu-id="c09a2-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="c09a2-113">Tylko jeden modyfikator dostępu jest dozwolony dla elementu członkowskiego lub typu, z wyjątkiem tego, że używane są kombinacje `protected internal` lub `private protected`.</span><span class="sxs-lookup"><span data-stu-id="c09a2-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="c09a2-114">Modyfikatory dostępu są niedozwolone w przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="c09a2-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="c09a2-115">Przestrzenie nazw nie mają ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="c09a2-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="c09a2-116">W zależności od kontekstu, w którym występuje Deklaracja elementu członkowskiego, dozwolone są tylko niektóre zadeklarowane podano.</span><span class="sxs-lookup"><span data-stu-id="c09a2-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="c09a2-117">Jeśli w deklaracji elementu członkowskiego nie określono modyfikatora dostępu, zostanie użyta domyślna dostępność.</span><span class="sxs-lookup"><span data-stu-id="c09a2-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="c09a2-118">Typy najwyższego poziomu, które nie są zagnieżdżone w innych typach, mogą mieć tylko `internal` lub `public` ułatwienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="c09a2-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="c09a2-119">Domyślne ułatwienia dostępu dla tych typów są `internal`.</span><span class="sxs-lookup"><span data-stu-id="c09a2-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="c09a2-120">Zagnieżdżone typy, które są elementami członkowskimi innych typów, mogą mieć zadeklarowane podano, jak wskazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c09a2-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="c09a2-121">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c09a2-121">Members of</span></span>|<span data-ttu-id="c09a2-122">Dostępność domyślnego elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c09a2-122">Default member accessibility</span></span>|<span data-ttu-id="c09a2-123">Dozwolone zadeklarowane dostępność elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c09a2-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="c09a2-124">Brak</span><span class="sxs-lookup"><span data-stu-id="c09a2-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="c09a2-125">Brak</span><span class="sxs-lookup"><span data-stu-id="c09a2-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="c09a2-126">Dostępność typu zagnieżdżonego zależy od jego [domeny dostępności](./accessibility-domain.md), który jest określany przez zadeklarowaną dostępność elementu członkowskiego i domenę dostępności typu natychmiastowego.</span><span class="sxs-lookup"><span data-stu-id="c09a2-126">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="c09a2-127">Jednak domena dostępności typu zagnieżdżonego nie może przekroczyć tego typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="c09a2-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c09a2-128">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c09a2-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c09a2-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c09a2-129">See also</span></span>

- [<span data-ttu-id="c09a2-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c09a2-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c09a2-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c09a2-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c09a2-132">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c09a2-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c09a2-133">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="c09a2-133">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="c09a2-134">Domena dostępności</span><span class="sxs-lookup"><span data-stu-id="c09a2-134">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="c09a2-135">Ograniczenia dotyczące używania poziomów ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="c09a2-135">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="c09a2-136">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="c09a2-136">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="c09a2-137">public</span><span class="sxs-lookup"><span data-stu-id="c09a2-137">public</span></span>](./public.md)
- [<span data-ttu-id="c09a2-138">private</span><span class="sxs-lookup"><span data-stu-id="c09a2-138">private</span></span>](./private.md)
- [<span data-ttu-id="c09a2-139">protected</span><span class="sxs-lookup"><span data-stu-id="c09a2-139">protected</span></span>](./protected.md)
- [<span data-ttu-id="c09a2-140">internal</span><span class="sxs-lookup"><span data-stu-id="c09a2-140">internal</span></span>](./internal.md)
