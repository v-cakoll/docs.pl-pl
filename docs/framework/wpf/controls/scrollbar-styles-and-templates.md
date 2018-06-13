---
title: ScrollBar — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 926fc3373bb40eb12462dcead278d458cefad7cf
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457583"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="e7e09-102">ScrollBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="e7e09-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="e7e09-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="e7e09-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="e7e09-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="e7e09-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e7e09-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e7e09-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="e7e09-106">Części paska przewijania</span><span class="sxs-lookup"><span data-stu-id="e7e09-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="e7e09-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="e7e09-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="e7e09-108">Część</span><span class="sxs-lookup"><span data-stu-id="e7e09-108">Part</span></span>|<span data-ttu-id="e7e09-109">Typ</span><span class="sxs-lookup"><span data-stu-id="e7e09-109">Type</span></span>|<span data-ttu-id="e7e09-110">Opis</span><span class="sxs-lookup"><span data-stu-id="e7e09-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e7e09-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="e7e09-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="e7e09-112">Kontener dla elementu, który wskazuje położenie <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="e7e09-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="e7e09-113">Stany pasek przewijania</span><span class="sxs-lookup"><span data-stu-id="e7e09-113">ScrollBar States</span></span>  
 <span data-ttu-id="e7e09-114">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="e7e09-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="e7e09-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="e7e09-115">VisualState Name</span></span>|<span data-ttu-id="e7e09-116">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e7e09-116">VisualStateGroup Name</span></span>|<span data-ttu-id="e7e09-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e7e09-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="e7e09-118">Normalny</span><span class="sxs-lookup"><span data-stu-id="e7e09-118">Normal</span></span>|<span data-ttu-id="e7e09-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e7e09-119">CommonStates</span></span>|<span data-ttu-id="e7e09-120">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="e7e09-120">The default state.</span></span>|  
|<span data-ttu-id="e7e09-121">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="e7e09-121">MouseOver</span></span>|<span data-ttu-id="e7e09-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e7e09-122">CommonStates</span></span>|<span data-ttu-id="e7e09-123">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="e7e09-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="e7e09-124">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="e7e09-124">Disabled</span></span>|<span data-ttu-id="e7e09-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e7e09-125">CommonStates</span></span>|<span data-ttu-id="e7e09-126">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="e7e09-126">The control is disabled.</span></span>|  
|<span data-ttu-id="e7e09-127">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="e7e09-127">Valid</span></span>|<span data-ttu-id="e7e09-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e7e09-128">ValidationStates</span></span>|<span data-ttu-id="e7e09-129">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="e7e09-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e7e09-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e7e09-130">InvalidFocused</span></span>|<span data-ttu-id="e7e09-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e7e09-131">ValidationStates</span></span>|<span data-ttu-id="e7e09-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="e7e09-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e7e09-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e7e09-133">InvalidUnfocused</span></span>|<span data-ttu-id="e7e09-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e7e09-134">ValidationStates</span></span>|<span data-ttu-id="e7e09-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="e7e09-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="e7e09-136">Przykład ControlTemplate pasek przewijania</span><span class="sxs-lookup"><span data-stu-id="e7e09-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="e7e09-137">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="e7e09-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="e7e09-138">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="e7e09-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e7e09-139">Pełny przykład, zobacz [style próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="e7e09-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e09-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7e09-140">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e7e09-141">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="e7e09-141">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="e7e09-142">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="e7e09-142">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="e7e09-143">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="e7e09-143">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="e7e09-144">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e7e09-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
