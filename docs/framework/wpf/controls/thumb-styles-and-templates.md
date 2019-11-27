---
title: Style i szablony miniatury
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: 0d0d88e3b527beacfa5f879027e696aa75b18147
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283681"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="d2456-102">Style i szablony miniatury</span><span class="sxs-lookup"><span data-stu-id="d2456-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="d2456-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="d2456-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="d2456-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="d2456-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d2456-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="d2456-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="d2456-106">Części kciuka</span><span class="sxs-lookup"><span data-stu-id="d2456-106">Thumb Parts</span></span>

<span data-ttu-id="d2456-107">Formant <xref:System.Windows.Controls.Primitives.Thumb> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="d2456-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="d2456-108">Stany kciuka</span><span class="sxs-lookup"><span data-stu-id="d2456-108">Thumb States</span></span>

<span data-ttu-id="d2456-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="d2456-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="d2456-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="d2456-110">VisualState Name</span></span>|<span data-ttu-id="d2456-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d2456-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d2456-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d2456-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="d2456-113">Normalne</span><span class="sxs-lookup"><span data-stu-id="d2456-113">Normal</span></span>|<span data-ttu-id="d2456-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d2456-114">CommonStates</span></span>|<span data-ttu-id="d2456-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="d2456-115">The default state.</span></span>|
|<span data-ttu-id="d2456-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="d2456-116">MouseOver</span></span>|<span data-ttu-id="d2456-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d2456-117">CommonStates</span></span>|<span data-ttu-id="d2456-118">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="d2456-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="d2456-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="d2456-119">Pressed</span></span>|<span data-ttu-id="d2456-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d2456-120">CommonStates</span></span>|<span data-ttu-id="d2456-121">Kontrolka zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="d2456-121">The control is pressed.</span></span>|
|<span data-ttu-id="d2456-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="d2456-122">Disabled</span></span>|<span data-ttu-id="d2456-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d2456-123">CommonStates</span></span>|<span data-ttu-id="d2456-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="d2456-124">The control is disabled.</span></span>|
|<span data-ttu-id="d2456-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="d2456-125">Focused</span></span>|<span data-ttu-id="d2456-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d2456-126">FocusStates</span></span>|<span data-ttu-id="d2456-127">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="d2456-127">The control has focus.</span></span>|
|<span data-ttu-id="d2456-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="d2456-128">Unfocused</span></span>|<span data-ttu-id="d2456-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d2456-129">FocusStates</span></span>|<span data-ttu-id="d2456-130">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="d2456-130">The control does not have focus.</span></span>|
|<span data-ttu-id="d2456-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="d2456-131">Valid</span></span>|<span data-ttu-id="d2456-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2456-132">ValidationStates</span></span>|<span data-ttu-id="d2456-133">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="d2456-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="d2456-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d2456-134">InvalidFocused</span></span>|<span data-ttu-id="d2456-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2456-135">ValidationStates</span></span>|<span data-ttu-id="d2456-136">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="d2456-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="d2456-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d2456-137">InvalidUnfocused</span></span>|<span data-ttu-id="d2456-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2456-138">ValidationStates</span></span>|<span data-ttu-id="d2456-139">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="d2456-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="d2456-140">Przykład ControlTemplate kciuka</span><span class="sxs-lookup"><span data-stu-id="d2456-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="d2456-141">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="d2456-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="d2456-142">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="d2456-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="d2456-143">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d2456-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2456-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2456-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d2456-145">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="d2456-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d2456-146">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="d2456-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d2456-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="d2456-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="d2456-148">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="d2456-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
