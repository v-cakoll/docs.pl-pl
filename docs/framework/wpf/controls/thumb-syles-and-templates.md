---
title: Style i szablony miniatury
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9f0b8559497939737b97568a679953d392d5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="f21a8-102">Style i szablony miniatury</span><span class="sxs-lookup"><span data-stu-id="f21a8-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="f21a8-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Primitives.Thumb> formantu.</span><span class="sxs-lookup"><span data-stu-id="f21a8-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="f21a8-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="f21a8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f21a8-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f21a8-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="f21a8-106">Części przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="f21a8-106">Thumb Parts</span></span>  
 <span data-ttu-id="f21a8-107"><xref:System.Windows.Controls.Primitives.Thumb> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="f21a8-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="f21a8-108">Stany przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="f21a8-108">Thumb States</span></span>  
 <span data-ttu-id="f21a8-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.Thumb> formantu.</span><span class="sxs-lookup"><span data-stu-id="f21a8-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="f21a8-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="f21a8-110">VisualState Name</span></span>|<span data-ttu-id="f21a8-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f21a8-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f21a8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f21a8-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f21a8-113">Normalny</span><span class="sxs-lookup"><span data-stu-id="f21a8-113">Normal</span></span>|<span data-ttu-id="f21a8-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f21a8-114">CommonStates</span></span>|<span data-ttu-id="f21a8-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="f21a8-115">The default state.</span></span>|  
|<span data-ttu-id="f21a8-116">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="f21a8-116">MouseOver</span></span>|<span data-ttu-id="f21a8-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f21a8-117">CommonStates</span></span>|<span data-ttu-id="f21a8-118">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="f21a8-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f21a8-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="f21a8-119">Pressed</span></span>|<span data-ttu-id="f21a8-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f21a8-120">CommonStates</span></span>|<span data-ttu-id="f21a8-121">Formant zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="f21a8-121">The control is pressed.</span></span>|  
|<span data-ttu-id="f21a8-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="f21a8-122">Disabled</span></span>|<span data-ttu-id="f21a8-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f21a8-123">CommonStates</span></span>|<span data-ttu-id="f21a8-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="f21a8-124">The control is disabled.</span></span>|  
|<span data-ttu-id="f21a8-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="f21a8-125">Focused</span></span>|<span data-ttu-id="f21a8-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f21a8-126">FocusStates</span></span>|<span data-ttu-id="f21a8-127">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="f21a8-127">The control has focus.</span></span>|  
|<span data-ttu-id="f21a8-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="f21a8-128">Unfocused</span></span>|<span data-ttu-id="f21a8-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f21a8-129">FocusStates</span></span>|<span data-ttu-id="f21a8-130">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="f21a8-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="f21a8-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="f21a8-131">Valid</span></span>|<span data-ttu-id="f21a8-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f21a8-132">ValidationStates</span></span>|<span data-ttu-id="f21a8-133">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="f21a8-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f21a8-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f21a8-134">InvalidFocused</span></span>|<span data-ttu-id="f21a8-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f21a8-135">ValidationStates</span></span>|<span data-ttu-id="f21a8-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="f21a8-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f21a8-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f21a8-137">InvalidUnfocused</span></span>|<span data-ttu-id="f21a8-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f21a8-138">ValidationStates</span></span>|<span data-ttu-id="f21a8-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="f21a8-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="f21a8-140">Przykład ControlTemplate przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="f21a8-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="f21a8-141">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.Thumb> formantu.</span><span class="sxs-lookup"><span data-stu-id="f21a8-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="f21a8-142">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="f21a8-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f21a8-143">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="f21a8-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f21a8-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f21a8-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f21a8-145">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="f21a8-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f21a8-146">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="f21a8-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f21a8-147">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="f21a8-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f21a8-148">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f21a8-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
