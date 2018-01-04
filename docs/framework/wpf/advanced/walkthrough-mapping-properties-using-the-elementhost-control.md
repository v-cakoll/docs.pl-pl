---
title: "Wskazówki: mapowanie właściwości z użyciem formantu ElementHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0db7b9677b5c8c415b6d0b3f49bd149c06843a33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="8cfc7-102">Wskazówki: mapowanie właściwości z użyciem formantu ElementHost</span><span class="sxs-lookup"><span data-stu-id="8cfc7-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>
<span data-ttu-id="8cfc7-103">Ten przewodnik przedstawia sposób użycia <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> właściwości do mapowania [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>  
  
 <span data-ttu-id="8cfc7-104">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="8cfc7-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="8cfc7-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="8cfc7-106">Definiowanie nowego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-106">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="8cfc7-107">Usuwanie mapowania właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-107">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="8cfc7-108">Rozszerzanie domyślne mapowanie właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-108">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="8cfc7-109">Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [mapowania właściwości przy użyciu przykładowych formantu ElementHost](http://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="8cfc7-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](http://go.microsoft.com/fwlink/?LinkID=160018).</span></span>  
  
 <span data-ttu-id="8cfc7-110">Gdy skończysz, będzie można mapować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiadającego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości w elemencie hostowanej.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8cfc7-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8cfc7-111">Prerequisites</span></span>  
 <span data-ttu-id="8cfc7-112">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="8cfc7-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="8cfc7-113">.,</span><span class="sxs-lookup"><span data-stu-id="8cfc7-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="8cfc7-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="8cfc7-114">Creating the Project</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="8cfc7-115">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="8cfc7-115">To create the project</span></span>  
  
1.  <span data-ttu-id="8cfc7-116">Utwórz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projekt aplikacji o nazwie `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-116">Create a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project named `PropertyMappingWithElementHost`.</span></span> <span data-ttu-id="8cfc7-117">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="8cfc7-117">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="8cfc7-118">W Eksploratorze rozwiązań, dodaj odwołania do następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-118">In Solution Explorer, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>  
  
    -   <span data-ttu-id="8cfc7-119">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="8cfc7-119">PresentationCore</span></span>  
  
    -   <span data-ttu-id="8cfc7-120">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="8cfc7-120">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="8cfc7-121">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="8cfc7-121">WindowsBase</span></span>  
  
    -   <span data-ttu-id="8cfc7-122">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="8cfc7-122">WindowsFormsIntegration</span></span>  
  
3.  <span data-ttu-id="8cfc7-123">Skopiuj następujący kod w górnej części `Form1` pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-123">Copy the following code into the top of the `Form1` code file.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="8cfc7-124">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-124">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="8cfc7-125">Kliknij dwukrotnie formularza, aby dodać obsługę zdarzeń dla <xref:System.Windows.Forms.Form.Load> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-125">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
5.  <span data-ttu-id="8cfc7-126">Powrót do projektanta formularzy systemu Windows i Dodaj program obsługi zdarzeń w formularzu <xref:System.Windows.Forms.Control.Resize> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-126">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="8cfc7-127">Aby uzyskać więcej informacji, zobacz [porady: tworzenie zdarzeń obsługi przy użyciu narzędzia Projektant](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).</span><span class="sxs-lookup"><span data-stu-id="8cfc7-127">For more information, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
6.  <span data-ttu-id="8cfc7-128">Deklarowanie <xref:System.Windows.Forms.Integration.ElementHost> w `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-128">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a><span data-ttu-id="8cfc7-129">Definiowanie nowych mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="8cfc7-129">Defining New Property Mappings</span></span>  
 <span data-ttu-id="8cfc7-130"><xref:System.Windows.Forms.Integration.ElementHost> Kontrola zapewnia kilka domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-130">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="8cfc7-131">Dodaj nowe mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metoda <xref:System.Windows.Forms.Integration.ElementHost> formantu <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-131">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-new-property-mappings"></a><span data-ttu-id="8cfc7-132">Aby zdefiniować nowe mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="8cfc7-132">To define new property mappings</span></span>  
  
1.  <span data-ttu-id="8cfc7-133">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-133">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     <span data-ttu-id="8cfc7-134">`AddMarginMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.Forms.Control.Margin%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-134">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>  
  
     <span data-ttu-id="8cfc7-135">`OnMarginChange` Tłumaczy — metoda <xref:System.Windows.Forms.Control.Margin%2A> właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-135">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>  
  
2.  <span data-ttu-id="8cfc7-136">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-136">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     <span data-ttu-id="8cfc7-137">`AddRegionMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.Forms.Control.Region%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-137">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="8cfc7-138">`OnRegionChange` Tłumaczy — metoda <xref:System.Windows.Forms.Control.Region%2A> właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-138">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="8cfc7-139">`Form1_Resize` Metoda obsługuje formularza <xref:System.Windows.Forms.Control.Resize> zdarzeń i rozmiar obszaru przycinania w celu dopasowania elementu hostowanej.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-139">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="8cfc7-140">Usuwanie mapowania właściwości domyślne</span><span class="sxs-lookup"><span data-stu-id="8cfc7-140">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="8cfc7-141">Usuń domyślne mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metoda <xref:System.Windows.Forms.Integration.ElementHost> formantu <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-141">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="8cfc7-142">Aby usunąć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="8cfc7-142">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="8cfc7-143">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-143">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     <span data-ttu-id="8cfc7-144">`RemoveCursorMapping` Metoda usuwa domyślnego mapowania dla <xref:System.Windows.Forms.Control.Cursor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-144">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="8cfc7-145">Rozszerzanie domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="8cfc7-145">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="8cfc7-146">Można użyć domyślnego mapowania właściwości i rozszerzać go z własnych mapowania.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-146">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="8cfc7-147">Aby rozszerzyć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="8cfc7-147">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="8cfc7-148">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-148">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     <span data-ttu-id="8cfc7-149">`ExtendBackColorMapping` Metoda dodaje translatora właściwości niestandardowych do istniejącej <xref:System.Windows.Forms.Control.BackColor%2A> mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-149">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>  
  
     <span data-ttu-id="8cfc7-150">`OnBackColorChange` — Metoda przypisuje określony obraz sterowania hostowanej <xref:System.Windows.Controls.Control.Background%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-150">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="8cfc7-151">`OnBackColorChange` Metoda jest wywoływana po zastosowaniu domyślne mapowanie właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-151">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="8cfc7-152">Inicjowanie mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="8cfc7-152">Initializing Your Property Mappings</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="8cfc7-153">Aby zainicjować mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="8cfc7-153">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="8cfc7-154">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-154">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     <span data-ttu-id="8cfc7-155">`Form1_Load` Dojścia metody <xref:System.Windows.Forms.Form.Load> zdarzeń i wykonuje następujące inicjowania.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-155">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="8cfc7-156">Tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-156">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>  
  
    -   <span data-ttu-id="8cfc7-157">Wywołuje metody zdefiniowanych we wcześniejszej części przewodnika, aby skonfigurować mapowań właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-157">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="8cfc7-158">Przypisuje wartości początkowej do mapowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-158">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="8cfc7-159">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8cfc7-159">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfc7-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cfc7-160">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="8cfc7-161">Mapowanie właściwości Windows Forms i WPF</span><span class="sxs-lookup"><span data-stu-id="8cfc7-161">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="8cfc7-162">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="8cfc7-162">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="8cfc7-163">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8cfc7-163">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
