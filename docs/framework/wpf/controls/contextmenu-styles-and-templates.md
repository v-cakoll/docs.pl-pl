---
title: ContextMenu — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: 671fb0a4f178c9e16149f6d47945670ea0e64d48
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="c4685-102">ContextMenu — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="c4685-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="c4685-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.ContextMenu> formantu.</span><span class="sxs-lookup"><span data-stu-id="c4685-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="c4685-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="c4685-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c4685-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c4685-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="c4685-106">Części ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c4685-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="c4685-107"><xref:System.Windows.Controls.ContextMenu> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="c4685-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="c4685-108">Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ContextMenu>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="c4685-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="c4685-109">( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element <xref:System.Windows.Controls.ContextMenu>; <xref:System.Windows.Controls.ScrollViewer> włącza przewijanie w kontrolce).</span><span class="sxs-lookup"><span data-stu-id="c4685-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="c4685-110">Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym elementu <xref:System.Windows.Controls.ScrollViewer>, musisz podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="c4685-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="c4685-111">Stany ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c4685-111">ContextMenu States</span></span>  
 <span data-ttu-id="c4685-112">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.ContextMenu> formantu.</span><span class="sxs-lookup"><span data-stu-id="c4685-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="c4685-113">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="c4685-113">VisualState Name</span></span>|<span data-ttu-id="c4685-114">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c4685-114">VisualStateGroup Name</span></span>|<span data-ttu-id="c4685-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c4685-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c4685-116">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="c4685-116">Valid</span></span>|<span data-ttu-id="c4685-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4685-117">ValidationStates</span></span>|<span data-ttu-id="c4685-118">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="c4685-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c4685-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c4685-119">InvalidFocused</span></span>|<span data-ttu-id="c4685-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4685-120">ValidationStates</span></span>|<span data-ttu-id="c4685-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="c4685-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c4685-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c4685-122">InvalidUnfocused</span></span>|<span data-ttu-id="c4685-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4685-123">ValidationStates</span></span>|<span data-ttu-id="c4685-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="c4685-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="c4685-125">Przykład ControlTemplate ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c4685-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="c4685-126">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ContextMenu> formantu.</span><span class="sxs-lookup"><span data-stu-id="c4685-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="c4685-127"><xref:System.Windows.Controls.ControlTemplate> Używa następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="c4685-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c4685-128">Pełny przykład, zobacz [style próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="c4685-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4685-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4685-129">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c4685-130">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="c4685-130">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c4685-131">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="c4685-131">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c4685-132">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="c4685-132">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c4685-133">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c4685-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
