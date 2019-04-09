---
title: GroupBox — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 5ef8e4b44bc2b6072fa730f33c10191b64954f7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078996"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="23d5c-102">GroupBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="23d5c-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a> <span data-ttu-id="23d5c-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.GroupBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="23d5c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="23d5c-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="23d5c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="23d5c-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="23d5c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="23d5c-106">Części GroupBox</span><span class="sxs-lookup"><span data-stu-id="23d5c-106">GroupBox Parts</span></span>  
 <span data-ttu-id="23d5c-107"><xref:System.Windows.Controls.GroupBox> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="23d5c-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="23d5c-108">Pole grupy stanów</span><span class="sxs-lookup"><span data-stu-id="23d5c-108">GroupBox States</span></span>  
 <span data-ttu-id="23d5c-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.GroupBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="23d5c-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="23d5c-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="23d5c-110">VisualState Name</span></span>|<span data-ttu-id="23d5c-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="23d5c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="23d5c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="23d5c-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="23d5c-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="23d5c-113">Valid</span></span>|<span data-ttu-id="23d5c-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="23d5c-114">ValidationStates</span></span>|<span data-ttu-id="23d5c-115">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="23d5c-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="23d5c-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="23d5c-116">InvalidFocused</span></span>|<span data-ttu-id="23d5c-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="23d5c-117">ValidationStates</span></span>|<span data-ttu-id="23d5c-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="23d5c-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="23d5c-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="23d5c-119">InvalidUnfocused</span></span>|<span data-ttu-id="23d5c-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="23d5c-120">ValidationStates</span></span>|<span data-ttu-id="23d5c-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="23d5c-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="23d5c-122">Przykład ControlTemplate GroupBox</span><span class="sxs-lookup"><span data-stu-id="23d5c-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="23d5c-123">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.GroupBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="23d5c-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="23d5c-124"><xref:System.Windows.Controls.ControlTemplate> Używa co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="23d5c-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="23d5c-125">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="23d5c-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d5c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23d5c-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="23d5c-127">Style i szablony formantu</span><span class="sxs-lookup"><span data-stu-id="23d5c-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="23d5c-128">Niestandardowe dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="23d5c-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="23d5c-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="23d5c-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="23d5c-130">Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="23d5c-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
