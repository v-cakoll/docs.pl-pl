---
title: Style i szablony wbudowane
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b88ef444283f4e1e85009c59b39f3cc41965d300
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460006"
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="d9498-102">Style i szablony wbudowane</span><span class="sxs-lookup"><span data-stu-id="d9498-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="d9498-103">zapewnia <xref:System.Windows.Style> obiektów i obiektów szablonów (<xref:System.Windows.FrameworkTemplate> podklas) jako sposób definiowania wyglądu elementu w zasobach, dzięki czemu mogą być używane wiele razy.</span><span class="sxs-lookup"><span data-stu-id="d9498-103">provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="d9498-104">Z tego powodu atrybuty w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], które pobierają typy <xref:System.Windows.Style> i <xref:System.Windows.FrameworkTemplate> niemal zawsze tworzą odwołania do zasobów do istniejących stylów i szablonów zamiast definiować nowe.</span><span class="sxs-lookup"><span data-stu-id="d9498-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="d9498-105">Ograniczenia stylów i szablonów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="d9498-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="d9498-106">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]właściwości stylu i szablonu można ustawić w jeden z dwóch sposobów.</span><span class="sxs-lookup"><span data-stu-id="d9498-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="d9498-107">Można użyć składni atrybutu, aby odwołać się do stylu, który został zdefiniowany w ramach zasobu, na przykład `<`*obiektu* *`Style="{StaticResource``}" .../>`* .</span><span class="sxs-lookup"><span data-stu-id="d9498-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="d9498-108">Lub można użyć składni elementu właściwości, aby zdefiniować styl wbudowany, na przykład:</span><span class="sxs-lookup"><span data-stu-id="d9498-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="d9498-109">`>` `<` *obiektu*</span><span class="sxs-lookup"><span data-stu-id="d9498-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="d9498-110">`.Style>` `<` *obiektu*</span><span class="sxs-lookup"><span data-stu-id="d9498-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="d9498-111">`<` `Style``.../>`</span><span class="sxs-lookup"><span data-stu-id="d9498-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="d9498-112">`.Style>` `</` *obiektu*</span><span class="sxs-lookup"><span data-stu-id="d9498-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="d9498-113">`>` `</` *obiektu*</span><span class="sxs-lookup"><span data-stu-id="d9498-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="d9498-114">Użycie atrybutu jest znacznie bardziej powszechne.</span><span class="sxs-lookup"><span data-stu-id="d9498-114">The attribute usage is much more common.</span></span> <span data-ttu-id="d9498-115">Styl, który jest zdefiniowany w tekście i nie jest zdefiniowany w zasobach, jest koniecznie objęty zakresem zawierającym tylko element i nie można go ponownie użyć, ponieważ nie ma klucza zasobu.</span><span class="sxs-lookup"><span data-stu-id="d9498-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="d9498-116">Ogólnie rzecz biorąc, styl zdefiniowany przez zasób jest bardziej uniwersalny i przydatny, co jest bardziej pomocne z ogólnym modelem programowania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zasadą oddzielania logiki programu w kodzie od projektowania w znaczniku.</span><span class="sxs-lookup"><span data-stu-id="d9498-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="d9498-117">Zwykle nie istnieje powód, aby ustawić styl lub szablon w tekście, nawet jeśli zamierzasz użyć tego stylu lub szablonu w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d9498-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="d9498-118">Większość elementów, które mogą przyjmować styl lub szablon, obsługują również właściwość content i model zawartości.</span><span class="sxs-lookup"><span data-stu-id="d9498-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="d9498-119">Jeśli używasz tylko dowolnego drzewa logicznego, które tworzysz za pośrednictwem stylu lub tworzenia szablonów raz, łatwiej jest wypełniać tę właściwość zawartości z odpowiednikami elementów podrzędnych w znacznikach bezpośrednich.</span><span class="sxs-lookup"><span data-stu-id="d9498-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="d9498-120">Dzięki temu wszystkie mechanizmy stylu i szablonu zostaną całkowicie pominięte.</span><span class="sxs-lookup"><span data-stu-id="d9498-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="d9498-121">Inne składnie włączane przez rozszerzenia znaczników, które zwracają obiekt, są również dostępne dla stylów i szablonów.</span><span class="sxs-lookup"><span data-stu-id="d9498-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="d9498-122">Dwa takie rozszerzenia, które mają możliwe scenariusze, obejmują [szablonbinding](templatebinding-markup-extension.md) i <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="d9498-122">Two such extensions that have possible scenarios include [TemplateBinding](templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9498-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9498-123">See also</span></span>

- [<span data-ttu-id="d9498-124">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="d9498-124">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
