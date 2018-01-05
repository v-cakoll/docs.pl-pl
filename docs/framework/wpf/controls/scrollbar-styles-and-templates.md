---
title: "ScrollBar — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14b40a458b271a4f8b88c167367771235f25c7a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="c1acd-102">ScrollBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="c1acd-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="c1acd-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="c1acd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="c1acd-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="c1acd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c1acd-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c1acd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="c1acd-106">Części paska przewijania</span><span class="sxs-lookup"><span data-stu-id="c1acd-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="c1acd-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="c1acd-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="c1acd-108">Część</span><span class="sxs-lookup"><span data-stu-id="c1acd-108">Part</span></span>|<span data-ttu-id="c1acd-109">Typ</span><span class="sxs-lookup"><span data-stu-id="c1acd-109">Type</span></span>|<span data-ttu-id="c1acd-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c1acd-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c1acd-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="c1acd-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="c1acd-112">Kontener dla elementu, który wskazuje położenie <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="c1acd-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="c1acd-113">Stany pasek przewijania</span><span class="sxs-lookup"><span data-stu-id="c1acd-113">ScrollBar States</span></span>  
 <span data-ttu-id="c1acd-114">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="c1acd-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="c1acd-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="c1acd-115">VisualState Name</span></span>|<span data-ttu-id="c1acd-116">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c1acd-116">VisualStateGroup Name</span></span>|<span data-ttu-id="c1acd-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c1acd-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="c1acd-118">Normalny</span><span class="sxs-lookup"><span data-stu-id="c1acd-118">Normal</span></span>|<span data-ttu-id="c1acd-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c1acd-119">CommonStates</span></span>|<span data-ttu-id="c1acd-120">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="c1acd-120">The default state.</span></span>|  
|<span data-ttu-id="c1acd-121">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="c1acd-121">MouseOver</span></span>|<span data-ttu-id="c1acd-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c1acd-122">CommonStates</span></span>|<span data-ttu-id="c1acd-123">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="c1acd-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="c1acd-124">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="c1acd-124">Disabled</span></span>|<span data-ttu-id="c1acd-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c1acd-125">CommonStates</span></span>|<span data-ttu-id="c1acd-126">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="c1acd-126">The control is disabled.</span></span>|  
|<span data-ttu-id="c1acd-127">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="c1acd-127">Valid</span></span>|<span data-ttu-id="c1acd-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c1acd-128">ValidationStates</span></span>|<span data-ttu-id="c1acd-129">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="c1acd-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c1acd-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c1acd-130">InvalidFocused</span></span>|<span data-ttu-id="c1acd-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c1acd-131">ValidationStates</span></span>|<span data-ttu-id="c1acd-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="c1acd-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c1acd-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c1acd-133">InvalidUnfocused</span></span>|<span data-ttu-id="c1acd-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c1acd-134">ValidationStates</span></span>|<span data-ttu-id="c1acd-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="c1acd-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="c1acd-136">Przykład ControlTemplate pasek przewijania</span><span class="sxs-lookup"><span data-stu-id="c1acd-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="c1acd-137">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="c1acd-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="c1acd-138">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="c1acd-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c1acd-139">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="c1acd-139">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1acd-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1acd-140">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c1acd-141">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="c1acd-141">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c1acd-142">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="c1acd-142">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c1acd-143">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="c1acd-143">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c1acd-144">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c1acd-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
