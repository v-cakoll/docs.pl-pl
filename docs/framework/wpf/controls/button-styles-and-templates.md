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
ms.openlocfilehash: 64764d43191d30c191c5d6519982b16cfc86d26e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460954"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="cd4bc-102">Style i szablony przycisków</span><span class="sxs-lookup"><span data-stu-id="cd4bc-102">Button Styles and Templates</span></span>
<span data-ttu-id="cd4bc-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="cd4bc-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="cd4bc-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="cd4bc-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="cd4bc-106">Części przycisku</span><span class="sxs-lookup"><span data-stu-id="cd4bc-106">Button Parts</span></span>  
 <span data-ttu-id="cd4bc-107">Formant <xref:System.Windows.Controls.Button> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="cd4bc-108">Stany przycisków</span><span class="sxs-lookup"><span data-stu-id="cd4bc-108">Button States</span></span>  
 <span data-ttu-id="cd4bc-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="cd4bc-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="cd4bc-110">VisualState Name</span></span>|<span data-ttu-id="cd4bc-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="cd4bc-111">VisualStateGroup Name</span></span>|<span data-ttu-id="cd4bc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cd4bc-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="cd4bc-113">Typow</span><span class="sxs-lookup"><span data-stu-id="cd4bc-113">Normal</span></span>|<span data-ttu-id="cd4bc-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd4bc-114">CommonStates</span></span>|<span data-ttu-id="cd4bc-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-115">The default state.</span></span>|  
|<span data-ttu-id="cd4bc-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="cd4bc-116">MouseOver</span></span>|<span data-ttu-id="cd4bc-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd4bc-117">CommonStates</span></span>|<span data-ttu-id="cd4bc-118">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="cd4bc-119">Styczn</span><span class="sxs-lookup"><span data-stu-id="cd4bc-119">Pressed</span></span>|<span data-ttu-id="cd4bc-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd4bc-120">CommonStates</span></span>|<span data-ttu-id="cd4bc-121">Kontrolka zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-121">The control is pressed.</span></span>|  
|<span data-ttu-id="cd4bc-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="cd4bc-122">Disabled</span></span>|<span data-ttu-id="cd4bc-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd4bc-123">CommonStates</span></span>|<span data-ttu-id="cd4bc-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-124">The control is disabled.</span></span>|  
|<span data-ttu-id="cd4bc-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="cd4bc-125">Focused</span></span>|<span data-ttu-id="cd4bc-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cd4bc-126">FocusStates</span></span>|<span data-ttu-id="cd4bc-127">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-127">The control has focus.</span></span>|  
|<span data-ttu-id="cd4bc-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="cd4bc-128">Unfocused</span></span>|<span data-ttu-id="cd4bc-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cd4bc-129">FocusStates</span></span>|<span data-ttu-id="cd4bc-130">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="cd4bc-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="cd4bc-131">Valid</span></span>|<span data-ttu-id="cd4bc-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cd4bc-132">ValidationStates</span></span>|<span data-ttu-id="cd4bc-133">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="cd4bc-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="cd4bc-134">InvalidFocused</span></span>|<span data-ttu-id="cd4bc-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cd4bc-135">ValidationStates</span></span>|<span data-ttu-id="cd4bc-136">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, a kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="cd4bc-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="cd4bc-137">InvalidUnfocused</span></span>|<span data-ttu-id="cd4bc-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cd4bc-138">ValidationStates</span></span>|<span data-ttu-id="cd4bc-139">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` i formant nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="cd4bc-140">Przykład ControlTemplate przycisku</span><span class="sxs-lookup"><span data-stu-id="cd4bc-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="cd4bc-141">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="cd4bc-142">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="cd4bc-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="cd4bc-143">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="cd4bc-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd4bc-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd4bc-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="cd4bc-145">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="cd4bc-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="cd4bc-146">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="cd4bc-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="cd4bc-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="cd4bc-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="cd4bc-148">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="cd4bc-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
