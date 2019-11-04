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
ms.openlocfilehash: b1dd575d58571b845fc849ca432ad440d1ce3ec4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458264"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="ede42-102">StatusBar — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="ede42-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="ede42-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="ede42-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="ede42-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="ede42-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ede42-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ede42-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="ede42-106">StatusBar części</span><span class="sxs-lookup"><span data-stu-id="ede42-106">StatusBar Parts</span></span>  
 <span data-ttu-id="ede42-107">Formant <xref:System.Windows.Controls.Primitives.StatusBar> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="ede42-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="ede42-108">Stany StatusBar</span><span class="sxs-lookup"><span data-stu-id="ede42-108">StatusBar States</span></span>  
 <span data-ttu-id="ede42-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="ede42-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="ede42-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="ede42-110">VisualState Name</span></span>|<span data-ttu-id="ede42-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ede42-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ede42-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ede42-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ede42-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="ede42-113">Valid</span></span>|<span data-ttu-id="ede42-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ede42-114">ValidationStates</span></span>|<span data-ttu-id="ede42-115">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="ede42-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ede42-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ede42-116">InvalidFocused</span></span>|<span data-ttu-id="ede42-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ede42-117">ValidationStates</span></span>|<span data-ttu-id="ede42-118">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="ede42-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ede42-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ede42-119">InvalidUnfocused</span></span>|<span data-ttu-id="ede42-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ede42-120">ValidationStates</span></span>|<span data-ttu-id="ede42-121">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="ede42-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="ede42-122">StatusBarItem części</span><span class="sxs-lookup"><span data-stu-id="ede42-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="ede42-123">Formant <xref:System.Windows.Controls.Primitives.StatusBarItem> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="ede42-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="ede42-124">Stany StatusBar</span><span class="sxs-lookup"><span data-stu-id="ede42-124">StatusBar States</span></span>  
 <span data-ttu-id="ede42-125">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.StatusBarItem>.</span><span class="sxs-lookup"><span data-stu-id="ede42-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="ede42-126">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="ede42-126">VisualState Name</span></span>|<span data-ttu-id="ede42-127">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ede42-127">VisualStateGroup Name</span></span>|<span data-ttu-id="ede42-128">Opis</span><span class="sxs-lookup"><span data-stu-id="ede42-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ede42-129">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="ede42-129">Valid</span></span>|<span data-ttu-id="ede42-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ede42-130">ValidationStates</span></span>|<span data-ttu-id="ede42-131">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="ede42-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ede42-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ede42-132">InvalidFocused</span></span>|<span data-ttu-id="ede42-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ede42-133">ValidationStates</span></span>|<span data-ttu-id="ede42-134">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="ede42-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ede42-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ede42-135">InvalidUnfocused</span></span>|<span data-ttu-id="ede42-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ede42-136">ValidationStates</span></span>|<span data-ttu-id="ede42-137">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="ede42-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="ede42-138">Przykład StatusBar ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ede42-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="ede42-139">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="ede42-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="ede42-140"><xref:System.Windows.Controls.ControlTemplate> używa co najmniej jednego z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="ede42-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ede42-141">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="ede42-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede42-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ede42-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ede42-143">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="ede42-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ede42-144">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="ede42-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ede42-145">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="ede42-145">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ede42-146">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ede42-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
