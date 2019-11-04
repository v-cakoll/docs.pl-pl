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
ms.openlocfilehash: 7c4680a3ea9352e94d628e786fc8e4fd71018d00
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458249"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="fa36a-102">TextBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="fa36a-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="fa36a-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fa36a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="fa36a-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="fa36a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fa36a-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="fa36a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="fa36a-106">Elementy TextBox</span><span class="sxs-lookup"><span data-stu-id="fa36a-106">TextBox Parts</span></span>  
 <span data-ttu-id="fa36a-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fa36a-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="fa36a-108">Części</span><span class="sxs-lookup"><span data-stu-id="fa36a-108">Part</span></span>|<span data-ttu-id="fa36a-109">Typ</span><span class="sxs-lookup"><span data-stu-id="fa36a-109">Type</span></span>|<span data-ttu-id="fa36a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fa36a-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fa36a-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="fa36a-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="fa36a-112">Element wizualizacji, który może zawierać <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="fa36a-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="fa36a-113">Tekst <xref:System.Windows.Controls.TextBox> zostanie wyświetlony w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="fa36a-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="fa36a-114">Stany pól TextBox</span><span class="sxs-lookup"><span data-stu-id="fa36a-114">TextBox States</span></span>  
 <span data-ttu-id="fa36a-115">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fa36a-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="fa36a-116">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="fa36a-116">VisualState Name</span></span>|<span data-ttu-id="fa36a-117">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="fa36a-117">VisualStateGroup Name</span></span>|<span data-ttu-id="fa36a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="fa36a-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="fa36a-119">Typow</span><span class="sxs-lookup"><span data-stu-id="fa36a-119">Normal</span></span>|<span data-ttu-id="fa36a-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fa36a-120">CommonStates</span></span>|<span data-ttu-id="fa36a-121">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="fa36a-121">The default state.</span></span>|  
|<span data-ttu-id="fa36a-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="fa36a-122">MouseOver</span></span>|<span data-ttu-id="fa36a-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fa36a-123">CommonStates</span></span>|<span data-ttu-id="fa36a-124">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="fa36a-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="fa36a-125">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="fa36a-125">Disabled</span></span>|<span data-ttu-id="fa36a-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fa36a-126">CommonStates</span></span>|<span data-ttu-id="fa36a-127">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="fa36a-127">The control is disabled.</span></span>|  
|<span data-ttu-id="fa36a-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="fa36a-128">ReadOnly</span></span>|<span data-ttu-id="fa36a-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fa36a-129">CommonStates</span></span>|<span data-ttu-id="fa36a-130">Użytkownik nie może zmienić tekstu w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fa36a-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="fa36a-131">Fokus</span><span class="sxs-lookup"><span data-stu-id="fa36a-131">Focused</span></span>|<span data-ttu-id="fa36a-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fa36a-132">FocusStates</span></span>|<span data-ttu-id="fa36a-133">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="fa36a-133">The control has focus.</span></span>|  
|<span data-ttu-id="fa36a-134">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="fa36a-134">Unfocused</span></span>|<span data-ttu-id="fa36a-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fa36a-135">FocusStates</span></span>|<span data-ttu-id="fa36a-136">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="fa36a-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="fa36a-137">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="fa36a-137">Valid</span></span>|<span data-ttu-id="fa36a-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fa36a-138">ValidationStates</span></span>|<span data-ttu-id="fa36a-139">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="fa36a-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="fa36a-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fa36a-140">InvalidFocused</span></span>|<span data-ttu-id="fa36a-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fa36a-141">ValidationStates</span></span>|<span data-ttu-id="fa36a-142">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="fa36a-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="fa36a-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fa36a-143">InvalidUnfocused</span></span>|<span data-ttu-id="fa36a-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fa36a-144">ValidationStates</span></span>|<span data-ttu-id="fa36a-145">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="fa36a-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="fa36a-146">ControlTemplate — przykład pola tekstowego</span><span class="sxs-lookup"><span data-stu-id="fa36a-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="fa36a-147">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fa36a-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="fa36a-148">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="fa36a-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="fa36a-149">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="fa36a-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa36a-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa36a-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="fa36a-151">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="fa36a-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="fa36a-152">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="fa36a-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="fa36a-153">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="fa36a-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="fa36a-154">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="fa36a-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
