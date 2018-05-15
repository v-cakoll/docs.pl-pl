---
title: PasswordBox — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: a5002aa9596eb45ad92ef67ebc599efac32e94b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="c7765-102">PasswordBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="c7765-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="c7765-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.PasswordBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="c7765-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="c7765-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="c7765-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c7765-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c7765-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="c7765-106">Części PasswordBox</span><span class="sxs-lookup"><span data-stu-id="c7765-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="c7765-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.PasswordBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="c7765-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="c7765-108">Część</span><span class="sxs-lookup"><span data-stu-id="c7765-108">Part</span></span>|<span data-ttu-id="c7765-109">Typ</span><span class="sxs-lookup"><span data-stu-id="c7765-109">Type</span></span>|<span data-ttu-id="c7765-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c7765-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c7765-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="c7765-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="c7765-112">Element wizualny, który może zawierać <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="c7765-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="c7765-113">Tekst <xref:System.Windows.Controls.PasswordBox> jest wyświetlany w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="c7765-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="c7765-114">Stany PasswordBox</span><span class="sxs-lookup"><span data-stu-id="c7765-114">PasswordBox States</span></span>  
 <span data-ttu-id="c7765-115">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.PasswordBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="c7765-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="c7765-116">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="c7765-116">VisualState Name</span></span>|<span data-ttu-id="c7765-117">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c7765-117">VisualStateGroup Name</span></span>|<span data-ttu-id="c7765-118">Opis</span><span class="sxs-lookup"><span data-stu-id="c7765-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c7765-119">Normalny</span><span class="sxs-lookup"><span data-stu-id="c7765-119">Normal</span></span>|<span data-ttu-id="c7765-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7765-120">CommonStates</span></span>|<span data-ttu-id="c7765-121">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="c7765-121">The default state.</span></span>|  
|<span data-ttu-id="c7765-122">Etykietka wskaźnika myszy</span><span class="sxs-lookup"><span data-stu-id="c7765-122">MouseOver</span></span>|<span data-ttu-id="c7765-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7765-123">CommonStates</span></span>|<span data-ttu-id="c7765-124">Wskaźnik myszy znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="c7765-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="c7765-125">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="c7765-125">Disabled</span></span>|<span data-ttu-id="c7765-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7765-126">CommonStates</span></span>|<span data-ttu-id="c7765-127">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="c7765-127">The control is disabled.</span></span>|  
|<span data-ttu-id="c7765-128">Fokus</span><span class="sxs-lookup"><span data-stu-id="c7765-128">Focused</span></span>|<span data-ttu-id="c7765-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c7765-129">FocusStates</span></span>|<span data-ttu-id="c7765-130">Formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="c7765-130">The control has focus.</span></span>|  
|<span data-ttu-id="c7765-131">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="c7765-131">Unfocused</span></span>|<span data-ttu-id="c7765-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c7765-132">FocusStates</span></span>|<span data-ttu-id="c7765-133">Formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="c7765-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="c7765-134">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="c7765-134">Valid</span></span>|<span data-ttu-id="c7765-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7765-135">ValidationStates</span></span>|<span data-ttu-id="c7765-136">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="c7765-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c7765-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c7765-137">InvalidFocused</span></span>|<span data-ttu-id="c7765-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7765-138">ValidationStates</span></span>|<span data-ttu-id="c7765-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="c7765-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c7765-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c7765-140">InvalidUnfocused</span></span>|<span data-ttu-id="c7765-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7765-141">ValidationStates</span></span>|<span data-ttu-id="c7765-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="c7765-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="c7765-143">Przykład ControlTemplate PasswordBox</span><span class="sxs-lookup"><span data-stu-id="c7765-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="c7765-144">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.PasswordBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="c7765-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="c7765-145">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="c7765-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c7765-146">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="c7765-146">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7765-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7765-147">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c7765-148">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="c7765-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c7765-149">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="c7765-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c7765-150">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="c7765-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c7765-151">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c7765-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
