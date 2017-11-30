---
title: Style i szablony okien
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0415bfae8e1065759efaac1a779655444451fa24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="e519b-102">Style i szablony okien</span><span class="sxs-lookup"><span data-stu-id="e519b-102">Window Styles and Templates</span></span>
<span data-ttu-id="e519b-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Window> formantu.</span><span class="sxs-lookup"><span data-stu-id="e519b-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="e519b-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="e519b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e519b-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e519b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="e519b-106">Części okna</span><span class="sxs-lookup"><span data-stu-id="e519b-106">Window Parts</span></span>  
 <span data-ttu-id="e519b-107"><xref:System.Windows.Window> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="e519b-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="e519b-108">Stany okien</span><span class="sxs-lookup"><span data-stu-id="e519b-108">Window States</span></span>  
 <span data-ttu-id="e519b-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Window> formantu.</span><span class="sxs-lookup"><span data-stu-id="e519b-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="e519b-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="e519b-110">VisualState Name</span></span>|<span data-ttu-id="e519b-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e519b-111">VisualStateGroup Name</span></span>|<span data-ttu-id="e519b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e519b-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e519b-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="e519b-113">Valid</span></span>|<span data-ttu-id="e519b-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e519b-114">ValidationStates</span></span>|<span data-ttu-id="e519b-115">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="e519b-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e519b-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e519b-116">InvalidFocused</span></span>|<span data-ttu-id="e519b-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e519b-117">ValidationStates</span></span>|<span data-ttu-id="e519b-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="e519b-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e519b-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e519b-119">InvalidUnfocused</span></span>|<span data-ttu-id="e519b-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e519b-120">ValidationStates</span></span>|<span data-ttu-id="e519b-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="e519b-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="e519b-122">Przykład ControlTemplate okna</span><span class="sxs-lookup"><span data-stu-id="e519b-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="e519b-123">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Window> formantu.</span><span class="sxs-lookup"><span data-stu-id="e519b-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="e519b-124"><xref:System.Windows.Controls.ControlTemplate> Korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="e519b-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e519b-125">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="e519b-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e519b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e519b-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e519b-127">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="e519b-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="e519b-128">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="e519b-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="e519b-129">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="e519b-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="e519b-130">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e519b-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
