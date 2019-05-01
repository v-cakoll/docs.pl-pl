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
ms.openlocfilehash: 86f212326bc707e4b07b8cab8d9a95d4f6ef8920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053319"
---
# <a name="repeatbutton-styles-and-templates"></a><span data-ttu-id="d47c6-102">RepeatButton — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="d47c6-102">RepeatButton Styles and Templates</span></span>

<span data-ttu-id="d47c6-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Primitives.RepeatButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d47c6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="d47c6-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d47c6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d47c6-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d47c6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="repeatbutton-parts"></a><span data-ttu-id="d47c6-106">RepeatButton części</span><span class="sxs-lookup"><span data-stu-id="d47c6-106">RepeatButton Parts</span></span>

<span data-ttu-id="d47c6-107"><xref:System.Windows.Controls.Primitives.RepeatButton> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="d47c6-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>

## <a name="repeatbutton-states"></a><span data-ttu-id="d47c6-108">RepeatButton stanów</span><span class="sxs-lookup"><span data-stu-id="d47c6-108">RepeatButton States</span></span>

<span data-ttu-id="d47c6-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.RepeatButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d47c6-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

|<span data-ttu-id="d47c6-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="d47c6-110">VisualState Name</span></span>|<span data-ttu-id="d47c6-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d47c6-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d47c6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d47c6-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="d47c6-113">Normalne</span><span class="sxs-lookup"><span data-stu-id="d47c6-113">Normal</span></span>|<span data-ttu-id="d47c6-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d47c6-114">CommonStates</span></span>|<span data-ttu-id="d47c6-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="d47c6-115">The default state.</span></span>|
|<span data-ttu-id="d47c6-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="d47c6-116">MouseOver</span></span>|<span data-ttu-id="d47c6-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d47c6-117">CommonStates</span></span>|<span data-ttu-id="d47c6-118">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="d47c6-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="d47c6-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="d47c6-119">Pressed</span></span>|<span data-ttu-id="d47c6-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d47c6-120">CommonStates</span></span>|<span data-ttu-id="d47c6-121">Użytkownik naciśnie kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="d47c6-121">The control is pressed.</span></span>|
|<span data-ttu-id="d47c6-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="d47c6-122">Disabled</span></span>|<span data-ttu-id="d47c6-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d47c6-123">CommonStates</span></span>|<span data-ttu-id="d47c6-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="d47c6-124">The control is disabled.</span></span>|
|<span data-ttu-id="d47c6-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="d47c6-125">Focused</span></span>|<span data-ttu-id="d47c6-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d47c6-126">FocusStates</span></span>|<span data-ttu-id="d47c6-127">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="d47c6-127">The control has focus.</span></span>|
|<span data-ttu-id="d47c6-128">Po przeniesieniu fokusu</span><span class="sxs-lookup"><span data-stu-id="d47c6-128">Unfocused</span></span>|<span data-ttu-id="d47c6-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d47c6-129">FocusStates</span></span>|<span data-ttu-id="d47c6-130">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="d47c6-130">The control does not have focus.</span></span>|
|<span data-ttu-id="d47c6-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="d47c6-131">Valid</span></span>|<span data-ttu-id="d47c6-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d47c6-132">ValidationStates</span></span>|<span data-ttu-id="d47c6-133">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="d47c6-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="d47c6-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d47c6-134">InvalidFocused</span></span>|<span data-ttu-id="d47c6-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d47c6-135">ValidationStates</span></span>|<span data-ttu-id="d47c6-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="d47c6-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="d47c6-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d47c6-137">InvalidUnfocused</span></span>|<span data-ttu-id="d47c6-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d47c6-138">ValidationStates</span></span>|<span data-ttu-id="d47c6-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="d47c6-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="d47c6-140">Przykład ControlTemplate RepeatButton</span><span class="sxs-lookup"><span data-stu-id="d47c6-140">RepeatButton ControlTemplate Example</span></span>

<span data-ttu-id="d47c6-141">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.RepeatButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d47c6-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

<span data-ttu-id="d47c6-142">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="d47c6-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="d47c6-143">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d47c6-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="d47c6-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d47c6-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d47c6-145">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="d47c6-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d47c6-146">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="d47c6-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d47c6-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="d47c6-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="d47c6-148">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d47c6-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
