---
title: TextBox — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: c04c1386f4663f5893915a07a1e0896a69c5412a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663677"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="f116e-102">TextBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="f116e-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="f116e-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f116e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="f116e-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f116e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f116e-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f116e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="f116e-106">Części pola tekstowego</span><span class="sxs-lookup"><span data-stu-id="f116e-106">TextBox Parts</span></span>  
 <span data-ttu-id="f116e-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f116e-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="f116e-108">Część</span><span class="sxs-lookup"><span data-stu-id="f116e-108">Part</span></span>|<span data-ttu-id="f116e-109">Typ</span><span class="sxs-lookup"><span data-stu-id="f116e-109">Type</span></span>|<span data-ttu-id="f116e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f116e-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f116e-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="f116e-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="f116e-112">Element wizualny, który może zawierać <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="f116e-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="f116e-113">Tekst <xref:System.Windows.Controls.TextBox> jest wyświetlana w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="f116e-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="f116e-114">Stany TextBox</span><span class="sxs-lookup"><span data-stu-id="f116e-114">TextBox States</span></span>  
 <span data-ttu-id="f116e-115">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f116e-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="f116e-116">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="f116e-116">VisualState Name</span></span>|<span data-ttu-id="f116e-117">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f116e-117">VisualStateGroup Name</span></span>|<span data-ttu-id="f116e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f116e-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f116e-119">Normalne</span><span class="sxs-lookup"><span data-stu-id="f116e-119">Normal</span></span>|<span data-ttu-id="f116e-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f116e-120">CommonStates</span></span>|<span data-ttu-id="f116e-121">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="f116e-121">The default state.</span></span>|  
|<span data-ttu-id="f116e-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f116e-122">MouseOver</span></span>|<span data-ttu-id="f116e-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f116e-123">CommonStates</span></span>|<span data-ttu-id="f116e-124">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="f116e-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f116e-125">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="f116e-125">Disabled</span></span>|<span data-ttu-id="f116e-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f116e-126">CommonStates</span></span>|<span data-ttu-id="f116e-127">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="f116e-127">The control is disabled.</span></span>|  
|<span data-ttu-id="f116e-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="f116e-128">ReadOnly</span></span>|<span data-ttu-id="f116e-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f116e-129">CommonStates</span></span>|<span data-ttu-id="f116e-130">Użytkownik nie może zmieniać tekst w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f116e-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="f116e-131">Fokus</span><span class="sxs-lookup"><span data-stu-id="f116e-131">Focused</span></span>|<span data-ttu-id="f116e-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f116e-132">FocusStates</span></span>|<span data-ttu-id="f116e-133">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="f116e-133">The control has focus.</span></span>|  
|<span data-ttu-id="f116e-134">Po przeniesieniu fokusu</span><span class="sxs-lookup"><span data-stu-id="f116e-134">Unfocused</span></span>|<span data-ttu-id="f116e-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f116e-135">FocusStates</span></span>|<span data-ttu-id="f116e-136">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="f116e-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="f116e-137">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="f116e-137">Valid</span></span>|<span data-ttu-id="f116e-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f116e-138">ValidationStates</span></span>|<span data-ttu-id="f116e-139">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="f116e-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f116e-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f116e-140">InvalidFocused</span></span>|<span data-ttu-id="f116e-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f116e-141">ValidationStates</span></span>|<span data-ttu-id="f116e-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="f116e-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f116e-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f116e-143">InvalidUnfocused</span></span>|<span data-ttu-id="f116e-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f116e-144">ValidationStates</span></span>|<span data-ttu-id="f116e-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="f116e-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="f116e-146">Przykład ControlTemplate TextBox</span><span class="sxs-lookup"><span data-stu-id="f116e-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="f116e-147">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f116e-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="f116e-148">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="f116e-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f116e-149">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f116e-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f116e-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f116e-150">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f116e-151">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="f116e-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="f116e-152">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="f116e-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="f116e-153">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="f116e-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="f116e-154">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f116e-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
