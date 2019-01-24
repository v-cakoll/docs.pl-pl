---
title: StatusBar — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: ee3bd060268d5ab6f713a74f871d7de0dd77782b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660466"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="7b7d9-102">StatusBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="7b7d9-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="7b7d9-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Primitives.StatusBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="7b7d9-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7b7d9-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="7b7d9-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="7b7d9-106">Części pasek stanu</span><span class="sxs-lookup"><span data-stu-id="7b7d9-106">StatusBar Parts</span></span>  
 <span data-ttu-id="7b7d9-107"><xref:System.Windows.Controls.Primitives.StatusBar> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="7b7d9-108">Stany pasek stanu</span><span class="sxs-lookup"><span data-stu-id="7b7d9-108">StatusBar States</span></span>  
 <span data-ttu-id="7b7d9-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.StatusBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="7b7d9-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="7b7d9-110">VisualState Name</span></span>|<span data-ttu-id="7b7d9-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7b7d9-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7b7d9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7b7d9-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7b7d9-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="7b7d9-113">Valid</span></span>|<span data-ttu-id="7b7d9-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7b7d9-114">ValidationStates</span></span>|<span data-ttu-id="7b7d9-115">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7b7d9-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7b7d9-116">InvalidFocused</span></span>|<span data-ttu-id="7b7d9-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7b7d9-117">ValidationStates</span></span>|<span data-ttu-id="7b7d9-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7b7d9-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7b7d9-119">InvalidUnfocused</span></span>|<span data-ttu-id="7b7d9-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7b7d9-120">ValidationStates</span></span>|<span data-ttu-id="7b7d9-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="7b7d9-122">Części StatusBarItem</span><span class="sxs-lookup"><span data-stu-id="7b7d9-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="7b7d9-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="7b7d9-124">Stany pasek stanu</span><span class="sxs-lookup"><span data-stu-id="7b7d9-124">StatusBar States</span></span>  
 <span data-ttu-id="7b7d9-125">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.StatusBarItem> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="7b7d9-126">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="7b7d9-126">VisualState Name</span></span>|<span data-ttu-id="7b7d9-127">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7b7d9-127">VisualStateGroup Name</span></span>|<span data-ttu-id="7b7d9-128">Opis</span><span class="sxs-lookup"><span data-stu-id="7b7d9-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7b7d9-129">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="7b7d9-129">Valid</span></span>|<span data-ttu-id="7b7d9-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7b7d9-130">ValidationStates</span></span>|<span data-ttu-id="7b7d9-131">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7b7d9-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7b7d9-132">InvalidFocused</span></span>|<span data-ttu-id="7b7d9-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7b7d9-133">ValidationStates</span></span>|<span data-ttu-id="7b7d9-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7b7d9-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7b7d9-135">InvalidUnfocused</span></span>|<span data-ttu-id="7b7d9-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7b7d9-136">ValidationStates</span></span>|<span data-ttu-id="7b7d9-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="7b7d9-138">Przykład ControlTemplate pasek stanu</span><span class="sxs-lookup"><span data-stu-id="7b7d9-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="7b7d9-139">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.StatusBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="7b7d9-140"><xref:System.Windows.Controls.ControlTemplate> Używa co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="7b7d9-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7b7d9-141">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="7b7d9-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7d9-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b7d9-142">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7b7d9-143">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="7b7d9-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="7b7d9-144">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="7b7d9-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="7b7d9-145">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="7b7d9-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="7b7d9-146">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7b7d9-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
