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
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671982"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="b177f-102">ScrollBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="b177f-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="b177f-103">W tym temacie opisano style i szablony dla <xref:System.Windows.Controls.Primitives.ScrollBar> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b177f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="b177f-104">Można zmienić wartość domyślną <xref:System.Windows.Controls.ControlTemplate> , aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="b177f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b177f-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="b177f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="b177f-106">Składniki ScrollBar</span><span class="sxs-lookup"><span data-stu-id="b177f-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="b177f-107">W poniższej tabeli wymieniono nazwane części <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="b177f-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="b177f-108">Części</span><span class="sxs-lookup"><span data-stu-id="b177f-108">Part</span></span>|<span data-ttu-id="b177f-109">Typ</span><span class="sxs-lookup"><span data-stu-id="b177f-109">Type</span></span>|<span data-ttu-id="b177f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b177f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b177f-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="b177f-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="b177f-112">Kontener dla elementu, który wskazuje pozycję <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="b177f-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="b177f-113">Stany ScrollBar</span><span class="sxs-lookup"><span data-stu-id="b177f-113">ScrollBar States</span></span>  
 <span data-ttu-id="b177f-114">Poniższa tabela zawiera listę stanów wizualnych <xref:System.Windows.Controls.Primitives.ScrollBar> dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b177f-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="b177f-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="b177f-115">VisualState Name</span></span>|<span data-ttu-id="b177f-116">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="b177f-116">VisualStateGroup Name</span></span>|<span data-ttu-id="b177f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b177f-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="b177f-118">Normalne</span><span class="sxs-lookup"><span data-stu-id="b177f-118">Normal</span></span>|<span data-ttu-id="b177f-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b177f-119">CommonStates</span></span>|<span data-ttu-id="b177f-120">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="b177f-120">The default state.</span></span>|  
|<span data-ttu-id="b177f-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="b177f-121">MouseOver</span></span>|<span data-ttu-id="b177f-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b177f-122">CommonStates</span></span>|<span data-ttu-id="b177f-123">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="b177f-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="b177f-124">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="b177f-124">Disabled</span></span>|<span data-ttu-id="b177f-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b177f-125">CommonStates</span></span>|<span data-ttu-id="b177f-126">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="b177f-126">The control is disabled.</span></span>|  
|<span data-ttu-id="b177f-127">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="b177f-127">Valid</span></span>|<span data-ttu-id="b177f-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b177f-128">ValidationStates</span></span>|<span data-ttu-id="b177f-129">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> i dołączonej właściwości to `false`.</span><span class="sxs-lookup"><span data-stu-id="b177f-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b177f-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b177f-130">InvalidFocused</span></span>|<span data-ttu-id="b177f-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b177f-131">ValidationStates</span></span>|<span data-ttu-id="b177f-132">Dołączona właściwość jest `true` i ma fokus. <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b177f-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="b177f-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b177f-133">InvalidUnfocused</span></span>|<span data-ttu-id="b177f-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b177f-134">ValidationStates</span></span>|<span data-ttu-id="b177f-135">Dołączona właściwość jest `true` i formant nie ma fokusu. <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b177f-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="b177f-136">Przykład ControlTemplate ScrollBar</span><span class="sxs-lookup"><span data-stu-id="b177f-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="b177f-137">Poniższy przykład pokazuje, <xref:System.Windows.Controls.ControlTemplate> jak zdefiniować <xref:System.Windows.Controls.Primitives.ScrollBar> dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b177f-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="b177f-138">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="b177f-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b177f-139">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="b177f-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b177f-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b177f-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b177f-141">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="b177f-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b177f-142">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="b177f-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b177f-143">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="b177f-143">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="b177f-144">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="b177f-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
