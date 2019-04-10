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
ms.openlocfilehash: ebd21829591b8fefe87aeba0b86280f18eff4f06
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203733"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="12c8b-102">Style i szablony okien</span><span class="sxs-lookup"><span data-stu-id="12c8b-102">Window Styles and Templates</span></span>
<span data-ttu-id="12c8b-103">W tym temacie opisano, style i szablony <xref:System.Windows.Window> kontroli.</span><span class="sxs-lookup"><span data-stu-id="12c8b-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="12c8b-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="12c8b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="12c8b-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="12c8b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="12c8b-106">Części okna</span><span class="sxs-lookup"><span data-stu-id="12c8b-106">Window Parts</span></span>  
 <span data-ttu-id="12c8b-107"><xref:System.Windows.Window> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="12c8b-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="12c8b-108">Stany okien</span><span class="sxs-lookup"><span data-stu-id="12c8b-108">Window States</span></span>  
 <span data-ttu-id="12c8b-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Window> kontroli.</span><span class="sxs-lookup"><span data-stu-id="12c8b-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="12c8b-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="12c8b-110">VisualState Name</span></span>|<span data-ttu-id="12c8b-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="12c8b-111">VisualStateGroup Name</span></span>|<span data-ttu-id="12c8b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="12c8b-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="12c8b-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="12c8b-113">Valid</span></span>|<span data-ttu-id="12c8b-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="12c8b-114">ValidationStates</span></span>|<span data-ttu-id="12c8b-115">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="12c8b-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="12c8b-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="12c8b-116">InvalidFocused</span></span>|<span data-ttu-id="12c8b-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="12c8b-117">ValidationStates</span></span>|<span data-ttu-id="12c8b-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="12c8b-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="12c8b-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="12c8b-119">InvalidUnfocused</span></span>|<span data-ttu-id="12c8b-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="12c8b-120">ValidationStates</span></span>|<span data-ttu-id="12c8b-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="12c8b-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="12c8b-122">Przykład ControlTemplate okna</span><span class="sxs-lookup"><span data-stu-id="12c8b-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="12c8b-123">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Window> kontroli.</span><span class="sxs-lookup"><span data-stu-id="12c8b-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="12c8b-124"><xref:System.Windows.Controls.ControlTemplate> Używa co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="12c8b-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="12c8b-125">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="12c8b-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c8b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12c8b-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="12c8b-127">Style i szablony formantu</span><span class="sxs-lookup"><span data-stu-id="12c8b-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="12c8b-128">Niestandardowe dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="12c8b-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="12c8b-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="12c8b-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="12c8b-130">Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="12c8b-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
