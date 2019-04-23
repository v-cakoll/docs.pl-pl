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
ms.openlocfilehash: 32d8aac99d40693e66c7b52a6c7d2c116d2f3baf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225810"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="89ede-102">NavigationWindow — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="89ede-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="89ede-103">W tym temacie opisano, style i szablony <xref:System.Windows.Navigation.NavigationWindow> kontroli.</span><span class="sxs-lookup"><span data-stu-id="89ede-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="89ede-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="89ede-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="89ede-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="89ede-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="89ede-106">Navigationwindow — elementy</span><span class="sxs-lookup"><span data-stu-id="89ede-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="89ede-107">Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Navigation.NavigationWindow> kontroli.</span><span class="sxs-lookup"><span data-stu-id="89ede-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="89ede-108">Część</span><span class="sxs-lookup"><span data-stu-id="89ede-108">Part</span></span>|<span data-ttu-id="89ede-109">Typ</span><span class="sxs-lookup"><span data-stu-id="89ede-109">Type</span></span>|<span data-ttu-id="89ede-110">Opis</span><span class="sxs-lookup"><span data-stu-id="89ede-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="89ede-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="89ede-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="89ede-112">Obszar zawartości.</span><span class="sxs-lookup"><span data-stu-id="89ede-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="89ede-113">Navigationwindow — Stany</span><span class="sxs-lookup"><span data-stu-id="89ede-113">NavigationWindow States</span></span>  
 <span data-ttu-id="89ede-114">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Navigation.NavigationWindow> kontroli.</span><span class="sxs-lookup"><span data-stu-id="89ede-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="89ede-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="89ede-115">VisualState Name</span></span>|<span data-ttu-id="89ede-116">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="89ede-116">VisualStateGroup Name</span></span>|<span data-ttu-id="89ede-117">Opis</span><span class="sxs-lookup"><span data-stu-id="89ede-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="89ede-118">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="89ede-118">Valid</span></span>|<span data-ttu-id="89ede-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="89ede-119">ValidationStates</span></span>|<span data-ttu-id="89ede-120">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="89ede-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="89ede-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="89ede-121">InvalidFocused</span></span>|<span data-ttu-id="89ede-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="89ede-122">ValidationStates</span></span>|<span data-ttu-id="89ede-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="89ede-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="89ede-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="89ede-124">InvalidUnfocused</span></span>|<span data-ttu-id="89ede-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="89ede-125">ValidationStates</span></span>|<span data-ttu-id="89ede-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="89ede-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="89ede-127">Przykład ControlTemplate NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="89ede-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="89ede-128">Chociaż ten przykład zawiera wszystkie elementy, które są zdefiniowane w <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Navigation.NavigationWindow> domyślnie określone wartości powinny być uważane za przykłady.</span><span class="sxs-lookup"><span data-stu-id="89ede-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="89ede-129">W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="89ede-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="89ede-130">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="89ede-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ede-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89ede-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="89ede-132">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="89ede-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="89ede-133">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="89ede-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="89ede-134">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="89ede-134">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="89ede-135">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="89ede-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
