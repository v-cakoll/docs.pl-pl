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
ms.openlocfilehash: d2bb348fc9c0348fd8093452e022df7ab4e0b3f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137088"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="877df-102">Style i szablony etykiet</span><span class="sxs-lookup"><span data-stu-id="877df-102">Label Styles and Templates</span></span>
<span data-ttu-id="877df-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Label> kontroli.</span><span class="sxs-lookup"><span data-stu-id="877df-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="877df-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="877df-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="877df-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="877df-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="877df-106">Etykieta części</span><span class="sxs-lookup"><span data-stu-id="877df-106">Label Parts</span></span>  
 <span data-ttu-id="877df-107"><xref:System.Windows.Controls.Label> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="877df-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="877df-108">Etykieta stanów</span><span class="sxs-lookup"><span data-stu-id="877df-108">Label States</span></span>  
 <span data-ttu-id="877df-109">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Label> kontroli.</span><span class="sxs-lookup"><span data-stu-id="877df-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="877df-110">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="877df-110">VisualState Name</span></span>|<span data-ttu-id="877df-111">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="877df-111">VisualStateGroup Name</span></span>|<span data-ttu-id="877df-112">Opis</span><span class="sxs-lookup"><span data-stu-id="877df-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="877df-113">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="877df-113">Valid</span></span>|<span data-ttu-id="877df-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="877df-114">ValidationStates</span></span>|<span data-ttu-id="877df-115">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="877df-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="877df-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="877df-116">InvalidFocused</span></span>|<span data-ttu-id="877df-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="877df-117">ValidationStates</span></span>|<span data-ttu-id="877df-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="877df-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="877df-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="877df-119">InvalidUnfocused</span></span>|<span data-ttu-id="877df-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="877df-120">ValidationStates</span></span>|<span data-ttu-id="877df-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="877df-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="877df-122">Przykład ControlTemplate etykiety</span><span class="sxs-lookup"><span data-stu-id="877df-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="877df-123">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Label> kontroli.</span><span class="sxs-lookup"><span data-stu-id="877df-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="877df-124"><xref:System.Windows.Controls.ControlTemplate> Używa co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="877df-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="877df-125">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="877df-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877df-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="877df-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="877df-127">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="877df-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="877df-128">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="877df-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="877df-129">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="877df-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="877df-130">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="877df-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
