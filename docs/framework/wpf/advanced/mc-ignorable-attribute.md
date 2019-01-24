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
ms.openlocfilehash: 25f5fb254ec6f952d7cafa2cb893e35daa0e9029
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573939"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="25a0e-102">mc:Ignorable — Atrybut</span><span class="sxs-lookup"><span data-stu-id="25a0e-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="25a0e-103">Określa, która [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] prefiksy przestrzeni nazw w pliku znaczników mogą być ignorowane przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora.</span><span class="sxs-lookup"><span data-stu-id="25a0e-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="25a0e-104">`mc:Ignorable` Atrybut obsługuje zgodność znaczników, zarówno dla mapowania niestandardowej przestrzeni nazw i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="25a0e-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="25a0e-105">Użycie atrybutu XAML (prefiks jednego)</span><span class="sxs-lookup"><span data-stu-id="25a0e-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="25a0e-106">Użycie atrybutu XAML (dwóch prefiksy)</span><span class="sxs-lookup"><span data-stu-id="25a0e-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="25a0e-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="25a0e-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25a0e-108">*ignorablePrefix ignorablePrefix1, itp.*</span><span class="sxs-lookup"><span data-stu-id="25a0e-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="25a0e-109">Dowolny ciąg prawidłowy prefiks, na Specyfikacja XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="25a0e-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="25a0e-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="25a0e-110">*ignorableUri*</span></span>|<span data-ttu-id="25a0e-111">Wszelkie prawidłowy identyfikator URI do wyznaczania obszaru nazw, na Specyfikacja XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="25a0e-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="25a0e-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="25a0e-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="25a0e-113">Element, który może być ignorowane przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementacji procesora, jeśli nie można rozpoznać typu bazowego.</span><span class="sxs-lookup"><span data-stu-id="25a0e-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25a0e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25a0e-114">Remarks</span></span>  
 <span data-ttu-id="25a0e-115">`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Prefiks przestrzeni nazw jest do Konwencja prefiks zalecane do użycia podczas mapowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przestrzeni nazw zgodności [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25a0e-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="25a0e-116">Elementy lub atrybuty, których część prefiks nazwy elementu są identyfikowane jako `mc:Ignorable` nie będą powodowały błędy podczas przetwarzania przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora.</span><span class="sxs-lookup"><span data-stu-id="25a0e-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="25a0e-117">Jeśli ten atrybut nie można rozpoznać typu podstawowego lub konstrukcji programowania, ten element jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="25a0e-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="25a0e-118">Należy jednak pamiętać, że zignorowane elementy nadal może generować dodatkowe błędy analizy dla wymagania dotyczące dodatkowych elementów, które są efekty uboczne tego elementu nie są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="25a0e-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="25a0e-119">Na przykład konkretnego elementu modelu zawartości mogą wymagać dokładnie jeden element podrzędny, ale jeśli element podrzędny określonego była w `mc:Ignorable` prefiksu i element podrzędny określonego nie można rozpoznać do typu, a następnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora może Zgłoś błąd.</span><span class="sxs-lookup"><span data-stu-id="25a0e-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="25a0e-120">`mc:Ignorable` ma zastosowanie tylko do mapowania przestrzeni nazw na ciągi znaków identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="25a0e-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="25a0e-121">`mc:Ignorable` nie ma zastosowania do mapowania przestrzeni nazw do zestawów, które określają [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeni nazw i zestawu (lub domyślne do bieżącego pliku wykonywalnego jako zestawu).</span><span class="sxs-lookup"><span data-stu-id="25a0e-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="25a0e-122">W przypadku wdrażania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, implementacji procesora nie trzeba zwiększyć, analizowania lub przetwarzania błędów na rozpoznawanie typu do celów dowolny element lub atrybut, który jest kwalifikowana za prefiks, który jest identyfikowany jako `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="25a0e-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="25a0e-123">Ale implementacji procesora nadal może zgłaszać wyjątki, które są wynikiem dodatkowej elementu nie można załadować lub być przetworzone, takich jak w przykładzie element podrzędny jednego z podanych wcześniej.</span><span class="sxs-lookup"><span data-stu-id="25a0e-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="25a0e-124">Domyślnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora zignoruje zawartości w obrębie elementu zignorowane.</span><span class="sxs-lookup"><span data-stu-id="25a0e-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="25a0e-125">Można jednak określić atrybut dodatkowe [MC: processcontent — atrybut](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), jest wymagane dalsze przetwarzanie zawartości w obrębie elementu ignorowane przez następnego elementu nadrzędnego dostępne.</span><span class="sxs-lookup"><span data-stu-id="25a0e-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="25a0e-126">W atrybucie, przy użyciu co najmniej jeden znak spacji jako separator, na przykład można określić wiele prefiksów: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="25a0e-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="25a0e-127">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Nazw definiuje innych elementów i atrybutów, które nie zostały zamieszczone w tym obszarze [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25a0e-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="25a0e-128">Aby uzyskać więcej informacji, zobacz [specyfikacji zgodności znaczników XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="25a0e-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a0e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25a0e-129">See also</span></span>
- <xref:System.Windows.Markup.XamlReader>
- [<span data-ttu-id="25a0e-130">PresentationOptions:Freeze, atrybut</span><span class="sxs-lookup"><span data-stu-id="25a0e-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
- [<span data-ttu-id="25a0e-131">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="25a0e-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="25a0e-132">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="25a0e-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
