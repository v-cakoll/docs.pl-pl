---
title: Style i szablony klatek
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
ms.openlocfilehash: 6b084cfa31efebe2456871a99cd810741aa26609
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131029"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="9eb27-102">Style i szablony klatek</span><span class="sxs-lookup"><span data-stu-id="9eb27-102">Frame Styles and Templates</span></span>
<span data-ttu-id="9eb27-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Frame> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9eb27-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="9eb27-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9eb27-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9eb27-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="9eb27-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="9eb27-106">Części ramki</span><span class="sxs-lookup"><span data-stu-id="9eb27-106">Frame Parts</span></span>  
 <span data-ttu-id="9eb27-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Frame> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9eb27-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="9eb27-108">Część</span><span class="sxs-lookup"><span data-stu-id="9eb27-108">Part</span></span>|<span data-ttu-id="9eb27-109">Typ</span><span class="sxs-lookup"><span data-stu-id="9eb27-109">Type</span></span>|<span data-ttu-id="9eb27-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9eb27-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9eb27-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="9eb27-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="9eb27-112">Obszar zawartości.</span><span class="sxs-lookup"><span data-stu-id="9eb27-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="9eb27-113">Stany ramki</span><span class="sxs-lookup"><span data-stu-id="9eb27-113">Frame States</span></span>  
 <span data-ttu-id="9eb27-114">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Frame> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9eb27-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="9eb27-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="9eb27-115">VisualState Name</span></span>|<span data-ttu-id="9eb27-116">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="9eb27-116">VisualStateGroup Name</span></span>|<span data-ttu-id="9eb27-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9eb27-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9eb27-118">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="9eb27-118">Valid</span></span>|<span data-ttu-id="9eb27-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9eb27-119">ValidationStates</span></span>|<span data-ttu-id="9eb27-120">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="9eb27-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9eb27-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9eb27-121">InvalidFocused</span></span>|<span data-ttu-id="9eb27-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9eb27-122">ValidationStates</span></span>|<span data-ttu-id="9eb27-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="9eb27-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9eb27-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9eb27-124">InvalidUnfocused</span></span>|<span data-ttu-id="9eb27-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9eb27-125">ValidationStates</span></span>|<span data-ttu-id="9eb27-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="9eb27-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="9eb27-127">Przykład ControlTemplate ramki</span><span class="sxs-lookup"><span data-stu-id="9eb27-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="9eb27-128">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Frame> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9eb27-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="9eb27-129">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="9eb27-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9eb27-130">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="9eb27-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb27-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9eb27-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="9eb27-132">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="9eb27-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="9eb27-133">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="9eb27-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="9eb27-134">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="9eb27-134">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="9eb27-135">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9eb27-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
