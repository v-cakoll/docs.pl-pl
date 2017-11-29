---
title: Style i szablony suwaka
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9dfa340cf42e5e7ed105bf14eb0f7a24ea85a1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="c4a61-102">Style i szablony suwaka</span><span class="sxs-lookup"><span data-stu-id="c4a61-102">Slider Styles and Templates</span></span>
<span data-ttu-id="c4a61-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Slider> formantu.</span><span class="sxs-lookup"><span data-stu-id="c4a61-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="c4a61-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="c4a61-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c4a61-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c4a61-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="c4a61-106">Części suwaka</span><span class="sxs-lookup"><span data-stu-id="c4a61-106">Slider Parts</span></span>  
 <span data-ttu-id="c4a61-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Slider> formantu.</span><span class="sxs-lookup"><span data-stu-id="c4a61-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="c4a61-108">Część</span><span class="sxs-lookup"><span data-stu-id="c4a61-108">Part</span></span>|<span data-ttu-id="c4a61-109">Typ</span><span class="sxs-lookup"><span data-stu-id="c4a61-109">Type</span></span>|<span data-ttu-id="c4a61-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c4a61-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c4a61-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="c4a61-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="c4a61-112">Kontener dla elementu, który wskazuje położenie <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="c4a61-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="c4a61-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="c4a61-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="c4a61-114">Element, który wyświetla wybranego zakresu wzdłuż <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="c4a61-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="c4a61-115">Wybranego zakresu jest widoczny tylko wtedy, gdy <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> jest właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="c4a61-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="c4a61-116">Stany suwaka</span><span class="sxs-lookup"><span data-stu-id="c4a61-116">Slider States</span></span>  
 <span data-ttu-id="c4a61-117">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Slider> formantu.</span><span class="sxs-lookup"><span data-stu-id="c4a61-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="c4a61-118">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="c4a61-118">VisualState Name</span></span>|<span data-ttu-id="c4a61-119">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c4a61-119">VisualStateGroup Name</span></span>|<span data-ttu-id="c4a61-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c4a61-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="c4a61-121">Normalny</span><span class="sxs-lookup"><span data-stu-id="c4a61-121">Normal</span></span>|<span data-ttu-id="c4a61-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4a61-122">CommonStates</span></span>|<span data-ttu-id="c4a61-123">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="c4a61-123">The default state.</span></span>|  
|<span data-ttu-id="c4a61-124">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="c4a61-124">MouseOver</span></span>|<span data-ttu-id="c4a61-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4a61-125">CommonStates</span></span>|<span data-ttu-id="c4a61-126">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="c4a61-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="c4a61-127">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="c4a61-127">Disabled</span></span>|<span data-ttu-id="c4a61-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4a61-128">CommonStates</span></span>|<span data-ttu-id="c4a61-129">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="c4a61-129">The control is disabled.</span></span>|  
|<span data-ttu-id="c4a61-130">Fokus</span><span class="sxs-lookup"><span data-stu-id="c4a61-130">Focused</span></span>|<span data-ttu-id="c4a61-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c4a61-131">FocusStates</span></span>|<span data-ttu-id="c4a61-132">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="c4a61-132">The control has focus.</span></span>|  
|<span data-ttu-id="c4a61-133">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="c4a61-133">Unfocused</span></span>|<span data-ttu-id="c4a61-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c4a61-134">FocusStates</span></span>|<span data-ttu-id="c4a61-135">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="c4a61-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="c4a61-136">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="c4a61-136">Valid</span></span>|<span data-ttu-id="c4a61-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4a61-137">ValidationStates</span></span>|<span data-ttu-id="c4a61-138">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="c4a61-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c4a61-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c4a61-139">InvalidFocused</span></span>|<span data-ttu-id="c4a61-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4a61-140">ValidationStates</span></span>|<span data-ttu-id="c4a61-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="c4a61-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c4a61-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c4a61-142">InvalidUnfocused</span></span>|<span data-ttu-id="c4a61-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4a61-143">ValidationStates</span></span>|<span data-ttu-id="c4a61-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="c4a61-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="c4a61-145">Przykład ControlTemplate suwaka</span><span class="sxs-lookup"><span data-stu-id="c4a61-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="c4a61-146">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Slider> formantu.</span><span class="sxs-lookup"><span data-stu-id="c4a61-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="c4a61-147">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="c4a61-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c4a61-148">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="c4a61-148">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a61-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4a61-149">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c4a61-150">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="c4a61-150">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c4a61-151">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="c4a61-151">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c4a61-152">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="c4a61-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c4a61-153">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c4a61-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
