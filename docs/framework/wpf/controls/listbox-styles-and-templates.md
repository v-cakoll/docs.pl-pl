---
title: "ListBox — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edf8c50424a9694c4e00f5bf319d3122999bda85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="listbox-styles-and-templates"></a><span data-ttu-id="2f682-102">ListBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="2f682-102">ListBox Styles and Templates</span></span>
<span data-ttu-id="2f682-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.ListBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="2f682-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="2f682-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="2f682-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2f682-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2f682-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listbox-parts"></a><span data-ttu-id="2f682-106">Części ListBox</span><span class="sxs-lookup"><span data-stu-id="2f682-106">ListBox Parts</span></span>  
 <span data-ttu-id="2f682-107"><xref:System.Windows.Controls.ListBox> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="2f682-107">The <xref:System.Windows.Controls.ListBox> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="2f682-108">Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ListBox>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2f682-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListBox>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="2f682-109">( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element <xref:System.Windows.Controls.ListBox>; <xref:System.Windows.Controls.ScrollViewer> włącza przewijanie w kontrolce).</span><span class="sxs-lookup"><span data-stu-id="2f682-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListBox>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="2f682-110">Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym elementu <xref:System.Windows.Controls.ScrollViewer>, musisz podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="2f682-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listbox-states"></a><span data-ttu-id="2f682-111">Stany ListBox</span><span class="sxs-lookup"><span data-stu-id="2f682-111">ListBox States</span></span>  
 <span data-ttu-id="2f682-112">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.ListBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="2f682-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="2f682-113">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="2f682-113">VisualState Name</span></span>|<span data-ttu-id="2f682-114">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2f682-114">VisualStateGroup Name</span></span>|<span data-ttu-id="2f682-115">Opis</span><span class="sxs-lookup"><span data-stu-id="2f682-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2f682-116">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="2f682-116">Valid</span></span>|<span data-ttu-id="2f682-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2f682-117">ValidationStates</span></span>|<span data-ttu-id="2f682-118">Formant jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2f682-118">The control is valid.</span></span>|  
|<span data-ttu-id="2f682-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2f682-119">InvalidFocused</span></span>|<span data-ttu-id="2f682-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2f682-120">ValidationStates</span></span>|<span data-ttu-id="2f682-121">Formant nie jest prawidłowy i ma fokus.</span><span class="sxs-lookup"><span data-stu-id="2f682-121">The control is not valid and has focus.</span></span>|  
|<span data-ttu-id="2f682-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2f682-122">InvalidUnfocused</span></span>|<span data-ttu-id="2f682-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2f682-123">ValidationStates</span></span>|<span data-ttu-id="2f682-124">Formant jest nieprawidłowy i nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="2f682-124">The control is not valid and does not have focus.</span></span>|  
  
## <a name="listboxitem-parts"></a><span data-ttu-id="2f682-125">Części ListBoxItem</span><span class="sxs-lookup"><span data-stu-id="2f682-125">ListBoxItem Parts</span></span>  
 <span data-ttu-id="2f682-126"><xref:System.Windows.Controls.ListBoxItem> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="2f682-126">The <xref:System.Windows.Controls.ListBoxItem> control does not have any named parts.</span></span>  
  
## <a name="listboxitem-states"></a><span data-ttu-id="2f682-127">Stany ListBoxItem</span><span class="sxs-lookup"><span data-stu-id="2f682-127">ListBoxItem States</span></span>  
 <span data-ttu-id="2f682-128">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.ListBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="2f682-128">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="2f682-129">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="2f682-129">VisualState Name</span></span>|<span data-ttu-id="2f682-130">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2f682-130">VisualStateGroup Name</span></span>|<span data-ttu-id="2f682-131">Opis</span><span class="sxs-lookup"><span data-stu-id="2f682-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2f682-132">Normalny</span><span class="sxs-lookup"><span data-stu-id="2f682-132">Normal</span></span>|<span data-ttu-id="2f682-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2f682-133">CommonStates</span></span>|<span data-ttu-id="2f682-134">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="2f682-134">The default state.</span></span>|  
|<span data-ttu-id="2f682-135">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="2f682-135">MouseOver</span></span>|<span data-ttu-id="2f682-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2f682-136">CommonStates</span></span>|<span data-ttu-id="2f682-137">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="2f682-137">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="2f682-138">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="2f682-138">Disabled</span></span>|<span data-ttu-id="2f682-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2f682-139">CommonStates</span></span>|<span data-ttu-id="2f682-140">Element jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="2f682-140">The item is disabled.</span></span>|  
|<span data-ttu-id="2f682-141">Fokus</span><span class="sxs-lookup"><span data-stu-id="2f682-141">Focused</span></span>|<span data-ttu-id="2f682-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2f682-142">FocusStates</span></span>|<span data-ttu-id="2f682-143">Element ma fokus.</span><span class="sxs-lookup"><span data-stu-id="2f682-143">The item has focus.</span></span>|  
|<span data-ttu-id="2f682-144">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="2f682-144">Unfocused</span></span>|<span data-ttu-id="2f682-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2f682-145">FocusStates</span></span>|<span data-ttu-id="2f682-146">Element nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="2f682-146">The item does not have focus.</span></span>|  
|<span data-ttu-id="2f682-147">Niezaznaczony</span><span class="sxs-lookup"><span data-stu-id="2f682-147">Unselected</span></span>|<span data-ttu-id="2f682-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="2f682-148">SelectionStates</span></span>|<span data-ttu-id="2f682-149">Nie wybrano elementu.</span><span class="sxs-lookup"><span data-stu-id="2f682-149">The item is not selected.</span></span>|  
|<span data-ttu-id="2f682-150">Wybrane</span><span class="sxs-lookup"><span data-stu-id="2f682-150">Selected</span></span>|<span data-ttu-id="2f682-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="2f682-151">SelectionStates</span></span>|<span data-ttu-id="2f682-152">Element jest wybrany currentlyplate.</span><span class="sxs-lookup"><span data-stu-id="2f682-152">The item is currentlyplate selected.</span></span>|  
|<span data-ttu-id="2f682-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="2f682-153">SelectedUnfocused</span></span>|<span data-ttu-id="2f682-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="2f682-154">SelectionStates</span></span>|<span data-ttu-id="2f682-155">Element jest wybrany, ale nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="2f682-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="2f682-156">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="2f682-156">Valid</span></span>|<span data-ttu-id="2f682-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2f682-157">ValidationStates</span></span>|<span data-ttu-id="2f682-158">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="2f682-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2f682-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2f682-159">InvalidFocused</span></span>|<span data-ttu-id="2f682-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2f682-160">ValidationStates</span></span>|<span data-ttu-id="2f682-161"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="2f682-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2f682-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2f682-162">InvalidUnfocused</span></span>|<span data-ttu-id="2f682-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2f682-163">ValidationStates</span></span>|<span data-ttu-id="2f682-164"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="2f682-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listbox-controltemplate-example"></a><span data-ttu-id="2f682-165">Przykład ControlTemplate ListBox</span><span class="sxs-lookup"><span data-stu-id="2f682-165">ListBox ControlTemplate Example</span></span>  
 <span data-ttu-id="2f682-166">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ListBoxItem> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2f682-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListBox> and <xref:System.Windows.Controls.ListBoxItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 <span data-ttu-id="2f682-167">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="2f682-167">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2f682-168">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="2f682-168">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f682-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f682-169">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="2f682-170">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="2f682-170">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="2f682-171">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="2f682-171">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="2f682-172">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="2f682-172">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="2f682-173">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="2f682-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
