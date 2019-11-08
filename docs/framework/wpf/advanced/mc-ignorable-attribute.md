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
ms.openlocfilehash: e14ab0ebc7d44e2792307b16c7c0581ff7a71bc6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740825"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="17c10-102">mc:Ignorable — Atrybut</span><span class="sxs-lookup"><span data-stu-id="17c10-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="17c10-103">Określa, które prefiksy przestrzeni nazw XML, które można napotkać w pliku znaczników, mogą zostać zignorowane przez procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="17c10-103">Specifies which XML namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="17c10-104">Atrybut `mc:Ignorable` obsługuje zgodność znaczników zarówno dla niestandardowego mapowania przestrzeni nazw, jak i dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wersji.</span><span class="sxs-lookup"><span data-stu-id="17c10-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="17c10-105">Użycie atrybutu języka XAML (pojedynczy prefiks)</span><span class="sxs-lookup"><span data-stu-id="17c10-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="17c10-106">Użycie atrybutu języka XAML (dwa prefiksy)</span><span class="sxs-lookup"><span data-stu-id="17c10-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="17c10-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="17c10-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17c10-108">*ignorablePrefix, ignorablePrefix1 itd.*</span><span class="sxs-lookup"><span data-stu-id="17c10-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="17c10-109">Dowolny prawidłowy ciąg prefiksu na specyfikację XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="17c10-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="17c10-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="17c10-110">*ignorableUri*</span></span>|<span data-ttu-id="17c10-111">Dowolny prawidłowy identyfikator URI służący do wyznaczania przestrzeni nazw, zgodnie ze specyfikacją XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="17c10-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="17c10-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="17c10-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="17c10-113">Element, który może być ignorowany przez implementacje procesora [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], jeśli nie można rozpoznać typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="17c10-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17c10-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17c10-114">Remarks</span></span>  
 <span data-ttu-id="17c10-115">Prefiks przestrzeni nazw XML `mc` jest zalecaną konwencją prefiksu do użycia podczas mapowania przestrzeni nazw zgodności [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `http://schemas.openxmlformats.org/markup-compatibility/2006`.</span><span class="sxs-lookup"><span data-stu-id="17c10-115">The `mc` XML namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace `http://schemas.openxmlformats.org/markup-compatibility/2006`.</span></span>  
  
 <span data-ttu-id="17c10-116">Elementy lub atrybuty, w których części prefiksu nazwy elementu są identyfikowane jako `mc:Ignorable` nie będą powodować błędów podczas przetwarzania przez procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="17c10-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="17c10-117">Jeśli ten atrybut nie może zostać rozpoznany jako typ podstawowy lub konstrukcja programistyczna, ten element jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="17c10-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="17c10-118">Należy jednak zauważyć, że zignorowane elementy nadal mogą generować dodatkowe błędy analizy dla dodatkowych wymagań elementu, które są efektami ubocznymi tego elementu, który nie jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="17c10-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="17c10-119">Na przykład model zawartości określonego elementu może wymagać dokładnie jednego elementu podrzędnego, ale jeśli określony element podrzędny znajdował się w prefiksie `mc:Ignorable`, a określony element podrzędny nie mógł zostać rozpoznany jako typ, wówczas procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] może zgłosić błąd.</span><span class="sxs-lookup"><span data-stu-id="17c10-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="17c10-120">`mc:Ignorable` stosuje się tylko do mapowań przestrzeni nazw do ciągów identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="17c10-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="17c10-121">`mc:Ignorable` nie ma zastosowania do mapowań przestrzeni nazw na zestawy, które określają przestrzeń nazw CLR i zestaw (lub domyślny bieżący plik wykonywalny jako zestaw).</span><span class="sxs-lookup"><span data-stu-id="17c10-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a CLR namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="17c10-122">W przypadku wdrażania procesora [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacja procesora nie może podnieść lub przetwarzać błędów podczas rozpoznawania typów dla każdego elementu lub atrybutu, który jest kwalifikowany przez prefiks identyfikowany jako `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="17c10-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="17c10-123">Ale implementacja procesora może nadal zgłaszać wyjątki, które są pomocniczym wynikiem elementu, którego nie można załadować lub przetworzyć, np. przykładem elementu z pojedynczym elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="17c10-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="17c10-124">Domyślnie procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zignoruje zawartość w ignorowanym elemencie.</span><span class="sxs-lookup"><span data-stu-id="17c10-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="17c10-125">Można jednak określić dodatkowy atrybut, [MC: ProcessContent Attribute](mc-processcontent-attribute.md), aby wymagać ciągłego przetwarzania zawartości w zignorowanym elemencie przez następny dostępny element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="17c10-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="17c10-126">W atrybucie można określić wiele prefiksów, używając co najmniej jednego znaku odstępu jako separatora, na przykład: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="17c10-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="17c10-127">Przestrzeń nazw `http://schemas.openxmlformats.org/markup-compatibility/2006` definiuje inne elementy i atrybuty, które nie są udokumentowane w tym obszarze zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="17c10-127">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="17c10-128">Aby uzyskać więcej informacji, zobacz [Specyfikacja zgodności znaczników XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="17c10-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17c10-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17c10-129">See also</span></span>

- <xref:System.Windows.Markup.XamlReader>
- [<span data-ttu-id="17c10-130">PresentationOptions:Freeze, atrybut</span><span class="sxs-lookup"><span data-stu-id="17c10-130">PresentationOptions:Freeze Attribute</span></span>](presentationoptions-freeze-attribute.md)
- [<span data-ttu-id="17c10-131">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="17c10-131">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="17c10-132">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="17c10-132">Documents in WPF</span></span>](documents-in-wpf.md)
