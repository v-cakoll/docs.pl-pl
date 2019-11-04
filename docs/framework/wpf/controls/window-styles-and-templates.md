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
ms.openlocfilehash: 48fe5887ebad86efad1b1aae39ba03a26fda3bd8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460021"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="beac0-102">Style i szablony okien</span><span class="sxs-lookup"><span data-stu-id="beac0-102">Window Styles and Templates</span></span>
<span data-ttu-id="beac0-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="beac0-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="beac0-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="beac0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="beac0-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="beac0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="beac0-106">Części okna</span><span class="sxs-lookup"><span data-stu-id="beac0-106">Window Parts</span></span>  
 <span data-ttu-id="beac0-107">Formant <xref:System.Windows.Window> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="beac0-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="beac0-108">Stany okna</span><span class="sxs-lookup"><span data-stu-id="beac0-108">Window States</span></span>  
 <span data-ttu-id="beac0-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="beac0-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="beac0-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="beac0-110">VisualState Name</span></span>|<span data-ttu-id="beac0-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="beac0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="beac0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="beac0-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="beac0-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="beac0-113">Valid</span></span>|<span data-ttu-id="beac0-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="beac0-114">ValidationStates</span></span>|<span data-ttu-id="beac0-115">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="beac0-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="beac0-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="beac0-116">InvalidFocused</span></span>|<span data-ttu-id="beac0-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="beac0-117">ValidationStates</span></span>|<span data-ttu-id="beac0-118">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="beac0-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="beac0-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="beac0-119">InvalidUnfocused</span></span>|<span data-ttu-id="beac0-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="beac0-120">ValidationStates</span></span>|<span data-ttu-id="beac0-121">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="beac0-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="beac0-122">Przykład okna ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="beac0-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="beac0-123">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="beac0-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="beac0-124"><xref:System.Windows.Controls.ControlTemplate> używa co najmniej jednego z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="beac0-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="beac0-125">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="beac0-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beac0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="beac0-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="beac0-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="beac0-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="beac0-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="beac0-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="beac0-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="beac0-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="beac0-130">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="beac0-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
