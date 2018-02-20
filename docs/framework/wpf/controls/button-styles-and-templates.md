---
title: "Style i szablony przycisków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d783b3141463ca2c74ddd649848ea49e154415b6
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="ae09d-102">Style i szablony przycisków</span><span class="sxs-lookup"><span data-stu-id="ae09d-102">Button Styles and Templates</span></span>
<span data-ttu-id="ae09d-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="ae09d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="ae09d-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="ae09d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ae09d-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ae09d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="ae09d-106">Przycisk części</span><span class="sxs-lookup"><span data-stu-id="ae09d-106">Button Parts</span></span>  
 <span data-ttu-id="ae09d-107"><xref:System.Windows.Controls.Button> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="ae09d-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="ae09d-108">Stany przycisku</span><span class="sxs-lookup"><span data-stu-id="ae09d-108">Button States</span></span>  
 <span data-ttu-id="ae09d-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="ae09d-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="ae09d-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="ae09d-110">VisualState Name</span></span>|<span data-ttu-id="ae09d-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ae09d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ae09d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ae09d-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ae09d-113">Normalny</span><span class="sxs-lookup"><span data-stu-id="ae09d-113">Normal</span></span>|<span data-ttu-id="ae09d-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ae09d-114">CommonStates</span></span>|<span data-ttu-id="ae09d-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="ae09d-115">The default state.</span></span>|  
|<span data-ttu-id="ae09d-116">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="ae09d-116">MouseOver</span></span>|<span data-ttu-id="ae09d-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ae09d-117">CommonStates</span></span>|<span data-ttu-id="ae09d-118">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="ae09d-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="ae09d-119">Naciśnięto</span><span class="sxs-lookup"><span data-stu-id="ae09d-119">Pressed</span></span>|<span data-ttu-id="ae09d-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ae09d-120">CommonStates</span></span>|<span data-ttu-id="ae09d-121">Formant zostanie naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="ae09d-121">The control is pressed.</span></span>|  
|<span data-ttu-id="ae09d-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="ae09d-122">Disabled</span></span>|<span data-ttu-id="ae09d-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ae09d-123">CommonStates</span></span>|<span data-ttu-id="ae09d-124">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="ae09d-124">The control is disabled.</span></span>|  
|<span data-ttu-id="ae09d-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="ae09d-125">Focused</span></span>|<span data-ttu-id="ae09d-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ae09d-126">FocusStates</span></span>|<span data-ttu-id="ae09d-127">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="ae09d-127">The control has focus.</span></span>|  
|<span data-ttu-id="ae09d-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="ae09d-128">Unfocused</span></span>|<span data-ttu-id="ae09d-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ae09d-129">FocusStates</span></span>|<span data-ttu-id="ae09d-130">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="ae09d-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="ae09d-131">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="ae09d-131">Valid</span></span>|<span data-ttu-id="ae09d-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ae09d-132">ValidationStates</span></span>|<span data-ttu-id="ae09d-133">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="ae09d-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ae09d-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ae09d-134">InvalidFocused</span></span>|<span data-ttu-id="ae09d-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ae09d-135">ValidationStates</span></span>|<span data-ttu-id="ae09d-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` i formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="ae09d-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="ae09d-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ae09d-137">InvalidUnfocused</span></span>|<span data-ttu-id="ae09d-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ae09d-138">ValidationStates</span></span>|<span data-ttu-id="ae09d-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` i formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="ae09d-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="ae09d-140">Przykład ControlTemplate przycisku</span><span class="sxs-lookup"><span data-stu-id="ae09d-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="ae09d-141">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="ae09d-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="ae09d-142">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="ae09d-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ae09d-143">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="ae09d-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae09d-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae09d-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="ae09d-145">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="ae09d-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="ae09d-146">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="ae09d-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="ae09d-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="ae09d-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ae09d-148">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ae09d-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
