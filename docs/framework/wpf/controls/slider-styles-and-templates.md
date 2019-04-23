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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103197"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="886cd-102">Style i szablony suwaka</span><span class="sxs-lookup"><span data-stu-id="886cd-102">Slider Styles and Templates</span></span>
<span data-ttu-id="886cd-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Slider> kontroli.</span><span class="sxs-lookup"><span data-stu-id="886cd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="886cd-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="886cd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="886cd-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="886cd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="886cd-106">Części suwaka</span><span class="sxs-lookup"><span data-stu-id="886cd-106">Slider Parts</span></span>  
 <span data-ttu-id="886cd-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Slider> kontroli.</span><span class="sxs-lookup"><span data-stu-id="886cd-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="886cd-108">Część</span><span class="sxs-lookup"><span data-stu-id="886cd-108">Part</span></span>|<span data-ttu-id="886cd-109">Typ</span><span class="sxs-lookup"><span data-stu-id="886cd-109">Type</span></span>|<span data-ttu-id="886cd-110">Opis</span><span class="sxs-lookup"><span data-stu-id="886cd-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="886cd-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="886cd-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="886cd-112">Kontener dla elementu, który wskazuje pozycję <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="886cd-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="886cd-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="886cd-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="886cd-114">Element, który wyświetla zaznaczony zakres wzdłuż <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="886cd-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="886cd-115">Wybranego zakresu jest widoczny tylko wtedy, gdy <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="886cd-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="886cd-116">Stany suwaka</span><span class="sxs-lookup"><span data-stu-id="886cd-116">Slider States</span></span>  
 <span data-ttu-id="886cd-117">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Slider> kontroli.</span><span class="sxs-lookup"><span data-stu-id="886cd-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="886cd-118">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="886cd-118">VisualState Name</span></span>|<span data-ttu-id="886cd-119">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="886cd-119">VisualStateGroup Name</span></span>|<span data-ttu-id="886cd-120">Opis</span><span class="sxs-lookup"><span data-stu-id="886cd-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="886cd-121">Normalne</span><span class="sxs-lookup"><span data-stu-id="886cd-121">Normal</span></span>|<span data-ttu-id="886cd-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="886cd-122">CommonStates</span></span>|<span data-ttu-id="886cd-123">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="886cd-123">The default state.</span></span>|  
|<span data-ttu-id="886cd-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="886cd-124">MouseOver</span></span>|<span data-ttu-id="886cd-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="886cd-125">CommonStates</span></span>|<span data-ttu-id="886cd-126">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="886cd-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="886cd-127">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="886cd-127">Disabled</span></span>|<span data-ttu-id="886cd-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="886cd-128">CommonStates</span></span>|<span data-ttu-id="886cd-129">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="886cd-129">The control is disabled.</span></span>|  
|<span data-ttu-id="886cd-130">Fokus</span><span class="sxs-lookup"><span data-stu-id="886cd-130">Focused</span></span>|<span data-ttu-id="886cd-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="886cd-131">FocusStates</span></span>|<span data-ttu-id="886cd-132">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="886cd-132">The control has focus.</span></span>|  
|<span data-ttu-id="886cd-133">Po przeniesieniu fokusu</span><span class="sxs-lookup"><span data-stu-id="886cd-133">Unfocused</span></span>|<span data-ttu-id="886cd-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="886cd-134">FocusStates</span></span>|<span data-ttu-id="886cd-135">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="886cd-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="886cd-136">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="886cd-136">Valid</span></span>|<span data-ttu-id="886cd-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="886cd-137">ValidationStates</span></span>|<span data-ttu-id="886cd-138">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="886cd-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="886cd-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="886cd-139">InvalidFocused</span></span>|<span data-ttu-id="886cd-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="886cd-140">ValidationStates</span></span>|<span data-ttu-id="886cd-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="886cd-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="886cd-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="886cd-142">InvalidUnfocused</span></span>|<span data-ttu-id="886cd-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="886cd-143">ValidationStates</span></span>|<span data-ttu-id="886cd-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="886cd-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="886cd-145">Przykład ControlTemplate suwaka</span><span class="sxs-lookup"><span data-stu-id="886cd-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="886cd-146">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Slider> kontroli.</span><span class="sxs-lookup"><span data-stu-id="886cd-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="886cd-147">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="886cd-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="886cd-148">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="886cd-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886cd-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="886cd-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="886cd-150">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="886cd-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="886cd-151">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="886cd-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="886cd-152">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="886cd-152">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="886cd-153">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="886cd-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
