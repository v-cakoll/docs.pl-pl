---
title: Attributes1
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: KrzysztofCwalina
ms.openlocfilehash: 7ab499d5a9c8388e9081a07921d3e444c0cdd879
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131433"
---
# <a name="attributes"></a><span data-ttu-id="0e245-102">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0e245-102">Attributes</span></span>
<span data-ttu-id="0e245-103"><xref:System.Attribute?displayProperty=nameWithType> Klasa bazowa służy do definiowania atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="0e245-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="0e245-104">Atrybuty są adnotacji, które mogą być dodawane do elementów programowania, takich jak zestawy, typy, elementy członkowskie i parametry.</span><span class="sxs-lookup"><span data-stu-id="0e245-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="0e245-105">Są przechowywane w metadanych zestawu i można uzyskać dostęp w czasie wykonywania za pomocą odbicia interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="0e245-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="0e245-106">Na przykład definiuje platformę <xref:System.ObsoleteAttribute>, które można zastosować do typu lub elementu członkowskiego, aby wskazać, że typ lub składowa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="0e245-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="0e245-107">Atrybuty mogą mieć jedną lub więcej właściwości, wykonujących dodatkowych danych powiązany z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="0e245-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="0e245-108">Na przykład `ObsoleteAttribute` może zawierać dodatkowe informacje o wersji, w którym typu lub elementu członkowskiego stało się przestarzałe i opis nowych interfejsów API, zastępując przestarzałych API.</span><span class="sxs-lookup"><span data-stu-id="0e245-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="0e245-109">Niektóre właściwości atrybutu musi być określona, jeśli ten atrybut jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="0e245-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="0e245-110">Są one określane jako wymagane właściwości lub wymagane argumenty, ponieważ są one reprezentowane jako parametry pozycyjne konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0e245-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="0e245-111">Na przykład <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> właściwość <xref:System.Diagnostics.ConditionalAttribute> jest właściwością wymaganą.</span><span class="sxs-lookup"><span data-stu-id="0e245-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="0e245-112">Właściwości, które nie muszą być określone, gdy ten atrybut jest stosowany noszą nazwę właściwości opcjonalnych (lub opcjonalne argumenty).</span><span class="sxs-lookup"><span data-stu-id="0e245-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="0e245-113">Są one reprezentowane przez właściwości do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="0e245-113">They are represented by settable properties.</span></span> <span data-ttu-id="0e245-114">Kompilatory zapewniają specjalnej składni, aby ustawić te właściwości, jeśli atrybut jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="0e245-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="0e245-115">Na przykład <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> właściwość reprezentuje opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="0e245-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="0e245-116">**✓ DO** nazwy klas atrybutów niestandardowych z sufiksem "Atrybutu".</span><span class="sxs-lookup"><span data-stu-id="0e245-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="0e245-117">**✓ DO** zastosować <xref:System.AttributeUsageAttribute> atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="0e245-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="0e245-118">**✓ DO** Podaj można ustawić właściwości dla argumentów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="0e245-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="0e245-119">**✓ DO** Podaj właściwości tylko do pobrania dla wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="0e245-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="0e245-120">**✓ DO** podać parametry konstruktora zainicjować właściwości odpowiadającej wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="0e245-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="0e245-121">Każdy parametr powinien mieć taką samą nazwę (mimo że przy użyciu innej wielkości liter), jak odpowiadającą właściwość.</span><span class="sxs-lookup"><span data-stu-id="0e245-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="0e245-122">**X AVOID** podając parametrami konstruktora zainicjować właściwości odpowiadającej Argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="0e245-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="0e245-123">Innymi słowy nie ma właściwości, które można ustawić za pomocą zarówno konstruktora, jak i metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="0e245-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="0e245-124">Ta wytyczna sprawia, że bardzo jawnych argumentów, które są opcjonalne i które są wymagane i pozwala uniknąć konieczności wykonując ten sam efekt na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="0e245-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="0e245-125">**X AVOID** przeładowania konstruktorów atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="0e245-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="0e245-126">Wyraźnie posiadanie tylko jednego konstruktora komunikuje się użytkownik, który argumentów wymaganych i opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="0e245-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="0e245-127">**✓ DO** zapieczętować klas atrybutów niestandardowych, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="0e245-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="0e245-128">Dzięki temu szybsze wyszukiwania dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0e245-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="0e245-129">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="0e245-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0e245-130">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="0e245-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e245-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e245-131">See also</span></span>

- [<span data-ttu-id="0e245-132">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="0e245-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="0e245-133">Zalecenia dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="0e245-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
