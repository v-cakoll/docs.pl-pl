---
title: "Wskazówki: tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc357b8ad1ff450c699878dfffe1fbb6e2440f49
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="1571d-102">Wskazówki: tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="1571d-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="1571d-103">W tym temacie przedstawiono sposób tworzenia formantu Windows Presentation Foundation (WPF) do użycia w aplikacjach opartych na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1571d-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>  
  
 <span data-ttu-id="1571d-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="1571d-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="1571d-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="1571d-105">Create the project.</span></span>  
  
-   <span data-ttu-id="1571d-106">Utwórz nową kontrolkę WPF.</span><span class="sxs-lookup"><span data-stu-id="1571d-106">Create a new WPF control.</span></span>  
  
-   <span data-ttu-id="1571d-107">Dodaj nowy formant WPF do formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1571d-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="1571d-108">Formant WPF znajduje się w <xref:System.Windows.Forms.Integration.ElementHost> formantu.</span><span class="sxs-lookup"><span data-stu-id="1571d-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1571d-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="1571d-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1571d-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="1571d-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1571d-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1571d-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1571d-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1571d-112">Prerequisites</span></span>  
 <span data-ttu-id="1571d-113">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="1571d-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="1571d-114">.</span><span class="sxs-lookup"><span data-stu-id="1571d-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="1571d-115">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="1571d-115">Creating the Project</span></span>  
 <span data-ttu-id="1571d-116">Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1571d-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1571d-117">Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.</span><span class="sxs-lookup"><span data-stu-id="1571d-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="1571d-118">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="1571d-118">To create the project</span></span>  
  
-   <span data-ttu-id="1571d-119">Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="1571d-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `HostingWpf`.</span></span>  
  
## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="1571d-120">Tworzenie nowego formantu WPF</span><span class="sxs-lookup"><span data-stu-id="1571d-120">Creating a New WPF Control</span></span>  
 <span data-ttu-id="1571d-121">Tworzenie nowego formantu WPF i dodanie go do projektu jest tak proste, jak dodać innego elementu do projektu.</span><span class="sxs-lookup"><span data-stu-id="1571d-121">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="1571d-122">Projektant formularzy systemu Windows współdziała z określonego rodzaju formantu o nazwie *formantu złożonego*, lub *kontrolki użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="1571d-122">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="1571d-123">Aby uzyskać więcej informacji na temat formanty użytkownika WPF, zobacz <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="1571d-123">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1571d-124"><xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> Wpisz WPF różni się od typu formantu użytkownika udostępniane przez formularze systemu Windows o nazwie <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1571d-124">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>  
  
#### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="1571d-125">Aby utworzyć nową kontrolkę WPF</span><span class="sxs-lookup"><span data-stu-id="1571d-125">To create a new WPF control</span></span>  
  
