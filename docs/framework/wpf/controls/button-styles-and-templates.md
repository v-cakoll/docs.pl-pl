---
title: Style i szablony przycisków
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: afd06d013dc7bd1940480e3800a87bed13d314b3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355574"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="37cc0-102">Style i szablony przycisków</span><span class="sxs-lookup"><span data-stu-id="37cc0-102">Button Styles and Templates</span></span>
<span data-ttu-id="37cc0-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="37cc0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="37cc0-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="37cc0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="37cc0-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="37cc0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="37cc0-106">Przycisk części</span><span class="sxs-lookup"><span data-stu-id="37cc0-106">Button Parts</span></span>  
 <span data-ttu-id="37cc0-107"><xref:System.Windows.Controls.Button> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="37cc0-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="37cc0-108">Stany przycisku</span><span class="sxs-lookup"><span data-stu-id="37cc0-108">Button States</span></span>  
 <span data-ttu-id="37cc0-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="37cc0-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="37cc0-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="37cc0-110">VisualState Name</span></span>|<span data-ttu-id="37cc0-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="37cc0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="37cc0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="37cc0-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="37cc0-113">Normalne</span><span class="sxs-lookup"><span data-stu-id="37cc0-113">Normal</span></span>|<span data-ttu-id="37cc0-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="37cc0-114">CommonStates</span></span>|<span data-ttu-id="37cc0-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="37cc0-115">The default state.</span></span>|  
|<span data-ttu-id="37cc0-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="37cc0-116">MouseOver</span></span>|<span data-ttu-id="37cc0-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="37cc0-117">CommonStates</span></span>|<span data-ttu-id="37cc0-118">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="37cc0-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="37cc0-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="37cc0-119">Pressed</span></span>|<span data-ttu-id="37cc0-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="37cc0-120">CommonStates</span></span>|<span data-ttu-id="37cc0-121">Użytkownik naciśnie kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="37cc0-121">The control is pressed.</span></span>|  
|<span data-ttu-id="37cc0-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="37cc0-122">Disabled</span></span>|<span data-ttu-id="37cc0-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="37cc0-123">CommonStates</span></span>|<span data-ttu-id="37cc0-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="37cc0-124">The control is disabled.</span></span>|  
|<span data-ttu-id="37cc0-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="37cc0-125">Focused</span></span>|<span data-ttu-id="37cc0-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="37cc0-126">FocusStates</span></span>|<span data-ttu-id="37cc0-127">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="37cc0-127">The control has focus.</span></span>|  
|<span data-ttu-id="37cc0-128">Po przeniesieniu fokusu</span><span class="sxs-lookup"><span data-stu-id="37cc0-128">Unfocused</span></span>|<span data-ttu-id="37cc0-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="37cc0-129">FocusStates</span></span>|<span data-ttu-id="37cc0-130">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="37cc0-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="37cc0-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="37cc0-131">Valid</span></span>|<span data-ttu-id="37cc0-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="37cc0-132">ValidationStates</span></span>|<span data-ttu-id="37cc0-133">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="37cc0-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="37cc0-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="37cc0-134">InvalidFocused</span></span>|<span data-ttu-id="37cc0-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="37cc0-135">ValidationStates</span></span>|<span data-ttu-id="37cc0-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` i kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="37cc0-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="37cc0-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="37cc0-137">InvalidUnfocused</span></span>|<span data-ttu-id="37cc0-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="37cc0-138">ValidationStates</span></span>|<span data-ttu-id="37cc0-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` i kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="37cc0-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="37cc0-140">Przycisk przykład ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="37cc0-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="37cc0-141">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="37cc0-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="37cc0-142">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="37cc0-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="37cc0-143">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="37cc0-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37cc0-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37cc0-144">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="37cc0-145">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="37cc0-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="37cc0-146">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="37cc0-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="37cc0-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="37cc0-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="37cc0-148">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="37cc0-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
