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
ms.workload: dotnet
ms.openlocfilehash: 74f8a693a143e1c6788dd79a1c1bbd1954f8cfd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="fecdd-102">ScrollViewer — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="fecdd-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="fecdd-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.ScrollViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="fecdd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="fecdd-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="fecdd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fecdd-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="fecdd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="fecdd-106">Części ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="fecdd-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="fecdd-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.ScrollViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="fecdd-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="fecdd-108">Część</span><span class="sxs-lookup"><span data-stu-id="fecdd-108">Part</span></span>|<span data-ttu-id="fecdd-109">Typ</span><span class="sxs-lookup"><span data-stu-id="fecdd-109">Type</span></span>|<span data-ttu-id="fecdd-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fecdd-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fecdd-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="fecdd-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="fecdd-112">Symbol zastępczy zawartości w <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="fecdd-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="fecdd-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="fecdd-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="fecdd-114"><xref:System.Windows.Controls.Primitives.ScrollBar> Umożliwia przewijanie zawartości w poziomie.</span><span class="sxs-lookup"><span data-stu-id="fecdd-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="fecdd-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="fecdd-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="fecdd-116"><xref:System.Windows.Controls.Primitives.ScrollBar> Używane przewijanie zawartości w pionie.</span><span class="sxs-lookup"><span data-stu-id="fecdd-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="fecdd-117">Stany ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="fecdd-117">ScrollViewer States</span></span>  
 <span data-ttu-id="fecdd-118">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.ScrollViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="fecdd-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="fecdd-119">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="fecdd-119">VisualState Name</span></span>|<span data-ttu-id="fecdd-120">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="fecdd-120">VisualStateGroup Name</span></span>|<span data-ttu-id="fecdd-121">Opis</span><span class="sxs-lookup"><span data-stu-id="fecdd-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fecdd-122">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="fecdd-122">Valid</span></span>|<span data-ttu-id="fecdd-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fecdd-123">ValidationStates</span></span>|<span data-ttu-id="fecdd-124">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="fecdd-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="fecdd-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fecdd-125">InvalidFocused</span></span>|<span data-ttu-id="fecdd-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fecdd-126">ValidationStates</span></span>|<span data-ttu-id="fecdd-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="fecdd-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="fecdd-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fecdd-128">InvalidUnfocused</span></span>|<span data-ttu-id="fecdd-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fecdd-129">ValidationStates</span></span>|<span data-ttu-id="fecdd-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="fecdd-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="fecdd-131">Przykład ControlTemplate ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="fecdd-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="fecdd-132">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ScrollViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="fecdd-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="fecdd-133">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="fecdd-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="fecdd-134">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="fecdd-134">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fecdd-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fecdd-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="fecdd-136">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="fecdd-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="fecdd-137">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="fecdd-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="fecdd-138">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="fecdd-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="fecdd-139">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="fecdd-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
