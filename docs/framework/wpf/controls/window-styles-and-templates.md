---
title: Style i szablony okien
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
ms.openlocfilehash: 9095405c47d4e113a2f0e7d572ba1209718f4b37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640085"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="d2ce7-102">Style i szablony okien</span><span class="sxs-lookup"><span data-stu-id="d2ce7-102">Window Styles and Templates</span></span>
<span data-ttu-id="d2ce7-103">W tym temacie opisano, style i szablony <xref:System.Windows.Window> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d2ce7-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="d2ce7-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d2ce7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d2ce7-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d2ce7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="d2ce7-106">Części okna</span><span class="sxs-lookup"><span data-stu-id="d2ce7-106">Window Parts</span></span>  
 <span data-ttu-id="d2ce7-107"><xref:System.Windows.Window> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="d2ce7-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="d2ce7-108">Stany okien</span><span class="sxs-lookup"><span data-stu-id="d2ce7-108">Window States</span></span>  
 <span data-ttu-id="d2ce7-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Window> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d2ce7-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="d2ce7-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="d2ce7-110">VisualState Name</span></span>|<span data-ttu-id="d2ce7-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d2ce7-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d2ce7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d2ce7-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d2ce7-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="d2ce7-113">Valid</span></span>|<span data-ttu-id="d2ce7-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2ce7-114">ValidationStates</span></span>|<span data-ttu-id="d2ce7-115">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="d2ce7-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d2ce7-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d2ce7-116">InvalidFocused</span></span>|<span data-ttu-id="d2ce7-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2ce7-117">ValidationStates</span></span>|<span data-ttu-id="d2ce7-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="d2ce7-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d2ce7-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d2ce7-119">InvalidUnfocused</span></span>|<span data-ttu-id="d2ce7-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2ce7-120">ValidationStates</span></span>|<span data-ttu-id="d2ce7-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="d2ce7-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="d2ce7-122">Przykład ControlTemplate okna</span><span class="sxs-lookup"><span data-stu-id="d2ce7-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="d2ce7-123">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Window> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d2ce7-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="d2ce7-124"><xref:System.Windows.Controls.ControlTemplate> Używa co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="d2ce7-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d2ce7-125">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d2ce7-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ce7-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2ce7-126">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d2ce7-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="d2ce7-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="d2ce7-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="d2ce7-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="d2ce7-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="d2ce7-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="d2ce7-130">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d2ce7-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
