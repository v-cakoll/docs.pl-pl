---
title: Style i szablony suwaka
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
ms.openlocfilehash: ea7e9f5323f29adf10ad8cfe890a85ff91071733
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457972"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="8ddec-102">Style i szablony suwaka</span><span class="sxs-lookup"><span data-stu-id="8ddec-102">Slider Styles and Templates</span></span>
<span data-ttu-id="8ddec-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Slider> formantu.</span><span class="sxs-lookup"><span data-stu-id="8ddec-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="8ddec-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="8ddec-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8ddec-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="8ddec-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="8ddec-106">Części suwaka</span><span class="sxs-lookup"><span data-stu-id="8ddec-106">Slider Parts</span></span>  
 <span data-ttu-id="8ddec-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Slider> formantu.</span><span class="sxs-lookup"><span data-stu-id="8ddec-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="8ddec-108">Część</span><span class="sxs-lookup"><span data-stu-id="8ddec-108">Part</span></span>|<span data-ttu-id="8ddec-109">Typ</span><span class="sxs-lookup"><span data-stu-id="8ddec-109">Type</span></span>|<span data-ttu-id="8ddec-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8ddec-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8ddec-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="8ddec-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="8ddec-112">Kontener dla elementu, który wskazuje położenie <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="8ddec-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="8ddec-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="8ddec-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="8ddec-114">Element, który wyświetla wybranego zakresu wzdłuż <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="8ddec-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="8ddec-115">Wybranego zakresu jest widoczny tylko wtedy, gdy <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> jest właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="8ddec-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="8ddec-116">Stany suwaka</span><span class="sxs-lookup"><span data-stu-id="8ddec-116">Slider States</span></span>  
 <span data-ttu-id="8ddec-117">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Slider> formantu.</span><span class="sxs-lookup"><span data-stu-id="8ddec-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="8ddec-118">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="8ddec-118">VisualState Name</span></span>|<span data-ttu-id="8ddec-119">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="8ddec-119">VisualStateGroup Name</span></span>|<span data-ttu-id="8ddec-120">Opis</span><span class="sxs-lookup"><span data-stu-id="8ddec-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="8ddec-121">Normalny</span><span class="sxs-lookup"><span data-stu-id="8ddec-121">Normal</span></span>|<span data-ttu-id="8ddec-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8ddec-122">CommonStates</span></span>|<span data-ttu-id="8ddec-123">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="8ddec-123">The default state.</span></span>|  
|<span data-ttu-id="8ddec-124">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="8ddec-124">MouseOver</span></span>|<span data-ttu-id="8ddec-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8ddec-125">CommonStates</span></span>|<span data-ttu-id="8ddec-126">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="8ddec-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="8ddec-127">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="8ddec-127">Disabled</span></span>|<span data-ttu-id="8ddec-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8ddec-128">CommonStates</span></span>|<span data-ttu-id="8ddec-129">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="8ddec-129">The control is disabled.</span></span>|  
|<span data-ttu-id="8ddec-130">Fokus</span><span class="sxs-lookup"><span data-stu-id="8ddec-130">Focused</span></span>|<span data-ttu-id="8ddec-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8ddec-131">FocusStates</span></span>|<span data-ttu-id="8ddec-132">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="8ddec-132">The control has focus.</span></span>|  
|<span data-ttu-id="8ddec-133">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="8ddec-133">Unfocused</span></span>|<span data-ttu-id="8ddec-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8ddec-134">FocusStates</span></span>|<span data-ttu-id="8ddec-135">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="8ddec-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="8ddec-136">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="8ddec-136">Valid</span></span>|<span data-ttu-id="8ddec-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8ddec-137">ValidationStates</span></span>|<span data-ttu-id="8ddec-138">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="8ddec-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8ddec-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8ddec-139">InvalidFocused</span></span>|<span data-ttu-id="8ddec-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8ddec-140">ValidationStates</span></span>|<span data-ttu-id="8ddec-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="8ddec-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8ddec-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8ddec-142">InvalidUnfocused</span></span>|<span data-ttu-id="8ddec-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8ddec-143">ValidationStates</span></span>|<span data-ttu-id="8ddec-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="8ddec-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="8ddec-145">Przykład ControlTemplate suwaka</span><span class="sxs-lookup"><span data-stu-id="8ddec-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="8ddec-146">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Slider> formantu.</span><span class="sxs-lookup"><span data-stu-id="8ddec-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="8ddec-147">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="8ddec-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8ddec-148">Pełny przykład, zobacz [style próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="8ddec-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ddec-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ddec-149">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="8ddec-150">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="8ddec-150">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="8ddec-151">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="8ddec-151">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="8ddec-152">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="8ddec-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="8ddec-153">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="8ddec-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