1.  <span data-ttu-id="1571d-126">W **Eksploratora rozwiązań**, Dodaj nową **Biblioteka kontrolek użytkownika WPF** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="1571d-126">In **Solution Explorer**, add a new **WPF User Control Library** project to the solution.</span></span> <span data-ttu-id="1571d-127">Użyj nazwy domyślnej biblioteki formantu `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="1571d-127">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="1571d-128">Domyślna nazwa formantu to `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="1571d-128">The default control name is `UserControl1.xaml`.</span></span>  
  
     <span data-ttu-id="1571d-129">Dodawanie nowego formantu ma następujące skutki.</span><span class="sxs-lookup"><span data-stu-id="1571d-129">Adding the new control has the following effects.</span></span>  
  
    -   <span data-ttu-id="1571d-130">Dodawany jest UserControl1.xaml pliku.</span><span class="sxs-lookup"><span data-stu-id="1571d-130">File UserControl1.xaml is added.</span></span>  
  
    -   <span data-ttu-id="1571d-131">Plik UserControl1.xaml.cs lub UserControl1.xaml.vb jest dodawany.</span><span class="sxs-lookup"><span data-stu-id="1571d-131">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="1571d-132">Ten plik zawiera kodem obsługi zdarzeń i innych implementacji.</span><span class="sxs-lookup"><span data-stu-id="1571d-132">This file contains the code-behind for event handlers and other implementation.</span></span>  
  
    -   <span data-ttu-id="1571d-133">Odwołania do zestawów WPF zostaną dodane.</span><span class="sxs-lookup"><span data-stu-id="1571d-133">References to WPF assemblies are added.</span></span>  
  
    -   <span data-ttu-id="1571d-134">Otworzy się w pliku UserControl1.xaml [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1571d-134">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="1571d-135">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="1571d-135">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="1571d-136">Aby uzyskać więcej informacji, zobacz [porady: Wybierz i Przenieś elementy na powierzchnię projektu](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="1571d-136">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="1571d-137">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="1571d-137">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="1571d-138">Z **przybornika**, przeciągnij <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> sterowania na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="1571d-138">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>  
  
5.  <span data-ttu-id="1571d-139">W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanego zawartości**.</span><span class="sxs-lookup"><span data-stu-id="1571d-139">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1571d-140">Ogólnie rzecz biorąc należy udostępnić dokładniejsze zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="1571d-140">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="1571d-141"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontroli jest tu używany wyłącznie w celach ilustracyjnych.</span><span class="sxs-lookup"><span data-stu-id="1571d-141">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
6.  <span data-ttu-id="1571d-142">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="1571d-142">Build the project.</span></span>  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="1571d-143">Dodawanie formantu WPF do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1571d-143">Adding a WPF Control to a Windows Form</span></span>  
 <span data-ttu-id="1571d-144">Nowego formantu WPF jest gotowy do użycia w formularzu.</span><span class="sxs-lookup"><span data-stu-id="1571d-144">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="1571d-145">Formularze systemu Windows używa <xref:System.Windows.Forms.Integration.ElementHost> formantu do hosta zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="1571d-145">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content</span></span>  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="1571d-146">Aby dodać kontrolkę WPF do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1571d-146">To add a WPF control to a Windows Form</span></span>  
  
1.  <span data-ttu-id="1571d-147">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1571d-147">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="1571d-148">W **przybornika**, Znajdź kartę **formanty użytkownika WPF WPFUserControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="1571d-148">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>  
  
3.  <span data-ttu-id="1571d-149">Przeciągnij wystąpienia `UserControl1` na formularzu.</span><span class="sxs-lookup"><span data-stu-id="1571d-149">Drag an instance of `UserControl1` onto the form.</span></span>  
  
    -   <span data-ttu-id="1571d-150"><xref:System.Windows.Forms.Integration.ElementHost> Kontroli jest tworzony automatycznie w formularzu kontrolki WPF hosta.</span><span class="sxs-lookup"><span data-stu-id="1571d-150">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>  
  
    -   <span data-ttu-id="1571d-151"><xref:System.Windows.Forms.Integration.ElementHost> Nosi nazwę formantu `elementHost1` i w **właściwości** okna, można wyświetlić jego <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="1571d-151">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>  
  
    -   <span data-ttu-id="1571d-152">Odwołania do zestawów WPF zostaną dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="1571d-152">References to WPF assemblies are added to the project.</span></span>  
  
    -   <span data-ttu-id="1571d-153">`elementHost1` Formantem panelu tag inteligentny pokazujący dostępne opcje hostingu.</span><span class="sxs-lookup"><span data-stu-id="1571d-153">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>  
  
4.  <span data-ttu-id="1571d-154">W **zadania ElementHost** panelu tagów inteligentnych, wybierz opcję **Zadokuj w kontenerze nadrzędnym**.</span><span class="sxs-lookup"><span data-stu-id="1571d-154">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>  
  
5.  <span data-ttu-id="1571d-155">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="1571d-155">Press F5 to build and run the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1571d-156">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1571d-156">Next Steps</span></span>  
 <span data-ttu-id="1571d-157">Formularze systemu Windows i WPF są różnych technologii, ale są one przeznaczone do ściśle współpracować.</span><span class="sxs-lookup"><span data-stu-id="1571d-157">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="1571d-158">Aby zapewnić bardziej rozbudowane wygląd i zachowanie w aplikacji, należy spróbować wykonać następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="1571d-158">To provide richer appearance and behavior in your applications, try the following.</span></span>  
  
-   <span data-ttu-id="1571d-159">Hostowanie kontrolki formularza systemu Windows, na stronie programu WPF.</span><span class="sxs-lookup"><span data-stu-id="1571d-159">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="1571d-160">Aby uzyskać więcej informacji, zobacz [wskazówki: hostowanie kontrolki formularza systemu Windows na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="1571d-160">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
-   <span data-ttu-id="1571d-161">Style wizualne formularzy systemu Windows stosowane do zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="1571d-161">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="1571d-162">Aby uzyskać więcej informacji, zobacz [porady: Włączanie style wizualne w aplikacji hybrydowych](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="1571d-162">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>  
  
-   <span data-ttu-id="1571d-163">Zmienianie stylu zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="1571d-163">Change the style of your WPF content.</span></span> <span data-ttu-id="1571d-164">Aby uzyskać więcej informacji, zobacz [wskazówki: nadawanie stylu zawartości WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="1571d-164">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1571d-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1571d-165">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="1571d-166">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="1571d-166">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="1571d-167">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="1571d-167">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="1571d-168">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="1571d-168">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
