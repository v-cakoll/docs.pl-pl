---
title: GroupBox — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 539bf5b0ef8772ea469123442d152726d0948be9
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457790"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="9ac04-102">GroupBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="9ac04-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a> <span data-ttu-id="9ac04-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.GroupBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="9ac04-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="9ac04-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="9ac04-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9ac04-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="9ac04-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="9ac04-106">GroupBox — elementy</span><span class="sxs-lookup"><span data-stu-id="9ac04-106">GroupBox Parts</span></span>  
 <span data-ttu-id="9ac04-107"><xref:System.Windows.Controls.GroupBox> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="9ac04-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="9ac04-108">GroupBox — Stany</span><span class="sxs-lookup"><span data-stu-id="9ac04-108">GroupBox States</span></span>  
 <span data-ttu-id="9ac04-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.GroupBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="9ac04-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="9ac04-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="9ac04-110">VisualState Name</span></span>|<span data-ttu-id="9ac04-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="9ac04-111">VisualStateGroup Name</span></span>|<span data-ttu-id="9ac04-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9ac04-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9ac04-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="9ac04-113">Valid</span></span>|<span data-ttu-id="9ac04-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9ac04-114">ValidationStates</span></span>|<span data-ttu-id="9ac04-115">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="9ac04-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9ac04-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9ac04-116">InvalidFocused</span></span>|<span data-ttu-id="9ac04-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9ac04-117">ValidationStates</span></span>|<span data-ttu-id="9ac04-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="9ac04-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9ac04-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9ac04-119">InvalidUnfocused</span></span>|<span data-ttu-id="9ac04-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9ac04-120">ValidationStates</span></span>|<span data-ttu-id="9ac04-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="9ac04-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="9ac04-122">Przykład ControlTemplate GroupBox</span><span class="sxs-lookup"><span data-stu-id="9ac04-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="9ac04-123">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.GroupBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="9ac04-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="9ac04-124"><xref:System.Windows.Controls.ControlTemplate> Korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="9ac04-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9ac04-125">Pełny przykład, zobacz [style próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="9ac04-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac04-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ac04-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="9ac04-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="9ac04-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="9ac04-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="9ac04-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="9ac04-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="9ac04-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="9ac04-130">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9ac04-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
