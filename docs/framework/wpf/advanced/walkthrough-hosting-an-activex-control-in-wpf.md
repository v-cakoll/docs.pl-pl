---
title: Hostowanie kontrolki ActiveX w WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: f2d9345eaaba7b85a217e6b230ae202f27ad3af8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742627"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="61baa-102">Wskazówki: hosting formantu ActiveX w WPF</span><span class="sxs-lookup"><span data-stu-id="61baa-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="61baa-103">Aby umożliwić lepszą interakcję z przeglądarkami, możesz użyć kontrolek ActiveX firmy Microsoft w aplikacji opartej na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61baa-103">To enable improved interaction with browsers, you can use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="61baa-104">W tym instruktażu pokazano, jak hostować Media Player Microsoft Windows jako kontrolkę na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stronie.</span><span class="sxs-lookup"><span data-stu-id="61baa-104">This walkthrough demonstrates how you can host the Microsoft Windows Media Player as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="61baa-105">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="61baa-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="61baa-106">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="61baa-106">Creating the project.</span></span>

- <span data-ttu-id="61baa-107">Tworzenie kontrolki ActiveX.</span><span class="sxs-lookup"><span data-stu-id="61baa-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="61baa-108">Hostowanie kontrolki ActiveX na stronie WPF.</span><span class="sxs-lookup"><span data-stu-id="61baa-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="61baa-109">Po ukończeniu tego przewodnika dowiesz się, jak używać kontrolek ActiveX firmy Microsoft w aplikacji opartej na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61baa-109">When you have completed this walkthrough, you will understand how to use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="61baa-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="61baa-110">Prerequisites</span></span>
 <span data-ttu-id="61baa-111">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="61baa-111">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="61baa-112">System Microsoft Windows Media Player zainstalowany na komputerze, na którym jest zainstalowany program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="61baa-112">Microsoft Windows Media Player installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="61baa-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="61baa-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="61baa-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="61baa-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="61baa-115">Aby utworzyć i skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="61baa-115">To create and set up the project</span></span>

1. <span data-ttu-id="61baa-116">Utwórz projekt aplikacji WPF o nazwie `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="61baa-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="61baa-117">Dodaj projekt biblioteki formantów Windows Forms do rozwiązania i nadaj nazwę projektowi `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="61baa-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="61baa-118">W projekcie WmpAxLib Dodaj odwołanie do zestawu Media Player systemu Windows o nazwie WMP. dll.</span><span class="sxs-lookup"><span data-stu-id="61baa-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="61baa-119">Otwórz **Przybornik**.</span><span class="sxs-lookup"><span data-stu-id="61baa-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="61baa-120">Kliknij prawym przyciskiem myszy w **przyborniku**, a następnie kliknij pozycję **Wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="61baa-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="61baa-121">Kliknij kartę **składniki com** , wybierz formant **Media Player systemu Windows** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="61baa-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="61baa-122">Kontrolka Media Player systemu Windows jest dodawana do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="61baa-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="61baa-123">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy plik **UserControl1** , a następnie kliknij polecenie **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="61baa-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="61baa-124">Zmień nazwę na `WmpAxControl.vb` lub `WmpAxControl.cs`, w zależności od języka.</span><span class="sxs-lookup"><span data-stu-id="61baa-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="61baa-125">Jeśli zostanie wyświetlony monit o zmianę nazwy wszystkich odwołań, kliknij przycisk **tak**.</span><span class="sxs-lookup"><span data-stu-id="61baa-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="61baa-126">Tworzenie kontrolki ActiveX</span><span class="sxs-lookup"><span data-stu-id="61baa-126">Creating the ActiveX Control</span></span>
<span data-ttu-id="61baa-127">Program Visual Studio automatycznie generuje klasę otoki <xref:System.Windows.Forms.AxHost> dla kontrolki ActiveX firmy Microsoft po dodaniu kontrolki do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="61baa-127">Visual Studio automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a Microsoft ActiveX control when the control is added to a design surface.</span></span> <span data-ttu-id="61baa-128">Poniższa procedura tworzy zarządzany zestaw o nazwie AxInterop. WMPLib. dll.</span><span class="sxs-lookup"><span data-stu-id="61baa-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="61baa-129">Aby utworzyć kontrolkę ActiveX</span><span class="sxs-lookup"><span data-stu-id="61baa-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="61baa-130">Otwórz WmpAxControl. vb lub WmpAxControl.cs w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="61baa-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="61baa-131">Z **przybornika**dodaj formant Media Player systemu Windows do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="61baa-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="61baa-132">W okno Właściwości ustaw wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> kontrolki Windows Media Player na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="61baa-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="61baa-133">Kompiluj projekt biblioteki formantów WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="61baa-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="61baa-134">Hostowanie kontrolki ActiveX na stronie WPF</span><span class="sxs-lookup"><span data-stu-id="61baa-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="61baa-135">Aby hostować formant ActiveX</span><span class="sxs-lookup"><span data-stu-id="61baa-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="61baa-136">W projekcie HostingAxInWpf Dodaj odwołanie do wygenerowanego zestawu współdziałania ActiveX.</span><span class="sxs-lookup"><span data-stu-id="61baa-136">In the HostingAxInWpf project, add a reference to the generated ActiveX interoperability assembly.</span></span>

     <span data-ttu-id="61baa-137">Ten zestaw ma nazwę AxInterop. WMPLib. dll i został dodany do folderu debugowania projektu WmpAxLib podczas importowania formantu Media Player systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="61baa-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="61baa-138">Dodaj odwołanie do zestawu WindowsFormsIntegration o nazwie WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="61baa-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="61baa-139">Dodaj odwołanie do zestawu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] o nazwie System. Windows. Forms. dll.</span><span class="sxs-lookup"><span data-stu-id="61baa-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="61baa-140">Otwórz MainWindow. XAML w projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="61baa-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="61baa-141">Nadaj nazwę elementowi <xref:System.Windows.Controls.Grid> `grid1`.</span><span class="sxs-lookup"><span data-stu-id="61baa-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="61baa-142">W widoku widok Projekt lub XAML wybierz element <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="61baa-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="61baa-143">W okno Właściwości kliknij kartę **zdarzenia** .</span><span class="sxs-lookup"><span data-stu-id="61baa-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="61baa-144">Kliknij dwukrotnie zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="61baa-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="61baa-145">Wstaw poniższy kod, aby obsłużyć zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="61baa-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="61baa-146">Ten kod tworzy wystąpienie formantu <xref:System.Windows.Forms.Integration.WindowsFormsHost> i dodaje wystąpienie formantu `AxWindowsMediaPlayer` jako jego element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="61baa-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="61baa-147">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="61baa-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61baa-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61baa-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="61baa-149">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="61baa-149">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="61baa-150">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="61baa-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="61baa-151">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="61baa-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
