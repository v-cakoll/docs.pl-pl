---
title: '{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}'
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: c7bbbda88bd2fddb235b9ae639848e08a452c913
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741787"
---
# <a name="attributes"></a><span data-ttu-id="a743e-102">{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a743e-102">Attributes</span></span>
<span data-ttu-id="a743e-103"><xref:System.Attribute?displayProperty=nameWithType> jest klasą bazową służącą do definiowania atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a743e-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="a743e-104">Atrybuty są adnotacjami, które mogą być dodawane do elementów programistycznych, takich jak zestawy, typy, elementy członkowskie i parametry.</span><span class="sxs-lookup"><span data-stu-id="a743e-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="a743e-105">Są one przechowywane w metadanych zestawu i dostępne w czasie wykonywania przy użyciu interfejsów API odbicia.</span><span class="sxs-lookup"><span data-stu-id="a743e-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="a743e-106">Na przykład struktura definiuje <xref:System.ObsoleteAttribute>, które mogą być stosowane do typu lub elementu członkowskiego, aby wskazać, że typ lub element członkowski jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="a743e-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="a743e-107">Atrybuty mogą zawierać jedną lub więcej właściwości, które zawierają dodatkowe dane związane z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="a743e-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="a743e-108">Na przykład `ObsoleteAttribute` może zawierać dodatkowe informacje o wersji, w której typ lub element członkowski został uznany za przestarzały, a także opis nowych interfejsów API zastępujących przestarzały interfejs API.</span><span class="sxs-lookup"><span data-stu-id="a743e-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>

 <span data-ttu-id="a743e-109">Podczas stosowania atrybutu należy określić pewne właściwości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a743e-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="a743e-110">Są one określane jako wymagane właściwości lub wymagane argumenty, ponieważ są reprezentowane jako parametry konstruktora pozycyjnyego.</span><span class="sxs-lookup"><span data-stu-id="a743e-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="a743e-111">Na przykład właściwość <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> <xref:System.Diagnostics.ConditionalAttribute> jest właściwością wymaganą.</span><span class="sxs-lookup"><span data-stu-id="a743e-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="a743e-112">Właściwości, które nie muszą być określone, gdy atrybut jest stosowany, nazywa się opcjonalnymi właściwościami (lub argumentami opcjonalnymi).</span><span class="sxs-lookup"><span data-stu-id="a743e-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="a743e-113">Są one reprezentowane przez właściwości settable.</span><span class="sxs-lookup"><span data-stu-id="a743e-113">They are represented by settable properties.</span></span> <span data-ttu-id="a743e-114">Kompilatory zapewniają specjalną składnię do ustawiania tych właściwości podczas stosowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a743e-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="a743e-115">Na przykład właściwość <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> reprezentuje opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="a743e-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="a743e-116">✔️ Nadaj nazwę klasom atrybutów niestandardowych z sufiksem "Attribute".</span><span class="sxs-lookup"><span data-stu-id="a743e-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="a743e-117">✔️ zastosować <xref:System.AttributeUsageAttribute> do atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a743e-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="a743e-118">✔️ udostępniają właściwości settable dla opcjonalnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="a743e-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="a743e-119">✔️ udostępniają właściwości tylko do pobrania dla wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="a743e-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="a743e-120">✔️ udostępniają parametry konstruktora, aby inicjować właściwości odpowiadające argumentom wymaganym.</span><span class="sxs-lookup"><span data-stu-id="a743e-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="a743e-121">Każdy parametr powinien mieć taką samą nazwę (choć z inną wielkością liter) jako odpowiednią właściwość.</span><span class="sxs-lookup"><span data-stu-id="a743e-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="a743e-122">❌ unikać udostępniania parametrów konstruktora, aby inicjować właściwości odpowiadające argumentom opcjonalnym.</span><span class="sxs-lookup"><span data-stu-id="a743e-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="a743e-123">Innymi słowy, nie mają właściwości, które można ustawić przy użyciu zarówno konstruktora, jak i metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="a743e-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="a743e-124">Te wytyczne czynią bardzo jawne, które argumenty są opcjonalne i które są wymagane i nie mają dwóch sposobów na wykonanie tego samego działania.</span><span class="sxs-lookup"><span data-stu-id="a743e-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="a743e-125">❌ uniknąć przeładowania konstruktorów atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a743e-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="a743e-126">Posiadanie tylko jednego konstruktora jasno komunikuje się z użytkownikiem, które argumenty są wymagane i które są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a743e-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="a743e-127">✔️ należy zapieczętować klasy atrybutów niestandardowych, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a743e-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="a743e-128">Powoduje to szybsze wyszukiwanie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a743e-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="a743e-129">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="a743e-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a743e-130">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="a743e-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a743e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a743e-131">See also</span></span>

- [<span data-ttu-id="a743e-132">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="a743e-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="a743e-133">Zalecenia dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="a743e-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
