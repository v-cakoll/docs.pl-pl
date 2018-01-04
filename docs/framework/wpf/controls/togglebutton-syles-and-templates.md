---
title: "ToggleButton — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c143717b691e79771fbaa55724d9d9748259e3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="togglebutton-syles-and-templates"></a><span data-ttu-id="e1775-102">ToggleButton — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="e1775-102">ToggleButton Syles and Templates</span></span>
<span data-ttu-id="e1775-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Primitives.ToggleButton> formantu.</span><span class="sxs-lookup"><span data-stu-id="e1775-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="e1775-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="e1775-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e1775-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e1775-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="togglebutton-parts"></a><span data-ttu-id="e1775-106">Części ToggleButton</span><span class="sxs-lookup"><span data-stu-id="e1775-106">ToggleButton Parts</span></span>  
 <span data-ttu-id="e1775-107"><xref:System.Windows.Controls.Primitives.ToggleButton> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="e1775-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>  
  
## <a name="togglebutton-states"></a><span data-ttu-id="e1775-108">Stany ToggleButton</span><span class="sxs-lookup"><span data-stu-id="e1775-108">ToggleButton States</span></span>  
 <span data-ttu-id="e1775-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.ToggleButton> formantu.</span><span class="sxs-lookup"><span data-stu-id="e1775-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
|<span data-ttu-id="e1775-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="e1775-110">VisualState Name</span></span>|<span data-ttu-id="e1775-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e1775-111">VisualStateGroup Name</span></span>|<span data-ttu-id="e1775-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e1775-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e1775-113">Normalny</span><span class="sxs-lookup"><span data-stu-id="e1775-113">Normal</span></span>|<span data-ttu-id="e1775-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e1775-114">CommonStates</span></span>|<span data-ttu-id="e1775-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="e1775-115">The default state.</span></span>|  
|<span data-ttu-id="e1775-116">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="e1775-116">MouseOver</span></span>|<span data-ttu-id="e1775-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e1775-117">CommonStates</span></span>|<span data-ttu-id="e1775-118">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="e1775-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="e1775-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="e1775-119">Pressed</span></span>|<span data-ttu-id="e1775-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e1775-120">CommonStates</span></span>|<span data-ttu-id="e1775-121">Formant zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="e1775-121">The control is pressed.</span></span>|  
|<span data-ttu-id="e1775-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="e1775-122">Disabled</span></span>|<span data-ttu-id="e1775-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e1775-123">CommonStates</span></span>|<span data-ttu-id="e1775-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="e1775-124">The control is disabled.</span></span>|  
|<span data-ttu-id="e1775-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="e1775-125">Focused</span></span>|<span data-ttu-id="e1775-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e1775-126">FocusStates</span></span>|<span data-ttu-id="e1775-127">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="e1775-127">The control has focus.</span></span>|  
|<span data-ttu-id="e1775-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="e1775-128">Unfocused</span></span>|<span data-ttu-id="e1775-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e1775-129">FocusStates</span></span>|<span data-ttu-id="e1775-130">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="e1775-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="e1775-131">Zaznaczone</span><span class="sxs-lookup"><span data-stu-id="e1775-131">Checked</span></span>|<span data-ttu-id="e1775-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="e1775-132">CheckStates</span></span>|<span data-ttu-id="e1775-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>jest `true`.</span><span class="sxs-lookup"><span data-stu-id="e1775-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="e1775-134">Unchecked</span><span class="sxs-lookup"><span data-stu-id="e1775-134">Unchecked</span></span>|<span data-ttu-id="e1775-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="e1775-135">CheckStates</span></span>|<span data-ttu-id="e1775-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>jest `false`.</span><span class="sxs-lookup"><span data-stu-id="e1775-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="e1775-137">Nieokreślony</span><span class="sxs-lookup"><span data-stu-id="e1775-137">Indeterminate</span></span>|<span data-ttu-id="e1775-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="e1775-138">CheckStates</span></span>|<span data-ttu-id="e1775-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>jest `true`, i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `null`.</span><span class="sxs-lookup"><span data-stu-id="e1775-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="e1775-140">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="e1775-140">Valid</span></span>|<span data-ttu-id="e1775-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e1775-141">ValidationStates</span></span>|<span data-ttu-id="e1775-142">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="e1775-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e1775-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e1775-143">InvalidFocused</span></span>|<span data-ttu-id="e1775-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e1775-144">ValidationStates</span></span>|<span data-ttu-id="e1775-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="e1775-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e1775-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e1775-146">InvalidUnfocused</span></span>|<span data-ttu-id="e1775-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e1775-147">ValidationStates</span></span>|<span data-ttu-id="e1775-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="e1775-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e1775-149">Jeśli nieokreślony stan wizualny nie istnieje w szablonie formantu, jako domyślny stan wizualny używany jest niezaznaczone stanu wizualnego.</span><span class="sxs-lookup"><span data-stu-id="e1775-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>  
  
## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="e1775-150">Przykład ControlTemplate ToggleButton</span><span class="sxs-lookup"><span data-stu-id="e1775-150">ToggleButton ControlTemplate Example</span></span>  
 <span data-ttu-id="e1775-151">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.ToggleButton> formantu.</span><span class="sxs-lookup"><span data-stu-id="e1775-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 <span data-ttu-id="e1775-152">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="e1775-152">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e1775-153">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="e1775-153">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1775-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1775-154">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e1775-155">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="e1775-155">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="e1775-156">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="e1775-156">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="e1775-157">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="e1775-157">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="e1775-158">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e1775-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
