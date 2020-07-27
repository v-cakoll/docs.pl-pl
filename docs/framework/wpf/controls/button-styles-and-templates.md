---
title: Style i szablony przycisków
description: Dowiedz się więcej na temat stylów i szablonów dla kontrolki przycisku Windows Presentation Foundation. Zmodyfikuj ControlTemplate, aby nadać formantowi unikatowy wygląd.
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 11509adeef397f26eb040e6e98d0edb333b2515f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166259"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="a30af-104">Style i szablony przycisków</span><span class="sxs-lookup"><span data-stu-id="a30af-104">Button Styles and Templates</span></span>
<span data-ttu-id="a30af-105">W tym temacie opisano style i szablony dla <xref:System.Windows.Controls.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a30af-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="a30af-106">Można zmienić wartość domyślną, <xref:System.Windows.Controls.ControlTemplate> aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="a30af-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a30af-107">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="a30af-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="a30af-108">Części przycisku</span><span class="sxs-lookup"><span data-stu-id="a30af-108">Button Parts</span></span>  
 <span data-ttu-id="a30af-109"><xref:System.Windows.Controls.Button>Kontrolka nie ma żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="a30af-109">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="a30af-110">Stany przycisków</span><span class="sxs-lookup"><span data-stu-id="a30af-110">Button States</span></span>  
 <span data-ttu-id="a30af-111">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a30af-111">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="a30af-112">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="a30af-112">VisualState Name</span></span>|<span data-ttu-id="a30af-113">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a30af-113">VisualStateGroup Name</span></span>|<span data-ttu-id="a30af-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a30af-114">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a30af-115">Normalne</span><span class="sxs-lookup"><span data-stu-id="a30af-115">Normal</span></span>|<span data-ttu-id="a30af-116">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a30af-116">CommonStates</span></span>|<span data-ttu-id="a30af-117">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="a30af-117">The default state.</span></span>|  
|<span data-ttu-id="a30af-118">MouseOver</span><span class="sxs-lookup"><span data-stu-id="a30af-118">MouseOver</span></span>|<span data-ttu-id="a30af-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a30af-119">CommonStates</span></span>|<span data-ttu-id="a30af-120">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="a30af-120">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="a30af-121">Naciśnięte</span><span class="sxs-lookup"><span data-stu-id="a30af-121">Pressed</span></span>|<span data-ttu-id="a30af-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a30af-122">CommonStates</span></span>|<span data-ttu-id="a30af-123">Kontrolka zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="a30af-123">The control is pressed.</span></span>|  
|<span data-ttu-id="a30af-124">Disabled</span><span class="sxs-lookup"><span data-stu-id="a30af-124">Disabled</span></span>|<span data-ttu-id="a30af-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a30af-125">CommonStates</span></span>|<span data-ttu-id="a30af-126">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="a30af-126">The control is disabled.</span></span>|  
|<span data-ttu-id="a30af-127">Ustawiono fokus</span><span class="sxs-lookup"><span data-stu-id="a30af-127">Focused</span></span>|<span data-ttu-id="a30af-128">FocusStates</span><span class="sxs-lookup"><span data-stu-id="a30af-128">FocusStates</span></span>|<span data-ttu-id="a30af-129">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="a30af-129">The control has focus.</span></span>|  
|<span data-ttu-id="a30af-130">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="a30af-130">Unfocused</span></span>|<span data-ttu-id="a30af-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="a30af-131">FocusStates</span></span>|<span data-ttu-id="a30af-132">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="a30af-132">The control does not have focus.</span></span>|  
|<span data-ttu-id="a30af-133">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="a30af-133">Valid</span></span>|<span data-ttu-id="a30af-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a30af-134">ValidationStates</span></span>|<span data-ttu-id="a30af-135">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości to `false` .</span><span class="sxs-lookup"><span data-stu-id="a30af-135">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a30af-136">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a30af-136">InvalidFocused</span></span>|<span data-ttu-id="a30af-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a30af-137">ValidationStates</span></span>|<span data-ttu-id="a30af-138"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość jest `true` i ma fokus.</span><span class="sxs-lookup"><span data-stu-id="a30af-138">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="a30af-139">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a30af-139">InvalidUnfocused</span></span>|<span data-ttu-id="a30af-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a30af-140">ValidationStates</span></span>|<span data-ttu-id="a30af-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość jest `true` i formant nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="a30af-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="a30af-142">Przykład ControlTemplate przycisku</span><span class="sxs-lookup"><span data-stu-id="a30af-142">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="a30af-143">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a30af-143">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="a30af-144">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="a30af-144">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a30af-145">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="a30af-145">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30af-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a30af-146">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="a30af-147">Style i szablony formantu</span><span class="sxs-lookup"><span data-stu-id="a30af-147">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="a30af-148">Niestandardowe dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="a30af-148">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="a30af-149">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="a30af-149">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="a30af-150">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="a30af-150">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
