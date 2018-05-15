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
ms.openlocfilehash: 85bbad93780536d0f95bdde2a1baaae044c9023b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="ea9eb-102">StatusBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="ea9eb-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="ea9eb-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Primitives.StatusBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="ea9eb-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ea9eb-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ea9eb-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="ea9eb-106">Części pasek stanu</span><span class="sxs-lookup"><span data-stu-id="ea9eb-106">StatusBar Parts</span></span>  
 <span data-ttu-id="ea9eb-107"><xref:System.Windows.Controls.Primitives.StatusBar> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="ea9eb-108">Stany pasek stanu</span><span class="sxs-lookup"><span data-stu-id="ea9eb-108">StatusBar States</span></span>  
 <span data-ttu-id="ea9eb-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.StatusBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="ea9eb-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="ea9eb-110">VisualState Name</span></span>|<span data-ttu-id="ea9eb-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ea9eb-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ea9eb-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ea9eb-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ea9eb-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="ea9eb-113">Valid</span></span>|<span data-ttu-id="ea9eb-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea9eb-114">ValidationStates</span></span>|<span data-ttu-id="ea9eb-115">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ea9eb-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ea9eb-116">InvalidFocused</span></span>|<span data-ttu-id="ea9eb-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea9eb-117">ValidationStates</span></span>|<span data-ttu-id="ea9eb-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ea9eb-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ea9eb-119">InvalidUnfocused</span></span>|<span data-ttu-id="ea9eb-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea9eb-120">ValidationStates</span></span>|<span data-ttu-id="ea9eb-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="ea9eb-122">Części StatusBarItem</span><span class="sxs-lookup"><span data-stu-id="ea9eb-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="ea9eb-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="ea9eb-124">Stany pasek stanu</span><span class="sxs-lookup"><span data-stu-id="ea9eb-124">StatusBar States</span></span>  
 <span data-ttu-id="ea9eb-125">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.StatusBarItem> formantu.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="ea9eb-126">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="ea9eb-126">VisualState Name</span></span>|<span data-ttu-id="ea9eb-127">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ea9eb-127">VisualStateGroup Name</span></span>|<span data-ttu-id="ea9eb-128">Opis</span><span class="sxs-lookup"><span data-stu-id="ea9eb-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ea9eb-129">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="ea9eb-129">Valid</span></span>|<span data-ttu-id="ea9eb-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea9eb-130">ValidationStates</span></span>|<span data-ttu-id="ea9eb-131">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ea9eb-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ea9eb-132">InvalidFocused</span></span>|<span data-ttu-id="ea9eb-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea9eb-133">ValidationStates</span></span>|<span data-ttu-id="ea9eb-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ea9eb-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ea9eb-135">InvalidUnfocused</span></span>|<span data-ttu-id="ea9eb-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea9eb-136">ValidationStates</span></span>|<span data-ttu-id="ea9eb-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="ea9eb-138">Przykład ControlTemplate pasek stanu</span><span class="sxs-lookup"><span data-stu-id="ea9eb-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="ea9eb-139">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.StatusBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="ea9eb-140"><xref:System.Windows.Controls.ControlTemplate> Korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="ea9eb-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ea9eb-141">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="ea9eb-141">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea9eb-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea9eb-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="ea9eb-143">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="ea9eb-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="ea9eb-144">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="ea9eb-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="ea9eb-145">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="ea9eb-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ea9eb-146">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ea9eb-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
