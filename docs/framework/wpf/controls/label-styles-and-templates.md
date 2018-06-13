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
ms.openlocfilehash: 9d2f5e4d886d8fc46ecb14dd4f1bda67debdae97
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457647"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="27904-102">Style i szablony etykiet</span><span class="sxs-lookup"><span data-stu-id="27904-102">Label Styles and Templates</span></span>
<span data-ttu-id="27904-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="27904-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="27904-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="27904-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="27904-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="27904-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="27904-106">Części etykiety</span><span class="sxs-lookup"><span data-stu-id="27904-106">Label Parts</span></span>  
 <span data-ttu-id="27904-107"><xref:System.Windows.Controls.Label> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="27904-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="27904-108">Etykieta zawiera</span><span class="sxs-lookup"><span data-stu-id="27904-108">Label States</span></span>  
 <span data-ttu-id="27904-109">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="27904-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="27904-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="27904-110">VisualState Name</span></span>|<span data-ttu-id="27904-111">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="27904-111">VisualStateGroup Name</span></span>|<span data-ttu-id="27904-112">Opis</span><span class="sxs-lookup"><span data-stu-id="27904-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="27904-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="27904-113">Valid</span></span>|<span data-ttu-id="27904-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="27904-114">ValidationStates</span></span>|<span data-ttu-id="27904-115">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="27904-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="27904-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="27904-116">InvalidFocused</span></span>|<span data-ttu-id="27904-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="27904-117">ValidationStates</span></span>|<span data-ttu-id="27904-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="27904-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="27904-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="27904-119">InvalidUnfocused</span></span>|<span data-ttu-id="27904-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="27904-120">ValidationStates</span></span>|<span data-ttu-id="27904-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="27904-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="27904-122">Przykład ControlTemplate etykiety</span><span class="sxs-lookup"><span data-stu-id="27904-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="27904-123">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Label> formantu.</span><span class="sxs-lookup"><span data-stu-id="27904-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="27904-124"><xref:System.Windows.Controls.ControlTemplate> Korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="27904-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="27904-125">Pełny przykład, zobacz [style próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="27904-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27904-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27904-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="27904-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="27904-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="27904-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="27904-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="27904-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="27904-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="27904-130">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="27904-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
