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
ms.openlocfilehash: 7d1cf353f7e6c4b87c13598e7e6029960cd0f715
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197817"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="0e4e9-102">Wskazówki: mapowanie właściwości z użyciem formantu ElementHost</span><span class="sxs-lookup"><span data-stu-id="0e4e9-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>

<span data-ttu-id="0e4e9-103">W tym instruktażu przedstawiono sposób użycia właściwości <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> do mapowania właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na odpowiednie właściwości w hostowanym elemencie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e4e9-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>

<span data-ttu-id="0e4e9-104">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="0e4e9-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="0e4e9-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-105">Creating the project.</span></span>

- <span data-ttu-id="0e4e9-106">Definiowanie nowego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-106">Defining a new property mapping.</span></span>

- <span data-ttu-id="0e4e9-107">Usuwanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-107">Removing a default property mapping.</span></span>

- <span data-ttu-id="0e4e9-108">Rozszerzanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-108">Extending a default property mapping.</span></span>

<span data-ttu-id="0e4e9-109">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [Mapowanie właściwości przy użyciu przykładu kontrolki ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="0e4e9-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](https://go.microsoft.com/fwlink/?LinkID=160018).</span></span>

<span data-ttu-id="0e4e9-110">Po zakończeniu będzie możliwe mapowanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiednich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości w hostowanym elemencie.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e4e9-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0e4e9-111">Prerequisites</span></span>

<span data-ttu-id="0e4e9-112">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="0e4e9-112">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="0e4e9-113">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0e4e9-113">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="0e4e9-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="0e4e9-114">Creating the Project</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="0e4e9-115">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="0e4e9-115">To create the project</span></span>

1. <span data-ttu-id="0e4e9-116">Utwórz projekt **aplikacji Windows Forms** o nazwie `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-116">Create a **Windows Forms App** project named `PropertyMappingWithElementHost`.</span></span>

2. <span data-ttu-id="0e4e9-117">W **Eksplorator rozwiązań**Dodaj odwołania do następujących zestawów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e4e9-117">In **Solution Explorer**, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>

    - <span data-ttu-id="0e4e9-118">'Presentationcore</span><span class="sxs-lookup"><span data-stu-id="0e4e9-118">PresentationCore</span></span>

    - <span data-ttu-id="0e4e9-119">Platformie docelowej</span><span class="sxs-lookup"><span data-stu-id="0e4e9-119">PresentationFramework</span></span>

    - <span data-ttu-id="0e4e9-120">'Windowsbase</span><span class="sxs-lookup"><span data-stu-id="0e4e9-120">WindowsBase</span></span>

    - <span data-ttu-id="0e4e9-121">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="0e4e9-121">WindowsFormsIntegration</span></span>

3. <span data-ttu-id="0e4e9-122">Skopiuj poniższy kod do góry pliku kodu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-122">Copy the following code into the top of the `Form1` code file.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. <span data-ttu-id="0e4e9-123">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-123">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="0e4e9-124">Kliknij dwukrotnie formularz, aby dodać program obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Form.Load>.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-124">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>

5. <span data-ttu-id="0e4e9-125">Wróć do Projektant formularzy systemu Windows i Dodaj procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Resize> formularza.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-125">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="0e4e9-126">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń przy użyciu projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0e4e9-126">For more information, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>

6. <span data-ttu-id="0e4e9-127">Zadeklaruj pole <xref:System.Windows.Forms.Integration.ElementHost> w klasie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-127">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a><span data-ttu-id="0e4e9-128">Definiowanie nowych mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="0e4e9-128">Defining New Property Mappings</span></span>

<span data-ttu-id="0e4e9-129">Formant <xref:System.Windows.Forms.Integration.ElementHost> zawiera kilka domyślnych mapowań właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-129">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="0e4e9-130">Aby dodać nowe mapowanie właściwości, należy wywołać metodę <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>kontrolce <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-define-new-property-mappings"></a><span data-ttu-id="0e4e9-131">Aby zdefiniować nowe mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="0e4e9-131">To define new property mappings</span></span>

1. <span data-ttu-id="0e4e9-132">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-132">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     <span data-ttu-id="0e4e9-133">Metoda `AddMarginMapping` dodaje nowe mapowanie dla właściwości <xref:System.Windows.Forms.Control.Margin%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-133">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>

     <span data-ttu-id="0e4e9-134">Metoda `OnMarginChange` przekształca Właściwość <xref:System.Windows.Forms.Control.Margin%2A> na Właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-134">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>

2. <span data-ttu-id="0e4e9-135">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-135">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     <span data-ttu-id="0e4e9-136">Metoda `AddRegionMapping` dodaje nowe mapowanie dla właściwości <xref:System.Windows.Forms.Control.Region%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-136">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="0e4e9-137">Metoda `OnRegionChange` przekształca Właściwość <xref:System.Windows.Forms.Control.Region%2A> na Właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-137">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="0e4e9-138">Metoda `Form1_Resize` obsługuje zdarzenie <xref:System.Windows.Forms.Control.Resize> formularza i rozmiary obszaru przycinania w celu dopasowania go do hostowanego elementu.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-138">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="0e4e9-139">Usuwanie domyślnego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="0e4e9-139">Removing a Default Property Mapping</span></span>

<span data-ttu-id="0e4e9-140">Usuń domyślne mapowanie właściwości, wywołując metodę <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>kontroli <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-140">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="0e4e9-141">Aby usunąć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="0e4e9-141">To remove a default property mapping</span></span>

- <span data-ttu-id="0e4e9-142">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-142">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     <span data-ttu-id="0e4e9-143">Metoda `RemoveCursorMapping` usuwa mapowanie domyślne dla właściwości <xref:System.Windows.Forms.Control.Cursor%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-143">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="0e4e9-144">Rozszerzanie domyślnego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="0e4e9-144">Extending a Default Property Mapping</span></span>

<span data-ttu-id="0e4e9-145">Można użyć domyślnego mapowania właściwości, a także poszerzyć go przy użyciu własnego mapowania.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-145">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="0e4e9-146">Aby zwiększyć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="0e4e9-146">To extend a default property mapping</span></span>

- <span data-ttu-id="0e4e9-147">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-147">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     <span data-ttu-id="0e4e9-148">Metoda `ExtendBackColorMapping` dodaje translator właściwości niestandardowych do istniejącego mapowania właściwości <xref:System.Windows.Forms.Control.BackColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-148">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>

     <span data-ttu-id="0e4e9-149">Metoda `OnBackColorChange` przypisuje określony obraz do właściwości <xref:System.Windows.Controls.Control.Background%2A> kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-149">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="0e4e9-150">Metoda `OnBackColorChange` jest wywoływana po zastosowaniu domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-150">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>

## <a name="initialize-your-property-mappings"></a><span data-ttu-id="0e4e9-151">Inicjuj mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="0e4e9-151">Initialize your property mappings</span></span>

1. <span data-ttu-id="0e4e9-152">Skopiuj następujący kod do definicji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-152">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     <span data-ttu-id="0e4e9-153">Metoda `Form1_Load` obsługuje zdarzenie <xref:System.Windows.Forms.Form.Load> i wykonuje następujące inicjalizacje.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-153">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>

    - <span data-ttu-id="0e4e9-154">Tworzy element <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e4e9-154">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>

    - <span data-ttu-id="0e4e9-155">Wywołuje metody zdefiniowane wcześniej w przewodniku, aby skonfigurować mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-155">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="0e4e9-156">Przypisuje początkowe wartości do mapowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-156">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="0e4e9-157">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="0e4e9-157">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e4e9-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e4e9-158">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="0e4e9-159">Mapowanie właściwości Windows Forms i WPF</span><span class="sxs-lookup"><span data-stu-id="0e4e9-159">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="0e4e9-160">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0e4e9-160">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="0e4e9-161">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0e4e9-161">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
