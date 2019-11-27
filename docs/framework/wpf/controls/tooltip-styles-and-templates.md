---
title: ToolTip — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: c7a14034d665c124d01e8a4b43c5d42968241925
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283648"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="4cec4-102">ToolTip — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="4cec4-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="4cec4-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="4cec4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="4cec4-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="4cec4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="4cec4-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="4cec4-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="4cec4-106">Części etykietki narzędzi</span><span class="sxs-lookup"><span data-stu-id="4cec4-106">ToolTip Parts</span></span>  
 <span data-ttu-id="4cec4-107">Formant <xref:System.Windows.Controls.ToolTip> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="4cec4-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="4cec4-108">Stany etykietki narzędzi</span><span class="sxs-lookup"><span data-stu-id="4cec4-108">ToolTip States</span></span>  
 <span data-ttu-id="4cec4-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="4cec4-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="4cec4-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="4cec4-110">VisualState Name</span></span>|<span data-ttu-id="4cec4-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="4cec4-111">VisualStateGroup Name</span></span>|<span data-ttu-id="4cec4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4cec4-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4cec4-113">Zamknięte</span><span class="sxs-lookup"><span data-stu-id="4cec4-113">Closed</span></span>|<span data-ttu-id="4cec4-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="4cec4-114">OpenStates</span></span>|<span data-ttu-id="4cec4-115">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="4cec4-115">The default state.</span></span>|  
|<span data-ttu-id="4cec4-116">Otwarty</span><span class="sxs-lookup"><span data-stu-id="4cec4-116">Open</span></span>|<span data-ttu-id="4cec4-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="4cec4-117">OpenStates</span></span>|<span data-ttu-id="4cec4-118"><xref:System.Windows.Controls.ToolTip> jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="4cec4-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="4cec4-119">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="4cec4-119">Valid</span></span>|<span data-ttu-id="4cec4-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4cec4-120">ValidationStates</span></span>|<span data-ttu-id="4cec4-121">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4cec4-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4cec4-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="4cec4-122">InvalidFocused</span></span>|<span data-ttu-id="4cec4-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4cec4-123">ValidationStates</span></span>|<span data-ttu-id="4cec4-124">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="4cec4-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="4cec4-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="4cec4-125">InvalidUnfocused</span></span>|<span data-ttu-id="4cec4-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4cec4-126">ValidationStates</span></span>|<span data-ttu-id="4cec4-127">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="4cec4-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="4cec4-128">Przykład ControlTemplate etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="4cec4-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="4cec4-129">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="4cec4-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="4cec4-130">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="4cec4-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="4cec4-131">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="4cec4-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cec4-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4cec4-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="4cec4-133">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="4cec4-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="4cec4-134">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="4cec4-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="4cec4-135">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="4cec4-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="4cec4-136">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="4cec4-136">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
