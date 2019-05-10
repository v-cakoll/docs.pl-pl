---
title: 'Przewodnik: mapowanie właściwości przy użyciu kontrolki WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: a7c36e8fc150fe3268120ed728f1bed87d24e800
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623587"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="f3a7e-102">Przewodnik: mapowanie właściwości przy użyciu kontrolki WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="f3a7e-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="f3a7e-103">W tym instruktażu dowiesz się, jak używać <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> właściwości, aby zamapować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="f3a7e-104">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="f3a7e-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="f3a7e-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-105">Creating the project.</span></span>

- <span data-ttu-id="f3a7e-106">Definiowanie układów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-106">Defining the application layout.</span></span>

- <span data-ttu-id="f3a7e-107">Definiowanie nowego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-107">Defining a new property mapping.</span></span>

- <span data-ttu-id="f3a7e-108">Usuwanie mapowania właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-108">Removing a default property mapping.</span></span>

- <span data-ttu-id="f3a7e-109">Zastępowanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-109">Replacing a default property mapping.</span></span>

- <span data-ttu-id="f3a7e-110">Rozszerzanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-110">Extending a default property mapping.</span></span>

<span data-ttu-id="f3a7e-111">Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [Mapowanie właściwości przy użyciu przykładu elementu WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="f3a7e-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="f3a7e-112">Po zakończeniu będzie można mapować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f3a7e-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f3a7e-113">Prerequisites</span></span>

<span data-ttu-id="f3a7e-114">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="f3a7e-114">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="f3a7e-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f3a7e-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="f3a7e-116">Tworzenie i konfigurowanie projektu</span><span class="sxs-lookup"><span data-stu-id="f3a7e-116">Create and set up the project</span></span>

1. <span data-ttu-id="f3a7e-117">Tworzenie **aplikacja WPF** projektu o nazwie `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="f3a7e-118">W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu WindowsFormsIntegration, która nosi nazwę WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="f3a7e-119">W **Eksploratora rozwiązań**, dodaj odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="f3a7e-120">Definiowanie układu aplikacji</span><span class="sxs-lookup"><span data-stu-id="f3a7e-120">Defining the Application Layout</span></span>

<span data-ttu-id="f3a7e-121">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— Na podstawie aplikacja używa <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu hosta [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="f3a7e-122">Aby zdefiniować układ aplikacji</span><span class="sxs-lookup"><span data-stu-id="f3a7e-122">To define the application layout</span></span>

1. <span data-ttu-id="f3a7e-123">Otwórz Window1.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3a7e-123">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

2. <span data-ttu-id="f3a7e-124">Zastąp istniejący kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="f3a7e-125">Otwórz Window1.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="f3a7e-126">W górnej części pliku zaimportuj następujące przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="f3a7e-127">Definiowanie nowe mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="f3a7e-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="f3a7e-128"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu udostępnia kilka domyślne mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="f3a7e-129">Dodaj nowe mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metody <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="f3a7e-130">Aby zdefiniować nowe mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="f3a7e-130">To define a new property mapping</span></span>

- <span data-ttu-id="f3a7e-131">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="f3a7e-132">`AddClipMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.UIElement.Clip%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="f3a7e-133">`OnClipChange` Tłumaczy metoda <xref:System.Windows.UIElement.Clip%2A> właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="f3a7e-134">`Window1_SizeChanged` Obsługiwała okna <xref:System.Windows.FrameworkElement.SizeChanged> zdarzeń i rozmiar obszaru przycinania do rozmiaru okna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="f3a7e-135">Usuwanie mapowania właściwości domyślne</span><span class="sxs-lookup"><span data-stu-id="f3a7e-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="f3a7e-136">Usuń mapowanie właściwości domyślne przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metody <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="f3a7e-137">Aby usunąć mapowanie właściwości domyślne</span><span class="sxs-lookup"><span data-stu-id="f3a7e-137">To remove a default property mapping</span></span>

- <span data-ttu-id="f3a7e-138">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="f3a7e-139">`RemoveCursorMapping` Metoda usuwa domyślnego mapowania dla <xref:System.Windows.FrameworkElement.Cursor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="f3a7e-140">Zastępowanie domyślnego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="f3a7e-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="f3a7e-141">Zastąp domyślne mapowanie właściwości przez usunięcie domyślnego mapowania i wywoływania <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metody <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="f3a7e-142">Aby zastąpić domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="f3a7e-142">To replace a default property mapping</span></span>

- <span data-ttu-id="f3a7e-143">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="f3a7e-144">`ReplaceFlowDirectionMapping` Metoda zastępuje domyślne mapowanie dla <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="f3a7e-145">`OnFlowDirectionChange` Tłumaczy metoda <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="f3a7e-146">`cb_CheckedChanged` Metodę uchwytów <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenie na <xref:System.Windows.Forms.CheckBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="f3a7e-147">Przypisuje <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości na podstawie wartości z <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości</span><span class="sxs-lookup"><span data-stu-id="f3a7e-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="f3a7e-148">Rozszerzanie domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="f3a7e-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="f3a7e-149">Możesz użyć domyślnego mapowania właściwości i rozszerzać go za pomocą własnych mapowania.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="f3a7e-150">Aby rozszerzyć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="f3a7e-150">To extend a default property mapping</span></span>

- <span data-ttu-id="f3a7e-151">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="f3a7e-152">`ExtendBackgroundMapping` Metoda dodaje translator właściwości niestandardowych do istniejących <xref:System.Windows.Controls.Control.Background%2A> mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="f3a7e-153">`OnBackgroundChange` Metoda przypisuje określonego obrazu do obsługiwanego formantu <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="f3a7e-154">`OnBackgroundChange` Metoda jest wywoływana po zastosowaniu do domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="f3a7e-155">Inicjowanie mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="f3a7e-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="f3a7e-156">Konfigurowanie mapowań właściwości przez wywołanie metody opisany wcześniej w <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="f3a7e-157">Aby zainicjować mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="f3a7e-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="f3a7e-158">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="f3a7e-159">`WindowLoaded` Metodę uchwytów <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i wykonuje następujące inicjowanie.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    - <span data-ttu-id="f3a7e-160">Tworzy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-160">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>

    - <span data-ttu-id="f3a7e-161">Wywołuje metody, które są zdefiniowane we wcześniejszej części przewodnika do skonfigurowania mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="f3a7e-162">Przypisuje wartości początkowe, aby mapowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="f3a7e-163">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="f3a7e-164">Kliknij pole wyboru, aby zobaczyć efekt <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapowania.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="f3a7e-165">Po kliknięciu pola wyboru, układ odwraca orientacji lewa prawa.</span><span class="sxs-lookup"><span data-stu-id="f3a7e-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3a7e-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3a7e-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f3a7e-167">Mapowanie właściwości Windows Forms i WPF</span><span class="sxs-lookup"><span data-stu-id="f3a7e-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="f3a7e-168">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3a7e-168">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="f3a7e-169">Przewodnik: Hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="f3a7e-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)