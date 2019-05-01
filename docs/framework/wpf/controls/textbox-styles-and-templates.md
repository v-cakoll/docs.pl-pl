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
ms.openlocfilehash: ccc89e0e0c8977398ed162b246ff6cdede3b8351
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790874"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="3e3ae-102">TextBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="3e3ae-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="3e3ae-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="3e3ae-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3e3ae-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="3e3ae-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="3e3ae-106">Części pola tekstowego</span><span class="sxs-lookup"><span data-stu-id="3e3ae-106">TextBox Parts</span></span>  
 <span data-ttu-id="3e3ae-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="3e3ae-108">Część</span><span class="sxs-lookup"><span data-stu-id="3e3ae-108">Part</span></span>|<span data-ttu-id="3e3ae-109">Typ</span><span class="sxs-lookup"><span data-stu-id="3e3ae-109">Type</span></span>|<span data-ttu-id="3e3ae-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3e3ae-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3e3ae-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="3e3ae-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3e3ae-112">Element wizualny, który może zawierać <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="3e3ae-113">Tekst <xref:System.Windows.Controls.TextBox> jest wyświetlana w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="3e3ae-114">Stany TextBox</span><span class="sxs-lookup"><span data-stu-id="3e3ae-114">TextBox States</span></span>  
 <span data-ttu-id="3e3ae-115">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="3e3ae-116">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="3e3ae-116">VisualState Name</span></span>|<span data-ttu-id="3e3ae-117">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="3e3ae-117">VisualStateGroup Name</span></span>|<span data-ttu-id="3e3ae-118">Opis</span><span class="sxs-lookup"><span data-stu-id="3e3ae-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="3e3ae-119">Normalne</span><span class="sxs-lookup"><span data-stu-id="3e3ae-119">Normal</span></span>|<span data-ttu-id="3e3ae-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3e3ae-120">CommonStates</span></span>|<span data-ttu-id="3e3ae-121">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-121">The default state.</span></span>|  
|<span data-ttu-id="3e3ae-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="3e3ae-122">MouseOver</span></span>|<span data-ttu-id="3e3ae-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3e3ae-123">CommonStates</span></span>|<span data-ttu-id="3e3ae-124">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="3e3ae-125">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="3e3ae-125">Disabled</span></span>|<span data-ttu-id="3e3ae-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3e3ae-126">CommonStates</span></span>|<span data-ttu-id="3e3ae-127">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-127">The control is disabled.</span></span>|  
|<span data-ttu-id="3e3ae-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="3e3ae-128">ReadOnly</span></span>|<span data-ttu-id="3e3ae-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3e3ae-129">CommonStates</span></span>|<span data-ttu-id="3e3ae-130">Użytkownik nie może zmieniać tekst w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="3e3ae-131">Fokus</span><span class="sxs-lookup"><span data-stu-id="3e3ae-131">Focused</span></span>|<span data-ttu-id="3e3ae-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3e3ae-132">FocusStates</span></span>|<span data-ttu-id="3e3ae-133">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-133">The control has focus.</span></span>|  
|<span data-ttu-id="3e3ae-134">Po przeniesieniu fokusu</span><span class="sxs-lookup"><span data-stu-id="3e3ae-134">Unfocused</span></span>|<span data-ttu-id="3e3ae-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3e3ae-135">FocusStates</span></span>|<span data-ttu-id="3e3ae-136">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="3e3ae-137">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="3e3ae-137">Valid</span></span>|<span data-ttu-id="3e3ae-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3e3ae-138">ValidationStates</span></span>|<span data-ttu-id="3e3ae-139">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3e3ae-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3e3ae-140">InvalidFocused</span></span>|<span data-ttu-id="3e3ae-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3e3ae-141">ValidationStates</span></span>|<span data-ttu-id="3e3ae-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3e3ae-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3e3ae-143">InvalidUnfocused</span></span>|<span data-ttu-id="3e3ae-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3e3ae-144">ValidationStates</span></span>|<span data-ttu-id="3e3ae-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="3e3ae-146">Przykład ControlTemplate TextBox</span><span class="sxs-lookup"><span data-stu-id="3e3ae-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="3e3ae-147">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="3e3ae-148">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="3e3ae-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3e3ae-149">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="3e3ae-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e3ae-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e3ae-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3e3ae-151">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="3e3ae-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3e3ae-152">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="3e3ae-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3e3ae-153">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="3e3ae-153">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="3e3ae-154">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="3e3ae-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
