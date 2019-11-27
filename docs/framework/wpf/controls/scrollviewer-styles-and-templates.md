---
title: ScrollViewer — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: b54dcacf55a750d7c1253db20147d18de47d027e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283397"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="0426c-102">ScrollViewer — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="0426c-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="0426c-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="0426c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="0426c-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="0426c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0426c-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="0426c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="0426c-106">ScrollViewer części</span><span class="sxs-lookup"><span data-stu-id="0426c-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="0426c-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="0426c-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="0426c-108">Części</span><span class="sxs-lookup"><span data-stu-id="0426c-108">Part</span></span>|<span data-ttu-id="0426c-109">Type</span><span class="sxs-lookup"><span data-stu-id="0426c-109">Type</span></span>|<span data-ttu-id="0426c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0426c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0426c-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="0426c-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="0426c-112">Symbol zastępczy zawartości w <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="0426c-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="0426c-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="0426c-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="0426c-114"><xref:System.Windows.Controls.Primitives.ScrollBar> używany do przewijania zawartości w poziomie.</span><span class="sxs-lookup"><span data-stu-id="0426c-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="0426c-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="0426c-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="0426c-116"><xref:System.Windows.Controls.Primitives.ScrollBar> używany do przewijania zawartości w pionie.</span><span class="sxs-lookup"><span data-stu-id="0426c-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="0426c-117">Stany ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="0426c-117">ScrollViewer States</span></span>  
 <span data-ttu-id="0426c-118">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="0426c-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="0426c-119">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="0426c-119">VisualState Name</span></span>|<span data-ttu-id="0426c-120">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="0426c-120">VisualStateGroup Name</span></span>|<span data-ttu-id="0426c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0426c-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0426c-122">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="0426c-122">Valid</span></span>|<span data-ttu-id="0426c-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0426c-123">ValidationStates</span></span>|<span data-ttu-id="0426c-124">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="0426c-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0426c-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0426c-125">InvalidFocused</span></span>|<span data-ttu-id="0426c-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0426c-126">ValidationStates</span></span>|<span data-ttu-id="0426c-127">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="0426c-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="0426c-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0426c-128">InvalidUnfocused</span></span>|<span data-ttu-id="0426c-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0426c-129">ValidationStates</span></span>|<span data-ttu-id="0426c-130">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="0426c-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="0426c-131">Przykład ScrollViewer ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="0426c-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="0426c-132">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="0426c-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="0426c-133">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="0426c-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="0426c-134">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="0426c-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0426c-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0426c-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="0426c-136">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="0426c-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="0426c-137">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="0426c-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="0426c-138">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="0426c-138">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="0426c-139">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="0426c-139">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
