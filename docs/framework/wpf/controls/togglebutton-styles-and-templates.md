---
title: ToggleButton — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: a4c449a561017659db7f54fd3cdb8964742650de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283674"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="25b8c-102">ToggleButton — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="25b8c-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="25b8c-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="25b8c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="25b8c-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="25b8c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="25b8c-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="25b8c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="25b8c-106">ToggleButton części</span><span class="sxs-lookup"><span data-stu-id="25b8c-106">ToggleButton Parts</span></span>

<span data-ttu-id="25b8c-107">Formant <xref:System.Windows.Controls.Primitives.ToggleButton> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="25b8c-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="25b8c-108">Stany ToggleButton</span><span class="sxs-lookup"><span data-stu-id="25b8c-108">ToggleButton States</span></span>

<span data-ttu-id="25b8c-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="25b8c-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="25b8c-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="25b8c-110">VisualState Name</span></span>|<span data-ttu-id="25b8c-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="25b8c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="25b8c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="25b8c-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="25b8c-113">Normalne</span><span class="sxs-lookup"><span data-stu-id="25b8c-113">Normal</span></span>|<span data-ttu-id="25b8c-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-114">CommonStates</span></span>|<span data-ttu-id="25b8c-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="25b8c-115">The default state.</span></span>|
|<span data-ttu-id="25b8c-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="25b8c-116">MouseOver</span></span>|<span data-ttu-id="25b8c-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-117">CommonStates</span></span>|<span data-ttu-id="25b8c-118">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="25b8c-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="25b8c-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="25b8c-119">Pressed</span></span>|<span data-ttu-id="25b8c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-120">CommonStates</span></span>|<span data-ttu-id="25b8c-121">Kontrolka zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="25b8c-121">The control is pressed.</span></span>|
|<span data-ttu-id="25b8c-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="25b8c-122">Disabled</span></span>|<span data-ttu-id="25b8c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-123">CommonStates</span></span>|<span data-ttu-id="25b8c-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="25b8c-124">The control is disabled.</span></span>|
|<span data-ttu-id="25b8c-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="25b8c-125">Focused</span></span>|<span data-ttu-id="25b8c-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-126">FocusStates</span></span>|<span data-ttu-id="25b8c-127">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="25b8c-127">The control has focus.</span></span>|
|<span data-ttu-id="25b8c-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="25b8c-128">Unfocused</span></span>|<span data-ttu-id="25b8c-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-129">FocusStates</span></span>|<span data-ttu-id="25b8c-130">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="25b8c-130">The control does not have focus.</span></span>|
|<span data-ttu-id="25b8c-131">Zaznaczone</span><span class="sxs-lookup"><span data-stu-id="25b8c-131">Checked</span></span>|<span data-ttu-id="25b8c-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-132">CheckStates</span></span>|<span data-ttu-id="25b8c-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="25b8c-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="25b8c-134">Unchecked</span><span class="sxs-lookup"><span data-stu-id="25b8c-134">Unchecked</span></span>|<span data-ttu-id="25b8c-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-135">CheckStates</span></span>|<span data-ttu-id="25b8c-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="25b8c-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="25b8c-137">Nieokreślony</span><span class="sxs-lookup"><span data-stu-id="25b8c-137">Indeterminate</span></span>|<span data-ttu-id="25b8c-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-138">CheckStates</span></span>|<span data-ttu-id="25b8c-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> jest `true`, a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`.</span><span class="sxs-lookup"><span data-stu-id="25b8c-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="25b8c-140">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="25b8c-140">Valid</span></span>|<span data-ttu-id="25b8c-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-141">ValidationStates</span></span>|<span data-ttu-id="25b8c-142">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="25b8c-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="25b8c-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="25b8c-143">InvalidFocused</span></span>|<span data-ttu-id="25b8c-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-144">ValidationStates</span></span>|<span data-ttu-id="25b8c-145">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="25b8c-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="25b8c-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="25b8c-146">InvalidUnfocused</span></span>|<span data-ttu-id="25b8c-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="25b8c-147">ValidationStates</span></span>|<span data-ttu-id="25b8c-148">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="25b8c-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="25b8c-149">Jeśli nieokreślony stan wizualny nie istnieje w szablonie kontrolki, wówczas niesprawdzony stan wizualizacji będzie używany jako domyślny stan wizualny.</span><span class="sxs-lookup"><span data-stu-id="25b8c-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="25b8c-150">Przykład ToggleButton ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="25b8c-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="25b8c-151">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="25b8c-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="25b8c-152">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="25b8c-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="25b8c-153">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="25b8c-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="25b8c-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25b8c-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="25b8c-155">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="25b8c-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="25b8c-156">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="25b8c-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="25b8c-157">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="25b8c-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="25b8c-158">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="25b8c-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
