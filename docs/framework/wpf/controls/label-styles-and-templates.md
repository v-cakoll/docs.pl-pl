---
title: Style i szablony etykiet
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
ms.openlocfilehash: a56b03d2b851f518dc76dd07e5d182688da7111d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="35fb6-102">Style i szablony etykiet</span><span class="sxs-lookup"><span data-stu-id="35fb6-102">Label Styles and Templates</span></span>
<span data-ttu-id="35fb6-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="35fb6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="35fb6-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="35fb6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="35fb6-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="35fb6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="35fb6-106">Części etykiety</span><span class="sxs-lookup"><span data-stu-id="35fb6-106">Label Parts</span></span>  
 <span data-ttu-id="35fb6-107"><xref:System.Windows.Controls.Label> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="35fb6-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="35fb6-108">Etykieta zawiera</span><span class="sxs-lookup"><span data-stu-id="35fb6-108">Label States</span></span>  
 <span data-ttu-id="35fb6-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="35fb6-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="35fb6-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="35fb6-110">VisualState Name</span></span>|<span data-ttu-id="35fb6-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="35fb6-111">VisualStateGroup Name</span></span>|<span data-ttu-id="35fb6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="35fb6-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="35fb6-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="35fb6-113">Valid</span></span>|<span data-ttu-id="35fb6-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="35fb6-114">ValidationStates</span></span>|<span data-ttu-id="35fb6-115">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="35fb6-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="35fb6-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="35fb6-116">InvalidFocused</span></span>|<span data-ttu-id="35fb6-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="35fb6-117">ValidationStates</span></span>|<span data-ttu-id="35fb6-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="35fb6-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="35fb6-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="35fb6-119">InvalidUnfocused</span></span>|<span data-ttu-id="35fb6-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="35fb6-120">ValidationStates</span></span>|<span data-ttu-id="35fb6-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="35fb6-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="35fb6-122">Przykład ControlTemplate etykiety</span><span class="sxs-lookup"><span data-stu-id="35fb6-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="35fb6-123">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="35fb6-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="35fb6-124"><xref:System.Windows.Controls.ControlTemplate> Korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="35fb6-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="35fb6-125">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="35fb6-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fb6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35fb6-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="35fb6-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="35fb6-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="35fb6-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="35fb6-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="35fb6-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="35fb6-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="35fb6-130">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="35fb6-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
