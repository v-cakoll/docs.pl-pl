---
title: "GroupBox — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a39e09812c54df533fdac27b5bfcaedd3fb93ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="f182f-102">GroupBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="f182f-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="f182f-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.GroupBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="f182f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="f182f-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="f182f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f182f-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f182f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="f182f-106">GroupBox — elementy</span><span class="sxs-lookup"><span data-stu-id="f182f-106">GroupBox Parts</span></span>  
 <span data-ttu-id="f182f-107"><xref:System.Windows.Controls.GroupBox> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="f182f-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="f182f-108">GroupBox — Stany</span><span class="sxs-lookup"><span data-stu-id="f182f-108">GroupBox States</span></span>  
 <span data-ttu-id="f182f-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.GroupBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="f182f-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="f182f-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="f182f-110">VisualState Name</span></span>|<span data-ttu-id="f182f-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f182f-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f182f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f182f-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f182f-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="f182f-113">Valid</span></span>|<span data-ttu-id="f182f-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f182f-114">ValidationStates</span></span>|<span data-ttu-id="f182f-115">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="f182f-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f182f-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f182f-116">InvalidFocused</span></span>|<span data-ttu-id="f182f-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f182f-117">ValidationStates</span></span>|<span data-ttu-id="f182f-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="f182f-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f182f-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f182f-119">InvalidUnfocused</span></span>|<span data-ttu-id="f182f-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f182f-120">ValidationStates</span></span>|<span data-ttu-id="f182f-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="f182f-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="f182f-122">Przykład ControlTemplate GroupBox</span><span class="sxs-lookup"><span data-stu-id="f182f-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="f182f-123">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.GroupBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="f182f-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="f182f-124"><xref:System.Windows.Controls.ControlTemplate> Korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="f182f-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f182f-125">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="f182f-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f182f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f182f-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f182f-127">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="f182f-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f182f-128">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="f182f-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f182f-129">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="f182f-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f182f-130">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f182f-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
