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
ms.openlocfilehash: 385a69ad2bd17ae4c51437245915109aad446bdf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103197"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="cc8b1-102">Style i szablony suwaka</span><span class="sxs-lookup"><span data-stu-id="cc8b1-102">Slider Styles and Templates</span></span>
<span data-ttu-id="cc8b1-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Slider> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="cc8b1-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="cc8b1-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="cc8b1-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="cc8b1-106">Części suwaka</span><span class="sxs-lookup"><span data-stu-id="cc8b1-106">Slider Parts</span></span>  
 <span data-ttu-id="cc8b1-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Slider> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="cc8b1-108">Część</span><span class="sxs-lookup"><span data-stu-id="cc8b1-108">Part</span></span>|<span data-ttu-id="cc8b1-109">Typ</span><span class="sxs-lookup"><span data-stu-id="cc8b1-109">Type</span></span>|<span data-ttu-id="cc8b1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cc8b1-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="cc8b1-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="cc8b1-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="cc8b1-112">Kontener dla elementu, który wskazuje pozycję <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="cc8b1-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="cc8b1-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="cc8b1-114">Element, który wyświetla zaznaczony zakres wzdłuż <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="cc8b1-115">Wybranego zakresu jest widoczny tylko wtedy, gdy <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="cc8b1-116">Stany suwaka</span><span class="sxs-lookup"><span data-stu-id="cc8b1-116">Slider States</span></span>  
 <span data-ttu-id="cc8b1-117">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Slider> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="cc8b1-118">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="cc8b1-118">VisualState Name</span></span>|<span data-ttu-id="cc8b1-119">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="cc8b1-119">VisualStateGroup Name</span></span>|<span data-ttu-id="cc8b1-120">Opis</span><span class="sxs-lookup"><span data-stu-id="cc8b1-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="cc8b1-121">Normalne</span><span class="sxs-lookup"><span data-stu-id="cc8b1-121">Normal</span></span>|<span data-ttu-id="cc8b1-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cc8b1-122">CommonStates</span></span>|<span data-ttu-id="cc8b1-123">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-123">The default state.</span></span>|  
|<span data-ttu-id="cc8b1-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="cc8b1-124">MouseOver</span></span>|<span data-ttu-id="cc8b1-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cc8b1-125">CommonStates</span></span>|<span data-ttu-id="cc8b1-126">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="cc8b1-127">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="cc8b1-127">Disabled</span></span>|<span data-ttu-id="cc8b1-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cc8b1-128">CommonStates</span></span>|<span data-ttu-id="cc8b1-129">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-129">The control is disabled.</span></span>|  
|<span data-ttu-id="cc8b1-130">Fokus</span><span class="sxs-lookup"><span data-stu-id="cc8b1-130">Focused</span></span>|<span data-ttu-id="cc8b1-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cc8b1-131">FocusStates</span></span>|<span data-ttu-id="cc8b1-132">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-132">The control has focus.</span></span>|  
|<span data-ttu-id="cc8b1-133">Po przeniesieniu fokusu</span><span class="sxs-lookup"><span data-stu-id="cc8b1-133">Unfocused</span></span>|<span data-ttu-id="cc8b1-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cc8b1-134">FocusStates</span></span>|<span data-ttu-id="cc8b1-135">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="cc8b1-136">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="cc8b1-136">Valid</span></span>|<span data-ttu-id="cc8b1-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cc8b1-137">ValidationStates</span></span>|<span data-ttu-id="cc8b1-138">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="cc8b1-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="cc8b1-139">InvalidFocused</span></span>|<span data-ttu-id="cc8b1-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cc8b1-140">ValidationStates</span></span>|<span data-ttu-id="cc8b1-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="cc8b1-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="cc8b1-142">InvalidUnfocused</span></span>|<span data-ttu-id="cc8b1-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cc8b1-143">ValidationStates</span></span>|<span data-ttu-id="cc8b1-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="cc8b1-145">Przykład ControlTemplate suwaka</span><span class="sxs-lookup"><span data-stu-id="cc8b1-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="cc8b1-146">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Slider> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="cc8b1-147">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="cc8b1-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="cc8b1-148">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="cc8b1-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc8b1-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc8b1-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="cc8b1-150">Style i szablony formantu</span><span class="sxs-lookup"><span data-stu-id="cc8b1-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="cc8b1-151">Niestandardowe dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="cc8b1-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="cc8b1-152">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="cc8b1-152">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="cc8b1-153">Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="cc8b1-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
