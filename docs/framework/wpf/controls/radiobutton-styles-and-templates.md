---
title: "RadioButton — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], RadioButton
- RadioButton [WPF], styles and templates
- ControlTemplate [WPF], RadioButton
- states [WPF], RadioButton
- templates [WPF], RadioButton
- parts [WPF], RadioButton
ms.assetid: 9acf93f7-dd2f-4010-8ce0-1edd81c52ae2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 384a587fe01fb69ff5d377f2aa34d03ff110880d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="radiobutton-styles-and-templates"></a><span data-ttu-id="76eb1-102">RadioButton — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="76eb1-102">RadioButton Styles and Templates</span></span>
<span data-ttu-id="76eb1-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.RadioButton> formantu.</span><span class="sxs-lookup"><span data-stu-id="76eb1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.RadioButton> control.</span></span> <span data-ttu-id="76eb1-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="76eb1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="76eb1-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="76eb1-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="radiobutton-parts"></a><span data-ttu-id="76eb1-106">Elementy RadioButton</span><span class="sxs-lookup"><span data-stu-id="76eb1-106">RadioButton Parts</span></span>  
 <span data-ttu-id="76eb1-107"><xref:System.Windows.Controls.RadioButton> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="76eb1-107">The <xref:System.Windows.Controls.RadioButton> control does not have any named parts.</span></span>  
  
## <a name="radiobutton-states"></a><span data-ttu-id="76eb1-108">Stany RadioButton</span><span class="sxs-lookup"><span data-stu-id="76eb1-108">RadioButton States</span></span>  
 <span data-ttu-id="76eb1-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.RadioButton> formantu.</span><span class="sxs-lookup"><span data-stu-id="76eb1-109">The following table lists the visual states for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
|<span data-ttu-id="76eb1-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="76eb1-110">VisualState Name</span></span>|<span data-ttu-id="76eb1-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="76eb1-111">VisualStateGroup Name</span></span>|<span data-ttu-id="76eb1-112">Opis</span><span class="sxs-lookup"><span data-stu-id="76eb1-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="76eb1-113">Normalny</span><span class="sxs-lookup"><span data-stu-id="76eb1-113">Normal</span></span>|<span data-ttu-id="76eb1-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-114">CommonStates</span></span>|<span data-ttu-id="76eb1-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="76eb1-115">The default state.</span></span>|  
|<span data-ttu-id="76eb1-116">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="76eb1-116">MouseOver</span></span>|<span data-ttu-id="76eb1-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-117">CommonStates</span></span>|<span data-ttu-id="76eb1-118">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="76eb1-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="76eb1-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="76eb1-119">Pressed</span></span>|<span data-ttu-id="76eb1-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-120">CommonStates</span></span>|<span data-ttu-id="76eb1-121">Formant zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="76eb1-121">The control is pressed.</span></span>|  
|<span data-ttu-id="76eb1-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="76eb1-122">Disabled</span></span>|<span data-ttu-id="76eb1-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-123">CommonStates</span></span>|<span data-ttu-id="76eb1-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="76eb1-124">The control is disabled.</span></span>|  
|<span data-ttu-id="76eb1-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="76eb1-125">Focused</span></span>|<span data-ttu-id="76eb1-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-126">FocusStates</span></span>|<span data-ttu-id="76eb1-127">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="76eb1-127">The control has focus.</span></span>|  
|<span data-ttu-id="76eb1-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="76eb1-128">Unfocused</span></span>|<span data-ttu-id="76eb1-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-129">FocusStates</span></span>|<span data-ttu-id="76eb1-130">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="76eb1-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="76eb1-131">Zaznaczone</span><span class="sxs-lookup"><span data-stu-id="76eb1-131">Checked</span></span>|<span data-ttu-id="76eb1-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-132">CheckStates</span></span>|<span data-ttu-id="76eb1-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>jest `true`.</span><span class="sxs-lookup"><span data-stu-id="76eb1-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="76eb1-134">Unchecked</span><span class="sxs-lookup"><span data-stu-id="76eb1-134">Unchecked</span></span>|<span data-ttu-id="76eb1-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-135">CheckStates</span></span>|<span data-ttu-id="76eb1-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>jest `false`.</span><span class="sxs-lookup"><span data-stu-id="76eb1-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="76eb1-137">Nieokreślony</span><span class="sxs-lookup"><span data-stu-id="76eb1-137">Indeterminate</span></span>|<span data-ttu-id="76eb1-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-138">CheckStates</span></span>|<span data-ttu-id="76eb1-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>jest `true`, i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `null`.</span><span class="sxs-lookup"><span data-stu-id="76eb1-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="76eb1-140">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="76eb1-140">Valid</span></span>|<span data-ttu-id="76eb1-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-141">ValidationStates</span></span>|<span data-ttu-id="76eb1-142">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="76eb1-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="76eb1-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="76eb1-143">InvalidFocused</span></span>|<span data-ttu-id="76eb1-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-144">ValidationStates</span></span>|<span data-ttu-id="76eb1-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="76eb1-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="76eb1-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="76eb1-146">InvalidUnfocused</span></span>|<span data-ttu-id="76eb1-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="76eb1-147">ValidationStates</span></span>|<span data-ttu-id="76eb1-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="76eb1-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="radiobutton-controltemplate-example"></a><span data-ttu-id="76eb1-149">Przykład ControlTemplate elementu RadioButton</span><span class="sxs-lookup"><span data-stu-id="76eb1-149">RadioButton ControlTemplate Example</span></span>  
 <span data-ttu-id="76eb1-150">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.RadioButton> formantu.</span><span class="sxs-lookup"><span data-stu-id="76eb1-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
 <span data-ttu-id="76eb1-151">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="76eb1-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="76eb1-152">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="76eb1-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76eb1-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76eb1-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="76eb1-154">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="76eb1-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="76eb1-155">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="76eb1-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="76eb1-156">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="76eb1-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="76eb1-157">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="76eb1-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
