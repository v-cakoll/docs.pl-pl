---
title: mc:Ignorable — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: b68909d94ad8cc5bba75b2c520db82c5ccf1b922
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206188"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="792cf-102">mc:Ignorable — Atrybut</span><span class="sxs-lookup"><span data-stu-id="792cf-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="792cf-103">Określa, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] które prefiksy przestrzeni nazw napotkane w pliku znaczników mogą zostać zignorowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przez procesor.</span><span class="sxs-lookup"><span data-stu-id="792cf-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="792cf-104">Ten `mc:Ignorable` atrybut obsługuje zgodność znaczników zarówno dla niestandardowego mapowania przestrzeni nazw, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jak i do przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="792cf-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="792cf-105">Użycie atrybutu języka XAML (pojedynczy prefiks)</span><span class="sxs-lookup"><span data-stu-id="792cf-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="792cf-106">Użycie atrybutu języka XAML (dwa prefiksy)</span><span class="sxs-lookup"><span data-stu-id="792cf-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="792cf-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="792cf-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="792cf-108">*ignorablePrefix, ignorablePrefix1 itd.*</span><span class="sxs-lookup"><span data-stu-id="792cf-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="792cf-109">Dowolny prawidłowy ciąg prefiksu na specyfikację XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="792cf-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="792cf-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="792cf-110">*ignorableUri*</span></span>|<span data-ttu-id="792cf-111">Dowolny prawidłowy identyfikator URI służący do wyznaczania przestrzeni nazw, zgodnie ze specyfikacją XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="792cf-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="792cf-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="792cf-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="792cf-113">Element, który może być ignorowany [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przez implementacje procesora, jeśli nie można rozpoznać typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="792cf-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="792cf-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="792cf-114">Remarks</span></span>  
 <span data-ttu-id="792cf-115">Prefiks przestrzeni nazw jest zalecaną konwencją prefiksu używaną podczas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mapowania przestrzeni `http://schemas.openxmlformats.org/markup-compatibility/2006`nazw zgodności. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] `mc`</span><span class="sxs-lookup"><span data-stu-id="792cf-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace `http://schemas.openxmlformats.org/markup-compatibility/2006`.</span></span>  
  
 <span data-ttu-id="792cf-116">Elementy lub atrybuty, w których część prefiksu nazwy elementu jest identyfikowana `mc:Ignorable` jako nie powoduje błędów podczas przetwarzania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przez procesor.</span><span class="sxs-lookup"><span data-stu-id="792cf-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="792cf-117">Jeśli ten atrybut nie może zostać rozpoznany jako typ podstawowy lub konstrukcja programistyczna, ten element jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="792cf-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="792cf-118">Należy jednak zauważyć, że zignorowane elementy nadal mogą generować dodatkowe błędy analizy dla dodatkowych wymagań elementu, które są efektami ubocznymi tego elementu, który nie jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="792cf-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="792cf-119">Na przykład model zawartości określonego elementu może wymagać dokładnie jednego elementu podrzędnego, ale jeśli określony element podrzędny znajduje się w `mc:Ignorable` prefiksie, a określony element podrzędny nie został rozpoznany jako typ, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor może Zgłoś błąd.</span><span class="sxs-lookup"><span data-stu-id="792cf-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="792cf-120">`mc:Ignorable`stosuje się tylko do mapowań przestrzeni nazw do ciągów identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="792cf-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="792cf-121">`mc:Ignorable`nie dotyczy mapowań przestrzeni nazw do zestawów, które określają przestrzeń nazw CLR i zestaw (lub domyślny bieżący plik wykonywalny jako zestaw).</span><span class="sxs-lookup"><span data-stu-id="792cf-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a CLR namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="792cf-122">W przypadku wdrażania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora implementacja procesora nie może podnieść lub przetwarzać błędów podczas rozpoznawania typów dla każdego elementu lub atrybutu, który jest kwalifikowany przez prefiks identyfikowany jako `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="792cf-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="792cf-123">Ale implementacja procesora może nadal zgłaszać wyjątki, które są pomocniczym wynikiem elementu, którego nie można załadować lub przetworzyć, np. przykładem elementu z pojedynczym elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="792cf-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="792cf-124">Domyślnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor zignoruje zawartość w ignorowanym elemencie.</span><span class="sxs-lookup"><span data-stu-id="792cf-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="792cf-125">Można jednak określić dodatkowy atrybut, [MC: ProcessContent Attribute](mc-processcontent-attribute.md), aby wymagać ciągłego przetwarzania zawartości w zignorowanym elemencie przez następny dostępny element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="792cf-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="792cf-126">W atrybucie można określić wiele prefiksów, używając co najmniej jednego znaku odstępu jako separatora, na przykład: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="792cf-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="792cf-127">`http://schemas.openxmlformats.org/markup-compatibility/2006` Przestrzeń nazw definiuje inne elementy i atrybuty, które nie są udokumentowane w tym obszarze zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="792cf-127">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="792cf-128">Aby uzyskać więcej informacji, zobacz [Specyfikacja zgodności znaczników XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="792cf-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792cf-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="792cf-129">See also</span></span>

- <xref:System.Windows.Markup.XamlReader>
- [<span data-ttu-id="792cf-130">PresentationOptions:Freeze, atrybut</span><span class="sxs-lookup"><span data-stu-id="792cf-130">PresentationOptions:Freeze Attribute</span></span>](presentationoptions-freeze-attribute.md)
- [<span data-ttu-id="792cf-131">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="792cf-131">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="792cf-132">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="792cf-132">Documents in WPF</span></span>](documents-in-wpf.md)
