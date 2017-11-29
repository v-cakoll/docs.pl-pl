---
title: "DocumentViewer — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7027fbee6a35b9219e65c9964db9a038e942f14e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="6e956-102">DocumentViewer — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="6e956-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="6e956-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.DocumentViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="6e956-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="6e956-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="6e956-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6e956-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6e956-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="6e956-106">Części DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="6e956-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="6e956-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.DocumentViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="6e956-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="6e956-108">Część</span><span class="sxs-lookup"><span data-stu-id="6e956-108">Part</span></span>|<span data-ttu-id="6e956-109">Typ</span><span class="sxs-lookup"><span data-stu-id="6e956-109">Type</span></span>|<span data-ttu-id="6e956-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6e956-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6e956-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="6e956-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="6e956-112">Zawartość i obszar przewijania.</span><span class="sxs-lookup"><span data-stu-id="6e956-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="6e956-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="6e956-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="6e956-114">Pole wyszukiwania na dole domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6e956-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="6e956-115">Stany DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="6e956-115">DocumentViewer States</span></span>  
 <span data-ttu-id="6e956-116">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.DocumentViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="6e956-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="6e956-117">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="6e956-117">VisualState Name</span></span>|<span data-ttu-id="6e956-118">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6e956-118">VisualStateGroup Name</span></span>|<span data-ttu-id="6e956-119">Opis</span><span class="sxs-lookup"><span data-stu-id="6e956-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6e956-120">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="6e956-120">Valid</span></span>|<span data-ttu-id="6e956-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6e956-121">ValidationStates</span></span>|<span data-ttu-id="6e956-122">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="6e956-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6e956-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6e956-123">InvalidFocused</span></span>|<span data-ttu-id="6e956-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6e956-124">ValidationStates</span></span>|<span data-ttu-id="6e956-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="6e956-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6e956-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6e956-126">InvalidUnfocused</span></span>|<span data-ttu-id="6e956-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6e956-127">ValidationStates</span></span>|<span data-ttu-id="6e956-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="6e956-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="6e956-129">Przykład ControlTemplate DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="6e956-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="6e956-130">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.DocumentViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="6e956-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="6e956-131">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="6e956-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6e956-132">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="6e956-132">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e956-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e956-133">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="6e956-134">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="6e956-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="6e956-135">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="6e956-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="6e956-136">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="6e956-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="6e956-137">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6e956-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
