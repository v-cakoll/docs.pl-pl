---
title: ContextMenu — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: 6650d5a7be8ebe8fc2dcd7af7c854da669de87f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912330"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="9a03c-102">ContextMenu — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="9a03c-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="9a03c-103">W tym temacie opisano, style i szablony <xref:System.Windows.Controls.ContextMenu> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9a03c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="9a03c-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9a03c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9a03c-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="9a03c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="9a03c-106">ContextMenu — elementy</span><span class="sxs-lookup"><span data-stu-id="9a03c-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="9a03c-107"><xref:System.Windows.Controls.ContextMenu> Formant nie ma żadnych części o nazwie.</span><span class="sxs-lookup"><span data-stu-id="9a03c-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="9a03c-108">Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ContextMenu>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w ramach <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="9a03c-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="9a03c-109">( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element na <xref:System.Windows.Controls.ContextMenu>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).</span><span class="sxs-lookup"><span data-stu-id="9a03c-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="9a03c-110">Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednie podrzędne <xref:System.Windows.Controls.ScrollViewer>, należy podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="9a03c-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="9a03c-111">ContextMenu — informacje o stanach</span><span class="sxs-lookup"><span data-stu-id="9a03c-111">ContextMenu States</span></span>  
 <span data-ttu-id="9a03c-112">Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.ContextMenu> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9a03c-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="9a03c-113">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="9a03c-113">VisualState Name</span></span>|<span data-ttu-id="9a03c-114">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="9a03c-114">VisualStateGroup Name</span></span>|<span data-ttu-id="9a03c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9a03c-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9a03c-116">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="9a03c-116">Valid</span></span>|<span data-ttu-id="9a03c-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9a03c-117">ValidationStates</span></span>|<span data-ttu-id="9a03c-118">Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="9a03c-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9a03c-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9a03c-119">InvalidFocused</span></span>|<span data-ttu-id="9a03c-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9a03c-120">ValidationStates</span></span>|<span data-ttu-id="9a03c-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="9a03c-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9a03c-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9a03c-122">InvalidUnfocused</span></span>|<span data-ttu-id="9a03c-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9a03c-123">ValidationStates</span></span>|<span data-ttu-id="9a03c-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="9a03c-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="9a03c-125">Przykład ControlTemplate ContextMenu</span><span class="sxs-lookup"><span data-stu-id="9a03c-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="9a03c-126">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ContextMenu> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9a03c-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="9a03c-127"><xref:System.Windows.Controls.ControlTemplate> Używa następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="9a03c-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9a03c-128">Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="9a03c-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a03c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a03c-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="9a03c-130">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="9a03c-130">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="9a03c-131">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="9a03c-131">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="9a03c-132">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="9a03c-132">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="9a03c-133">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9a03c-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
