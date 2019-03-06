---
title: StatusBar — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: 42bf7aa672addadbc4205c796c09914fe8f3054d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372480"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="b3839-102">StatusBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="b3839-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="b3839-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Primitives.StatusBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b3839-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="b3839-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b3839-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b3839-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="b3839-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="b3839-106">Części pasek stanu</span><span class="sxs-lookup"><span data-stu-id="b3839-106">StatusBar Parts</span></span>  
 <span data-ttu-id="b3839-107"><xref:System.Windows.Controls.Primitives.StatusBar> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="b3839-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="b3839-108">Stany pasek stanu</span><span class="sxs-lookup"><span data-stu-id="b3839-108">StatusBar States</span></span>  
 <span data-ttu-id="b3839-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.StatusBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b3839-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="b3839-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="b3839-110">VisualState Name</span></span>|<span data-ttu-id="b3839-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="b3839-111">VisualStateGroup Name</span></span>|<span data-ttu-id="b3839-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b3839-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b3839-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="b3839-113">Valid</span></span>|<span data-ttu-id="b3839-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b3839-114">ValidationStates</span></span>|<span data-ttu-id="b3839-115">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="b3839-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b3839-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b3839-116">InvalidFocused</span></span>|<span data-ttu-id="b3839-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b3839-117">ValidationStates</span></span>|<span data-ttu-id="b3839-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="b3839-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b3839-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b3839-119">InvalidUnfocused</span></span>|<span data-ttu-id="b3839-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b3839-120">ValidationStates</span></span>|<span data-ttu-id="b3839-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="b3839-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="b3839-122">Części StatusBarItem</span><span class="sxs-lookup"><span data-stu-id="b3839-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="b3839-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="b3839-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="b3839-124">Stany pasek stanu</span><span class="sxs-lookup"><span data-stu-id="b3839-124">StatusBar States</span></span>  
 <span data-ttu-id="b3839-125">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.StatusBarItem> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b3839-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="b3839-126">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="b3839-126">VisualState Name</span></span>|<span data-ttu-id="b3839-127">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="b3839-127">VisualStateGroup Name</span></span>|<span data-ttu-id="b3839-128">Opis</span><span class="sxs-lookup"><span data-stu-id="b3839-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b3839-129">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="b3839-129">Valid</span></span>|<span data-ttu-id="b3839-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b3839-130">ValidationStates</span></span>|<span data-ttu-id="b3839-131">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="b3839-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b3839-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b3839-132">InvalidFocused</span></span>|<span data-ttu-id="b3839-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b3839-133">ValidationStates</span></span>|<span data-ttu-id="b3839-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="b3839-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b3839-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b3839-135">InvalidUnfocused</span></span>|<span data-ttu-id="b3839-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b3839-136">ValidationStates</span></span>|<span data-ttu-id="b3839-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="b3839-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="b3839-138">Przykład ControlTemplate pasek stanu</span><span class="sxs-lookup"><span data-stu-id="b3839-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="b3839-139">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.StatusBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b3839-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="b3839-140"><xref:System.Windows.Controls.ControlTemplate> Używa co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="b3839-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b3839-141">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="b3839-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3839-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3839-142">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b3839-143">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="b3839-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b3839-144">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="b3839-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b3839-145">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="b3839-145">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="b3839-146">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="b3839-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
