---
title: 'Wskazówki: mapowanie właściwości z użyciem elementu WindowsFormsHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: 771c0d972420b929ac757ced684de70d2dc7a58d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="177c9-102">Wskazówki: mapowanie właściwości z użyciem elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="177c9-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>
<span data-ttu-id="177c9-103">Ten przewodnik przedstawia sposób użycia <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> właściwości do mapowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.</span><span class="sxs-lookup"><span data-stu-id="177c9-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
 <span data-ttu-id="177c9-104">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="177c9-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="177c9-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="177c9-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="177c9-106">Definiowanie układu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="177c9-106">Defining the application layout.</span></span>  
  
-   <span data-ttu-id="177c9-107">Definiowanie nowego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-107">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="177c9-108">Usuwanie mapowania właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="177c9-108">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="177c9-109">Zastępowanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-109">Replacing a default property mapping.</span></span>  
  
-   <span data-ttu-id="177c9-110">Rozszerzanie domyślne mapowanie właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-110">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="177c9-111">Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [mapowania właściwości za pomocą przykład elementu WindowsFormsHost](http://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="177c9-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](http://go.microsoft.com/fwlink/?LinkID=160019).</span></span>  
  
 <span data-ttu-id="177c9-112">Gdy skończysz, będzie można mapować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.</span><span class="sxs-lookup"><span data-stu-id="177c9-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="177c9-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="177c9-113">Prerequisites</span></span>  
 <span data-ttu-id="177c9-114">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="177c9-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="177c9-115">.</span><span class="sxs-lookup"><span data-stu-id="177c9-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="177c9-116">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="177c9-116">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="177c9-117">Tworzenie i konfigurowanie projektu</span><span class="sxs-lookup"><span data-stu-id="177c9-117">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="177c9-118">Utwórz projekt aplikacji WPF o nazwie `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="177c9-118">Create a WPF Application project named `PropertyMappingWithWfhSample`.</span></span>  
  
2.  <span data-ttu-id="177c9-119">W Eksploratorze rozwiązań Dodaj odwołanie do zestawu WindowsFormsIntegration, o nazwie WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="177c9-119">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="177c9-120">W Eksploratorze rozwiązań Dodaj odwołania do zestawów System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="177c9-120">In Solution Explorer, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="defining-the-application-layout"></a><span data-ttu-id="177c9-121">Definiowanie układ aplikacji</span><span class="sxs-lookup"><span data-stu-id="177c9-121">Defining the Application Layout</span></span>  
 <span data-ttu-id="177c9-122">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— Na podstawie aplikacja używa <xref:System.Windows.Forms.Integration.WindowsFormsHost> element do hosta [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.</span><span class="sxs-lookup"><span data-stu-id="177c9-122">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-define-the-application-layout"></a><span data-ttu-id="177c9-123">Aby zdefiniować układ aplikacji</span><span class="sxs-lookup"><span data-stu-id="177c9-123">To define the application layout</span></span>  
  
1.  <span data-ttu-id="177c9-124">Otwórz Window1.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="177c9-124">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="177c9-125">Zastąp istniejący kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="177c9-125">Replace the existing code with the following code.</span></span>  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  <span data-ttu-id="177c9-126">Otwórz Window1.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="177c9-126">Open Window1.xaml.cs in the Code Editor.</span></span>  
  
4.  <span data-ttu-id="177c9-127">W górnej części pliku należy zaimportować następujących przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="177c9-127">At the top of the file, import the following namespaces.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="177c9-128">Definiowanie nowe mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-128">Defining a New Property Mapping</span></span>  
 <span data-ttu-id="177c9-129"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element udostępnia kilka domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-129">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="177c9-130">Dodaj nowe mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="177c9-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="177c9-131">Aby zdefiniować nowe mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-131">To define a new property mapping</span></span>  
  
-   <span data-ttu-id="177c9-132">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="177c9-132">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     <span data-ttu-id="177c9-133">`AddClipMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.UIElement.Clip%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-133">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="177c9-134">`OnClipChange` Tłumaczy — metoda <xref:System.Windows.UIElement.Clip%2A> właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-134">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="177c9-135">`Window1_SizeChanged` Metoda obsługuje okna <xref:System.Windows.FrameworkElement.SizeChanged> zdarzeń i rozmiar obszaru przycinania w celu dopasowania do okna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="177c9-135">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="177c9-136">Usuwanie mapowania właściwości domyślne</span><span class="sxs-lookup"><span data-stu-id="177c9-136">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="177c9-137">Usuń domyślne mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="177c9-137">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="177c9-138">Aby usunąć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-138">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="177c9-139">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="177c9-139">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     <span data-ttu-id="177c9-140">`RemoveCursorMapping` Metoda usuwa domyślnego mapowania dla <xref:System.Windows.FrameworkElement.Cursor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-140">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>  
  
## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="177c9-141">Zastępowanie domyślnego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-141">Replacing a Default Property Mapping</span></span>  
 <span data-ttu-id="177c9-142">Zastąp domyślne mapowanie właściwości przez usunięcie domyślnego mapowania i wywoływania <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="177c9-142">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="177c9-143">Aby zastąpić domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-143">To replace a default property mapping</span></span>  
  
-   <span data-ttu-id="177c9-144">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="177c9-144">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     <span data-ttu-id="177c9-145">`ReplaceFlowDirectionMapping` Metoda zastępuje domyślne mapowanie dla <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-145">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>  
  
     <span data-ttu-id="177c9-146">`OnFlowDirectionChange` Tłumaczy — metoda <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-146">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>  
  
     <span data-ttu-id="177c9-147">`cb_CheckedChanged` Dojścia metody <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenia w <xref:System.Windows.Forms.CheckBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="177c9-147">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="177c9-148">Przypisuje <xref:System.Windows.FrameworkElement.FlowDirection%2A> na podstawie właściwości na wartość <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-148">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="177c9-149">Rozszerzanie domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-149">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="177c9-150">Można użyć domyślnego mapowania właściwości i rozszerzać go z własnych mapowania.</span><span class="sxs-lookup"><span data-stu-id="177c9-150">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="177c9-151">Aby rozszerzyć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-151">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="177c9-152">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="177c9-152">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     <span data-ttu-id="177c9-153">`ExtendBackgroundMapping` Metoda dodaje translatora właściwości niestandardowych do istniejącej <xref:System.Windows.Controls.Control.Background%2A> mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-153">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>  
  
     <span data-ttu-id="177c9-154">`OnBackgroundChange` — Metoda przypisuje określony obraz sterowania hostowanej <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-154">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="177c9-155">`OnBackgroundChange` Metoda jest wywoływana po zastosowaniu domyślne mapowanie właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-155">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="177c9-156">Inicjowanie mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-156">Initializing Your Property Mappings</span></span>  
 <span data-ttu-id="177c9-157">Konfigurowanie mapowań właściwości przez wywołanie metody opisany wcześniej w <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="177c9-157">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="177c9-158">Aby zainicjować mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="177c9-158">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="177c9-159">Skopiuj następujący kod do definicji `Window1` klasy.</span><span class="sxs-lookup"><span data-stu-id="177c9-159">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     <span data-ttu-id="177c9-160">`WindowLoaded` Dojścia metody <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i wykonuje następujące inicjowania.</span><span class="sxs-lookup"><span data-stu-id="177c9-160">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="177c9-161">Tworzy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="177c9-161">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>  
  
    -   <span data-ttu-id="177c9-162">Wywołuje metody zdefiniowanych we wcześniejszej części przewodnika, aby skonfigurować mapowań właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-162">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="177c9-163">Przypisuje wartości początkowej do mapowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="177c9-163">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="177c9-164">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="177c9-164">Press F5 to build and run the application.</span></span> <span data-ttu-id="177c9-165">Kliknij pole wyboru, aby zobaczyć efekt <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapowania.</span><span class="sxs-lookup"><span data-stu-id="177c9-165">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="177c9-166">Po kliknięciu pola wyboru układ odwraca orientacji od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="177c9-166">When you click the check box, the layout reverses its left-right orientation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177c9-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="177c9-167">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="177c9-168">Mapowanie właściwości Windows Forms i WPF</span><span class="sxs-lookup"><span data-stu-id="177c9-168">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="177c9-169">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="177c9-169">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="177c9-170">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="177c9-170">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
