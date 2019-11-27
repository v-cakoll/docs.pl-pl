---
title: RepeatButton — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 8585e98536fd908daa11f21da395cab44924d612
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283427"
---
# <a name="repeatbutton-styles-and-templates"></a><span data-ttu-id="7a7e0-102">RepeatButton — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="7a7e0-102">RepeatButton Styles and Templates</span></span>

<span data-ttu-id="7a7e0-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="7a7e0-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7a7e0-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="7a7e0-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="repeatbutton-parts"></a><span data-ttu-id="7a7e0-106">RepeatButton części</span><span class="sxs-lookup"><span data-stu-id="7a7e0-106">RepeatButton Parts</span></span>

<span data-ttu-id="7a7e0-107">Formant <xref:System.Windows.Controls.Primitives.RepeatButton> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>

## <a name="repeatbutton-states"></a><span data-ttu-id="7a7e0-108">Stany RepeatButton</span><span class="sxs-lookup"><span data-stu-id="7a7e0-108">RepeatButton States</span></span>

<span data-ttu-id="7a7e0-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

|<span data-ttu-id="7a7e0-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="7a7e0-110">VisualState Name</span></span>|<span data-ttu-id="7a7e0-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7a7e0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7a7e0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7a7e0-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="7a7e0-113">Normalne</span><span class="sxs-lookup"><span data-stu-id="7a7e0-113">Normal</span></span>|<span data-ttu-id="7a7e0-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a7e0-114">CommonStates</span></span>|<span data-ttu-id="7a7e0-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-115">The default state.</span></span>|
|<span data-ttu-id="7a7e0-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="7a7e0-116">MouseOver</span></span>|<span data-ttu-id="7a7e0-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a7e0-117">CommonStates</span></span>|<span data-ttu-id="7a7e0-118">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="7a7e0-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="7a7e0-119">Pressed</span></span>|<span data-ttu-id="7a7e0-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a7e0-120">CommonStates</span></span>|<span data-ttu-id="7a7e0-121">Kontrolka zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-121">The control is pressed.</span></span>|
|<span data-ttu-id="7a7e0-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="7a7e0-122">Disabled</span></span>|<span data-ttu-id="7a7e0-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a7e0-123">CommonStates</span></span>|<span data-ttu-id="7a7e0-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-124">The control is disabled.</span></span>|
|<span data-ttu-id="7a7e0-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="7a7e0-125">Focused</span></span>|<span data-ttu-id="7a7e0-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7a7e0-126">FocusStates</span></span>|<span data-ttu-id="7a7e0-127">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-127">The control has focus.</span></span>|
|<span data-ttu-id="7a7e0-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="7a7e0-128">Unfocused</span></span>|<span data-ttu-id="7a7e0-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7a7e0-129">FocusStates</span></span>|<span data-ttu-id="7a7e0-130">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-130">The control does not have focus.</span></span>|
|<span data-ttu-id="7a7e0-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="7a7e0-131">Valid</span></span>|<span data-ttu-id="7a7e0-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a7e0-132">ValidationStates</span></span>|<span data-ttu-id="7a7e0-133">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="7a7e0-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7a7e0-134">InvalidFocused</span></span>|<span data-ttu-id="7a7e0-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a7e0-135">ValidationStates</span></span>|<span data-ttu-id="7a7e0-136">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="7a7e0-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7a7e0-137">InvalidUnfocused</span></span>|<span data-ttu-id="7a7e0-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a7e0-138">ValidationStates</span></span>|<span data-ttu-id="7a7e0-139">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="7a7e0-140">Przykład RepeatButton ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7a7e0-140">RepeatButton ControlTemplate Example</span></span>

<span data-ttu-id="7a7e0-141">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

<span data-ttu-id="7a7e0-142">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7a7e0-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="7a7e0-143">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="7a7e0-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a7e0-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a7e0-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7a7e0-145">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="7a7e0-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="7a7e0-146">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="7a7e0-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="7a7e0-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="7a7e0-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7a7e0-148">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="7a7e0-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
