---
title: Thumb — style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: b7fc595f0c592d42f118c6b5542edf93716c2fca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57507311"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="39794-102">Thumb — style i szablony</span><span class="sxs-lookup"><span data-stu-id="39794-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="39794-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Primitives.Thumb> kontroli.</span><span class="sxs-lookup"><span data-stu-id="39794-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="39794-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="39794-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="39794-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="39794-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="39794-106">Części Thumb</span><span class="sxs-lookup"><span data-stu-id="39794-106">Thumb Parts</span></span>

<span data-ttu-id="39794-107"><xref:System.Windows.Controls.Primitives.Thumb> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="39794-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="39794-108">Stany przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="39794-108">Thumb States</span></span>

<span data-ttu-id="39794-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.Thumb> kontroli.</span><span class="sxs-lookup"><span data-stu-id="39794-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="39794-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="39794-110">VisualState Name</span></span>|<span data-ttu-id="39794-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="39794-111">VisualStateGroup Name</span></span>|<span data-ttu-id="39794-112">Opis</span><span class="sxs-lookup"><span data-stu-id="39794-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="39794-113">Normalne</span><span class="sxs-lookup"><span data-stu-id="39794-113">Normal</span></span>|<span data-ttu-id="39794-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="39794-114">CommonStates</span></span>|<span data-ttu-id="39794-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="39794-115">The default state.</span></span>|
|<span data-ttu-id="39794-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="39794-116">MouseOver</span></span>|<span data-ttu-id="39794-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="39794-117">CommonStates</span></span>|<span data-ttu-id="39794-118">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="39794-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="39794-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="39794-119">Pressed</span></span>|<span data-ttu-id="39794-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="39794-120">CommonStates</span></span>|<span data-ttu-id="39794-121">Użytkownik naciśnie kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="39794-121">The control is pressed.</span></span>|
|<span data-ttu-id="39794-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="39794-122">Disabled</span></span>|<span data-ttu-id="39794-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="39794-123">CommonStates</span></span>|<span data-ttu-id="39794-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="39794-124">The control is disabled.</span></span>|
|<span data-ttu-id="39794-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="39794-125">Focused</span></span>|<span data-ttu-id="39794-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="39794-126">FocusStates</span></span>|<span data-ttu-id="39794-127">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="39794-127">The control has focus.</span></span>|
|<span data-ttu-id="39794-128">Po przeniesieniu fokusu</span><span class="sxs-lookup"><span data-stu-id="39794-128">Unfocused</span></span>|<span data-ttu-id="39794-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="39794-129">FocusStates</span></span>|<span data-ttu-id="39794-130">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="39794-130">The control does not have focus.</span></span>|
|<span data-ttu-id="39794-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="39794-131">Valid</span></span>|<span data-ttu-id="39794-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="39794-132">ValidationStates</span></span>|<span data-ttu-id="39794-133">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="39794-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="39794-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="39794-134">InvalidFocused</span></span>|<span data-ttu-id="39794-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="39794-135">ValidationStates</span></span>|<span data-ttu-id="39794-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="39794-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="39794-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="39794-137">InvalidUnfocused</span></span>|<span data-ttu-id="39794-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="39794-138">ValidationStates</span></span>|<span data-ttu-id="39794-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="39794-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="39794-140">Przykład ControlTemplate Thumb</span><span class="sxs-lookup"><span data-stu-id="39794-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="39794-141">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.Thumb> kontroli.</span><span class="sxs-lookup"><span data-stu-id="39794-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="39794-142">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="39794-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="39794-143">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="39794-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="39794-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39794-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="39794-145">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="39794-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="39794-146">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="39794-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="39794-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="39794-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="39794-148">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="39794-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
