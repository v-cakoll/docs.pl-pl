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
ms.openlocfilehash: fa192e20ea84e96c9f85ff84e16c63b7f56c8a98
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283539"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="b8241-102">ContextMenu — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="b8241-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="b8241-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="b8241-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="b8241-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="b8241-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b8241-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="b8241-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="b8241-106">Składniki</span><span class="sxs-lookup"><span data-stu-id="b8241-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="b8241-107">Formant <xref:System.Windows.Controls.ContextMenu> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="b8241-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="b8241-108">Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ContextMenu>szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="b8241-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="b8241-109">(<xref:System.Windows.Controls.ItemsPresenter> wyświetla każdy element w <xref:System.Windows.Controls.ContextMenu>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).</span><span class="sxs-lookup"><span data-stu-id="b8241-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="b8241-110">Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer>, należy nadać <xref:System.Windows.Controls.ItemsPresenter> nazwę `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="b8241-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="b8241-111">Stany</span><span class="sxs-lookup"><span data-stu-id="b8241-111">ContextMenu States</span></span>  
 <span data-ttu-id="b8241-112">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="b8241-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="b8241-113">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="b8241-113">VisualState Name</span></span>|<span data-ttu-id="b8241-114">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="b8241-114">VisualStateGroup Name</span></span>|<span data-ttu-id="b8241-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b8241-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b8241-116">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="b8241-116">Valid</span></span>|<span data-ttu-id="b8241-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b8241-117">ValidationStates</span></span>|<span data-ttu-id="b8241-118">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="b8241-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b8241-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b8241-119">InvalidFocused</span></span>|<span data-ttu-id="b8241-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b8241-120">ValidationStates</span></span>|<span data-ttu-id="b8241-121">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="b8241-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b8241-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b8241-122">InvalidUnfocused</span></span>|<span data-ttu-id="b8241-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b8241-123">ValidationStates</span></span>|<span data-ttu-id="b8241-124">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="b8241-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="b8241-125">Przykład ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="b8241-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="b8241-126">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="b8241-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="b8241-127"><xref:System.Windows.Controls.ControlTemplate> używa następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="b8241-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b8241-128">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="b8241-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8241-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8241-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b8241-130">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="b8241-130">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b8241-131">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="b8241-131">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b8241-132">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="b8241-132">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="b8241-133">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="b8241-133">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
