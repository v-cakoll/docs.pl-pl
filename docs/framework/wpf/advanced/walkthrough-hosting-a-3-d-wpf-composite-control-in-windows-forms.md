---
title: "Wskazówki: Hosting złożonego formantu 3D WPF w Windows Forms"
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
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 064626e3975838062c2d2287d29aa268edb8f21e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="5cc7f-102">Wskazówki: Hosting złożonego formantu 3D WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cc7f-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>
<span data-ttu-id="5cc7f-103">W tym przewodniku przedstawiono sposób tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego kontroli i udostępnić go w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów i formularzy przy użyciu <xref:System.Windows.Forms.Integration.ElementHost> formantu.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
 <span data-ttu-id="5cc7f-104">W tym przewodniku zostaną zaimplementowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> zawiera dwa formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="5cc7f-105"><xref:System.Windows.Controls.UserControl> Wyświetla trójwymiarowy stożkowy (3-).</span><span class="sxs-lookup"><span data-stu-id="5cc7f-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="5cc7f-106">Renderowanie 3-obiektów jest znacznie łatwiejsze w przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niż z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cc7f-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="5cc7f-107">W związku z tym warto hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> klasy w celu utworzenia grafiki 3-w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cc7f-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="5cc7f-108">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="5cc7f-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="5cc7f-109">Tworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
-   <span data-ttu-id="5cc7f-110">Tworzenie projektu hosta formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-110">Creating the Windows Forms host project.</span></span>  
  
-   <span data-ttu-id="5cc7f-111">Hosting [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
 <span data-ttu-id="5cc7f-112">Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [Hosting 3-formantu złożonego WPF w przykładowym formularzy systemu Windows](http://go.microsoft.com/fwlink/?LinkID=160001).</span><span class="sxs-lookup"><span data-stu-id="5cc7f-112">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a 3-D WPF Composite Control in Windows Forms Sample](http://go.microsoft.com/fwlink/?LinkID=160001).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5cc7f-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5cc7f-113">Prerequisites</span></span>  
 <span data-ttu-id="5cc7f-114">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="5cc7f-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="5cc7f-115">.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-115">.</span></span>  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a><span data-ttu-id="5cc7f-116">Tworzenie kontrolki użytkownika</span><span class="sxs-lookup"><span data-stu-id="5cc7f-116">Creating the UserControl</span></span>  
  
#### <a name="to-create-the-usercontrol"></a><span data-ttu-id="5cc7f-117">Można utworzyć elementu UserControl</span><span class="sxs-lookup"><span data-stu-id="5cc7f-117">To create the UserControl</span></span>  
  
1.  <span data-ttu-id="5cc7f-118">Tworzenie projektu Biblioteka formantów WPF użytkownika o nazwie `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-118">Create a WPF User Control Library project named `HostingWpfUserControlInWf`.</span></span>  
  
2.  <span data-ttu-id="5cc7f-119">Otwórz UserControl1.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cc7f-119">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
3.  <span data-ttu-id="5cc7f-120">Zastąp następujący kod wygenerowany kod.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-120">Replace the generated code with the following code.</span></span>  
  
     <span data-ttu-id="5cc7f-121">Ten kod definiuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> zawiera dwa formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-121">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="5cc7f-122">Pierwszy formant podrzędny ma <xref:System.Windows.Controls.Label?displayProperty=nameWithType> formantu; druga jest <xref:System.Windows.Controls.Viewport3D> kontrolkę wyświetlającą stożkowy 3-w.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-122">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="5cc7f-123">Tworzenie projektu hosta formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5cc7f-123">Creating the Windows Forms Host Project</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="5cc7f-124">Aby utworzyć projekt z hosta</span><span class="sxs-lookup"><span data-stu-id="5cc7f-124">To create the host project</span></span>  
  
1.  <span data-ttu-id="5cc7f-125">Dodaj projekt aplikacji systemu Windows o nazwie `WpfUserControlHost` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-125">Add a Windows application project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="5cc7f-126">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="5cc7f-126">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="5cc7f-127">W Eksploratorze rozwiązań Dodaj odwołanie do zestawu WindowsFormsIntegration, o nazwie WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-127">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="5cc7f-128">Dodaj odwołania do następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów:</span><span class="sxs-lookup"><span data-stu-id="5cc7f-128">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>  
  
    -   <span data-ttu-id="5cc7f-129">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="5cc7f-129">PresentationCore</span></span>  
  
    -   <span data-ttu-id="5cc7f-130">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="5cc7f-130">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="5cc7f-131">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="5cc7f-131">WindowsBase</span></span>  
  
4.  <span data-ttu-id="5cc7f-132">Dodaj odwołanie do `HostingWpfUserControlInWf` projektu.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-132">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>  
  
5.  <span data-ttu-id="5cc7f-133">W Eksploratorze rozwiązań, ustaw `WpfUserControlHost` projekt jako projekt startowy.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-133">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a><span data-ttu-id="5cc7f-134">Hosting kontrolki systemu Windows Presentation Foundation użytkownika</span><span class="sxs-lookup"><span data-stu-id="5cc7f-134">Hosting the Windows Presentation Foundation UserControl</span></span>  
  
#### <a name="to-host-the-usercontrol"></a><span data-ttu-id="5cc7f-135">Na hoście UserControl</span><span class="sxs-lookup"><span data-stu-id="5cc7f-135">To host the UserControl</span></span>  
  
1.  <span data-ttu-id="5cc7f-136">W narzędziu Projektant dla formularzy systemu Windows otwórz Form1.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-136">In the Windows Forms Designer, open Form1.</span></span>  
  
2.  <span data-ttu-id="5cc7f-137">Kliknij w oknie właściwości **zdarzenia**, a następnie kliknij dwukrotnie <xref:System.Windows.Forms.Form.Load> zdarzeń, aby utworzyć program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-137">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>  
  
     <span data-ttu-id="5cc7f-138">Otwiera edytora kodu do nowo utworzonego `Form1_Load` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-138">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>  
  
3.  <span data-ttu-id="5cc7f-139">Zastąp kod w pliku Form1.cs następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-139">Replace the code in Form1.cs with the following code.</span></span>  
  
     <span data-ttu-id="5cc7f-140">`Form1_Load` Obsługi zdarzeń tworzy wystąpienie `UserControl1` i dodaje je <xref:System.Windows.Forms.Integration.ElementHost> kolekcja formantów podrzędnych formantu.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-140">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="5cc7f-141"><xref:System.Windows.Forms.Integration.ElementHost> Formant został dodany do formularza kolekcja formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-141">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="5cc7f-142">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="5cc7f-142">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc7f-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cc7f-143">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="5cc7f-144">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="5cc7f-144">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="5cc7f-145">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cc7f-145">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="5cc7f-146">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="5cc7f-146">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="5cc7f-147">Hostowanie formantu złożonego WPF w przykładowym formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5cc7f-147">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160001)
