---
title: ToolTip — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: 53b21f610ba957370fac70b79e6a827d624b6473
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="794c2-102">ToolTip — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="794c2-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="794c2-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.ToolTip> formantu.</span><span class="sxs-lookup"><span data-stu-id="794c2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="794c2-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="794c2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="794c2-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="794c2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="794c2-106">Elementy ToolTip</span><span class="sxs-lookup"><span data-stu-id="794c2-106">ToolTip Parts</span></span>  
 <span data-ttu-id="794c2-107"><xref:System.Windows.Controls.ToolTip> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="794c2-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="794c2-108">Stany etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="794c2-108">ToolTip States</span></span>  
 <span data-ttu-id="794c2-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.ToolTip> formantu.</span><span class="sxs-lookup"><span data-stu-id="794c2-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="794c2-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="794c2-110">VisualState Name</span></span>|<span data-ttu-id="794c2-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="794c2-111">VisualStateGroup Name</span></span>|<span data-ttu-id="794c2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="794c2-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="794c2-113">Zamknięte</span><span class="sxs-lookup"><span data-stu-id="794c2-113">Closed</span></span>|<span data-ttu-id="794c2-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="794c2-114">OpenStates</span></span>|<span data-ttu-id="794c2-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="794c2-115">The default state.</span></span>|  
|<span data-ttu-id="794c2-116">Otwarcie</span><span class="sxs-lookup"><span data-stu-id="794c2-116">Open</span></span>|<span data-ttu-id="794c2-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="794c2-117">OpenStates</span></span>|<span data-ttu-id="794c2-118"><xref:System.Windows.Controls.ToolTip> Jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="794c2-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="794c2-119">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="794c2-119">Valid</span></span>|<span data-ttu-id="794c2-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="794c2-120">ValidationStates</span></span>|<span data-ttu-id="794c2-121">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="794c2-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="794c2-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="794c2-122">InvalidFocused</span></span>|<span data-ttu-id="794c2-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="794c2-123">ValidationStates</span></span>|<span data-ttu-id="794c2-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="794c2-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="794c2-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="794c2-125">InvalidUnfocused</span></span>|<span data-ttu-id="794c2-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="794c2-126">ValidationStates</span></span>|<span data-ttu-id="794c2-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="794c2-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="794c2-128">Przykład ControlTemplate etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="794c2-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="794c2-129">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ToolTip> formantu.</span><span class="sxs-lookup"><span data-stu-id="794c2-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="794c2-130">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="794c2-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="794c2-131">Pełny przykład, zobacz [style próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="794c2-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="794c2-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="794c2-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="794c2-133">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="794c2-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="794c2-134">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="794c2-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="794c2-135">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="794c2-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="794c2-136">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="794c2-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
