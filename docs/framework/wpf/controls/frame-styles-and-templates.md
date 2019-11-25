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
ms.openlocfilehash: de853198c97c99319bea4a816c9a6eca5dc5d917
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283735"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="90a33-102">Style i szablony klatek</span><span class="sxs-lookup"><span data-stu-id="90a33-102">Frame Styles and Templates</span></span>
<span data-ttu-id="90a33-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="90a33-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="90a33-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="90a33-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="90a33-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="90a33-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="90a33-106">Części ramki</span><span class="sxs-lookup"><span data-stu-id="90a33-106">Frame Parts</span></span>  
 <span data-ttu-id="90a33-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="90a33-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="90a33-108">Części</span><span class="sxs-lookup"><span data-stu-id="90a33-108">Part</span></span>|<span data-ttu-id="90a33-109">Typ</span><span class="sxs-lookup"><span data-stu-id="90a33-109">Type</span></span>|<span data-ttu-id="90a33-110">Opis</span><span class="sxs-lookup"><span data-stu-id="90a33-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="90a33-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="90a33-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="90a33-112">Obszar zawartości.</span><span class="sxs-lookup"><span data-stu-id="90a33-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="90a33-113">Stany ramki</span><span class="sxs-lookup"><span data-stu-id="90a33-113">Frame States</span></span>  
 <span data-ttu-id="90a33-114">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="90a33-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="90a33-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="90a33-115">VisualState Name</span></span>|<span data-ttu-id="90a33-116">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="90a33-116">VisualStateGroup Name</span></span>|<span data-ttu-id="90a33-117">Opis</span><span class="sxs-lookup"><span data-stu-id="90a33-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="90a33-118">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="90a33-118">Valid</span></span>|<span data-ttu-id="90a33-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="90a33-119">ValidationStates</span></span>|<span data-ttu-id="90a33-120">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="90a33-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="90a33-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="90a33-121">InvalidFocused</span></span>|<span data-ttu-id="90a33-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="90a33-122">ValidationStates</span></span>|<span data-ttu-id="90a33-123">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="90a33-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="90a33-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="90a33-124">InvalidUnfocused</span></span>|<span data-ttu-id="90a33-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="90a33-125">ValidationStates</span></span>|<span data-ttu-id="90a33-126">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="90a33-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="90a33-127">Przykład ControlTemplate Frame</span><span class="sxs-lookup"><span data-stu-id="90a33-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="90a33-128">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="90a33-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="90a33-129">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="90a33-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="90a33-130">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="90a33-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a33-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90a33-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="90a33-132">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="90a33-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="90a33-133">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="90a33-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="90a33-134">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="90a33-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="90a33-135">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="90a33-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
