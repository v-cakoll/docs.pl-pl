---
title: Style i szablony ekspandera
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 04225458e9889c511b7aaa359239512e316cbb26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="expander-styles-and-templates"></a><span data-ttu-id="6753a-102">Style i szablony ekspandera</span><span class="sxs-lookup"><span data-stu-id="6753a-102">Expander Styles and Templates</span></span>
<span data-ttu-id="6753a-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Expander> formantu.</span><span class="sxs-lookup"><span data-stu-id="6753a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Expander> control.</span></span> <span data-ttu-id="6753a-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="6753a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6753a-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6753a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="expander-parts"></a><span data-ttu-id="6753a-106">Części Expander</span><span class="sxs-lookup"><span data-stu-id="6753a-106">Expander Parts</span></span>  
 <span data-ttu-id="6753a-107"><xref:System.Windows.Controls.Expander> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="6753a-107">The <xref:System.Windows.Controls.Expander> control does not have any named parts.</span></span>  
  
## <a name="expander-states"></a><span data-ttu-id="6753a-108">Stany Expander</span><span class="sxs-lookup"><span data-stu-id="6753a-108">Expander States</span></span>  
 <span data-ttu-id="6753a-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Expander> formantu.</span><span class="sxs-lookup"><span data-stu-id="6753a-109">The following table lists the visual states for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
|<span data-ttu-id="6753a-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="6753a-110">VisualState Name</span></span>|<span data-ttu-id="6753a-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6753a-111">VisualStateGroup Name</span></span>|<span data-ttu-id="6753a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6753a-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6753a-113">Normalny</span><span class="sxs-lookup"><span data-stu-id="6753a-113">Normal</span></span>|<span data-ttu-id="6753a-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6753a-114">CommonStates</span></span>|<span data-ttu-id="6753a-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="6753a-115">The default state.</span></span>|  
|<span data-ttu-id="6753a-116">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="6753a-116">MouseOver</span></span>|<span data-ttu-id="6753a-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6753a-117">CommonStates</span></span>|<span data-ttu-id="6753a-118">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="6753a-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="6753a-119">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="6753a-119">Disabled</span></span>|<span data-ttu-id="6753a-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6753a-120">CommonStates</span></span>|<span data-ttu-id="6753a-121">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="6753a-121">The control is disabled.</span></span>|  
|<span data-ttu-id="6753a-122">Fokus</span><span class="sxs-lookup"><span data-stu-id="6753a-122">Focused</span></span>|<span data-ttu-id="6753a-123">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6753a-123">FocusStates</span></span>|<span data-ttu-id="6753a-124">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="6753a-124">The control has focus.</span></span>|  
|<span data-ttu-id="6753a-125">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="6753a-125">Unfocused</span></span>|<span data-ttu-id="6753a-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6753a-126">FocusStates</span></span>|<span data-ttu-id="6753a-127">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="6753a-127">The control does not have focus.</span></span>|  
|<span data-ttu-id="6753a-128">Rozwinięty</span><span class="sxs-lookup"><span data-stu-id="6753a-128">Expanded</span></span>|<span data-ttu-id="6753a-129">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="6753a-129">ExpansionStates</span></span>|<span data-ttu-id="6753a-130">Kontrolka jest rozwinięta.</span><span class="sxs-lookup"><span data-stu-id="6753a-130">The control is expanded.</span></span>|  
|<span data-ttu-id="6753a-131">Zwinięte</span><span class="sxs-lookup"><span data-stu-id="6753a-131">Collapsed</span></span>|<span data-ttu-id="6753a-132">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="6753a-132">ExpansionStates</span></span>|<span data-ttu-id="6753a-133">Formant nie jest rozwinięty.</span><span class="sxs-lookup"><span data-stu-id="6753a-133">The control is not expanded.</span></span>|  
|<span data-ttu-id="6753a-134">ExpandDown</span><span class="sxs-lookup"><span data-stu-id="6753a-134">ExpandDown</span></span>|<span data-ttu-id="6753a-135">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="6753a-135">ExpandDirectionStates</span></span>|<span data-ttu-id="6753a-136">Kontrolki rozwijane w dół.</span><span class="sxs-lookup"><span data-stu-id="6753a-136">The control expands down.</span></span>|  
|<span data-ttu-id="6753a-137">ExpandUp</span><span class="sxs-lookup"><span data-stu-id="6753a-137">ExpandUp</span></span>|<span data-ttu-id="6753a-138">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="6753a-138">ExpandDirectionStates</span></span>|<span data-ttu-id="6753a-139">Formant rozszerza się.</span><span class="sxs-lookup"><span data-stu-id="6753a-139">The control expands up.</span></span>|  
|<span data-ttu-id="6753a-140">ExpandLeft</span><span class="sxs-lookup"><span data-stu-id="6753a-140">ExpandLeft</span></span>|<span data-ttu-id="6753a-141">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="6753a-141">ExpandDirectionStates</span></span>|<span data-ttu-id="6753a-142">Formant rozszerza się po lewej.</span><span class="sxs-lookup"><span data-stu-id="6753a-142">The control expands left.</span></span>|  
|<span data-ttu-id="6753a-143">ExpandRight</span><span class="sxs-lookup"><span data-stu-id="6753a-143">ExpandRight</span></span>|<span data-ttu-id="6753a-144">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="6753a-144">ExpandDirectionStates</span></span>|<span data-ttu-id="6753a-145">Kontrolki rozwijane w prawo.</span><span class="sxs-lookup"><span data-stu-id="6753a-145">The control expands right.</span></span>|  
|<span data-ttu-id="6753a-146">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="6753a-146">Valid</span></span>|<span data-ttu-id="6753a-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6753a-147">ValidationStates</span></span>|<span data-ttu-id="6753a-148">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="6753a-148">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6753a-149">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6753a-149">InvalidFocused</span></span>|<span data-ttu-id="6753a-150">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6753a-150">ValidationStates</span></span>|<span data-ttu-id="6753a-151"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="6753a-151">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6753a-152">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6753a-152">InvalidUnfocused</span></span>|<span data-ttu-id="6753a-153">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6753a-153">ValidationStates</span></span>|<span data-ttu-id="6753a-154"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="6753a-154">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="expander-controltemplate-example"></a><span data-ttu-id="6753a-155">Przykład ControlTemplate Expander</span><span class="sxs-lookup"><span data-stu-id="6753a-155">Expander ControlTemplate Example</span></span>  
 <span data-ttu-id="6753a-156">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Expander> formantu.</span><span class="sxs-lookup"><span data-stu-id="6753a-156">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 <span data-ttu-id="6753a-157">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="6753a-157">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6753a-158">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="6753a-158">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6753a-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6753a-159">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="6753a-160">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="6753a-160">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="6753a-161">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="6753a-161">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="6753a-162">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="6753a-162">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="6753a-163">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6753a-163">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
