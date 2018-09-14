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
ms.openlocfilehash: 5a3bbd1d4d75c84dda741d382c8dd7568dbb474b
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514083"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="303aa-102">x:ClassModifier — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="303aa-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="303aa-103">Modyfikuje zachowanie kompilacji XAML podczas `x:Class` jest również udostępniany.</span><span class="sxs-lookup"><span data-stu-id="303aa-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="303aa-104">W szczególności, zamiast tworzyć częściowym `class` zawierający `Public` (ustawienie domyślne), poziom dostępu podany `x:Class` jest tworzona przy użyciu `NotPublic` poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="303aa-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="303aa-105">To zachowanie ma wpływ na poziom dostępu dla klasy w generowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="303aa-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="303aa-106">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="303aa-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="303aa-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="303aa-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="303aa-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="303aa-108">*NotPublic*</span></span>|<span data-ttu-id="303aa-109">Dokładnie taki ciąg znaków do przekazania do określenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> różni się w zależności od używanego języka programowania związane z kodem.</span><span class="sxs-lookup"><span data-stu-id="303aa-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="303aa-110">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="303aa-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="303aa-111">Zależności</span><span class="sxs-lookup"><span data-stu-id="303aa-111">Dependencies</span></span>  
 <span data-ttu-id="303aa-112">[x: Class](../../../docs/framework/xaml-services/x-class-directive.md) również musi być podana w tym samym elemencie, a ten element musi być elementem głównym, na stronie.</span><span class="sxs-lookup"><span data-stu-id="303aa-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="303aa-113">Aby uzyskać więcej informacji, zobacz [ \[MS-XAML\] sekcji 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="303aa-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="303aa-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="303aa-114">Remarks</span></span>  
 <span data-ttu-id="303aa-115">Wartość `x:ClassModifier` w .NET Framework XAML Services użycia zależy od języka programowania.</span><span class="sxs-lookup"><span data-stu-id="303aa-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="303aa-116">Parametry do użycia zależy od tego, jak każdy język implementuje jego <xref:System.CodeDom.Compiler.CodeDomProvider> i konwertery typu, zwraca go do zdefiniowania znaczenie dla <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, i czy ten język jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="303aa-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="303aa-117">Dla języka C#, parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `internal`.</span><span class="sxs-lookup"><span data-stu-id="303aa-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="303aa-118">Dla programu Microsoft Visual Basic .NET, parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `Friend`.</span><span class="sxs-lookup"><span data-stu-id="303aa-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="303aa-119">Aby uzyskać [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], nie istnieje obsługujące kompilowanie XAML; w związku z tym, wartość do przekazania jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="303aa-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="303aa-120">Można również określić <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` w języku C# `Public` w języku Visual Basic); Jednakże, określając <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> rzadko jest wykonywana, ponieważ <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> już jest zachowaniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="303aa-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="303aa-121">Inne wartości z kodu użytkownika równoważne poziomu dostępu do ograniczenia, takie jak `private` w języku C# nie są istotne dla `x:ClassModifier` odwołania zagnieżdżona klasa nie są obsługiwane w XAML i dlatego <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modyfikator ma taki sam skutek.</span><span class="sxs-lookup"><span data-stu-id="303aa-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="303aa-122">Uwagi dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="303aa-122">Security Notes</span></span>  
 <span data-ttu-id="303aa-123">Poziom dostępu, zgodnie z deklaracją w `x:ClassModifier` jest nadal podlega procesowi interpretacji przez określonej struktury i ich funkcji.</span><span class="sxs-lookup"><span data-stu-id="303aa-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="303aa-124">WPF obejmuje funkcje, aby załadować i tworzenie wystąpień typów gdzie `x:ClassModifier` jest `internal`, jeśli z zasobu WPF za pomocą pakietu odwołanie do identyfikatora URI odwołuje się do tej klasy.</span><span class="sxs-lookup"><span data-stu-id="303aa-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="303aa-125">W wyniku tego przypadku i potencjalnie innych podoba Ci się zaimplementowane przez innych platform, nie należy polegać wyłącznie na `x:ClassModifier` zablokować wszystkie możliwe podczas tworzenia wystąpienia prób.</span><span class="sxs-lookup"><span data-stu-id="303aa-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303aa-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="303aa-126">See Also</span></span>  
 [<span data-ttu-id="303aa-127">x:Class, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="303aa-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="303aa-128">Plik codebehind i XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="303aa-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="303aa-129">x:FieldModifier, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="303aa-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [<span data-ttu-id="303aa-130">Zabezpieczenia (WPF)</span><span class="sxs-lookup"><span data-stu-id="303aa-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="303aa-131">Typy migrowane z WPF do System.Xaml</span><span class="sxs-lookup"><span data-stu-id="303aa-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
