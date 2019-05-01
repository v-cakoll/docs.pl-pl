---
title: ToolTip — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: 24def466509c12eb69307de139e83dd5a1ed5ce4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790679"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="ea323-102">ToolTip — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="ea323-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="ea323-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.ToolTip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ea323-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="ea323-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ea323-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ea323-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ea323-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="ea323-106">Części etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="ea323-106">ToolTip Parts</span></span>  
 <span data-ttu-id="ea323-107"><xref:System.Windows.Controls.ToolTip> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="ea323-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="ea323-108">Stany etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="ea323-108">ToolTip States</span></span>  
 <span data-ttu-id="ea323-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.ToolTip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ea323-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="ea323-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="ea323-110">VisualState Name</span></span>|<span data-ttu-id="ea323-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ea323-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ea323-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ea323-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ea323-113">Zamknięte</span><span class="sxs-lookup"><span data-stu-id="ea323-113">Closed</span></span>|<span data-ttu-id="ea323-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="ea323-114">OpenStates</span></span>|<span data-ttu-id="ea323-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="ea323-115">The default state.</span></span>|  
|<span data-ttu-id="ea323-116">Otwarcie</span><span class="sxs-lookup"><span data-stu-id="ea323-116">Open</span></span>|<span data-ttu-id="ea323-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="ea323-117">OpenStates</span></span>|<span data-ttu-id="ea323-118"><xref:System.Windows.Controls.ToolTip> Jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="ea323-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="ea323-119">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="ea323-119">Valid</span></span>|<span data-ttu-id="ea323-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea323-120">ValidationStates</span></span>|<span data-ttu-id="ea323-121">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="ea323-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ea323-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ea323-122">InvalidFocused</span></span>|<span data-ttu-id="ea323-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea323-123">ValidationStates</span></span>|<span data-ttu-id="ea323-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="ea323-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ea323-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ea323-125">InvalidUnfocused</span></span>|<span data-ttu-id="ea323-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea323-126">ValidationStates</span></span>|<span data-ttu-id="ea323-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="ea323-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="ea323-128">Przykład ControlTemplate etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="ea323-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="ea323-129">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ToolTip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ea323-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="ea323-130">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="ea323-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ea323-131">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="ea323-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea323-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea323-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ea323-133">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="ea323-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ea323-134">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="ea323-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ea323-135">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="ea323-135">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="ea323-136">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ea323-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
