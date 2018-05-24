---
title: ProgressBar — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 89aea3e80fe17ece8a17f62f62290d34ddd55c60
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="87dd1-102">ProgressBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="87dd1-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="87dd1-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.ProgressBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="87dd1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="87dd1-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="87dd1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="87dd1-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="87dd1-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="87dd1-106">Części ProgressBar</span><span class="sxs-lookup"><span data-stu-id="87dd1-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="87dd1-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.ProgressBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="87dd1-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="87dd1-108">Część</span><span class="sxs-lookup"><span data-stu-id="87dd1-108">Part</span></span>|<span data-ttu-id="87dd1-109">Typ</span><span class="sxs-lookup"><span data-stu-id="87dd1-109">Type</span></span>|<span data-ttu-id="87dd1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="87dd1-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="87dd1-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="87dd1-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="87dd1-112">Obiekt, który wskazuje postęp.</span><span class="sxs-lookup"><span data-stu-id="87dd1-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="87dd1-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="87dd1-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="87dd1-114">Obiekt, który określa ścieżkę wskaźnik postępu.</span><span class="sxs-lookup"><span data-stu-id="87dd1-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="87dd1-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="87dd1-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="87dd1-116">Obiekt embellishes pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="87dd1-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="87dd1-117">Stany ProgressBar</span><span class="sxs-lookup"><span data-stu-id="87dd1-117">ProgressBar States</span></span>  
 <span data-ttu-id="87dd1-118">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.ProgressBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="87dd1-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="87dd1-119">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="87dd1-119">VisualState Name</span></span>|<span data-ttu-id="87dd1-120">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="87dd1-120">VisualStateGroup Name</span></span>|<span data-ttu-id="87dd1-121">Opis</span><span class="sxs-lookup"><span data-stu-id="87dd1-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="87dd1-122">Określony</span><span class="sxs-lookup"><span data-stu-id="87dd1-122">Determinate</span></span>|<span data-ttu-id="87dd1-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="87dd1-123">CommonStates</span></span>|<span data-ttu-id="87dd1-124"><xref:System.Windows.Controls.ProgressBar> Raporty na podstawie postępu <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="87dd1-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="87dd1-125">Nieokreślony</span><span class="sxs-lookup"><span data-stu-id="87dd1-125">Indeterminate</span></span>|<span data-ttu-id="87dd1-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="87dd1-126">CommonStates</span></span>|<span data-ttu-id="87dd1-127"><xref:System.Windows.Controls.ProgressBar> Raporty ogólny postęp identycznych wzorca.</span><span class="sxs-lookup"><span data-stu-id="87dd1-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="87dd1-128">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="87dd1-128">Valid</span></span>|<span data-ttu-id="87dd1-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="87dd1-129">ValidationStates</span></span>|<span data-ttu-id="87dd1-130">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="87dd1-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="87dd1-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="87dd1-131">InvalidFocused</span></span>|<span data-ttu-id="87dd1-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="87dd1-132">ValidationStates</span></span>|<span data-ttu-id="87dd1-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="87dd1-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="87dd1-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="87dd1-134">InvalidUnfocused</span></span>|<span data-ttu-id="87dd1-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="87dd1-135">ValidationStates</span></span>|<span data-ttu-id="87dd1-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="87dd1-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="87dd1-137">Przykład ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="87dd1-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="87dd1-138">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ProgressBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="87dd1-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="87dd1-139">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="87dd1-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="87dd1-140">Pełny przykład, zobacz [style próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="87dd1-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87dd1-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87dd1-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="87dd1-142">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="87dd1-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="87dd1-143">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="87dd1-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="87dd1-144">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="87dd1-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="87dd1-145">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="87dd1-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
