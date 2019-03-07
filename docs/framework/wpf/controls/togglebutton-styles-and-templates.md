---
title: ToggleButton — style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: 46fd7d07c3904ee752ae3f467f65af4b0c031c84
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57507293"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="2ca67-102">ToggleButton — style i szablony</span><span class="sxs-lookup"><span data-stu-id="2ca67-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="2ca67-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Primitives.ToggleButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2ca67-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="2ca67-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2ca67-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2ca67-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2ca67-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="2ca67-106">ToggleButton części</span><span class="sxs-lookup"><span data-stu-id="2ca67-106">ToggleButton Parts</span></span>

<span data-ttu-id="2ca67-107"><xref:System.Windows.Controls.Primitives.ToggleButton> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="2ca67-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="2ca67-108">Stany ToggleButton</span><span class="sxs-lookup"><span data-stu-id="2ca67-108">ToggleButton States</span></span>

<span data-ttu-id="2ca67-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.ToggleButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2ca67-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="2ca67-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="2ca67-110">VisualState Name</span></span>|<span data-ttu-id="2ca67-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2ca67-111">VisualStateGroup Name</span></span>|<span data-ttu-id="2ca67-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2ca67-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="2ca67-113">Normalne</span><span class="sxs-lookup"><span data-stu-id="2ca67-113">Normal</span></span>|<span data-ttu-id="2ca67-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-114">CommonStates</span></span>|<span data-ttu-id="2ca67-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="2ca67-115">The default state.</span></span>|
|<span data-ttu-id="2ca67-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="2ca67-116">MouseOver</span></span>|<span data-ttu-id="2ca67-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-117">CommonStates</span></span>|<span data-ttu-id="2ca67-118">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="2ca67-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="2ca67-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="2ca67-119">Pressed</span></span>|<span data-ttu-id="2ca67-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-120">CommonStates</span></span>|<span data-ttu-id="2ca67-121">Użytkownik naciśnie kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="2ca67-121">The control is pressed.</span></span>|
|<span data-ttu-id="2ca67-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="2ca67-122">Disabled</span></span>|<span data-ttu-id="2ca67-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-123">CommonStates</span></span>|<span data-ttu-id="2ca67-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="2ca67-124">The control is disabled.</span></span>|
|<span data-ttu-id="2ca67-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="2ca67-125">Focused</span></span>|<span data-ttu-id="2ca67-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-126">FocusStates</span></span>|<span data-ttu-id="2ca67-127">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="2ca67-127">The control has focus.</span></span>|
|<span data-ttu-id="2ca67-128">Po przeniesieniu fokusu</span><span class="sxs-lookup"><span data-stu-id="2ca67-128">Unfocused</span></span>|<span data-ttu-id="2ca67-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-129">FocusStates</span></span>|<span data-ttu-id="2ca67-130">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="2ca67-130">The control does not have focus.</span></span>|
|<span data-ttu-id="2ca67-131">Zaznaczone</span><span class="sxs-lookup"><span data-stu-id="2ca67-131">Checked</span></span>|<span data-ttu-id="2ca67-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-132">CheckStates</span></span>|<span data-ttu-id="2ca67-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="2ca67-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="2ca67-134">Niezaznaczone</span><span class="sxs-lookup"><span data-stu-id="2ca67-134">Unchecked</span></span>|<span data-ttu-id="2ca67-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-135">CheckStates</span></span>|<span data-ttu-id="2ca67-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="2ca67-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="2ca67-137">Nieokreślony</span><span class="sxs-lookup"><span data-stu-id="2ca67-137">Indeterminate</span></span>|<span data-ttu-id="2ca67-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-138">CheckStates</span></span>|<span data-ttu-id="2ca67-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> jest `true`, i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `null`.</span><span class="sxs-lookup"><span data-stu-id="2ca67-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="2ca67-140">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="2ca67-140">Valid</span></span>|<span data-ttu-id="2ca67-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-141">ValidationStates</span></span>|<span data-ttu-id="2ca67-142">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="2ca67-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="2ca67-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2ca67-143">InvalidFocused</span></span>|<span data-ttu-id="2ca67-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-144">ValidationStates</span></span>|<span data-ttu-id="2ca67-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="2ca67-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="2ca67-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2ca67-146">InvalidUnfocused</span></span>|<span data-ttu-id="2ca67-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2ca67-147">ValidationStates</span></span>|<span data-ttu-id="2ca67-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="2ca67-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="2ca67-149">Jeśli nieokreślony stan wizualny nie istnieje w szablonie kontrolki, następnie nieoznaczonego stanu wizualnego będzie służyć jako domyślnego stanu wizualnego.</span><span class="sxs-lookup"><span data-stu-id="2ca67-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="2ca67-150">Przykład ControlTemplate ToggleButton</span><span class="sxs-lookup"><span data-stu-id="2ca67-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="2ca67-151">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.ToggleButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2ca67-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="2ca67-152">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="2ca67-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="2ca67-153">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2ca67-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ca67-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ca67-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2ca67-155">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="2ca67-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2ca67-156">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="2ca67-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2ca67-157">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="2ca67-157">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="2ca67-158">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="2ca67-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
