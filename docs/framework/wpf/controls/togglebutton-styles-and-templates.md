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
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805910"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="15f94-102">ToggleButton — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="15f94-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="15f94-103">W tym temacie opisano style <xref:System.Windows.Controls.Primitives.ToggleButton> i szablony formantu.</span><span class="sxs-lookup"><span data-stu-id="15f94-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="15f94-104">Można zmodyfikować <xref:System.Windows.Controls.ControlTemplate> wartość domyślną, aby nadać formancie unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="15f94-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="15f94-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu formantu](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="15f94-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="15f94-106">Część przycisku togglebutton</span><span class="sxs-lookup"><span data-stu-id="15f94-106">ToggleButton Parts</span></span>

<span data-ttu-id="15f94-107">Formant <xref:System.Windows.Controls.Primitives.ToggleButton> nie ma żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="15f94-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="15f94-108">Stany przycisku</span><span class="sxs-lookup"><span data-stu-id="15f94-108">ToggleButton States</span></span>

<span data-ttu-id="15f94-109">W poniższej tabeli wymieniono stany wizualne formantu. <xref:System.Windows.Controls.Primitives.ToggleButton></span><span class="sxs-lookup"><span data-stu-id="15f94-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="15f94-110">Nazwa visualstate</span><span class="sxs-lookup"><span data-stu-id="15f94-110">VisualState Name</span></span>|<span data-ttu-id="15f94-111">Nazwa grupy programu VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="15f94-111">VisualStateGroup Name</span></span>|<span data-ttu-id="15f94-112">Opis</span><span class="sxs-lookup"><span data-stu-id="15f94-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="15f94-113">Normalne</span><span class="sxs-lookup"><span data-stu-id="15f94-113">Normal</span></span>|<span data-ttu-id="15f94-114">CommonStates (CommonStates)</span><span class="sxs-lookup"><span data-stu-id="15f94-114">CommonStates</span></span>|<span data-ttu-id="15f94-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="15f94-115">The default state.</span></span>|
|<span data-ttu-id="15f94-116">Mouseover</span><span class="sxs-lookup"><span data-stu-id="15f94-116">MouseOver</span></span>|<span data-ttu-id="15f94-117">CommonStates (CommonStates)</span><span class="sxs-lookup"><span data-stu-id="15f94-117">CommonStates</span></span>|<span data-ttu-id="15f94-118">Wskaźnik myszy jest umieszczony nad formantem.</span><span class="sxs-lookup"><span data-stu-id="15f94-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="15f94-119">Naciśnięte</span><span class="sxs-lookup"><span data-stu-id="15f94-119">Pressed</span></span>|<span data-ttu-id="15f94-120">CommonStates (CommonStates)</span><span class="sxs-lookup"><span data-stu-id="15f94-120">CommonStates</span></span>|<span data-ttu-id="15f94-121">Formant jest wciśnięty.</span><span class="sxs-lookup"><span data-stu-id="15f94-121">The control is pressed.</span></span>|
|<span data-ttu-id="15f94-122">Disabled (Wyłączony)</span><span class="sxs-lookup"><span data-stu-id="15f94-122">Disabled</span></span>|<span data-ttu-id="15f94-123">CommonStates (CommonStates)</span><span class="sxs-lookup"><span data-stu-id="15f94-123">CommonStates</span></span>|<span data-ttu-id="15f94-124">Formant jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="15f94-124">The control is disabled.</span></span>|
|<span data-ttu-id="15f94-125">Ustawiono fokus</span><span class="sxs-lookup"><span data-stu-id="15f94-125">Focused</span></span>|<span data-ttu-id="15f94-126">FocusStates (Stan ostrości)</span><span class="sxs-lookup"><span data-stu-id="15f94-126">FocusStates</span></span>|<span data-ttu-id="15f94-127">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="15f94-127">The control has focus.</span></span>|
|<span data-ttu-id="15f94-128">Unfocused</span><span class="sxs-lookup"><span data-stu-id="15f94-128">Unfocused</span></span>|<span data-ttu-id="15f94-129">FocusStates (Stan ostrości)</span><span class="sxs-lookup"><span data-stu-id="15f94-129">FocusStates</span></span>|<span data-ttu-id="15f94-130">Formant nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="15f94-130">The control does not have focus.</span></span>|
|<span data-ttu-id="15f94-131">Zaznaczone</span><span class="sxs-lookup"><span data-stu-id="15f94-131">Checked</span></span>|<span data-ttu-id="15f94-132">Sprawdź Państwa</span><span class="sxs-lookup"><span data-stu-id="15f94-132">CheckStates</span></span>|<span data-ttu-id="15f94-133">Parametr <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="15f94-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="15f94-134">Niezaznaczone</span><span class="sxs-lookup"><span data-stu-id="15f94-134">Unchecked</span></span>|<span data-ttu-id="15f94-135">Sprawdź Państwa</span><span class="sxs-lookup"><span data-stu-id="15f94-135">CheckStates</span></span>|<span data-ttu-id="15f94-136">Parametr <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="15f94-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="15f94-137">Nieokreślony</span><span class="sxs-lookup"><span data-stu-id="15f94-137">Indeterminate</span></span>|<span data-ttu-id="15f94-138">Sprawdź Państwa</span><span class="sxs-lookup"><span data-stu-id="15f94-138">CheckStates</span></span>|<span data-ttu-id="15f94-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>jest `true`i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`jest .</span><span class="sxs-lookup"><span data-stu-id="15f94-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="15f94-140">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="15f94-140">Valid</span></span>|<span data-ttu-id="15f94-141">Stan sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="15f94-141">ValidationStates</span></span>|<span data-ttu-id="15f94-142">Formant używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej `false`właściwości jest .</span><span class="sxs-lookup"><span data-stu-id="15f94-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="15f94-143">Nieprawidłowo skupiony</span><span class="sxs-lookup"><span data-stu-id="15f94-143">InvalidFocused</span></span>|<span data-ttu-id="15f94-144">Stan sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="15f94-144">ValidationStates</span></span>|<span data-ttu-id="15f94-145">Dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> właściwość `true` jest i formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="15f94-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|
|<span data-ttu-id="15f94-146">Nieprawidłowy Nieskoncentrowany</span><span class="sxs-lookup"><span data-stu-id="15f94-146">InvalidUnfocused</span></span>|<span data-ttu-id="15f94-147">Stan sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="15f94-147">ValidationStates</span></span>|<span data-ttu-id="15f94-148">Dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> właściwość `true` jest i formant nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="15f94-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="15f94-149">Jeśli nieokreślony stan wizualny nie istnieje w szablonie formantu, stan wizualizacji niezaznaczone będzie używany jako domyślny stan wizualny.</span><span class="sxs-lookup"><span data-stu-id="15f94-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="15f94-150">Przykład panelu sterowania przyciskiem przełączania</span><span class="sxs-lookup"><span data-stu-id="15f94-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="15f94-151">W poniższym <xref:System.Windows.Controls.ControlTemplate> przykładzie pokazano, <xref:System.Windows.Controls.Primitives.ToggleButton> jak zdefiniować formantu.</span><span class="sxs-lookup"><span data-stu-id="15f94-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="15f94-152">W poprzednim przykładzie użyto co najmniej jednego z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="15f94-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="15f94-153">Aby uzyskać pełną próbkę, zobacz [Stylowanie za pomocą próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="15f94-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="15f94-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15f94-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="15f94-155">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="15f94-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="15f94-156">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="15f94-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="15f94-157">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="15f94-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="15f94-158">Tworzenie szablonu formantu</span><span class="sxs-lookup"><span data-stu-id="15f94-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
