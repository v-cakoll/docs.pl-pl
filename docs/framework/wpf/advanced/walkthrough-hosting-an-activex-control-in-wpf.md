---
title: 'Przewodnik: Hosting kontrolki ActiveX w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 25019444e107af2ad681e9f51adebbf01c444438
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668323"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="5e603-102">Przewodnik: Hosting kontrolki ActiveX w WPF</span><span class="sxs-lookup"><span data-stu-id="5e603-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="5e603-103">Aby włączone ulepszone współdziałanie z przeglądarki, można użyć [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] kontrolki w swojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e603-103">To enable improved interaction with browsers, you can use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="5e603-104">W tym instruktażu pokazano, jak możesz hostować [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] jako formant na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony.</span><span class="sxs-lookup"><span data-stu-id="5e603-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="5e603-105">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="5e603-105">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="5e603-106">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="5e603-106">Creating the project.</span></span>

-   <span data-ttu-id="5e603-107">Tworzenie kontrolki ActiveX.</span><span class="sxs-lookup"><span data-stu-id="5e603-107">Creating the ActiveX control.</span></span>

-   <span data-ttu-id="5e603-108">Hosting kontrolki ActiveX na stronie WPF.</span><span class="sxs-lookup"><span data-stu-id="5e603-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="5e603-109">Po ukończeniu tego przewodnika, wiedzieć, jak używać [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] kontrolki w Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e603-109">When you have completed this walkthrough, you will understand how to use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e603-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5e603-110">Prerequisites</span></span>
 <span data-ttu-id="5e603-111">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="5e603-111">You need the following components to complete this walkthrough:</span></span>

-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] <span data-ttu-id="5e603-112">zainstalowana na komputerze, na którym jest zainstalowany program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e603-112">installed on the computer where Visual Studio is installed.</span></span>

-   <span data-ttu-id="5e603-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5e603-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="5e603-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="5e603-114">Creating the Project</span></span>

#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="5e603-115">Aby utworzyć i skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="5e603-115">To create and set up the project</span></span>

1.  <span data-ttu-id="5e603-116">Utwórz projekt aplikacji WPF, o nazwie `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="5e603-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2.  <span data-ttu-id="5e603-117">Dodaj projekt Biblioteka kontrolek formularzy Windows do rozwiązania, a następnie nadaj projektowi nazwę `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="5e603-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3.  <span data-ttu-id="5e603-118">W projekcie WmpAxLib Dodaj odwołanie do zestawu Windows Media Player, która nosi nazwę wmp.dll.</span><span class="sxs-lookup"><span data-stu-id="5e603-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4.  <span data-ttu-id="5e603-119">Otwórz **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="5e603-119">Open the **Toolbox**.</span></span>

5.  <span data-ttu-id="5e603-120">Kliknij prawym przyciskiem myszy **przybornika**, a następnie kliknij przycisk **wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="5e603-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6.  <span data-ttu-id="5e603-121">Kliknij przycisk **składników COM** zaznacz **Windows Media Player** sterowania, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5e603-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="5e603-122">Formant programu Windows Media Player jest dodawany do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="5e603-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7.  <span data-ttu-id="5e603-123">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1** pliku, a następnie kliknij przycisk **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="5e603-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8.  <span data-ttu-id="5e603-124">Zmień nazwę na `WmpAxControl.vb` lub `WmpAxControl.cs`, w zależności od języka.</span><span class="sxs-lookup"><span data-stu-id="5e603-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="5e603-125">Jeśli zostanie wyświetlony monit o zmianę nazwy wszystkich odwołań, kliknij przycisk **tak**.</span><span class="sxs-lookup"><span data-stu-id="5e603-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="5e603-126">Tworzenie kontrolki ActiveX</span><span class="sxs-lookup"><span data-stu-id="5e603-126">Creating the ActiveX Control</span></span>
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] <span data-ttu-id="5e603-127">automatycznie generuje <xref:System.Windows.Forms.AxHost> klasy otoki dla [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] kontroli, gdy formant został dodany do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="5e603-127">automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] control when the control is added to a design surface.</span></span> <span data-ttu-id="5e603-128">Poniższa procedura tworzy zestaw zarządzany o nazwie AxInterop.WMPLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5e603-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

#### <a name="to-create-the-activex-control"></a><span data-ttu-id="5e603-129">Aby utworzyć formant ActiveX</span><span class="sxs-lookup"><span data-stu-id="5e603-129">To create the ActiveX control</span></span>

1.  <span data-ttu-id="5e603-130">Otwórz WmpAxControl.vb lub WmpAxControl.cs w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="5e603-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2.  <span data-ttu-id="5e603-131">Z **przybornika**, dodawanie formantu programu Windows Media Player do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="5e603-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3.  <span data-ttu-id="5e603-132">W oknie dialogowym właściwości ustawić wartość kontrolki Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="5e603-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4.  <span data-ttu-id="5e603-133">Tworzenie projektu biblioteki kontrolek WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="5e603-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="5e603-134">Hostowanie kontrolki ActiveX na stronie WPF</span><span class="sxs-lookup"><span data-stu-id="5e603-134">Hosting the ActiveX Control on a WPF Page</span></span>

#### <a name="to-host-the-activex-control"></a><span data-ttu-id="5e603-135">Do hostowania kontrolki ActiveX</span><span class="sxs-lookup"><span data-stu-id="5e603-135">To host the ActiveX control</span></span>

1.  <span data-ttu-id="5e603-136">W projekcie HostingAxInWpf, należy dodać odwołanie do wygenerowany [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] zestawu współdziałania.</span><span class="sxs-lookup"><span data-stu-id="5e603-136">In the HostingAxInWpf project, add a reference to the generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperability assembly.</span></span>

     <span data-ttu-id="5e603-137">Ten zestaw o nazwie AxInterop.WMPLib.dll i został dodany do folderu debugowania projektu WmpAxLib po zaimportowaniu formantu programu Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="5e603-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2.  <span data-ttu-id="5e603-138">Dodaj odwołanie do zestawu WindowsFormsIntegration, która nosi nazwę WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="5e603-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3.  <span data-ttu-id="5e603-139">Dodaj odwołanie do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zestawu, która nosi nazwę System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="5e603-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4.  <span data-ttu-id="5e603-140">Otwórz pliku MainWindow.xaml w Projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="5e603-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5.  <span data-ttu-id="5e603-141">Nazwa <xref:System.Windows.Controls.Grid> elementu `grid1`.</span><span class="sxs-lookup"><span data-stu-id="5e603-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6.  <span data-ttu-id="5e603-142">W widoku projektu lub XAML, wybierz <xref:System.Windows.Window> elementu.</span><span class="sxs-lookup"><span data-stu-id="5e603-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7.  <span data-ttu-id="5e603-143">W oknie dialogowym właściwości kliknij **zdarzenia** kartę.</span><span class="sxs-lookup"><span data-stu-id="5e603-143">In the Properties window, click the **Events** tab.</span></span>

8.  <span data-ttu-id="5e603-144">Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5e603-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="5e603-145">Wstaw następujący kod do obsługi <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5e603-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="5e603-146">Ten kod tworzy wystąpienie <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli i dodaje instancję `AxWindowsMediaPlayer` formant jako jego podrzędny.</span><span class="sxs-lookup"><span data-stu-id="5e603-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="5e603-147">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="5e603-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e603-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e603-148">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="5e603-149">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5e603-149">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="5e603-150">Przewodnik: Hostowanie kontrolki złożonej Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="5e603-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="5e603-151">Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e603-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
