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
ms.openlocfilehash: 227ccbda8d570868258508935a5d95f0f40663ab
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458840"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="90501-102">PasswordBox — Style i szablony</span><span class="sxs-lookup"><span data-stu-id="90501-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="90501-103">W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="90501-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="90501-104">Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="90501-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="90501-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="90501-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="90501-106">PasswordBox części</span><span class="sxs-lookup"><span data-stu-id="90501-106">PasswordBox Parts</span></span>

<span data-ttu-id="90501-107">W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="90501-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="90501-108">Części</span><span class="sxs-lookup"><span data-stu-id="90501-108">Part</span></span>|<span data-ttu-id="90501-109">Typ</span><span class="sxs-lookup"><span data-stu-id="90501-109">Type</span></span>|<span data-ttu-id="90501-110">Opis</span><span class="sxs-lookup"><span data-stu-id="90501-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="90501-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="90501-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="90501-112">Element wizualizacji, który może zawierać <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="90501-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="90501-113">Tekst <xref:System.Windows.Controls.PasswordBox> zostanie wyświetlony w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="90501-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="90501-114">Stany PasswordBox</span><span class="sxs-lookup"><span data-stu-id="90501-114">PasswordBox States</span></span>

<span data-ttu-id="90501-115">Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="90501-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="90501-116">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="90501-116">VisualState Name</span></span>|<span data-ttu-id="90501-117">Nazwa element VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="90501-117">VisualStateGroup Name</span></span>|<span data-ttu-id="90501-118">Opis</span><span class="sxs-lookup"><span data-stu-id="90501-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="90501-119">Typow</span><span class="sxs-lookup"><span data-stu-id="90501-119">Normal</span></span>|<span data-ttu-id="90501-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="90501-120">CommonStates</span></span>|<span data-ttu-id="90501-121">Stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="90501-121">The default state.</span></span>|
|<span data-ttu-id="90501-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="90501-122">MouseOver</span></span>|<span data-ttu-id="90501-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="90501-123">CommonStates</span></span>|<span data-ttu-id="90501-124">Wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="90501-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="90501-125">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="90501-125">Disabled</span></span>|<span data-ttu-id="90501-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="90501-126">CommonStates</span></span>|<span data-ttu-id="90501-127">Kontrolka jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="90501-127">The control is disabled.</span></span>|
|<span data-ttu-id="90501-128">Fokus</span><span class="sxs-lookup"><span data-stu-id="90501-128">Focused</span></span>|<span data-ttu-id="90501-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="90501-129">FocusStates</span></span>|<span data-ttu-id="90501-130">Kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="90501-130">The control has focus.</span></span>|
|<span data-ttu-id="90501-131">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="90501-131">Unfocused</span></span>|<span data-ttu-id="90501-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="90501-132">FocusStates</span></span>|<span data-ttu-id="90501-133">Kontrolka nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="90501-133">The control does not have focus.</span></span>|
|<span data-ttu-id="90501-134">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="90501-134">Valid</span></span>|<span data-ttu-id="90501-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="90501-135">ValidationStates</span></span>|<span data-ttu-id="90501-136">Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="90501-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="90501-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="90501-137">InvalidFocused</span></span>|<span data-ttu-id="90501-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="90501-138">ValidationStates</span></span>|<span data-ttu-id="90501-139">Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.</span><span class="sxs-lookup"><span data-stu-id="90501-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="90501-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="90501-140">InvalidUnfocused</span></span>|<span data-ttu-id="90501-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="90501-141">ValidationStates</span></span>|<span data-ttu-id="90501-142">Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.</span><span class="sxs-lookup"><span data-stu-id="90501-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="90501-143">Przykład PasswordBox ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="90501-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="90501-144">Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="90501-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="90501-145">W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.</span><span class="sxs-lookup"><span data-stu-id="90501-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="90501-146">Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="90501-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="90501-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90501-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="90501-148">Style i szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="90501-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="90501-149">Niestandardowe dostosowywanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="90501-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="90501-150">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="90501-150">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="90501-151">Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="90501-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
