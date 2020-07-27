---
title: TextBox — Style i szablony
description: Dowiedz się więcej na temat stylów i szablonów dla kontrolki TextBox Windows Presentation Foundation. Zmodyfikuj ControlTemplate, aby nadać formantowi unikatowy wygląd.
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164726"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="c4867-104">TextBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="c4867-104">TextBox Styles and Templates</span></span>
<span data-ttu-id="c4867-105">W tym temacie opisano style i szablony dla <xref:System.Windows.Controls.TextBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c4867-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="c4867-106">Można zmienić wartość domyślną, <xref:System.Windows.Controls.ControlTemplate> aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="c4867-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c4867-107">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="c4867-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="c4867-108">Elementy TextBox</span><span class="sxs-lookup"><span data-stu-id="c4867-108">TextBox Parts</span></span>  
 <span data-ttu-id="c4867-109">W poniższej tabeli wymieniono nazwane części <xref:System.Windows.Controls.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="c4867-109">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="c4867-110">Część</span><span class="sxs-lookup"><span data-stu-id="c4867-110">Part</span></span>|<span data-ttu-id="c4867-111">Typ</span><span class="sxs-lookup"><span data-stu-id="c4867-111">Type</span></span>|<span data-ttu-id="c4867-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c4867-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c4867-113">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="c4867-113">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="c4867-114">Element wizualizacji, który może zawierać <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="c4867-114">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="c4867-115">Tekst <xref:System.Windows.Controls.TextBox> jest wyświetlany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="c4867-115">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="c4867-116">Stany pól TextBox</span><span class="sxs-lookup"><span data-stu-id="c4867-116">TextBox States</span></span>  
 <span data-ttu-id="c4867-117">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.TextBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c4867-117">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="c4867-118">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="c4867-118">VisualState Name</span></span>|<span data-ttu-id="c4867-119">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c4867-119">VisualStateGroup Name</span></span>|<span data-ttu-id="c4867-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c4867-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="c4867-121">Normalne</span><span class="sxs-lookup"><span data-stu-id="c4867-121">Normal</span></span>|<span data-ttu-id="c4867-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4867-122">CommonStates</span></span>|<span data-ttu-id="c4867-123">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="c4867-123">The default state.</span></span>|  
|<span data-ttu-id="c4867-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="c4867-124">MouseOver</span></span>|<span data-ttu-id="c4867-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4867-125">CommonStates</span></span>|<span data-ttu-id="c4867-126">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="c4867-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="c4867-127">Disabled</span><span class="sxs-lookup"><span data-stu-id="c4867-127">Disabled</span></span>|<span data-ttu-id="c4867-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4867-128">CommonStates</span></span>|<span data-ttu-id="c4867-129">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="c4867-129">The control is disabled.</span></span>|  
|<span data-ttu-id="c4867-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c4867-130">ReadOnly</span></span>|<span data-ttu-id="c4867-131">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4867-131">CommonStates</span></span>|<span data-ttu-id="c4867-132">Użytkownik nie może zmienić tekstu w <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="c4867-132">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="c4867-133">Ustawiono fokus</span><span class="sxs-lookup"><span data-stu-id="c4867-133">Focused</span></span>|<span data-ttu-id="c4867-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c4867-134">FocusStates</span></span>|<span data-ttu-id="c4867-135">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="c4867-135">The control has focus.</span></span>|  
|<span data-ttu-id="c4867-136">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="c4867-136">Unfocused</span></span>|<span data-ttu-id="c4867-137">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c4867-137">FocusStates</span></span>|<span data-ttu-id="c4867-138">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="c4867-138">The control does not have focus.</span></span>|  
|<span data-ttu-id="c4867-139">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="c4867-139">Valid</span></span>|<span data-ttu-id="c4867-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4867-140">ValidationStates</span></span>|<span data-ttu-id="c4867-141">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości to `false` .</span><span class="sxs-lookup"><span data-stu-id="c4867-141">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c4867-142">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c4867-142">InvalidFocused</span></span>|<span data-ttu-id="c4867-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4867-143">ValidationStates</span></span>|<span data-ttu-id="c4867-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość ma `true` fokus.</span><span class="sxs-lookup"><span data-stu-id="c4867-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c4867-145">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c4867-145">InvalidUnfocused</span></span>|<span data-ttu-id="c4867-146">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4867-146">ValidationStates</span></span>|<span data-ttu-id="c4867-147"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość ma `true` kontrolkę, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="c4867-147">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="c4867-148">ControlTemplate — przykład pola tekstowego</span><span class="sxs-lookup"><span data-stu-id="c4867-148">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="c4867-149">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TextBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c4867-149">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="c4867-150">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="c4867-150">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c4867-151">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="c4867-151">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4867-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4867-152">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c4867-153">Style i szablony formantu</span><span class="sxs-lookup"><span data-stu-id="c4867-153">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c4867-154">Niestandardowe dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="c4867-154">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c4867-155">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="c4867-155">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c4867-156">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="c4867-156">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
