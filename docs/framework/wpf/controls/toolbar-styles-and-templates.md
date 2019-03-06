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
ms.openlocfilehash: 3e49683226f8c88a1d6bff678cc978c95a0d6864
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376913"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="38d25-102">ToolBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="38d25-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="38d25-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.ToolBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="38d25-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="38d25-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="38d25-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="38d25-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="38d25-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="38d25-106">Części paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="38d25-106">ToolBar Parts</span></span>  
 <span data-ttu-id="38d25-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.ToolBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="38d25-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="38d25-108">Część</span><span class="sxs-lookup"><span data-stu-id="38d25-108">Part</span></span>|<span data-ttu-id="38d25-109">Typ</span><span class="sxs-lookup"><span data-stu-id="38d25-109">Type</span></span>|<span data-ttu-id="38d25-110">Opis</span><span class="sxs-lookup"><span data-stu-id="38d25-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="38d25-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="38d25-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="38d25-112">Obiekt, który zawiera formanty na <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="38d25-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="38d25-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="38d25-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="38d25-114">Obiekt, który zawiera formanty, które znajdują się w obszarze przepełnienia <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="38d25-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="38d25-115">Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ToolBar>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w ramach <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="38d25-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="38d25-116">( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element na <xref:System.Windows.Controls.ToolBar>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).</span><span class="sxs-lookup"><span data-stu-id="38d25-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="38d25-117">Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednie podrzędne <xref:System.Windows.Controls.ScrollViewer>, należy podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="38d25-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="38d25-118">Stany paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="38d25-118">ToolBar States</span></span>  
 <span data-ttu-id="38d25-119">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.ToolBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="38d25-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="38d25-120">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="38d25-120">VisualState Name</span></span>|<span data-ttu-id="38d25-121">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="38d25-121">VisualStateGroup Name</span></span>|<span data-ttu-id="38d25-122">Opis</span><span class="sxs-lookup"><span data-stu-id="38d25-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="38d25-123">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="38d25-123">Valid</span></span>|<span data-ttu-id="38d25-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="38d25-124">ValidationStates</span></span>|<span data-ttu-id="38d25-125">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="38d25-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="38d25-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="38d25-126">InvalidFocused</span></span>|<span data-ttu-id="38d25-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="38d25-127">ValidationStates</span></span>|<span data-ttu-id="38d25-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="38d25-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="38d25-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="38d25-129">InvalidUnfocused</span></span>|<span data-ttu-id="38d25-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="38d25-130">ValidationStates</span></span>|<span data-ttu-id="38d25-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="38d25-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="38d25-132">Przykład ControlTemplate paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="38d25-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="38d25-133">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ToolBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="38d25-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="38d25-134">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="38d25-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="38d25-135">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="38d25-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d25-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38d25-136">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="38d25-137">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="38d25-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="38d25-138">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="38d25-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="38d25-139">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="38d25-139">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="38d25-140">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="38d25-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
