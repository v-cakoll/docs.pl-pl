---
title: mc:ProcessContent — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: e625d99cdb30368a798b4829d103f8f26b2c9274
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991856"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="e06e7-102">mc:ProcessContent — Atrybut</span><span class="sxs-lookup"><span data-stu-id="e06e7-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="e06e7-103">Określa, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] które elementy powinny nadal mieć zawartość przetworzoną przez odpowiednie elementy nadrzędne, nawet jeśli bezpośredni element nadrzędny może być [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorowany przez procesor z powodu określenia [atrybutu MC:](mc-ignorable-attribute.md)Ignore.</span><span class="sxs-lookup"><span data-stu-id="e06e7-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](mc-ignorable-attribute.md).</span></span> <span data-ttu-id="e06e7-104">Ten `mc:ProcessContent` atrybut obsługuje zgodność znaczników zarówno dla niestandardowego mapowania przestrzeni nazw, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jak i do przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="e06e7-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e06e7-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="e06e7-105">XAML Attribute Usage</span></span>  
  
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
  
## <a name="xaml-values"></a><span data-ttu-id="e06e7-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="e06e7-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e06e7-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="e06e7-107">*ignorablePrefix*</span></span>|<span data-ttu-id="e06e7-108">Dowolny prawidłowy ciąg prefiksu na specyfikację XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="e06e7-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="e06e7-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="e06e7-109">*ignorableUri*</span></span>|<span data-ttu-id="e06e7-110">Dowolny prawidłowy identyfikator URI służący do wyznaczania przestrzeni nazw, zgodnie ze specyfikacją XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="e06e7-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="e06e7-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="e06e7-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="e06e7-112">Element, który może być ignorowany [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przez implementacje procesora, jeśli nie można rozpoznać typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="e06e7-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="e06e7-113">*treści*</span><span class="sxs-lookup"><span data-stu-id="e06e7-113">*[content]*</span></span>|<span data-ttu-id="e06e7-114">*ThisElementCanBeIgnored* jest oznaczony jako ignorowany.</span><span class="sxs-lookup"><span data-stu-id="e06e7-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="e06e7-115">Jeśli procesor zignoruje ten element, *[zawartość]* jest przetwarzany przez *obiekt*.</span><span class="sxs-lookup"><span data-stu-id="e06e7-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e06e7-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e06e7-116">Remarks</span></span>  
 <span data-ttu-id="e06e7-117">Domyślnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor zignoruje zawartość w ignorowanym elemencie.</span><span class="sxs-lookup"><span data-stu-id="e06e7-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="e06e7-118">Można określić konkretny element przez `mc:ProcessContent`, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a procesor będzie kontynuował przetwarzanie zawartości w zignorowanym elemencie.</span><span class="sxs-lookup"><span data-stu-id="e06e7-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="e06e7-119">Zwykle jest to używane, jeśli zawartość jest zagnieżdżona w kilku tagach, co najmniej jeden z nich jest ignorowany i co najmniej jeden z nich nie jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="e06e7-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="e06e7-120">W atrybucie można określić wiele prefiksów, używając separatora spacji, na przykład: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="e06e7-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="e06e7-121">`http://schemas.openxmlformats.org/markup-compatibility/2006` Przestrzeń nazw definiuje inne elementy i atrybuty, które nie są udokumentowane w tym obszarze zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="e06e7-121">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="e06e7-122">Aby uzyskać więcej informacji, zobacz [Specyfikacja zgodności znaczników XML](https://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="e06e7-122">For more information, see [XML Markup Compatibility Specification](https://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06e7-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e06e7-123">See also</span></span>

- [<span data-ttu-id="e06e7-124">mc:Ignorable, atrybut</span><span class="sxs-lookup"><span data-stu-id="e06e7-124">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
- [<span data-ttu-id="e06e7-125">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="e06e7-125">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
