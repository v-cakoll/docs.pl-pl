---
title: 'Wskazówki: mapowanie właściwości z użyciem elementu WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: 94d175ec58f35b7e807786c221437d05c605c0bc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974224"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="81c06-102">Wskazówki: mapowanie właściwości z użyciem elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="81c06-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="81c06-103">W tym instruktażu przedstawiono sposób użycia właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> do mapowania właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do odpowiednich właściwości w hostowanej kontroli [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81c06-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="81c06-104">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="81c06-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="81c06-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="81c06-105">Creating the project.</span></span>

- <span data-ttu-id="81c06-106">Definiowanie układu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="81c06-106">Defining the application layout.</span></span>

- <span data-ttu-id="81c06-107">Definiowanie nowego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="81c06-107">Defining a new property mapping.</span></span>

- <span data-ttu-id="81c06-108">Usuwanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="81c06-108">Removing a default property mapping.</span></span>

- <span data-ttu-id="81c06-109">Zastępowanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="81c06-109">Replacing a default property mapping.</span></span>

- <span data-ttu-id="81c06-110">Rozszerzanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="81c06-110">Extending a default property mapping.</span></span>

<span data-ttu-id="81c06-111">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [Mapowanie właściwości przy użyciu przykładu elementu WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="81c06-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="81c06-112">Po zakończeniu będzie możliwe mapowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiednich właściwości w hostowanej kontrolce [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81c06-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="81c06-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="81c06-113">Prerequisites</span></span>

<span data-ttu-id="81c06-114">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="81c06-114">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="81c06-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="81c06-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="81c06-116">Tworzenie i Konfigurowanie projektu</span><span class="sxs-lookup"><span data-stu-id="81c06-116">Create and set up the project</span></span>

1. <span data-ttu-id="81c06-117">Utwórz projekt **aplikacji WPF** o nazwie `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="81c06-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="81c06-118">W **Eksplorator rozwiązań**Dodaj odwołanie do zestawu WindowsFormsIntegration o nazwie WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="81c06-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="81c06-119">W **Eksplorator rozwiązań**Dodaj odwołania do zestawów System. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="81c06-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="81c06-120">Definiowanie układu aplikacji</span><span class="sxs-lookup"><span data-stu-id="81c06-120">Defining the Application Layout</span></span>

<span data-ttu-id="81c06-121">Aplikacja oparta na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]używa elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> do hostowania kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81c06-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="81c06-122">Aby zdefiniować układ aplikacji</span><span class="sxs-lookup"><span data-stu-id="81c06-122">To define the application layout</span></span>

1. <span data-ttu-id="81c06-123">Otwórz window1. XAML w projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="81c06-123">Open Window1.xaml in the WPF Designer.</span></span>

2. <span data-ttu-id="81c06-124">Zastąp istniejący kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="81c06-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="81c06-125">Otwórz Window1.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="81c06-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="81c06-126">W górnej części pliku Zaimportuj następujące przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="81c06-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="81c06-127">Definiowanie nowego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="81c06-128">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zawiera kilka domyślnych mapowań właściwości.</span><span class="sxs-lookup"><span data-stu-id="81c06-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="81c06-129">Dodaj nowe mapowanie właściwości, wywołując metodę <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> w <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="81c06-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="81c06-130">Aby zdefiniować nowe mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-130">To define a new property mapping</span></span>

- <span data-ttu-id="81c06-131">Skopiuj następujący kod do definicji klasy `Window1`.</span><span class="sxs-lookup"><span data-stu-id="81c06-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="81c06-132">Metoda `AddClipMapping` dodaje nowe mapowanie dla właściwości <xref:System.Windows.UIElement.Clip%2A>.</span><span class="sxs-lookup"><span data-stu-id="81c06-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="81c06-133">Metoda `OnClipChange` przekształca Właściwość <xref:System.Windows.UIElement.Clip%2A> na Właściwość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>.</span><span class="sxs-lookup"><span data-stu-id="81c06-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="81c06-134">Metoda `Window1_SizeChanged` obsługuje zdarzenie <xref:System.Windows.FrameworkElement.SizeChanged> okna i rozmiary obszaru przycinania w celu dopasowania go do okna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="81c06-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="81c06-135">Usuwanie domyślnego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="81c06-136">Usuń domyślne mapowanie właściwości, wywołując metodę <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> w <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="81c06-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="81c06-137">Aby usunąć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-137">To remove a default property mapping</span></span>

- <span data-ttu-id="81c06-138">Skopiuj następujący kod do definicji klasy `Window1`.</span><span class="sxs-lookup"><span data-stu-id="81c06-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="81c06-139">Metoda `RemoveCursorMapping` usuwa mapowanie domyślne dla właściwości <xref:System.Windows.FrameworkElement.Cursor%2A>.</span><span class="sxs-lookup"><span data-stu-id="81c06-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="81c06-140">Zastępowanie domyślnego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="81c06-141">Zastąp domyślne mapowanie właściwości, usuwając mapowanie domyślne i wywołując metodę <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> w <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="81c06-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="81c06-142">Aby zastąpić domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-142">To replace a default property mapping</span></span>

- <span data-ttu-id="81c06-143">Skopiuj następujący kod do definicji klasy `Window1`.</span><span class="sxs-lookup"><span data-stu-id="81c06-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="81c06-144">Metoda `ReplaceFlowDirectionMapping` zastępuje domyślne mapowanie dla właściwości <xref:System.Windows.FrameworkElement.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="81c06-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="81c06-145">Metoda `OnFlowDirectionChange` przekształca Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> na Właściwość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A>.</span><span class="sxs-lookup"><span data-stu-id="81c06-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="81c06-146">Metoda `cb_CheckedChanged` obsługuje zdarzenie <xref:System.Windows.Forms.CheckBox.CheckedChanged> w kontrolce <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="81c06-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="81c06-147">Przypisuje Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> na podstawie wartości właściwości <xref:System.Windows.Forms.CheckBox.CheckState%2A></span><span class="sxs-lookup"><span data-stu-id="81c06-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="81c06-148">Rozszerzanie domyślnego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="81c06-149">Można użyć domyślnego mapowania właściwości, a także poszerzyć go przy użyciu własnego mapowania.</span><span class="sxs-lookup"><span data-stu-id="81c06-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="81c06-150">Aby zwiększyć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-150">To extend a default property mapping</span></span>

- <span data-ttu-id="81c06-151">Skopiuj następujący kod do definicji klasy `Window1`.</span><span class="sxs-lookup"><span data-stu-id="81c06-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="81c06-152">Metoda `ExtendBackgroundMapping` dodaje translator właściwości niestandardowych do istniejącego mapowania właściwości <xref:System.Windows.Controls.Control.Background%2A>.</span><span class="sxs-lookup"><span data-stu-id="81c06-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="81c06-153">Metoda `OnBackgroundChange` przypisuje określony obraz do właściwości <xref:System.Windows.Forms.Control.BackgroundImage%2A> kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="81c06-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="81c06-154">Metoda `OnBackgroundChange` jest wywoływana po zastosowaniu domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="81c06-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="81c06-155">Inicjowanie mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="81c06-156">Skonfiguruj mapowania właściwości, wywołując poprzednio opisane metody w obsłudze zdarzeń <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="81c06-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="81c06-157">Aby zainicjować mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="81c06-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="81c06-158">Skopiuj następujący kod do definicji klasy `Window1`.</span><span class="sxs-lookup"><span data-stu-id="81c06-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="81c06-159">Metoda `WindowLoaded` obsługuje zdarzenie <xref:System.Windows.FrameworkElement.Loaded> i wykonuje następujące inicjalizacje.</span><span class="sxs-lookup"><span data-stu-id="81c06-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    - <span data-ttu-id="81c06-160">Tworzy kontrolkę <xref:System.Windows.Forms.CheckBox> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81c06-160">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>

    - <span data-ttu-id="81c06-161">Wywołuje metody zdefiniowane wcześniej w przewodniku, aby skonfigurować mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="81c06-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="81c06-162">Przypisuje początkowe wartości do mapowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="81c06-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="81c06-163">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="81c06-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="81c06-164">Kliknij pole wyboru, aby zobaczyć efekt mapowania <xref:System.Windows.FrameworkElement.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="81c06-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="81c06-165">Po kliknięciu pola wyboru układ zmieni orientację w lewo i w prawo.</span><span class="sxs-lookup"><span data-stu-id="81c06-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="81c06-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81c06-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="81c06-167">Mapowanie właściwości Windows Forms i WPF</span><span class="sxs-lookup"><span data-stu-id="81c06-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="81c06-168">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="81c06-168">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="81c06-169">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="81c06-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
