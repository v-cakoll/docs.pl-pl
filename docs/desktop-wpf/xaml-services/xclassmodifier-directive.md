---
title: x:ClassModifier — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072033"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="08504-102">x:ClassModifier — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="08504-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="08504-103">Modyfikuje zachowanie kompilacji `x:Class` XAML, gdy jest również podana.</span><span class="sxs-lookup"><span data-stu-id="08504-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="08504-104">W szczególności zamiast tworzenia `class` częściowego, który `Public` ma poziom dostępu (domyślnie), dostarczone `x:Class` jest tworzony z poziomem `NotPublic` dostępu.</span><span class="sxs-lookup"><span data-stu-id="08504-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="08504-105">To zachowanie wpływa na poziom dostępu dla klasy w wygenerowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="08504-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="08504-106">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="08504-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="08504-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="08504-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="08504-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="08504-108">*NotPublic*</span></span>|<span data-ttu-id="08504-109">Dokładny ciąg do przekazania <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> do określenia w porównaniu różni się, w zależności od języka programowania związane z kodem, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="08504-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="08504-110">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="08504-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="08504-111">Zależności</span><span class="sxs-lookup"><span data-stu-id="08504-111">Dependencies</span></span>

<span data-ttu-id="08504-112">[x:Klasa](xclass-directive.md) musi być również podana na tym samym elemencie, a ten element musi być elementem głównym na stronie.</span><span class="sxs-lookup"><span data-stu-id="08504-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="08504-113">Aby uzyskać więcej informacji, zobacz [ \[rozdział 4.3.1.8 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="08504-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="08504-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08504-114">Remarks</span></span>

<span data-ttu-id="08504-115">Wartość `x:ClassModifier` użycia usług .NET XAML różni się w zależności od języka programowania.</span><span class="sxs-lookup"><span data-stu-id="08504-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="08504-116">Ciąg do użycia zależy od tego, <xref:System.CodeDom.Compiler.CodeDomProvider> jak każdy język implementuje jego i <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>konwertery typów zwraca do definiowania znaczeń dla i , i czy w tym języku jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="08504-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="08504-117">W przypadku języka C#ciąg, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> który `internal`ma być przekazywalny, to .</span><span class="sxs-lookup"><span data-stu-id="08504-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="08504-118">W przypadku programu Microsoft Visual Basic .NET <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`ciąg, który ma być przekazyny do wyznaczenia, to .</span><span class="sxs-lookup"><span data-stu-id="08504-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="08504-119">W przypadku języka C++/CLI nie istnieją żadne obiekty docelowe obsługujące kompilację XAML; w związku z tym wartość do przekazania jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="08504-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="08504-120">Można również <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> określić (`public` `Public` w języku C#, w języku Visual Basic); jednak określenie <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest rzadko wykonywane, ponieważ <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest już domyślne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="08504-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="08504-121">Inne wartości z równoważnych ograniczeń na poziomie `private` dostępu kodu użytkownika, `x:ClassModifier` takich jak w języku C#, nie są istotne dla <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ponieważ odwołania do klasy zagnieżdżonej nie są obsługiwane w XAML i dlatego modyfikator ma ten sam efekt.</span><span class="sxs-lookup"><span data-stu-id="08504-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="08504-122">Uwagi dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="08504-122">Security Notes</span></span>

<span data-ttu-id="08504-123">Poziom dostępu zadeklarowany `x:ClassModifier` w nadal podlega interpretacji przez określone ramy i ich możliwości.</span><span class="sxs-lookup"><span data-stu-id="08504-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="08504-124">WPF WPF zawiera możliwości ładowania i `x:ClassModifier` `internal`tworzenia wystąpienia typów, gdzie jest , jeśli ta klasa odwołuje się z zasobu WPF za pośrednictwem odwołania identyfikatora URI pakietu.</span><span class="sxs-lookup"><span data-stu-id="08504-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="08504-125">W konsekwencji tego przypadku i potencjalnie innych, takich jak on zaimplementowany przez inne struktury, nie polegać wyłącznie na `x:ClassModifier` zablokować wszystkie możliwe próby wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="08504-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="08504-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08504-126">See also</span></span>

- [<span data-ttu-id="08504-127">x:Class — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="08504-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="08504-128">Związane z kodem i XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="08504-128">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="08504-129">x:FieldModifier — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="08504-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="08504-130">Zabezpieczenia (WPF)</span><span class="sxs-lookup"><span data-stu-id="08504-130">Security (WPF)</span></span>](../../framework/wpf/security-wpf.md)
- [<span data-ttu-id="08504-131">Typy migrowane z WPF do System.Xaml</span><span class="sxs-lookup"><span data-stu-id="08504-131">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
