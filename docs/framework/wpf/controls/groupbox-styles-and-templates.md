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
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187481"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="0daa5-102">GroupBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="0daa5-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="0daa5-103">W tym temacie opisano style <xref:System.Windows.Controls.GroupBox> i szablony formantu.</span><span class="sxs-lookup"><span data-stu-id="0daa5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="0daa5-104">Można zmodyfikować <xref:System.Windows.Controls.ControlTemplate> wartość domyślną, aby nadać formancie unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="0daa5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0daa5-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu formantu](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="0daa5-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a><span data-ttu-id="0daa5-106">Części GroupBox</span><span class="sxs-lookup"><span data-stu-id="0daa5-106">GroupBox Parts</span></span>  
 <span data-ttu-id="0daa5-107">Formant <xref:System.Windows.Controls.GroupBox> nie ma żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="0daa5-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a><span data-ttu-id="0daa5-108">Stany GroupBox</span><span class="sxs-lookup"><span data-stu-id="0daa5-108">GroupBox States</span></span>  
 <span data-ttu-id="0daa5-109">W poniższej tabeli wymieniono stany wizualne formantu. <xref:System.Windows.Controls.GroupBox></span><span class="sxs-lookup"><span data-stu-id="0daa5-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="0daa5-110">Nazwa visualstate</span><span class="sxs-lookup"><span data-stu-id="0daa5-110">VisualState Name</span></span>|<span data-ttu-id="0daa5-111">Nazwa grupy programu VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="0daa5-111">VisualStateGroup Name</span></span>|<span data-ttu-id="0daa5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0daa5-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0daa5-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="0daa5-113">Valid</span></span>|<span data-ttu-id="0daa5-114">Stan sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="0daa5-114">ValidationStates</span></span>|<span data-ttu-id="0daa5-115">Formant używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej `false`właściwości jest .</span><span class="sxs-lookup"><span data-stu-id="0daa5-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0daa5-116">Nieprawidłowo skupiony</span><span class="sxs-lookup"><span data-stu-id="0daa5-116">InvalidFocused</span></span>|<span data-ttu-id="0daa5-117">Stan sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="0daa5-117">ValidationStates</span></span>|<span data-ttu-id="0daa5-118">Dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="0daa5-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="0daa5-119">Nieprawidłowy Nieskoncentrowany</span><span class="sxs-lookup"><span data-stu-id="0daa5-119">InvalidUnfocused</span></span>|<span data-ttu-id="0daa5-120">Stan sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="0daa5-120">ValidationStates</span></span>|<span data-ttu-id="0daa5-121">Dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> właściwość `true` ma formant nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="0daa5-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="0daa5-122">Przykład controltemplate skrzynki grupowej</span><span class="sxs-lookup"><span data-stu-id="0daa5-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="0daa5-123">W poniższym <xref:System.Windows.Controls.ControlTemplate> przykładzie pokazano, <xref:System.Windows.Controls.GroupBox> jak zdefiniować formantu.</span><span class="sxs-lookup"><span data-stu-id="0daa5-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="0daa5-124">Używa <xref:System.Windows.Controls.ControlTemplate> co najmniej jednego z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="0daa5-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="0daa5-125">Aby uzyskać pełną próbkę, zobacz [Stylowanie za pomocą próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="0daa5-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0daa5-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0daa5-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="0daa5-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="0daa5-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="0daa5-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="0daa5-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="0daa5-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="0daa5-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="0daa5-130">Tworzenie szablonu formantu</span><span class="sxs-lookup"><span data-stu-id="0daa5-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
