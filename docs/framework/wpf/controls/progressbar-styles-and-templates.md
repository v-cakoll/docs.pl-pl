---
title: ProgressBar — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: f948cf2b4f4cd2a4cb73b0cd5fc754240c850b83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099420"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="1a3b5-102">ProgressBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="1a3b5-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="1a3b5-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.ProgressBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="1a3b5-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1a3b5-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="1a3b5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="1a3b5-106">Części ProgressBar</span><span class="sxs-lookup"><span data-stu-id="1a3b5-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="1a3b5-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.ProgressBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="1a3b5-108">Część</span><span class="sxs-lookup"><span data-stu-id="1a3b5-108">Part</span></span>|<span data-ttu-id="1a3b5-109">Typ</span><span class="sxs-lookup"><span data-stu-id="1a3b5-109">Type</span></span>|<span data-ttu-id="1a3b5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1a3b5-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1a3b5-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="1a3b5-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="1a3b5-112">Obiekt, który wskazuje postęp.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="1a3b5-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="1a3b5-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="1a3b5-114">Obiekt, który określa ścieżkę wskaźnik postępu.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="1a3b5-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="1a3b5-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="1a3b5-116">Obiekt, który embellishes pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="1a3b5-117">Stany ProgressBar</span><span class="sxs-lookup"><span data-stu-id="1a3b5-117">ProgressBar States</span></span>  
 <span data-ttu-id="1a3b5-118">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.ProgressBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="1a3b5-119">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="1a3b5-119">VisualState Name</span></span>|<span data-ttu-id="1a3b5-120">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="1a3b5-120">VisualStateGroup Name</span></span>|<span data-ttu-id="1a3b5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="1a3b5-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="1a3b5-122">Określony</span><span class="sxs-lookup"><span data-stu-id="1a3b5-122">Determinate</span></span>|<span data-ttu-id="1a3b5-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1a3b5-123">CommonStates</span></span>|<xref:System.Windows.Controls.ProgressBar> <span data-ttu-id="1a3b5-124">Raporty postępu na podstawie <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-124">reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="1a3b5-125">Nieokreślony</span><span class="sxs-lookup"><span data-stu-id="1a3b5-125">Indeterminate</span></span>|<span data-ttu-id="1a3b5-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1a3b5-126">CommonStates</span></span>|<xref:System.Windows.Controls.ProgressBar> <span data-ttu-id="1a3b5-127">zgłasza ogólny postęp za pomocą wzorca powtarzania.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-127">reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="1a3b5-128">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="1a3b5-128">Valid</span></span>|<span data-ttu-id="1a3b5-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1a3b5-129">ValidationStates</span></span>|<span data-ttu-id="1a3b5-130">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1a3b5-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1a3b5-131">InvalidFocused</span></span>|<span data-ttu-id="1a3b5-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1a3b5-132">ValidationStates</span></span>|<span data-ttu-id="1a3b5-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1a3b5-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1a3b5-134">InvalidUnfocused</span></span>|<span data-ttu-id="1a3b5-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1a3b5-135">ValidationStates</span></span>|<span data-ttu-id="1a3b5-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="1a3b5-137">Przykład ControlTemplate elementu ProgressBar</span><span class="sxs-lookup"><span data-stu-id="1a3b5-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="1a3b5-138">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ProgressBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="1a3b5-139">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="1a3b5-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1a3b5-140">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="1a3b5-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3b5-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a3b5-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="1a3b5-142">Style i szablony formantu</span><span class="sxs-lookup"><span data-stu-id="1a3b5-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="1a3b5-143">Niestandardowe dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="1a3b5-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="1a3b5-144">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="1a3b5-144">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="1a3b5-145">Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="1a3b5-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
