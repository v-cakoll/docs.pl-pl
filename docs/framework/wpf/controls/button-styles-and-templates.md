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
ms.openlocfilehash: ef9f85848ebdda9dc4ae15d0f54847eacd46e24d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283581"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="07098-102">Style i szablony przycisków</span><span class="sxs-lookup"><span data-stu-id="07098-102">Button Styles and Templates</span></span>
<span data-ttu-id="07098-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="07098-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="07098-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="07098-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="07098-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="07098-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="07098-106">Części przycisku</span><span class="sxs-lookup"><span data-stu-id="07098-106">Button Parts</span></span>  
 <span data-ttu-id="07098-107">Formant <xref:System.Windows.Controls.Button> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="07098-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="07098-108">Stany przycisków</span><span class="sxs-lookup"><span data-stu-id="07098-108">Button States</span></span>  
 <span data-ttu-id="07098-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="07098-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="07098-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="07098-110">VisualState Name</span></span>|<span data-ttu-id="07098-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="07098-111">VisualStateGroup Name</span></span>|<span data-ttu-id="07098-112">Opis</span><span class="sxs-lookup"><span data-stu-id="07098-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="07098-113">Normalne</span><span class="sxs-lookup"><span data-stu-id="07098-113">Normal</span></span>|<span data-ttu-id="07098-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="07098-114">CommonStates</span></span>|<span data-ttu-id="07098-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="07098-115">The default state.</span></span>|  
|<span data-ttu-id="07098-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="07098-116">MouseOver</span></span>|<span data-ttu-id="07098-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="07098-117">CommonStates</span></span>|<span data-ttu-id="07098-118">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="07098-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="07098-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="07098-119">Pressed</span></span>|<span data-ttu-id="07098-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="07098-120">CommonStates</span></span>|<span data-ttu-id="07098-121">Kontrolka zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="07098-121">The control is pressed.</span></span>|  
|<span data-ttu-id="07098-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="07098-122">Disabled</span></span>|<span data-ttu-id="07098-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="07098-123">CommonStates</span></span>|<span data-ttu-id="07098-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="07098-124">The control is disabled.</span></span>|  
|<span data-ttu-id="07098-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="07098-125">Focused</span></span>|<span data-ttu-id="07098-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="07098-126">FocusStates</span></span>|<span data-ttu-id="07098-127">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="07098-127">The control has focus.</span></span>|  
|<span data-ttu-id="07098-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="07098-128">Unfocused</span></span>|<span data-ttu-id="07098-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="07098-129">FocusStates</span></span>|<span data-ttu-id="07098-130">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="07098-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="07098-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="07098-131">Valid</span></span>|<span data-ttu-id="07098-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="07098-132">ValidationStates</span></span>|<span data-ttu-id="07098-133">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="07098-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="07098-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="07098-134">InvalidFocused</span></span>|<span data-ttu-id="07098-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="07098-135">ValidationStates</span></span>|<span data-ttu-id="07098-136">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, a kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="07098-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="07098-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="07098-137">InvalidUnfocused</span></span>|<span data-ttu-id="07098-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="07098-138">ValidationStates</span></span>|<span data-ttu-id="07098-139">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` i formant nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="07098-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="07098-140">Przykład ControlTemplate przycisku</span><span class="sxs-lookup"><span data-stu-id="07098-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="07098-141">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="07098-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="07098-142">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="07098-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="07098-143">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="07098-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07098-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07098-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="07098-145">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="07098-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="07098-146">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="07098-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="07098-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="07098-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="07098-148">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="07098-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
