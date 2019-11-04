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
ms.openlocfilehash: 3a1bea39ba9b6d2cff9937a3fee1d1de41daf16b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459873"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="b770c-102">ProgressBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="b770c-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="b770c-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="b770c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="b770c-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="b770c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b770c-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="b770c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="b770c-106">Składniki ProgressBar</span><span class="sxs-lookup"><span data-stu-id="b770c-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="b770c-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="b770c-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="b770c-108">Części</span><span class="sxs-lookup"><span data-stu-id="b770c-108">Part</span></span>|<span data-ttu-id="b770c-109">Typ</span><span class="sxs-lookup"><span data-stu-id="b770c-109">Type</span></span>|<span data-ttu-id="b770c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b770c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b770c-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="b770c-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="b770c-112">Obiekt, który wskazuje postęp.</span><span class="sxs-lookup"><span data-stu-id="b770c-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="b770c-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="b770c-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="b770c-114">Obiekt, który definiuje ścieżkę wskaźnika postępu.</span><span class="sxs-lookup"><span data-stu-id="b770c-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="b770c-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="b770c-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="b770c-116">Obiekt, który przyozdobuje pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="b770c-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="b770c-117">ProgressBar — Stany</span><span class="sxs-lookup"><span data-stu-id="b770c-117">ProgressBar States</span></span>  
 <span data-ttu-id="b770c-118">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="b770c-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="b770c-119">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="b770c-119">VisualState Name</span></span>|<span data-ttu-id="b770c-120">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="b770c-120">VisualStateGroup Name</span></span>|<span data-ttu-id="b770c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b770c-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="b770c-122">Przerwij</span><span class="sxs-lookup"><span data-stu-id="b770c-122">Determinate</span></span>|<span data-ttu-id="b770c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b770c-123">CommonStates</span></span>|<span data-ttu-id="b770c-124"><xref:System.Windows.Controls.ProgressBar> raportuje postęp na podstawie właściwości <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="b770c-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="b770c-125">Określona</span><span class="sxs-lookup"><span data-stu-id="b770c-125">Indeterminate</span></span>|<span data-ttu-id="b770c-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b770c-126">CommonStates</span></span>|<span data-ttu-id="b770c-127"><xref:System.Windows.Controls.ProgressBar> raportuje ogólny postęp z powtarzalnym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="b770c-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="b770c-128">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="b770c-128">Valid</span></span>|<span data-ttu-id="b770c-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b770c-129">ValidationStates</span></span>|<span data-ttu-id="b770c-130">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="b770c-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b770c-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b770c-131">InvalidFocused</span></span>|<span data-ttu-id="b770c-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b770c-132">ValidationStates</span></span>|<span data-ttu-id="b770c-133">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="b770c-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b770c-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b770c-134">InvalidUnfocused</span></span>|<span data-ttu-id="b770c-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b770c-135">ValidationStates</span></span>|<span data-ttu-id="b770c-136">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="b770c-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="b770c-137">Przykład ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="b770c-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="b770c-138">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="b770c-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="b770c-139">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="b770c-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b770c-140">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="b770c-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b770c-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b770c-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b770c-142">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="b770c-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b770c-143">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="b770c-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b770c-144">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="b770c-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="b770c-145">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="b770c-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
