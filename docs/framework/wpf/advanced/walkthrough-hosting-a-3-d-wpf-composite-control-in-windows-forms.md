---
title: 'Wskazówki: Hosting złożonego formantu 3D WPF w Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: a9aca5d1aff1057d85509be517bb352b4b27bf9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548210"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="b1c94-102">Wskazówki: Hosting złożonego formantu 3D WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1c94-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>
<span data-ttu-id="b1c94-103">W tym przewodniku przedstawiono sposób tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego kontroli i udostępnić go w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów i formularzy przy użyciu <xref:System.Windows.Forms.Integration.ElementHost> formantu.</span><span class="sxs-lookup"><span data-stu-id="b1c94-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
 <span data-ttu-id="b1c94-104">W tym przewodniku zostaną zaimplementowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> zawiera dwa formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b1c94-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="b1c94-105"><xref:System.Windows.Controls.UserControl> Wyświetla trójwymiarowy stożkowy (3-).</span><span class="sxs-lookup"><span data-stu-id="b1c94-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="b1c94-106">Renderowanie 3-obiektów jest znacznie łatwiejsze w przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niż z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1c94-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="b1c94-107">W związku z tym warto hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> klasy w celu utworzenia grafiki 3-w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1c94-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="b1c94-108">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="b1c94-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="b1c94-109">Tworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="b1c94-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
-   <span data-ttu-id="b1c94-110">Tworzenie projektu hosta formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b1c94-110">Creating the Windows Forms host project.</span></span>  
  
-   <span data-ttu-id="b1c94-111">Hosting [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="b1c94-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
 <span data-ttu-id="b1c94-112">Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [Hosting 3-formantu złożonego WPF w przykładowym formularzy systemu Windows](http://go.microsoft.com/fwlink/?LinkID=160001).</span><span class="sxs-lookup"><span data-stu-id="b1c94-112">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a 3-D WPF Composite Control in Windows Forms Sample](http://go.microsoft.com/fwlink/?LinkID=160001).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b1c94-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b1c94-113">Prerequisites</span></span>  
 <span data-ttu-id="b1c94-114">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="b1c94-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="b1c94-115">.</span><span class="sxs-lookup"><span data-stu-id="b1c94-115">.</span></span>  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a><span data-ttu-id="b1c94-116">Tworzenie kontrolki użytkownika</span><span class="sxs-lookup"><span data-stu-id="b1c94-116">Creating the UserControl</span></span>  
  
#### <a name="to-create-the-usercontrol"></a><span data-ttu-id="b1c94-117">Można utworzyć elementu UserControl</span><span class="sxs-lookup"><span data-stu-id="b1c94-117">To create the UserControl</span></span>  
  
1.  <span data-ttu-id="b1c94-118">Tworzenie projektu Biblioteka formantów WPF użytkownika o nazwie `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="b1c94-118">Create a WPF User Control Library project named `HostingWpfUserControlInWf`.</span></span>  
  
2.  <span data-ttu-id="b1c94-119">Otwórz UserControl1.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1c94-119">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
3.  <span data-ttu-id="b1c94-120">Zastąp następujący kod wygenerowany kod.</span><span class="sxs-lookup"><span data-stu-id="b1c94-120">Replace the generated code with the following code.</span></span>  
  
     <span data-ttu-id="b1c94-121">Ten kod definiuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> zawiera dwa formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b1c94-121">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="b1c94-122">Pierwszy formant podrzędny ma <xref:System.Windows.Controls.Label?displayProperty=nameWithType> formantu; druga jest <xref:System.Windows.Controls.Viewport3D> kontrolkę wyświetlającą stożkowy 3-w.</span><span class="sxs-lookup"><span data-stu-id="b1c94-122">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="b1c94-123">Tworzenie projektu hosta formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b1c94-123">Creating the Windows Forms Host Project</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="b1c94-124">Aby utworzyć projekt z hosta</span><span class="sxs-lookup"><span data-stu-id="b1c94-124">To create the host project</span></span>  
  
1.  <span data-ttu-id="b1c94-125">Dodaj projekt aplikacji systemu Windows o nazwie `WpfUserControlHost` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b1c94-125">Add a Windows application project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="b1c94-126">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="b1c94-126">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="b1c94-127">W Eksploratorze rozwiązań Dodaj odwołanie do zestawu WindowsFormsIntegration, o nazwie WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="b1c94-127">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="b1c94-128">Dodaj odwołania do następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów:</span><span class="sxs-lookup"><span data-stu-id="b1c94-128">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>  
  
    -   <span data-ttu-id="b1c94-129">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="b1c94-129">PresentationCore</span></span>  
  
    -   <span data-ttu-id="b1c94-130">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="b1c94-130">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="b1c94-131">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="b1c94-131">WindowsBase</span></span>  
  
4.  <span data-ttu-id="b1c94-132">Dodaj odwołanie do `HostingWpfUserControlInWf` projektu.</span><span class="sxs-lookup"><span data-stu-id="b1c94-132">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>  
  
5.  <span data-ttu-id="b1c94-133">W Eksploratorze rozwiązań, ustaw `WpfUserControlHost` projekt jako projekt startowy.</span><span class="sxs-lookup"><span data-stu-id="b1c94-133">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a><span data-ttu-id="b1c94-134">Hosting kontrolki systemu Windows Presentation Foundation użytkownika</span><span class="sxs-lookup"><span data-stu-id="b1c94-134">Hosting the Windows Presentation Foundation UserControl</span></span>  
  
#### <a name="to-host-the-usercontrol"></a><span data-ttu-id="b1c94-135">Na hoście UserControl</span><span class="sxs-lookup"><span data-stu-id="b1c94-135">To host the UserControl</span></span>  
  
1.  <span data-ttu-id="b1c94-136">W narzędziu Projektant dla formularzy systemu Windows otwórz Form1.</span><span class="sxs-lookup"><span data-stu-id="b1c94-136">In the Windows Forms Designer, open Form1.</span></span>  
  
2.  <span data-ttu-id="b1c94-137">Kliknij w oknie właściwości **zdarzenia**, a następnie kliknij dwukrotnie <xref:System.Windows.Forms.Form.Load> zdarzeń, aby utworzyć program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b1c94-137">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>  
  
     <span data-ttu-id="b1c94-138">Otwiera edytora kodu do nowo utworzonego `Form1_Load` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b1c94-138">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>  
  
3.  <span data-ttu-id="b1c94-139">Zastąp kod w pliku Form1.cs następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="b1c94-139">Replace the code in Form1.cs with the following code.</span></span>  
  
     <span data-ttu-id="b1c94-140">`Form1_Load` Obsługi zdarzeń tworzy wystąpienie `UserControl1` i dodaje je <xref:System.Windows.Forms.Integration.ElementHost> kolekcja formantów podrzędnych formantu.</span><span class="sxs-lookup"><span data-stu-id="b1c94-140">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="b1c94-141"><xref:System.Windows.Forms.Integration.ElementHost> Formant został dodany do formularza kolekcja formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b1c94-141">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="b1c94-142">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b1c94-142">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c94-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1c94-143">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="b1c94-144">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="b1c94-144">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="b1c94-145">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1c94-145">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="b1c94-146">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="b1c94-146">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="b1c94-147">Hostowanie formantu złożonego WPF w przykładowym formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b1c94-147">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160001)
