---
title: Style i szablony etykiet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 013d21c7547531541c89435dbbdde65911ae3750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="297d9-102">Style i szablony etykiet</span><span class="sxs-lookup"><span data-stu-id="297d9-102">Label Styles and Templates</span></span>
<span data-ttu-id="297d9-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="297d9-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="297d9-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="297d9-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="297d9-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="297d9-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="297d9-106">Części etykiety</span><span class="sxs-lookup"><span data-stu-id="297d9-106">Label Parts</span></span>  
 <span data-ttu-id="297d9-107"><xref:System.Windows.Controls.Label> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="297d9-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="297d9-108">Etykieta zawiera</span><span class="sxs-lookup"><span data-stu-id="297d9-108">Label States</span></span>  
 <span data-ttu-id="297d9-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="297d9-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="297d9-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="297d9-110">VisualState Name</span></span>|<span data-ttu-id="297d9-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="297d9-111">VisualStateGroup Name</span></span>|<span data-ttu-id="297d9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="297d9-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="297d9-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="297d9-113">Valid</span></span>|<span data-ttu-id="297d9-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="297d9-114">ValidationStates</span></span>|<span data-ttu-id="297d9-115">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="297d9-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="297d9-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="297d9-116">InvalidFocused</span></span>|<span data-ttu-id="297d9-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="297d9-117">ValidationStates</span></span>|<span data-ttu-id="297d9-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="297d9-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="297d9-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="297d9-119">InvalidUnfocused</span></span>|<span data-ttu-id="297d9-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="297d9-120">ValidationStates</span></span>|<span data-ttu-id="297d9-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="297d9-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="297d9-122">Przykład ControlTemplate etykiety</span><span class="sxs-lookup"><span data-stu-id="297d9-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="297d9-123">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="297d9-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="297d9-124"><xref:System.Windows.Controls.ControlTemplate> Korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="297d9-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="297d9-125">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="297d9-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="297d9-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="297d9-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="297d9-127">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="297d9-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="297d9-128">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="297d9-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="297d9-129">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="297d9-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="297d9-130">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="297d9-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
