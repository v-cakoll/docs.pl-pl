---
title: Style i szablony etykiet
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
ms.openlocfilehash: c3bf4dc629bbb3e4ea21862c6893b001749f4649
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459389"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="ea2cd-102">Style i szablony etykiet</span><span class="sxs-lookup"><span data-stu-id="ea2cd-102">Label Styles and Templates</span></span>
<span data-ttu-id="ea2cd-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="ea2cd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="ea2cd-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="ea2cd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ea2cd-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ea2cd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="ea2cd-106">Części etykiet</span><span class="sxs-lookup"><span data-stu-id="ea2cd-106">Label Parts</span></span>  
 <span data-ttu-id="ea2cd-107">Formant <xref:System.Windows.Controls.Label> nie zawiera żadnych nazwanych części.</span><span class="sxs-lookup"><span data-stu-id="ea2cd-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="ea2cd-108">Stany etykiet</span><span class="sxs-lookup"><span data-stu-id="ea2cd-108">Label States</span></span>  
 <span data-ttu-id="ea2cd-109">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="ea2cd-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="ea2cd-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="ea2cd-110">VisualState Name</span></span>|<span data-ttu-id="ea2cd-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ea2cd-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ea2cd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ea2cd-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ea2cd-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="ea2cd-113">Valid</span></span>|<span data-ttu-id="ea2cd-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea2cd-114">ValidationStates</span></span>|<span data-ttu-id="ea2cd-115">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="ea2cd-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ea2cd-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ea2cd-116">InvalidFocused</span></span>|<span data-ttu-id="ea2cd-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea2cd-117">ValidationStates</span></span>|<span data-ttu-id="ea2cd-118">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="ea2cd-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ea2cd-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ea2cd-119">InvalidUnfocused</span></span>|<span data-ttu-id="ea2cd-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ea2cd-120">ValidationStates</span></span>|<span data-ttu-id="ea2cd-121">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="ea2cd-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="ea2cd-122">Przykład ControlTemplate etykiety</span><span class="sxs-lookup"><span data-stu-id="ea2cd-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="ea2cd-123">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="ea2cd-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="ea2cd-124"><xref:System.Windows.Controls.ControlTemplate> używa co najmniej jednego z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="ea2cd-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ea2cd-125">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="ea2cd-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2cd-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea2cd-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ea2cd-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="ea2cd-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ea2cd-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="ea2cd-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ea2cd-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="ea2cd-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ea2cd-130">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ea2cd-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
