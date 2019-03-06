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
ms.openlocfilehash: 5cd92a4cda40fd850824ae601821dab08c7389e6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370114"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="9cebc-102">ScrollViewer — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="9cebc-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="9cebc-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.ScrollViewer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9cebc-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="9cebc-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9cebc-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9cebc-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="9cebc-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="9cebc-106">Części ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="9cebc-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="9cebc-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.ScrollViewer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9cebc-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="9cebc-108">Część</span><span class="sxs-lookup"><span data-stu-id="9cebc-108">Part</span></span>|<span data-ttu-id="9cebc-109">Typ</span><span class="sxs-lookup"><span data-stu-id="9cebc-109">Type</span></span>|<span data-ttu-id="9cebc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9cebc-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9cebc-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="9cebc-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="9cebc-112">Symbol zastępczy zawartości <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="9cebc-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="9cebc-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="9cebc-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="9cebc-114"><xref:System.Windows.Controls.Primitives.ScrollBar> Umożliwia przewijanie zawartości w poziomie.</span><span class="sxs-lookup"><span data-stu-id="9cebc-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="9cebc-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="9cebc-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="9cebc-116"><xref:System.Windows.Controls.Primitives.ScrollBar> Umożliwia przewijanie zawartości w pionie.</span><span class="sxs-lookup"><span data-stu-id="9cebc-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="9cebc-117">Stany ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="9cebc-117">ScrollViewer States</span></span>  
 <span data-ttu-id="9cebc-118">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.ScrollViewer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9cebc-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="9cebc-119">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="9cebc-119">VisualState Name</span></span>|<span data-ttu-id="9cebc-120">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="9cebc-120">VisualStateGroup Name</span></span>|<span data-ttu-id="9cebc-121">Opis</span><span class="sxs-lookup"><span data-stu-id="9cebc-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9cebc-122">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="9cebc-122">Valid</span></span>|<span data-ttu-id="9cebc-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9cebc-123">ValidationStates</span></span>|<span data-ttu-id="9cebc-124">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="9cebc-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9cebc-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9cebc-125">InvalidFocused</span></span>|<span data-ttu-id="9cebc-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9cebc-126">ValidationStates</span></span>|<span data-ttu-id="9cebc-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="9cebc-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9cebc-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9cebc-128">InvalidUnfocused</span></span>|<span data-ttu-id="9cebc-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9cebc-129">ValidationStates</span></span>|<span data-ttu-id="9cebc-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="9cebc-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="9cebc-131">Przykład ControlTemplate ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="9cebc-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="9cebc-132">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ScrollViewer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9cebc-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="9cebc-133">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="9cebc-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9cebc-134">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="9cebc-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cebc-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cebc-135">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="9cebc-136">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="9cebc-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="9cebc-137">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="9cebc-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="9cebc-138">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="9cebc-138">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="9cebc-139">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9cebc-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
