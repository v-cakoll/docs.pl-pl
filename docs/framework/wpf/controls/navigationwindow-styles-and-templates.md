---
title: "NavigationWindow — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b48b0b4451f0cf93b86ee448db255f337a859b74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="0c221-102">NavigationWindow — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="0c221-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="0c221-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Navigation.NavigationWindow> formantu.</span><span class="sxs-lookup"><span data-stu-id="0c221-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="0c221-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="0c221-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0c221-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="0c221-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="0c221-106">Części NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="0c221-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="0c221-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Navigation.NavigationWindow> formantu.</span><span class="sxs-lookup"><span data-stu-id="0c221-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="0c221-108">Część</span><span class="sxs-lookup"><span data-stu-id="0c221-108">Part</span></span>|<span data-ttu-id="0c221-109">Typ</span><span class="sxs-lookup"><span data-stu-id="0c221-109">Type</span></span>|<span data-ttu-id="0c221-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0c221-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0c221-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="0c221-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="0c221-112">Obszar zawartości.</span><span class="sxs-lookup"><span data-stu-id="0c221-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="0c221-113">Stany NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="0c221-113">NavigationWindow States</span></span>  
 <span data-ttu-id="0c221-114">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Navigation.NavigationWindow> formantu.</span><span class="sxs-lookup"><span data-stu-id="0c221-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="0c221-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="0c221-115">VisualState Name</span></span>|<span data-ttu-id="0c221-116">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="0c221-116">VisualStateGroup Name</span></span>|<span data-ttu-id="0c221-117">Opis</span><span class="sxs-lookup"><span data-stu-id="0c221-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0c221-118">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="0c221-118">Valid</span></span>|<span data-ttu-id="0c221-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0c221-119">ValidationStates</span></span>|<span data-ttu-id="0c221-120">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="0c221-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0c221-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0c221-121">InvalidFocused</span></span>|<span data-ttu-id="0c221-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0c221-122">ValidationStates</span></span>|<span data-ttu-id="0c221-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="0c221-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="0c221-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0c221-124">InvalidUnfocused</span></span>|<span data-ttu-id="0c221-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0c221-125">ValidationStates</span></span>|<span data-ttu-id="0c221-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="0c221-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="0c221-127">Przykład ControlTemplate NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="0c221-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="0c221-128">Chociaż ten przykład zawiera wszystkie elementy, które są zdefiniowane w <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Navigation.NavigationWindow> domyślnie określone wartości należy traktować jako przykłady.</span><span class="sxs-lookup"><span data-stu-id="0c221-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="0c221-129">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="0c221-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="0c221-130">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="0c221-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c221-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c221-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="0c221-132">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="0c221-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="0c221-133">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="0c221-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="0c221-134">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="0c221-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="0c221-135">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="0c221-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
