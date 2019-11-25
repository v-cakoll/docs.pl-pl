---
title: ToolBar — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
ms.openlocfilehash: a984311234386cb205d5db35f18a743ca535ff05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283654"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="b859b-102">ToolBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="b859b-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="b859b-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="b859b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="b859b-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="b859b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b859b-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="b859b-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="b859b-106">Części paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="b859b-106">ToolBar Parts</span></span>  
 <span data-ttu-id="b859b-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="b859b-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="b859b-108">Części</span><span class="sxs-lookup"><span data-stu-id="b859b-108">Part</span></span>|<span data-ttu-id="b859b-109">Typ</span><span class="sxs-lookup"><span data-stu-id="b859b-109">Type</span></span>|<span data-ttu-id="b859b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b859b-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b859b-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="b859b-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="b859b-112">Obiekt, który zawiera kontrolki na <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="b859b-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="b859b-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="b859b-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="b859b-114">Obiekt, który zawiera kontrolki, które znajdują się w obszarze przepełnienia <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="b859b-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="b859b-115">Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ToolBar>szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="b859b-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="b859b-116">(<xref:System.Windows.Controls.ItemsPresenter> wyświetla każdy element w <xref:System.Windows.Controls.ToolBar>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).</span><span class="sxs-lookup"><span data-stu-id="b859b-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="b859b-117">Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer>, należy nadać <xref:System.Windows.Controls.ItemsPresenter> nazwę `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="b859b-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="b859b-118">Stany pasków narzędzi</span><span class="sxs-lookup"><span data-stu-id="b859b-118">ToolBar States</span></span>  
 <span data-ttu-id="b859b-119">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="b859b-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="b859b-120">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="b859b-120">VisualState Name</span></span>|<span data-ttu-id="b859b-121">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="b859b-121">VisualStateGroup Name</span></span>|<span data-ttu-id="b859b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b859b-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b859b-123">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="b859b-123">Valid</span></span>|<span data-ttu-id="b859b-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b859b-124">ValidationStates</span></span>|<span data-ttu-id="b859b-125">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="b859b-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b859b-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b859b-126">InvalidFocused</span></span>|<span data-ttu-id="b859b-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b859b-127">ValidationStates</span></span>|<span data-ttu-id="b859b-128">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="b859b-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b859b-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b859b-129">InvalidUnfocused</span></span>|<span data-ttu-id="b859b-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b859b-130">ValidationStates</span></span>|<span data-ttu-id="b859b-131">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="b859b-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="b859b-132">Przykład ControlTemplate na pasku narzędzi</span><span class="sxs-lookup"><span data-stu-id="b859b-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="b859b-133">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="b859b-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="b859b-134">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="b859b-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b859b-135">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="b859b-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b859b-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b859b-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b859b-137">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="b859b-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b859b-138">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="b859b-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b859b-139">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="b859b-139">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="b859b-140">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="b859b-140">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
