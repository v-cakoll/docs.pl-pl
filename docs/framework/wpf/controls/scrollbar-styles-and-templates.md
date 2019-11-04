---
title: ScrollBar — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: f30a0abb3e4252737e513b531b8d5f49a0d47f0b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458447"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="47e11-102">ScrollBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="47e11-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="47e11-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="47e11-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="47e11-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="47e11-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="47e11-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="47e11-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="47e11-106">Składniki ScrollBar</span><span class="sxs-lookup"><span data-stu-id="47e11-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="47e11-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="47e11-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="47e11-108">Części</span><span class="sxs-lookup"><span data-stu-id="47e11-108">Part</span></span>|<span data-ttu-id="47e11-109">Typ</span><span class="sxs-lookup"><span data-stu-id="47e11-109">Type</span></span>|<span data-ttu-id="47e11-110">Opis</span><span class="sxs-lookup"><span data-stu-id="47e11-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="47e11-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="47e11-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="47e11-112">Kontener dla elementu, który wskazuje pozycję <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="47e11-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="47e11-113">Stany ScrollBar</span><span class="sxs-lookup"><span data-stu-id="47e11-113">ScrollBar States</span></span>  
 <span data-ttu-id="47e11-114">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="47e11-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="47e11-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="47e11-115">VisualState Name</span></span>|<span data-ttu-id="47e11-116">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="47e11-116">VisualStateGroup Name</span></span>|<span data-ttu-id="47e11-117">Opis</span><span class="sxs-lookup"><span data-stu-id="47e11-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="47e11-118">Typow</span><span class="sxs-lookup"><span data-stu-id="47e11-118">Normal</span></span>|<span data-ttu-id="47e11-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="47e11-119">CommonStates</span></span>|<span data-ttu-id="47e11-120">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="47e11-120">The default state.</span></span>|  
|<span data-ttu-id="47e11-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="47e11-121">MouseOver</span></span>|<span data-ttu-id="47e11-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="47e11-122">CommonStates</span></span>|<span data-ttu-id="47e11-123">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="47e11-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="47e11-124">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="47e11-124">Disabled</span></span>|<span data-ttu-id="47e11-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="47e11-125">CommonStates</span></span>|<span data-ttu-id="47e11-126">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="47e11-126">The control is disabled.</span></span>|  
|<span data-ttu-id="47e11-127">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="47e11-127">Valid</span></span>|<span data-ttu-id="47e11-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="47e11-128">ValidationStates</span></span>|<span data-ttu-id="47e11-129">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="47e11-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="47e11-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="47e11-130">InvalidFocused</span></span>|<span data-ttu-id="47e11-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="47e11-131">ValidationStates</span></span>|<span data-ttu-id="47e11-132">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, a kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="47e11-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="47e11-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="47e11-133">InvalidUnfocused</span></span>|<span data-ttu-id="47e11-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="47e11-134">ValidationStates</span></span>|<span data-ttu-id="47e11-135">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` i formant nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="47e11-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="47e11-136">Przykład ControlTemplate ScrollBar</span><span class="sxs-lookup"><span data-stu-id="47e11-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="47e11-137">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="47e11-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="47e11-138">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="47e11-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="47e11-139">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="47e11-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e11-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47e11-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="47e11-141">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="47e11-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="47e11-142">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="47e11-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="47e11-143">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="47e11-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="47e11-144">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="47e11-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
