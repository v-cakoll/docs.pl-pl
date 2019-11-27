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
ms.openlocfilehash: f533142d5ba202bd4aaf628487eaaa2a18a535d0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283384"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="7a638-102">Style i szablony suwaka</span><span class="sxs-lookup"><span data-stu-id="7a638-102">Slider Styles and Templates</span></span>
<span data-ttu-id="7a638-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="7a638-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="7a638-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="7a638-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7a638-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="7a638-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="7a638-106">Części suwaka</span><span class="sxs-lookup"><span data-stu-id="7a638-106">Slider Parts</span></span>  
 <span data-ttu-id="7a638-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="7a638-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="7a638-108">Części</span><span class="sxs-lookup"><span data-stu-id="7a638-108">Part</span></span>|<span data-ttu-id="7a638-109">Type</span><span class="sxs-lookup"><span data-stu-id="7a638-109">Type</span></span>|<span data-ttu-id="7a638-110">Opis</span><span class="sxs-lookup"><span data-stu-id="7a638-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7a638-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="7a638-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="7a638-112">Kontener dla elementu, który wskazuje pozycję <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="7a638-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="7a638-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="7a638-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="7a638-114">Element, który wyświetla zakres zaznaczania wzdłuż <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="7a638-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="7a638-115">Zakres wyboru jest widoczny tylko wtedy, gdy właściwość <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="7a638-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="7a638-116">Stany suwaka</span><span class="sxs-lookup"><span data-stu-id="7a638-116">Slider States</span></span>  
 <span data-ttu-id="7a638-117">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="7a638-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="7a638-118">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="7a638-118">VisualState Name</span></span>|<span data-ttu-id="7a638-119">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7a638-119">VisualStateGroup Name</span></span>|<span data-ttu-id="7a638-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7a638-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="7a638-121">Normalne</span><span class="sxs-lookup"><span data-stu-id="7a638-121">Normal</span></span>|<span data-ttu-id="7a638-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a638-122">CommonStates</span></span>|<span data-ttu-id="7a638-123">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="7a638-123">The default state.</span></span>|  
|<span data-ttu-id="7a638-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="7a638-124">MouseOver</span></span>|<span data-ttu-id="7a638-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a638-125">CommonStates</span></span>|<span data-ttu-id="7a638-126">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="7a638-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="7a638-127">Wyłączono</span><span class="sxs-lookup"><span data-stu-id="7a638-127">Disabled</span></span>|<span data-ttu-id="7a638-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a638-128">CommonStates</span></span>|<span data-ttu-id="7a638-129">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="7a638-129">The control is disabled.</span></span>|  
|<span data-ttu-id="7a638-130">Fokus</span><span class="sxs-lookup"><span data-stu-id="7a638-130">Focused</span></span>|<span data-ttu-id="7a638-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7a638-131">FocusStates</span></span>|<span data-ttu-id="7a638-132">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="7a638-132">The control has focus.</span></span>|  
|<span data-ttu-id="7a638-133">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="7a638-133">Unfocused</span></span>|<span data-ttu-id="7a638-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7a638-134">FocusStates</span></span>|<span data-ttu-id="7a638-135">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="7a638-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="7a638-136">Prawidłowy</span><span class="sxs-lookup"><span data-stu-id="7a638-136">Valid</span></span>|<span data-ttu-id="7a638-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a638-137">ValidationStates</span></span>|<span data-ttu-id="7a638-138">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="7a638-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7a638-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7a638-139">InvalidFocused</span></span>|<span data-ttu-id="7a638-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a638-140">ValidationStates</span></span>|<span data-ttu-id="7a638-141">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="7a638-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7a638-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7a638-142">InvalidUnfocused</span></span>|<span data-ttu-id="7a638-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a638-143">ValidationStates</span></span>|<span data-ttu-id="7a638-144">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="7a638-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="7a638-145">Przykład ControlTemplateego suwaka</span><span class="sxs-lookup"><span data-stu-id="7a638-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="7a638-146">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="7a638-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="7a638-147">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7a638-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7a638-148">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="7a638-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a638-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a638-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7a638-150">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="7a638-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="7a638-151">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="7a638-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="7a638-152">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="7a638-152">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7a638-153">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="7a638-153">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
