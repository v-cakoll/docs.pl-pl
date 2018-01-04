---
title: "TextBox — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d4fdb652876f2df049b71c18b0b79b7b435da8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="733e8-102">TextBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="733e8-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="733e8-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="733e8-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="733e8-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="733e8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="733e8-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="733e8-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="733e8-106">Części pola tekstowego</span><span class="sxs-lookup"><span data-stu-id="733e8-106">TextBox Parts</span></span>  
 <span data-ttu-id="733e8-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="733e8-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="733e8-108">Część</span><span class="sxs-lookup"><span data-stu-id="733e8-108">Part</span></span>|<span data-ttu-id="733e8-109">Typ</span><span class="sxs-lookup"><span data-stu-id="733e8-109">Type</span></span>|<span data-ttu-id="733e8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="733e8-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="733e8-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="733e8-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="733e8-112">Element wizualny, który może zawierać <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="733e8-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="733e8-113">Tekst <xref:System.Windows.Controls.TextBox> jest wyświetlany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="733e8-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="733e8-114">Pole tekstowe stanów</span><span class="sxs-lookup"><span data-stu-id="733e8-114">TextBox States</span></span>  
 <span data-ttu-id="733e8-115">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="733e8-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="733e8-116">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="733e8-116">VisualState Name</span></span>|<span data-ttu-id="733e8-117">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="733e8-117">VisualStateGroup Name</span></span>|<span data-ttu-id="733e8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="733e8-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="733e8-119">Normalny</span><span class="sxs-lookup"><span data-stu-id="733e8-119">Normal</span></span>|<span data-ttu-id="733e8-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="733e8-120">CommonStates</span></span>|<span data-ttu-id="733e8-121">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="733e8-121">The default state.</span></span>|  
|<span data-ttu-id="733e8-122">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="733e8-122">MouseOver</span></span>|<span data-ttu-id="733e8-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="733e8-123">CommonStates</span></span>|<span data-ttu-id="733e8-124">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="733e8-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="733e8-125">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="733e8-125">Disabled</span></span>|<span data-ttu-id="733e8-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="733e8-126">CommonStates</span></span>|<span data-ttu-id="733e8-127">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="733e8-127">The control is disabled.</span></span>|  
|<span data-ttu-id="733e8-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="733e8-128">ReadOnly</span></span>|<span data-ttu-id="733e8-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="733e8-129">CommonStates</span></span>|<span data-ttu-id="733e8-130">Użytkownik nie może zmieniać tekst w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="733e8-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="733e8-131">Fokus</span><span class="sxs-lookup"><span data-stu-id="733e8-131">Focused</span></span>|<span data-ttu-id="733e8-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="733e8-132">FocusStates</span></span>|<span data-ttu-id="733e8-133">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="733e8-133">The control has focus.</span></span>|  
|<span data-ttu-id="733e8-134">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="733e8-134">Unfocused</span></span>|<span data-ttu-id="733e8-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="733e8-135">FocusStates</span></span>|<span data-ttu-id="733e8-136">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="733e8-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="733e8-137">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="733e8-137">Valid</span></span>|<span data-ttu-id="733e8-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="733e8-138">ValidationStates</span></span>|<span data-ttu-id="733e8-139">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="733e8-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="733e8-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="733e8-140">InvalidFocused</span></span>|<span data-ttu-id="733e8-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="733e8-141">ValidationStates</span></span>|<span data-ttu-id="733e8-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="733e8-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="733e8-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="733e8-143">InvalidUnfocused</span></span>|<span data-ttu-id="733e8-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="733e8-144">ValidationStates</span></span>|<span data-ttu-id="733e8-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="733e8-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="733e8-146">Przykład ControlTemplate pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="733e8-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="733e8-147">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="733e8-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="733e8-148">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="733e8-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="733e8-149">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="733e8-149">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733e8-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="733e8-150">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="733e8-151">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="733e8-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="733e8-152">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="733e8-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="733e8-153">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="733e8-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="733e8-154">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="733e8-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
