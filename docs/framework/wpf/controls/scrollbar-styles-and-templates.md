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
ms.openlocfilehash: 22b2206067302f621a94a1e9abca1607792b3393
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144511"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="05ec9-102">ScrollBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="05ec9-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="05ec9-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Primitives.ScrollBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="05ec9-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="05ec9-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="05ec9-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="05ec9-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="05ec9-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="05ec9-106">Części paska przewijania</span><span class="sxs-lookup"><span data-stu-id="05ec9-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="05ec9-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Primitives.ScrollBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="05ec9-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="05ec9-108">Część</span><span class="sxs-lookup"><span data-stu-id="05ec9-108">Part</span></span>|<span data-ttu-id="05ec9-109">Typ</span><span class="sxs-lookup"><span data-stu-id="05ec9-109">Type</span></span>|<span data-ttu-id="05ec9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="05ec9-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="05ec9-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="05ec9-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="05ec9-112">Kontener dla elementu, który wskazuje pozycję <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="05ec9-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="05ec9-113">Stany paska przewijania</span><span class="sxs-lookup"><span data-stu-id="05ec9-113">ScrollBar States</span></span>  
 <span data-ttu-id="05ec9-114">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.ScrollBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="05ec9-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="05ec9-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="05ec9-115">VisualState Name</span></span>|<span data-ttu-id="05ec9-116">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="05ec9-116">VisualStateGroup Name</span></span>|<span data-ttu-id="05ec9-117">Opis</span><span class="sxs-lookup"><span data-stu-id="05ec9-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="05ec9-118">Normalne</span><span class="sxs-lookup"><span data-stu-id="05ec9-118">Normal</span></span>|<span data-ttu-id="05ec9-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="05ec9-119">CommonStates</span></span>|<span data-ttu-id="05ec9-120">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="05ec9-120">The default state.</span></span>|  
|<span data-ttu-id="05ec9-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="05ec9-121">MouseOver</span></span>|<span data-ttu-id="05ec9-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="05ec9-122">CommonStates</span></span>|<span data-ttu-id="05ec9-123">Wskaźnik myszy jest umieszczony nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="05ec9-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="05ec9-124">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="05ec9-124">Disabled</span></span>|<span data-ttu-id="05ec9-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="05ec9-125">CommonStates</span></span>|<span data-ttu-id="05ec9-126">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="05ec9-126">The control is disabled.</span></span>|  
|<span data-ttu-id="05ec9-127">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="05ec9-127">Valid</span></span>|<span data-ttu-id="05ec9-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="05ec9-128">ValidationStates</span></span>|<span data-ttu-id="05ec9-129">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="05ec9-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="05ec9-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="05ec9-130">InvalidFocused</span></span>|<span data-ttu-id="05ec9-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="05ec9-131">ValidationStates</span></span>|<span data-ttu-id="05ec9-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="05ec9-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="05ec9-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="05ec9-133">InvalidUnfocused</span></span>|<span data-ttu-id="05ec9-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="05ec9-134">ValidationStates</span></span>|<span data-ttu-id="05ec9-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="05ec9-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="05ec9-136">Przykład ControlTemplate paska przewijania</span><span class="sxs-lookup"><span data-stu-id="05ec9-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="05ec9-137">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.ScrollBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="05ec9-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="05ec9-138">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="05ec9-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="05ec9-139">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="05ec9-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ec9-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05ec9-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="05ec9-141">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="05ec9-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="05ec9-142">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="05ec9-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="05ec9-143">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="05ec9-143">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="05ec9-144">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="05ec9-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
