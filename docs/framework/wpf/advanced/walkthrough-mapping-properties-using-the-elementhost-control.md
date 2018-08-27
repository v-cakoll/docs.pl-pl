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
ms.openlocfilehash: 89d2c6476334080fb162eadd4b2bf5984970f3fd
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934684"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="0d559-102">Wskazówki: mapowanie właściwości z użyciem formantu ElementHost</span><span class="sxs-lookup"><span data-stu-id="0d559-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>

<span data-ttu-id="0d559-103">W tym instruktażu dowiesz się, jak używać <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> właściwości, aby zamapować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="0d559-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>

<span data-ttu-id="0d559-104">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="0d559-104">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="0d559-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="0d559-105">Creating the project.</span></span>

-   <span data-ttu-id="0d559-106">Definiowanie nowego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-106">Defining a new property mapping.</span></span>

-   <span data-ttu-id="0d559-107">Usuwanie mapowania właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="0d559-107">Removing a default property mapping.</span></span>

-   <span data-ttu-id="0d559-108">Rozszerzanie domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-108">Extending a default property mapping.</span></span>

<span data-ttu-id="0d559-109">Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [Mapowanie właściwości przy użyciu przykładu formantu ElementHost](http://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="0d559-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](http://go.microsoft.com/fwlink/?LinkID=160018).</span></span>

<span data-ttu-id="0d559-110">Po zakończeniu będzie można mapować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiadającego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości hostowanego elementu.</span><span class="sxs-lookup"><span data-stu-id="0d559-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0d559-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0d559-111">Prerequisites</span></span>

<span data-ttu-id="0d559-112">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="0d559-112">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="0d559-113">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0d559-113">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="0d559-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="0d559-114">Creating the Project</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="0d559-115">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="0d559-115">To create the project</span></span>

1.  <span data-ttu-id="0d559-116">Tworzenie **Windows Forms App** projektu o nazwie `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="0d559-116">Create a **Windows Forms App** project named `PropertyMappingWithElementHost`.</span></span>

2.  <span data-ttu-id="0d559-117">W **Eksploratora rozwiązań**, dodaj odwołania do następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów.</span><span class="sxs-lookup"><span data-stu-id="0d559-117">In **Solution Explorer**, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>

    -   <span data-ttu-id="0d559-118">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="0d559-118">PresentationCore</span></span>

    -   <span data-ttu-id="0d559-119">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="0d559-119">PresentationFramework</span></span>

    -   <span data-ttu-id="0d559-120">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="0d559-120">WindowsBase</span></span>

    -   <span data-ttu-id="0d559-121">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="0d559-121">WindowsFormsIntegration</span></span>

3.  <span data-ttu-id="0d559-122">Skopiuj poniższy kod w górnej części `Form1` pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="0d559-122">Copy the following code into the top of the `Form1` code file.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4.  <span data-ttu-id="0d559-123">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="0d559-123">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="0d559-124">Kliknij dwukrotnie formularz, aby dodać moduł obsługi zdarzenia <xref:System.Windows.Forms.Form.Load> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0d559-124">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>

5.  <span data-ttu-id="0d559-125">Wróć do projektanta Windows Forms i Dodaj program obsługi zdarzeń w formularzu <xref:System.Windows.Forms.Control.Resize> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0d559-125">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="0d559-126">Aby uzyskać więcej informacji, zobacz [jak: utworzyć zdarzenie obsługi za pomocą projektanta](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span><span class="sxs-lookup"><span data-stu-id="0d559-126">For more information, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>

6.  <span data-ttu-id="0d559-127">Zadeklaruj <xref:System.Windows.Forms.Integration.ElementHost> pole `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="0d559-127">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a><span data-ttu-id="0d559-128">Definiowanie nowego mapowania właściwości</span><span class="sxs-lookup"><span data-stu-id="0d559-128">Defining New Property Mappings</span></span>

<span data-ttu-id="0d559-129"><xref:System.Windows.Forms.Integration.ElementHost> Control oferuje kilka domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-129">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="0d559-130">Dodaj nowe mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metody <xref:System.Windows.Forms.Integration.ElementHost> formantu <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d559-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-define-new-property-mappings"></a><span data-ttu-id="0d559-131">Aby zdefiniować nowe mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="0d559-131">To define new property mappings</span></span>

1.  <span data-ttu-id="0d559-132">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="0d559-132">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     <span data-ttu-id="0d559-133">`AddMarginMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.Forms.Control.Margin%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-133">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>

     <span data-ttu-id="0d559-134">`OnMarginChange` Tłumaczy metoda <xref:System.Windows.Forms.Control.Margin%2A> właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-134">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>

2.  <span data-ttu-id="0d559-135">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="0d559-135">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     <span data-ttu-id="0d559-136">`AddRegionMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.Forms.Control.Region%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-136">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="0d559-137">`OnRegionChange` Tłumaczy metoda <xref:System.Windows.Forms.Control.Region%2A> właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-137">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="0d559-138">`Form1_Resize` Obsługiwała formularza <xref:System.Windows.Forms.Control.Resize> zdarzeń i rozmiar obszaru przycinania, aby dopasować element hostowany.</span><span class="sxs-lookup"><span data-stu-id="0d559-138">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="0d559-139">Usuwanie mapowania właściwości domyślne</span><span class="sxs-lookup"><span data-stu-id="0d559-139">Removing a Default Property Mapping</span></span>

<span data-ttu-id="0d559-140">Usuń mapowanie właściwości domyślne przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metody <xref:System.Windows.Forms.Integration.ElementHost> formantu <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d559-140">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="0d559-141">Aby usunąć mapowanie właściwości domyślne</span><span class="sxs-lookup"><span data-stu-id="0d559-141">To remove a default property mapping</span></span>

-   <span data-ttu-id="0d559-142">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="0d559-142">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     <span data-ttu-id="0d559-143">`RemoveCursorMapping` Metoda usuwa domyślnego mapowania dla <xref:System.Windows.Forms.Control.Cursor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-143">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="0d559-144">Rozszerzanie domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="0d559-144">Extending a Default Property Mapping</span></span>

<span data-ttu-id="0d559-145">Możesz użyć domyślnego mapowania właściwości i rozszerzać go za pomocą własnych mapowania.</span><span class="sxs-lookup"><span data-stu-id="0d559-145">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="0d559-146">Aby rozszerzyć domyślne mapowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="0d559-146">To extend a default property mapping</span></span>

-   <span data-ttu-id="0d559-147">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="0d559-147">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     <span data-ttu-id="0d559-148">`ExtendBackColorMapping` Metoda dodaje translator właściwości niestandardowych do istniejących <xref:System.Windows.Forms.Control.BackColor%2A> mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-148">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>

     <span data-ttu-id="0d559-149">`OnBackColorChange` Metoda przypisuje określonego obrazu do obsługiwanego formantu <xref:System.Windows.Controls.Control.Background%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-149">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="0d559-150">`OnBackColorChange` Metoda jest wywoływana po zastosowaniu do domyślnego mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-150">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>

## <a name="initialize-your-property-mappings"></a><span data-ttu-id="0d559-151">Inicjowanie mapowań właściwości</span><span class="sxs-lookup"><span data-stu-id="0d559-151">Initialize your property mappings</span></span>

1.  <span data-ttu-id="0d559-152">Skopiuj następujący kod do definicji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="0d559-152">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     <span data-ttu-id="0d559-153">`Form1_Load` Metodę uchwytów <xref:System.Windows.Forms.Form.Load> zdarzeń i wykonuje następujące inicjowanie.</span><span class="sxs-lookup"><span data-stu-id="0d559-153">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>

    -   <span data-ttu-id="0d559-154">Tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="0d559-154">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>

    -   <span data-ttu-id="0d559-155">Wywołuje metody, które są zdefiniowane we wcześniejszej części przewodnika do skonfigurowania mapowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-155">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    -   <span data-ttu-id="0d559-156">Przypisuje wartości początkowe, aby mapowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d559-156">Assigns initial values to the mapped properties.</span></span>

2.  <span data-ttu-id="0d559-157">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="0d559-157">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d559-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d559-158">See Also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="0d559-159">Mapowanie właściwości Windows Forms i WPF</span><span class="sxs-lookup"><span data-stu-id="0d559-159">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="0d559-160">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="0d559-160">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
- [<span data-ttu-id="0d559-161">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d559-161">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)