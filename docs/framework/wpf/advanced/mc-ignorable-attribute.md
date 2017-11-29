---
title: "mc:Ignorable — Atrybut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3be5949ee26fbb21d913a7aefe2664202c5bef38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="dd524-102">mc:Ignorable — Atrybut</span><span class="sxs-lookup"><span data-stu-id="dd524-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="dd524-103">Określa, która [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] prefiksy przestrzeni nazw w pliku znaczników, może być ignorowane przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora.</span><span class="sxs-lookup"><span data-stu-id="dd524-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="dd524-104">`mc:Ignorable` Atrybut obsługuje zgodności znaczników, zarówno w przypadku mapowania niestandardowej przestrzeni nazw, jak i dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="dd524-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="dd524-105">Użycie atrybutu XAML (jeden przedrostek)</span><span class="sxs-lookup"><span data-stu-id="dd524-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="dd524-106">Użycie atrybutu XAML (dwie prefiksy)</span><span class="sxs-lookup"><span data-stu-id="dd524-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="dd524-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="dd524-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd524-108">*ignorablePrefix ignorablePrefix1, itp.*</span><span class="sxs-lookup"><span data-stu-id="dd524-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="dd524-109">Dowolny ciąg prawidłowy prefiks, na Specyfikacja XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="dd524-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="dd524-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="dd524-110">*ignorableUri*</span></span>|<span data-ttu-id="dd524-111">Wszelkie prawidłowy identyfikator URI przestrzeni nazw na Specyfikacja XML 1.0 wyznaczania.</span><span class="sxs-lookup"><span data-stu-id="dd524-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="dd524-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="dd524-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="dd524-113">Element, który może być ignorowane przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementacji procesora, jeśli nie można rozpoznać typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="dd524-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd524-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd524-114">Remarks</span></span>  
 <span data-ttu-id="dd524-115">`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Prefiks przestrzeni nazw jest Konwencji prefiks zalecaną do użycia podczas mapowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nazw zgodności [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd524-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="dd524-116">Elementów lub atrybutów, których część prefiks nazwy elementu są identyfikowane jako `mc:Ignorable` nie generuje błędy podczas przetwarzania przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora.</span><span class="sxs-lookup"><span data-stu-id="dd524-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="dd524-117">Jeśli tego atrybutu nie można rozpoznać typu podstawowego lub konstrukcji programującej, że element zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="dd524-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="dd524-118">Należy jednak pamiętać, że zignorowane elementy nadal może generować dodatkowe błędy analizy, dodatkowy element wymagania, które są efekty uboczne tego elementu nie są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="dd524-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="dd524-119">Na przykład dany element modelu zawartości mogą wymagać dokładnie jeden element podrzędny, ale jeśli był element podrzędny określonego `mc:Ignorable` prefiks i element podrzędny określonego nie można rozpoznać typu, a następnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora może Zgłoś błąd.</span><span class="sxs-lookup"><span data-stu-id="dd524-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="dd524-120">`mc:Ignorable`dotyczy tylko mapowania przestrzeni nazw na ciągi identyfikator.</span><span class="sxs-lookup"><span data-stu-id="dd524-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="dd524-121">`mc:Ignorable`nie ma zastosowania do mapowania przestrzeni nazw w zestawy, które określają [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeni nazw i zestawu (lub domyślne do bieżącego pliku wykonywalnego jako zestawu).</span><span class="sxs-lookup"><span data-stu-id="dd524-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="dd524-122">W przypadku wdrażania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, implementacji procesor nie musi wygenerować, analizy lub przetwarzania błędów rozpoznawania typu element lub atrybut, który jest kwalifikowana przez prefiks, który jest identyfikowany jako `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="dd524-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="dd524-123">Ale implementacji procesora nadal może zgłaszać wyjątki, które są wynikiem dodatkowej elementu nie powiodło się załadowanie lub być przetwarzane, takich jak na przykład element podrzędny co podane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="dd524-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="dd524-124">Domyślnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora zignoruje zawartość elementu została zignorowana.</span><span class="sxs-lookup"><span data-stu-id="dd524-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="dd524-125">Można jednak określić atrybut dodatkowe [mc:ProcessContent atrybutu](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), jest wymagane dalsze przetwarzanie zawartości w obrębie elementu zignorowane przez następnego elementu nadrzędnego dostępne.</span><span class="sxs-lookup"><span data-stu-id="dd524-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="dd524-126">Można określić wiele prefiksów w atrybucie przy użyciu co najmniej jeden znak odstępu jako separator, na przykład: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="dd524-126">Multiple prefixes can be specified in the attribute, using one or more whitespace characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  
  
 <span data-ttu-id="dd524-127">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Definiuje przestrzeń nazw innych elementów i atrybutów, które nie są opisane w tym obszarze [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd524-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="dd524-128">Aby uzyskać więcej informacji, zobacz [specyfikacji zgodności znaczników XML](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="dd524-128">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd524-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd524-129">See Also</span></span>  
 <xref:System.Windows.Markup.XamlReader>  
 [<span data-ttu-id="dd524-130">Atrybut PresentationOptions:Freeze</span><span class="sxs-lookup"><span data-stu-id="dd524-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [<span data-ttu-id="dd524-131">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="dd524-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="dd524-132">Dokumentów na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="dd524-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
