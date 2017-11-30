---
title: "ScrollViewer — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ac02896708744bc9b1c2d017da4e6f56ac32b53a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="6beb2-102">ScrollViewer — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="6beb2-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="6beb2-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.ScrollViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="6beb2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="6beb2-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="6beb2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6beb2-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6beb2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="6beb2-106">Części ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="6beb2-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="6beb2-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.ScrollViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="6beb2-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="6beb2-108">Część</span><span class="sxs-lookup"><span data-stu-id="6beb2-108">Part</span></span>|<span data-ttu-id="6beb2-109">Typ</span><span class="sxs-lookup"><span data-stu-id="6beb2-109">Type</span></span>|<span data-ttu-id="6beb2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6beb2-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6beb2-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="6beb2-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="6beb2-112">Symbol zastępczy zawartości w <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="6beb2-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="6beb2-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="6beb2-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="6beb2-114"><xref:System.Windows.Controls.Primitives.ScrollBar> Umożliwia przewijanie zawartości w poziomie.</span><span class="sxs-lookup"><span data-stu-id="6beb2-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="6beb2-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="6beb2-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="6beb2-116"><xref:System.Windows.Controls.Primitives.ScrollBar> Używane przewijanie zawartości w pionie.</span><span class="sxs-lookup"><span data-stu-id="6beb2-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="6beb2-117">Stany ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="6beb2-117">ScrollViewer States</span></span>  
 <span data-ttu-id="6beb2-118">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.ScrollViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="6beb2-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="6beb2-119">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="6beb2-119">VisualState Name</span></span>|<span data-ttu-id="6beb2-120">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6beb2-120">VisualStateGroup Name</span></span>|<span data-ttu-id="6beb2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="6beb2-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6beb2-122">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="6beb2-122">Valid</span></span>|<span data-ttu-id="6beb2-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6beb2-123">ValidationStates</span></span>|<span data-ttu-id="6beb2-124">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="6beb2-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6beb2-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6beb2-125">InvalidFocused</span></span>|<span data-ttu-id="6beb2-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6beb2-126">ValidationStates</span></span>|<span data-ttu-id="6beb2-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="6beb2-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6beb2-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6beb2-128">InvalidUnfocused</span></span>|<span data-ttu-id="6beb2-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6beb2-129">ValidationStates</span></span>|<span data-ttu-id="6beb2-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="6beb2-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="6beb2-131">Przykład ControlTemplate ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="6beb2-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="6beb2-132">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ScrollViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="6beb2-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="6beb2-133">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="6beb2-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6beb2-134">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="6beb2-134">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6beb2-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6beb2-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="6beb2-136">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="6beb2-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="6beb2-137">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="6beb2-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="6beb2-138">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="6beb2-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="6beb2-139">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6beb2-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
