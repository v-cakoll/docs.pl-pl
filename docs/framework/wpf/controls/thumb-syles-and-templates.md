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
ms.workload: dotnet
ms.openlocfilehash: 780ddc07c79aab111c17f9e7e551cfde85c68f3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="7727e-102">Style i szablony miniatury</span><span class="sxs-lookup"><span data-stu-id="7727e-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="7727e-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Primitives.Thumb> formantu.</span><span class="sxs-lookup"><span data-stu-id="7727e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="7727e-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="7727e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7727e-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="7727e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="7727e-106">Części przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="7727e-106">Thumb Parts</span></span>  
 <span data-ttu-id="7727e-107"><xref:System.Windows.Controls.Primitives.Thumb> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="7727e-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="7727e-108">Stany przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="7727e-108">Thumb States</span></span>  
 <span data-ttu-id="7727e-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.Thumb> formantu.</span><span class="sxs-lookup"><span data-stu-id="7727e-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="7727e-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="7727e-110">VisualState Name</span></span>|<span data-ttu-id="7727e-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7727e-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7727e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7727e-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7727e-113">Normalny</span><span class="sxs-lookup"><span data-stu-id="7727e-113">Normal</span></span>|<span data-ttu-id="7727e-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7727e-114">CommonStates</span></span>|<span data-ttu-id="7727e-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="7727e-115">The default state.</span></span>|  
|<span data-ttu-id="7727e-116">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="7727e-116">MouseOver</span></span>|<span data-ttu-id="7727e-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7727e-117">CommonStates</span></span>|<span data-ttu-id="7727e-118">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="7727e-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="7727e-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="7727e-119">Pressed</span></span>|<span data-ttu-id="7727e-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7727e-120">CommonStates</span></span>|<span data-ttu-id="7727e-121">Formant zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="7727e-121">The control is pressed.</span></span>|  
|<span data-ttu-id="7727e-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="7727e-122">Disabled</span></span>|<span data-ttu-id="7727e-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7727e-123">CommonStates</span></span>|<span data-ttu-id="7727e-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="7727e-124">The control is disabled.</span></span>|  
|<span data-ttu-id="7727e-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="7727e-125">Focused</span></span>|<span data-ttu-id="7727e-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7727e-126">FocusStates</span></span>|<span data-ttu-id="7727e-127">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="7727e-127">The control has focus.</span></span>|  
|<span data-ttu-id="7727e-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="7727e-128">Unfocused</span></span>|<span data-ttu-id="7727e-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7727e-129">FocusStates</span></span>|<span data-ttu-id="7727e-130">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="7727e-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="7727e-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="7727e-131">Valid</span></span>|<span data-ttu-id="7727e-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7727e-132">ValidationStates</span></span>|<span data-ttu-id="7727e-133">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="7727e-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7727e-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7727e-134">InvalidFocused</span></span>|<span data-ttu-id="7727e-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7727e-135">ValidationStates</span></span>|<span data-ttu-id="7727e-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="7727e-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7727e-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7727e-137">InvalidUnfocused</span></span>|<span data-ttu-id="7727e-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7727e-138">ValidationStates</span></span>|<span data-ttu-id="7727e-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="7727e-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="7727e-140">Przykład ControlTemplate przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="7727e-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="7727e-141">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.Thumb> formantu.</span><span class="sxs-lookup"><span data-stu-id="7727e-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="7727e-142">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="7727e-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7727e-143">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="7727e-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7727e-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7727e-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="7727e-145">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="7727e-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="7727e-146">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="7727e-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="7727e-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="7727e-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="7727e-148">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7727e-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
