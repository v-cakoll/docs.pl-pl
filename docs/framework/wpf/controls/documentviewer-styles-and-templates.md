---
title: DocumentViewer — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
ms.openlocfilehash: 7ac68e8666a0de5cf683e3c4186d7805168dadb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581009"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="2d2b4-102">DocumentViewer — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="2d2b4-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="2d2b4-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.DocumentViewer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="2d2b4-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2d2b4-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2d2b4-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="2d2b4-106">DocumentViewer — elementy</span><span class="sxs-lookup"><span data-stu-id="2d2b4-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="2d2b4-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.DocumentViewer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="2d2b4-108">Część</span><span class="sxs-lookup"><span data-stu-id="2d2b4-108">Part</span></span>|<span data-ttu-id="2d2b4-109">Typ</span><span class="sxs-lookup"><span data-stu-id="2d2b4-109">Type</span></span>|<span data-ttu-id="2d2b4-110">Opis</span><span class="sxs-lookup"><span data-stu-id="2d2b4-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d2b4-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="2d2b4-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="2d2b4-112">Zawartość i obszar przewijania.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="2d2b4-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="2d2b4-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="2d2b4-114">Pola wyszukiwania u dołu domyślnie.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="2d2b4-115">DocumentViewer — Stany</span><span class="sxs-lookup"><span data-stu-id="2d2b4-115">DocumentViewer States</span></span>  
 <span data-ttu-id="2d2b4-116">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.DocumentViewer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="2d2b4-117">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="2d2b4-117">VisualState Name</span></span>|<span data-ttu-id="2d2b4-118">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2d2b4-118">VisualStateGroup Name</span></span>|<span data-ttu-id="2d2b4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2d2b4-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d2b4-120">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="2d2b4-120">Valid</span></span>|<span data-ttu-id="2d2b4-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d2b4-121">ValidationStates</span></span>|<span data-ttu-id="2d2b4-122">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2d2b4-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2d2b4-123">InvalidFocused</span></span>|<span data-ttu-id="2d2b4-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d2b4-124">ValidationStates</span></span>|<span data-ttu-id="2d2b4-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2d2b4-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2d2b4-126">InvalidUnfocused</span></span>|<span data-ttu-id="2d2b4-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d2b4-127">ValidationStates</span></span>|<span data-ttu-id="2d2b4-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="2d2b4-129">DocumentViewer — ControlTemplate przykład</span><span class="sxs-lookup"><span data-stu-id="2d2b4-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="2d2b4-130">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.DocumentViewer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="2d2b4-131">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="2d2b4-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2d2b4-132">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2d2b4-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2b4-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d2b4-133">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2d2b4-134">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="2d2b4-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="2d2b4-135">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="2d2b4-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="2d2b4-136">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="2d2b4-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="2d2b4-137">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="2d2b4-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
