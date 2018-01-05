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
ms.workload: dotnet
ms.openlocfilehash: e1e623d9150f4848127cf662f583873e8e85f022
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="84418-102">Style i szablony okien</span><span class="sxs-lookup"><span data-stu-id="84418-102">Window Styles and Templates</span></span>
<span data-ttu-id="84418-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Window> formantu.</span><span class="sxs-lookup"><span data-stu-id="84418-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="84418-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="84418-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="84418-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="84418-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="84418-106">Części okna</span><span class="sxs-lookup"><span data-stu-id="84418-106">Window Parts</span></span>  
 <span data-ttu-id="84418-107"><xref:System.Windows.Window> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="84418-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="84418-108">Stany okien</span><span class="sxs-lookup"><span data-stu-id="84418-108">Window States</span></span>  
 <span data-ttu-id="84418-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Window> formantu.</span><span class="sxs-lookup"><span data-stu-id="84418-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="84418-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="84418-110">VisualState Name</span></span>|<span data-ttu-id="84418-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="84418-111">VisualStateGroup Name</span></span>|<span data-ttu-id="84418-112">Opis</span><span class="sxs-lookup"><span data-stu-id="84418-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="84418-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="84418-113">Valid</span></span>|<span data-ttu-id="84418-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="84418-114">ValidationStates</span></span>|<span data-ttu-id="84418-115">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="84418-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="84418-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="84418-116">InvalidFocused</span></span>|<span data-ttu-id="84418-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="84418-117">ValidationStates</span></span>|<span data-ttu-id="84418-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="84418-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="84418-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="84418-119">InvalidUnfocused</span></span>|<span data-ttu-id="84418-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="84418-120">ValidationStates</span></span>|<span data-ttu-id="84418-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="84418-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="84418-122">Przykład ControlTemplate okna</span><span class="sxs-lookup"><span data-stu-id="84418-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="84418-123">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Window> formantu.</span><span class="sxs-lookup"><span data-stu-id="84418-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="84418-124"><xref:System.Windows.Controls.ControlTemplate> Korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="84418-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="84418-125">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="84418-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84418-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84418-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="84418-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="84418-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="84418-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="84418-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="84418-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="84418-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="84418-130">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="84418-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
