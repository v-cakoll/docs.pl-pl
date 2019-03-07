---
title: PasswordBox — style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 7783330dd56ec5b2759e783a6935761eb3587978
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57507299"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="25689-102">PasswordBox — style i szablony</span><span class="sxs-lookup"><span data-stu-id="25689-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="25689-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.PasswordBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="25689-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="25689-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="25689-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="25689-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="25689-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="25689-106">Części PasswordBox</span><span class="sxs-lookup"><span data-stu-id="25689-106">PasswordBox Parts</span></span>

<span data-ttu-id="25689-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.PasswordBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="25689-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="25689-108">Część</span><span class="sxs-lookup"><span data-stu-id="25689-108">Part</span></span>|<span data-ttu-id="25689-109">Typ</span><span class="sxs-lookup"><span data-stu-id="25689-109">Type</span></span>|<span data-ttu-id="25689-110">Opis</span><span class="sxs-lookup"><span data-stu-id="25689-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="25689-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="25689-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="25689-112">Element wizualny, który może zawierać <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="25689-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="25689-113">Tekst <xref:System.Windows.Controls.PasswordBox> jest wyświetlana w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="25689-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="25689-114">Stany PasswordBox</span><span class="sxs-lookup"><span data-stu-id="25689-114">PasswordBox States</span></span>

<span data-ttu-id="25689-115">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.PasswordBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="25689-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="25689-116">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="25689-116">VisualState Name</span></span>|<span data-ttu-id="25689-117">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="25689-117">VisualStateGroup Name</span></span>|<span data-ttu-id="25689-118">Opis</span><span class="sxs-lookup"><span data-stu-id="25689-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="25689-119">Normalne</span><span class="sxs-lookup"><span data-stu-id="25689-119">Normal</span></span>|<span data-ttu-id="25689-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="25689-120">CommonStates</span></span>|<span data-ttu-id="25689-121">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="25689-121">The default state.</span></span>|
|<span data-ttu-id="25689-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="25689-122">MouseOver</span></span>|<span data-ttu-id="25689-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="25689-123">CommonStates</span></span>|<span data-ttu-id="25689-124">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="25689-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="25689-125">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="25689-125">Disabled</span></span>|<span data-ttu-id="25689-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="25689-126">CommonStates</span></span>|<span data-ttu-id="25689-127">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="25689-127">The control is disabled.</span></span>|
|<span data-ttu-id="25689-128">Fokus</span><span class="sxs-lookup"><span data-stu-id="25689-128">Focused</span></span>|<span data-ttu-id="25689-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="25689-129">FocusStates</span></span>|<span data-ttu-id="25689-130">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="25689-130">The control has focus.</span></span>|
|<span data-ttu-id="25689-131">Po przeniesieniu fokusu</span><span class="sxs-lookup"><span data-stu-id="25689-131">Unfocused</span></span>|<span data-ttu-id="25689-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="25689-132">FocusStates</span></span>|<span data-ttu-id="25689-133">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="25689-133">The control does not have focus.</span></span>|
|<span data-ttu-id="25689-134">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="25689-134">Valid</span></span>|<span data-ttu-id="25689-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="25689-135">ValidationStates</span></span>|<span data-ttu-id="25689-136">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="25689-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="25689-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="25689-137">InvalidFocused</span></span>|<span data-ttu-id="25689-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="25689-138">ValidationStates</span></span>|<span data-ttu-id="25689-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="25689-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="25689-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="25689-140">InvalidUnfocused</span></span>|<span data-ttu-id="25689-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="25689-141">ValidationStates</span></span>|<span data-ttu-id="25689-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="25689-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="25689-143">Przykład ControlTemplate PasswordBox</span><span class="sxs-lookup"><span data-stu-id="25689-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="25689-144">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.PasswordBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="25689-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="25689-145">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="25689-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="25689-146">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="25689-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="25689-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25689-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="25689-148">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="25689-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="25689-149">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="25689-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="25689-150">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="25689-150">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="25689-151">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="25689-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
