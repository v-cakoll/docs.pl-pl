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
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837236"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="36f19-102">x:ClassModifier — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="36f19-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="36f19-103">Modyfikuje zachowanie kompilacji XAML, gdy podano również `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="36f19-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="36f19-104">W przeciwieństwie do tworzenia częściowej `class`, która ma `Public` dostępu (wartość domyślna), udostępniony `x:Class` jest tworzony z poziomu dostępu `NotPublic`.</span><span class="sxs-lookup"><span data-stu-id="36f19-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="36f19-105">To zachowanie ma wpływ na poziom dostępu dla klasy w wygenerowanych zestawach.</span><span class="sxs-lookup"><span data-stu-id="36f19-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="36f19-106">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="36f19-106">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="36f19-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="36f19-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36f19-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="36f19-108">*NotPublic*</span></span>|<span data-ttu-id="36f19-109">Dokładny ciąg, który ma zostać przekazany do określenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>, a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> różni się w zależności od używanego języka programowania związanego z kodem.</span><span class="sxs-lookup"><span data-stu-id="36f19-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="36f19-110">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="36f19-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="36f19-111">Zależności</span><span class="sxs-lookup"><span data-stu-id="36f19-111">Dependencies</span></span>  
 <span data-ttu-id="36f19-112">[x:Class](x-class-directive.md) musi również znajdować się na tym samym elemencie, a element musi być elementem głównym na stronie.</span><span class="sxs-lookup"><span data-stu-id="36f19-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="36f19-113">Aby uzyskać więcej informacji, zobacz [sekcję\[MS-XAML\] sekcji 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="36f19-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36f19-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36f19-114">Remarks</span></span>  
 <span data-ttu-id="36f19-115">Wartość `x:ClassModifier` w .NET Framework użyciu usług XAML różni się w zależności od języka programowania.</span><span class="sxs-lookup"><span data-stu-id="36f19-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="36f19-116">Ciąg, który ma być używany, zależy od tego, w jaki sposób każdy język implementuje swoją <xref:System.CodeDom.Compiler.CodeDomProvider>, i konwertery typów, które zwraca, aby zdefiniować znaczenia dla <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>oraz czy w tym języku jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="36f19-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="36f19-117">Dla C#, ciąg, który ma zostać przekazany do wyznaczenia <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `internal`.</span><span class="sxs-lookup"><span data-stu-id="36f19-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="36f19-118">W przypadku programu Microsoft Visual Basic .NET ciąg, który ma zostać przekazany do wyznaczania <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `Friend`.</span><span class="sxs-lookup"><span data-stu-id="36f19-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="36f19-119">Dla C++/CLI nie istnieją żadne elementy docelowe, które obsługują kompilowanie kodu XAML; w związku z tym wartość do przekazania nie została określona.</span><span class="sxs-lookup"><span data-stu-id="36f19-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="36f19-120">Możesz również określić <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` w C#, `Public` w Visual Basic). jednak Określanie <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest rzadko wykonywane, ponieważ <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest już zachowaniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="36f19-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="36f19-121">Inne wartości mające równoważne ograniczenia poziomu dostępu do kodu użytkownika, takie jak `private` C#w, nie są istotne dla `x:ClassModifier`, ponieważ odwołania do klas zagnieżdżonych nie są obsługiwane w języku XAML i w związku z tym modyfikator <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ma ten sam efekt.</span><span class="sxs-lookup"><span data-stu-id="36f19-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="36f19-122">Uwagi dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="36f19-122">Security Notes</span></span>  
 <span data-ttu-id="36f19-123">Poziom dostępu zadeklarowany w `x:ClassModifier` nadal podlega interpretacji przez poszczególne struktury i ich możliwości.</span><span class="sxs-lookup"><span data-stu-id="36f19-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="36f19-124">WPF obejmuje możliwości ładowania i tworzenia wystąpienia typów, w których `x:ClassModifier` jest `internal`, jeśli ta klasa jest przywoływana z zasobu WPF za pomocą odwołania do identyfikatora URI pakietu.</span><span class="sxs-lookup"><span data-stu-id="36f19-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="36f19-125">W związku z tym w tym przypadku i potencjalnie innym, podobnym do wdrożonym przez inne struktury, nie należy polegać wyłącznie na `x:ClassModifier`, aby zablokować wszystkie możliwe próby utworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="36f19-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f19-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36f19-126">See also</span></span>

- [<span data-ttu-id="36f19-127">x:Class, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="36f19-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="36f19-128">Plik codebehind i XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="36f19-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="36f19-129">x:FieldModifier, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="36f19-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="36f19-130">Zabezpieczenia (WPF)</span><span class="sxs-lookup"><span data-stu-id="36f19-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="36f19-131">Typy migrowane z WPF do System.Xaml</span><span class="sxs-lookup"><span data-stu-id="36f19-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
