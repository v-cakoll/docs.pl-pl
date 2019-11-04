---
title: mc:ProcessContent — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: dde304cc2b9db9cb01f9264ca1359b8979512cfa
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458778"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="c6453-102">mc:ProcessContent — Atrybut</span><span class="sxs-lookup"><span data-stu-id="c6453-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="c6453-103">Określa, które elementy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinny nadal mieć zawartość przetworzoną przez odpowiednie elementy nadrzędne, nawet jeśli bezpośredni element nadrzędny może zostać zignorowany przez procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] z powodu określenia [atrybutu MC:](mc-ignorable-attribute.md)Ignore.</span><span class="sxs-lookup"><span data-stu-id="c6453-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](mc-ignorable-attribute.md).</span></span> <span data-ttu-id="c6453-104">Atrybut `mc:ProcessContent` obsługuje zgodność znaczników zarówno dla niestandardowego mapowania przestrzeni nazw, jak i dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wersji.</span><span class="sxs-lookup"><span data-stu-id="c6453-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c6453-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c6453-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c6453-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="c6453-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6453-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="c6453-107">*ignorablePrefix*</span></span>|<span data-ttu-id="c6453-108">Dowolny prawidłowy ciąg prefiksu na specyfikację XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="c6453-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="c6453-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="c6453-109">*ignorableUri*</span></span>|<span data-ttu-id="c6453-110">Dowolny prawidłowy identyfikator URI służący do wyznaczania przestrzeni nazw, zgodnie ze specyfikacją XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="c6453-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="c6453-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="c6453-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="c6453-112">Element, który może być ignorowany przez implementacje procesora [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], jeśli nie można rozpoznać typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="c6453-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="c6453-113">*treści*</span><span class="sxs-lookup"><span data-stu-id="c6453-113">*[content]*</span></span>|<span data-ttu-id="c6453-114">*ThisElementCanBeIgnored* jest oznaczony jako ignorowany.</span><span class="sxs-lookup"><span data-stu-id="c6453-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="c6453-115">Jeśli procesor zignoruje ten element, *[zawartość]* jest przetwarzany przez *obiekt*.</span><span class="sxs-lookup"><span data-stu-id="c6453-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6453-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6453-116">Remarks</span></span>  
 <span data-ttu-id="c6453-117">Domyślnie procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zignoruje zawartość w ignorowanym elemencie.</span><span class="sxs-lookup"><span data-stu-id="c6453-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="c6453-118">Można określić konkretny element według `mc:ProcessContent`, a procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] będzie kontynuował przetwarzanie zawartości w ignorowanym elemencie.</span><span class="sxs-lookup"><span data-stu-id="c6453-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="c6453-119">Zwykle jest to używane, jeśli zawartość jest zagnieżdżona w kilku tagach, co najmniej jeden z nich jest ignorowany i co najmniej jeden z nich nie jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="c6453-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="c6453-120">W atrybucie można określić wiele prefiksów, używając separatora spacji, na przykład: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="c6453-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="c6453-121">Przestrzeń nazw `http://schemas.openxmlformats.org/markup-compatibility/2006` definiuje inne elementy i atrybuty, które nie są udokumentowane w tym obszarze zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="c6453-121">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="c6453-122">Aby uzyskać więcej informacji, zobacz [Specyfikacja zgodności znaczników XML](https://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="c6453-122">For more information, see [XML Markup Compatibility Specification](https://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6453-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6453-123">See also</span></span>

- [<span data-ttu-id="c6453-124">mc:Ignorable, atrybut</span><span class="sxs-lookup"><span data-stu-id="c6453-124">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
- [<span data-ttu-id="c6453-125">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c6453-125">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
