---
title: mc:ProcessContent — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 2e93734b8ab4aefca080736db3a512f272625271
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545256"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="87fc9-102">mc:ProcessContent — Atrybut</span><span class="sxs-lookup"><span data-stu-id="87fc9-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="87fc9-103">Określa, która [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy nadal powinien mieć zawartość przetworzone przez elementy nadrzędne istotne, nawet wtedy, gdy element nadrzędny natychmiastowego może być ignorowane przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora z powodu określania [mc: atrybut Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) .</span><span class="sxs-lookup"><span data-stu-id="87fc9-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span></span> <span data-ttu-id="87fc9-104">`mc:ProcessContent` Atrybut obsługuje zgodności znaczników, zarówno w przypadku mapowania niestandardowej przestrzeni nazw, jak i dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="87fc9-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="87fc9-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="87fc9-105">XAML Attribute Usage</span></span>  
  
```  
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
  
## <a name="xaml-values"></a><span data-ttu-id="87fc9-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="87fc9-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87fc9-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="87fc9-107">*ignorablePrefix*</span></span>|<span data-ttu-id="87fc9-108">Dowolny ciąg prawidłowy prefiks, na Specyfikacja XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="87fc9-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="87fc9-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="87fc9-109">*ignorableUri*</span></span>|<span data-ttu-id="87fc9-110">Wszelkie prawidłowy identyfikator URI przestrzeni nazw na Specyfikacja XML 1.0 wyznaczania.</span><span class="sxs-lookup"><span data-stu-id="87fc9-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="87fc9-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="87fc9-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="87fc9-112">Element, który może być ignorowane przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementacji procesora, jeśli nie można rozpoznać typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="87fc9-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="87fc9-113">*[zawartość]*</span><span class="sxs-lookup"><span data-stu-id="87fc9-113">*[content]*</span></span>|<span data-ttu-id="87fc9-114">*ThisElementCanBeIgnored* jest oznaczony do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="87fc9-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="87fc9-115">Jeśli procesor ignoruje tego elementu *[zawartości]* jest przetwarzany przez *obiektu*.</span><span class="sxs-lookup"><span data-stu-id="87fc9-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87fc9-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87fc9-116">Remarks</span></span>  
 <span data-ttu-id="87fc9-117">Domyślnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora zignoruje zawartość elementu została zignorowana.</span><span class="sxs-lookup"><span data-stu-id="87fc9-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="87fc9-118">Można określić elementu określonych przez `mc:ProcessContent`, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora będą w dalszym ciągu przetwarzania zawartości w elemencie została zignorowana.</span><span class="sxs-lookup"><span data-stu-id="87fc9-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="87fc9-119">To zazwyczaj będzie można użyć, jeśli zawartość jest zagnieżdżony w kilku tagów, co najmniej jeden z nich do pominięcia i co najmniej jeden z nich nie jest do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="87fc9-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="87fc9-120">Można określić wiele prefiksów w atrybucie, używając separatora miejsca, na przykład: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="87fc9-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="87fc9-121">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Definiuje przestrzeń nazw innych elementów i atrybutów, które nie są opisane w tym obszarze [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87fc9-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="87fc9-122">Aby uzyskać więcej informacji, zobacz [specyfikacji zgodności znaczników XML](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="87fc9-122">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fc9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87fc9-123">See Also</span></span>  
 [<span data-ttu-id="87fc9-124">mc:Ignorable, atrybut</span><span class="sxs-lookup"><span data-stu-id="87fc9-124">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [<span data-ttu-id="87fc9-125">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="87fc9-125">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
