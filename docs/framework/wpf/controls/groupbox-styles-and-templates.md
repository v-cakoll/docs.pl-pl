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
ms.openlocfilehash: 0835c106ffbda86bca8e01bc61adebfc1ab0c2cb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459639"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="a85fd-102">GroupBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="a85fd-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="a85fd-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="a85fd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="a85fd-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="a85fd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a85fd-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="a85fd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="a85fd-106">Części grupy</span><span class="sxs-lookup"><span data-stu-id="a85fd-106">GroupBox Parts</span></span>  
 <span data-ttu-id="a85fd-107">Formant <xref:System.Windows.Controls.GroupBox> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="a85fd-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="a85fd-108">Stany grupy</span><span class="sxs-lookup"><span data-stu-id="a85fd-108">GroupBox States</span></span>  
 <span data-ttu-id="a85fd-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="a85fd-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="a85fd-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="a85fd-110">VisualState Name</span></span>|<span data-ttu-id="a85fd-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a85fd-111">VisualStateGroup Name</span></span>|<span data-ttu-id="a85fd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a85fd-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a85fd-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="a85fd-113">Valid</span></span>|<span data-ttu-id="a85fd-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a85fd-114">ValidationStates</span></span>|<span data-ttu-id="a85fd-115">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="a85fd-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a85fd-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a85fd-116">InvalidFocused</span></span>|<span data-ttu-id="a85fd-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a85fd-117">ValidationStates</span></span>|<span data-ttu-id="a85fd-118">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="a85fd-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a85fd-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a85fd-119">InvalidUnfocused</span></span>|<span data-ttu-id="a85fd-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a85fd-120">ValidationStates</span></span>|<span data-ttu-id="a85fd-121">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="a85fd-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="a85fd-122">Przykład ControlTemplate grupy</span><span class="sxs-lookup"><span data-stu-id="a85fd-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="a85fd-123">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="a85fd-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="a85fd-124"><xref:System.Windows.Controls.ControlTemplate> używa co najmniej jednego z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="a85fd-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a85fd-125">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="a85fd-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85fd-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a85fd-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="a85fd-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="a85fd-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="a85fd-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="a85fd-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="a85fd-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="a85fd-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="a85fd-130">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a85fd-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
