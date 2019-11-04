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
ms.openlocfilehash: 7a812ff913703e3aa8408da8a11d28ee5adfa7fd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460347"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="85600-102">DocumentViewer — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="85600-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="85600-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="85600-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="85600-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="85600-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="85600-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="85600-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="85600-106">DocumentViewer części</span><span class="sxs-lookup"><span data-stu-id="85600-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="85600-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="85600-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="85600-108">Części</span><span class="sxs-lookup"><span data-stu-id="85600-108">Part</span></span>|<span data-ttu-id="85600-109">Typ</span><span class="sxs-lookup"><span data-stu-id="85600-109">Type</span></span>|<span data-ttu-id="85600-110">Opis</span><span class="sxs-lookup"><span data-stu-id="85600-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="85600-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="85600-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="85600-112">Obszar zawartość i przewijanie.</span><span class="sxs-lookup"><span data-stu-id="85600-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="85600-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="85600-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="85600-114">Pole wyszukiwania na dole domyślnie.</span><span class="sxs-lookup"><span data-stu-id="85600-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="85600-115">Stany DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="85600-115">DocumentViewer States</span></span>  
 <span data-ttu-id="85600-116">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="85600-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="85600-117">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="85600-117">VisualState Name</span></span>|<span data-ttu-id="85600-118">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="85600-118">VisualStateGroup Name</span></span>|<span data-ttu-id="85600-119">Opis</span><span class="sxs-lookup"><span data-stu-id="85600-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="85600-120">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="85600-120">Valid</span></span>|<span data-ttu-id="85600-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="85600-121">ValidationStates</span></span>|<span data-ttu-id="85600-122">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="85600-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="85600-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="85600-123">InvalidFocused</span></span>|<span data-ttu-id="85600-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="85600-124">ValidationStates</span></span>|<span data-ttu-id="85600-125">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="85600-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="85600-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="85600-126">InvalidUnfocused</span></span>|<span data-ttu-id="85600-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="85600-127">ValidationStates</span></span>|<span data-ttu-id="85600-128">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="85600-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="85600-129">Przykład DocumentViewer ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="85600-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="85600-130">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="85600-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="85600-131">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="85600-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="85600-132">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="85600-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85600-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85600-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="85600-134">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="85600-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="85600-135">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="85600-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="85600-136">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="85600-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="85600-137">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="85600-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
