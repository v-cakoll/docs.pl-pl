---
title: 'Wskazówki: mapowanie właściwości z użyciem formantu ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 7ff4ff607ab70b55cda1e2c4736ff773d4907a22
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794117"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="dcc75-102">Wskazówki: mapowanie właściwości z użyciem formantu ElementHost</span><span class="sxs-lookup"><span data-stu-id="dcc75-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>

<span data-ttu-id="dcc75-103">W tym instruktażu przedstawiono sposób użycia właściwości <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> do mapowania właściwości Windows Forms na odpowiednie właściwości w hostowanym elemencie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcc75-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map Windows Forms properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>

<span data-ttu-id="dcc75-104">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="dcc75-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="dcc75-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="dcc75-105">Creating the project.</span></span>

- <span data-ttu-id="dcc75-106">Definiowanie nowego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcc75-106">Defining a new property mapping.</span></span>

- <span data-ttu-id="dcc75-107">Usuwanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcc75-107">Removing a default property mapping.</span></span>

- <span data-ttu-id="dcc75-108">Rozszerzanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcc75-108">Extending a default property mapping.</span></span>

<span data-ttu-id="dcc75-109">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [Mapowanie właściwości przy użyciu przykładu kontrolki ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="dcc75-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](https://go.microsoft.com/fwlink/?LinkID=160018).</span></span>

<span data-ttu-id="dcc75-110">Po zakończeniu będzie możliwe mapowanie Windows Forms właściwości do odpowiednich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości w hostowanym elemencie.</span><span class="sxs-lookup"><span data-stu-id="dcc75-110">When you are finished, you will be able to map Windows Forms properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dcc75-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="dcc75-111">Prerequisites</span></span>

<span data-ttu-id="dcc75-112">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="dcc75-112">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="dcc75-113">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dcc75-113">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="dcc75-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="dcc75-114">Creating the Project</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="dcc75-115">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="dcc75-115">To create the project</span></span>

1. <span data-ttu-id="dcc75-116">Utwórz projekt **aplikacji Windows Forms** o nazwie `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="dcc75-116">Create a **Windows Forms App** project named `PropertyMappingWithElementHost`.</span></span>

2. <span data-ttu-id="dcc75-117">W **Eksplorator rozwiązań**Dodaj odwołania do następujących zestawów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcc75-117">In **Solution Explorer**, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>

    - <span data-ttu-id="dcc75-118">'Presentationcore</span><span class="sxs-lookup"><span data-stu-id="dcc75-118">PresentationCore</span></span>

    - <span data-ttu-id="dcc75-119">Platformie docelowej</span><span class="sxs-lookup"><span data-stu-id="dcc75-119">PresentationFramework</span></span>

    - <span data-ttu-id="dcc75-120">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="dcc75-120">WindowsBase</span></span>

    - <span data-ttu-id="dcc75-121">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="dcc75-121">WindowsFormsIntegration</span></span>

3. <span data-ttu-id="dcc75-122">Skopiuj poniższy kod do góry pliku kodu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="dcc75-122">Copy the following code into the top of the `Form1` code file.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. <span data-ttu-id="dcc75-123">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dcc75-123">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="dcc75-124">Kliknij dwukrotnie formularz, aby dodać program obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Form.Load>.</span><span class="sxs-lookup"><span data-stu-id="dcc75-124">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>

5. <span data-ttu-id="dcc75-125">Wróć do Projektant formularzy systemu Windows i Dodaj procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Resize> formularza.</span><span class="sxs-lookup"><span data-stu-id="dcc75-125">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="dcc75-126">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń przy użyciu projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dcc75-126">For more information, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>

6. <span data-ttu-id="dcc75-127">Zadeklaruj pole <xref:System.Windows.Forms.Integration.ElementHost> w klasie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="dcc75-127">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a><span data-ttu-id="dcc75-128">Definiowanie nowych mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="dcc75-128">Defining New Property Mappings</span></span>

<span data-ttu-id="dcc75-129">Formant <xref:System.Windows.Forms.Integration.ElementHost> zawiera kilka domyślnych mapowań właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcc75-129">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="dcc75-130">Aby dodać nowe mapowanie właściwości, należy wywołać metodę <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>kontrolce <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="dcc75-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-define-new-property-mappings"></a><span data-ttu-id="dcc75-131">Aby zdefiniować nowe mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="dcc75-131">To define new property mappings</span></span>

1. <span data-ttu-id="dcc75-132">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="dcc75-132">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     <span data-ttu-id="dcc75-133">Metoda `AddMarginMapping` dodaje nowe mapowanie dla właściwości <xref:System.Windows.Forms.Control.Margin%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcc75-133">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>

     <span data-ttu-id="dcc75-134">Metoda `OnMarginChange` przekształca Właściwość <xref:System.Windows.Forms.Control.Margin%2A> na Właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcc75-134">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>

2. <span data-ttu-id="dcc75-135">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="dcc75-135">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     <span data-ttu-id="dcc75-136">Metoda `AddRegionMapping` dodaje nowe mapowanie dla właściwości <xref:System.Windows.Forms.Control.Region%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcc75-136">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="dcc75-137">Metoda `OnRegionChange` przekształca Właściwość <xref:System.Windows.Forms.Control.Region%2A> na Właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcc75-137">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="dcc75-138">Metoda `Form1_Resize` obsługuje zdarzenie <xref:System.Windows.Forms.Control.Resize> formularza i rozmiary obszaru przycinania w celu dopasowania go do hostowanego elementu.</span><span class="sxs-lookup"><span data-stu-id="dcc75-138">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="dcc75-139">Usuwanie domyślnego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="dcc75-139">Removing a Default Property Mapping</span></span>

<span data-ttu-id="dcc75-140">Usuń domyślne mapowanie właściwości, wywołując metodę <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>kontroli <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="dcc75-140">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="dcc75-141">Aby usunąć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="dcc75-141">To remove a default property mapping</span></span>

- <span data-ttu-id="dcc75-142">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="dcc75-142">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     <span data-ttu-id="dcc75-143">Metoda `RemoveCursorMapping` usuwa mapowanie domyślne dla właściwości <xref:System.Windows.Forms.Control.Cursor%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcc75-143">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="dcc75-144">Rozszerzanie domyślnego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="dcc75-144">Extending a Default Property Mapping</span></span>

<span data-ttu-id="dcc75-145">Można użyć domyślnego mapowania właściwości, a także poszerzyć go przy użyciu własnego mapowania.</span><span class="sxs-lookup"><span data-stu-id="dcc75-145">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="dcc75-146">Aby zwiększyć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="dcc75-146">To extend a default property mapping</span></span>

- <span data-ttu-id="dcc75-147">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="dcc75-147">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     <span data-ttu-id="dcc75-148">Metoda `ExtendBackColorMapping` dodaje translator właściwości niestandardowych do istniejącego mapowania właściwości <xref:System.Windows.Forms.Control.BackColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcc75-148">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>

     <span data-ttu-id="dcc75-149">Metoda `OnBackColorChange` przypisuje określony obraz do właściwości <xref:System.Windows.Controls.Control.Background%2A> kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="dcc75-149">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="dcc75-150">Metoda `OnBackColorChange` jest wywoływana po zastosowaniu domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcc75-150">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>

## <a name="initialize-your-property-mappings"></a><span data-ttu-id="dcc75-151">Inicjuj mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="dcc75-151">Initialize your property mappings</span></span>

1. <span data-ttu-id="dcc75-152">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="dcc75-152">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     <span data-ttu-id="dcc75-153">Metoda `Form1_Load` obsługuje zdarzenie <xref:System.Windows.Forms.Form.Load> i wykonuje następujące inicjalizacje.</span><span class="sxs-lookup"><span data-stu-id="dcc75-153">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>

    - <span data-ttu-id="dcc75-154">Tworzy element <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcc75-154">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>

    - <span data-ttu-id="dcc75-155">Wywołuje metody zdefiniowane wcześniej w przewodniku, aby skonfigurować mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcc75-155">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="dcc75-156">Przypisuje początkowe wartości do mapowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcc75-156">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="dcc75-157">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="dcc75-157">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcc75-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcc75-158">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="dcc75-159">Mapowanie właściwości Windows Forms i WPF</span><span class="sxs-lookup"><span data-stu-id="dcc75-159">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="dcc75-160">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dcc75-160">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="dcc75-161">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dcc75-161">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
