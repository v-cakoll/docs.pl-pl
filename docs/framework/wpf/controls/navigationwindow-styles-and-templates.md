---
title: NavigationWindow — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
ms.openlocfilehash: 5cc504956ce036505ac9261ea1438c7881fa2790
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283492"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="01b83-102">NavigationWindow — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="01b83-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="01b83-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="01b83-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="01b83-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="01b83-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="01b83-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="01b83-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="01b83-106">NavigationWindow części</span><span class="sxs-lookup"><span data-stu-id="01b83-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="01b83-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="01b83-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="01b83-108">Części</span><span class="sxs-lookup"><span data-stu-id="01b83-108">Part</span></span>|<span data-ttu-id="01b83-109">Typ</span><span class="sxs-lookup"><span data-stu-id="01b83-109">Type</span></span>|<span data-ttu-id="01b83-110">Opis</span><span class="sxs-lookup"><span data-stu-id="01b83-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="01b83-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="01b83-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="01b83-112">Obszar zawartości.</span><span class="sxs-lookup"><span data-stu-id="01b83-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="01b83-113">Stany NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="01b83-113">NavigationWindow States</span></span>  
 <span data-ttu-id="01b83-114">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="01b83-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="01b83-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="01b83-115">VisualState Name</span></span>|<span data-ttu-id="01b83-116">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="01b83-116">VisualStateGroup Name</span></span>|<span data-ttu-id="01b83-117">Opis</span><span class="sxs-lookup"><span data-stu-id="01b83-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="01b83-118">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="01b83-118">Valid</span></span>|<span data-ttu-id="01b83-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="01b83-119">ValidationStates</span></span>|<span data-ttu-id="01b83-120">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="01b83-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="01b83-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="01b83-121">InvalidFocused</span></span>|<span data-ttu-id="01b83-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="01b83-122">ValidationStates</span></span>|<span data-ttu-id="01b83-123">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="01b83-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="01b83-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="01b83-124">InvalidUnfocused</span></span>|<span data-ttu-id="01b83-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="01b83-125">ValidationStates</span></span>|<span data-ttu-id="01b83-126">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="01b83-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="01b83-127">Przykład NavigationWindow ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="01b83-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="01b83-128">Chociaż ten przykład zawiera wszystkie elementy, które są zdefiniowane w <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Navigation.NavigationWindow> domyślnie, konkretne wartości należy traktować jako przykłady.</span><span class="sxs-lookup"><span data-stu-id="01b83-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="01b83-129">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="01b83-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="01b83-130">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="01b83-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b83-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01b83-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="01b83-132">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="01b83-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="01b83-133">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="01b83-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="01b83-134">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="01b83-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="01b83-135">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="01b83-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
