---
title: Style i szablony wbudowane
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b566e157e2d4a9e9be21a678541bf5d5341a898c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091437"
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="71d3b-102">Style i szablony wbudowane</span><span class="sxs-lookup"><span data-stu-id="71d3b-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="71d3b-103">udostępnia <xref:System.Windows.Style> obiekty i szablonu (<xref:System.Windows.FrameworkTemplate> podklasy) jako sposób zdefiniować wygląd elementu w zasobach, dzięki czemu będzie można ich użyć wiele razy.</span><span class="sxs-lookup"><span data-stu-id="71d3b-103">provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="71d3b-104">Z tego powodu atrybutów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] typy, które wymagają <xref:System.Windows.Style> i <xref:System.Windows.FrameworkTemplate> prawie zawsze zasobów odwołuje się do istniejącego — style i szablony, a nie zdefiniować nowe wbudowane.</span><span class="sxs-lookup"><span data-stu-id="71d3b-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="71d3b-105">Ograniczenia style i Szablony wbudowane</span><span class="sxs-lookup"><span data-stu-id="71d3b-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="71d3b-106">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], z technicznego punktu widzenia można ustawić właściwości stylów i szablonów w jeden z dwóch sposobów.</span><span class="sxs-lookup"><span data-stu-id="71d3b-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="71d3b-107">Można użyć składni atrybutów stylu, który został zdefiniowany w ramach zasobu, na przykład odwołanie do `<` *obiektu*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span><span class="sxs-lookup"><span data-stu-id="71d3b-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="71d3b-108">Lub składnia elementu właściwości umożliwia definiowanie w tekście stylu, na przykład:</span><span class="sxs-lookup"><span data-stu-id="71d3b-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="71d3b-109">`<` *obiekt* `>`</span><span class="sxs-lookup"><span data-stu-id="71d3b-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="71d3b-110">`<` *obiekt* `.Style>`</span><span class="sxs-lookup"><span data-stu-id="71d3b-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="71d3b-111">`<` `Style`  `.../>`</span><span class="sxs-lookup"><span data-stu-id="71d3b-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="71d3b-112">`</` *obiekt* `.Style>`</span><span class="sxs-lookup"><span data-stu-id="71d3b-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="71d3b-113">`</` *obiekt* `>`</span><span class="sxs-lookup"><span data-stu-id="71d3b-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="71d3b-114">Użycie atrybutu jest znacznie bardziej powszechne.</span><span class="sxs-lookup"><span data-stu-id="71d3b-114">The attribute usage is much more common.</span></span> <span data-ttu-id="71d3b-115">Styl, który zdefiniowano w tekście i nie zdefiniowano w zasoby zawsze obejmuje tylko element zawierający i nie można ponownie użyć równie łatwo, ponieważ nie ma on zasobów klucza.</span><span class="sxs-lookup"><span data-stu-id="71d3b-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="71d3b-116">Ogólnie rzecz biorąc zdefiniowany zasób stylu jest bardziej wszechstronna i przydatne i jest bardziej zgodne ogólne [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oddzielenie logiki programu w kodzie, od projektowania w znacznikach zasady modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="71d3b-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="71d3b-117">Zwykle nie ma powodu do wbudowanej stylu lub szablonu, nawet jeśli zamierzasz używać stylu lub szablonu w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="71d3b-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="71d3b-118">Większość elementów, które mogą przejąć stylu lub szablonu obsługują również właściwość zawartości oraz model zawartości.</span><span class="sxs-lookup"><span data-stu-id="71d3b-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="71d3b-119">Jeśli używane są tylko niezależnie od drzewo logiczne Utwórz za pomocą stylów i szablonów raz, byłoby jeszcze łatwiej Wypełnij tę właściwość zawartości z elementami podrzędnymi równoważne, w znacznikach bezpośrednie.</span><span class="sxs-lookup"><span data-stu-id="71d3b-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="71d3b-120">Spowoduje to całkowicie pominąć mechanizmy stylów i szablonów.</span><span class="sxs-lookup"><span data-stu-id="71d3b-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="71d3b-121">Możliwe, style i szablony są również innych składni włączane przez rozszerzenia znaczników, które zwracają obiekt.</span><span class="sxs-lookup"><span data-stu-id="71d3b-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="71d3b-122">Dwa rozszerzenia, które mają możliwe scenariusze obejmują [TemplateBinding](templatebinding-markup-extension.md) i <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="71d3b-122">Two such extensions that have possible scenarios include [TemplateBinding](templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d3b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71d3b-123">See also</span></span>

- [<span data-ttu-id="71d3b-124">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="71d3b-124">Styling and Templating</span></span>](../controls/styling-and-templating.md)
