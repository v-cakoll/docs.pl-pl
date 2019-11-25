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
ms.openlocfilehash: 4ba90182468466773644c7375059f0cc01675b33
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283465"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="f732e-102">PasswordBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="f732e-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="f732e-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="f732e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="f732e-104">Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="f732e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f732e-105">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="f732e-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="f732e-106">PasswordBox części</span><span class="sxs-lookup"><span data-stu-id="f732e-106">PasswordBox Parts</span></span>

<span data-ttu-id="f732e-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="f732e-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="f732e-108">Części</span><span class="sxs-lookup"><span data-stu-id="f732e-108">Part</span></span>|<span data-ttu-id="f732e-109">Typ</span><span class="sxs-lookup"><span data-stu-id="f732e-109">Type</span></span>|<span data-ttu-id="f732e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f732e-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="f732e-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="f732e-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="f732e-112">Element wizualizacji, który może zawierać <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="f732e-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="f732e-113">Tekst <xref:System.Windows.Controls.PasswordBox> zostanie wyświetlony w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="f732e-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="f732e-114">Stany PasswordBox</span><span class="sxs-lookup"><span data-stu-id="f732e-114">PasswordBox States</span></span>

<span data-ttu-id="f732e-115">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="f732e-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="f732e-116">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="f732e-116">VisualState Name</span></span>|<span data-ttu-id="f732e-117">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f732e-117">VisualStateGroup Name</span></span>|<span data-ttu-id="f732e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f732e-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="f732e-119">Normalne</span><span class="sxs-lookup"><span data-stu-id="f732e-119">Normal</span></span>|<span data-ttu-id="f732e-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f732e-120">CommonStates</span></span>|<span data-ttu-id="f732e-121">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="f732e-121">The default state.</span></span>|
|<span data-ttu-id="f732e-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f732e-122">MouseOver</span></span>|<span data-ttu-id="f732e-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f732e-123">CommonStates</span></span>|<span data-ttu-id="f732e-124">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="f732e-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="f732e-125">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="f732e-125">Disabled</span></span>|<span data-ttu-id="f732e-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f732e-126">CommonStates</span></span>|<span data-ttu-id="f732e-127">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="f732e-127">The control is disabled.</span></span>|
|<span data-ttu-id="f732e-128">Fokus</span><span class="sxs-lookup"><span data-stu-id="f732e-128">Focused</span></span>|<span data-ttu-id="f732e-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f732e-129">FocusStates</span></span>|<span data-ttu-id="f732e-130">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="f732e-130">The control has focus.</span></span>|
|<span data-ttu-id="f732e-131">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="f732e-131">Unfocused</span></span>|<span data-ttu-id="f732e-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f732e-132">FocusStates</span></span>|<span data-ttu-id="f732e-133">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="f732e-133">The control does not have focus.</span></span>|
|<span data-ttu-id="f732e-134">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="f732e-134">Valid</span></span>|<span data-ttu-id="f732e-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f732e-135">ValidationStates</span></span>|<span data-ttu-id="f732e-136">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="f732e-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="f732e-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f732e-137">InvalidFocused</span></span>|<span data-ttu-id="f732e-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f732e-138">ValidationStates</span></span>|<span data-ttu-id="f732e-139">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="f732e-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="f732e-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f732e-140">InvalidUnfocused</span></span>|<span data-ttu-id="f732e-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f732e-141">ValidationStates</span></span>|<span data-ttu-id="f732e-142">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="f732e-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="f732e-143">Przykład PasswordBox ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f732e-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="f732e-144">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="f732e-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="f732e-145">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f732e-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="f732e-146">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f732e-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="f732e-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f732e-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f732e-148">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="f732e-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f732e-149">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="f732e-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f732e-150">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="f732e-150">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f732e-151">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="f732e-151">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
