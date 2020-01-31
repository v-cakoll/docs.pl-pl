---
title: Kontrolka złożona dla hosta 3W WPF w Windows Forms
titleSuffix: ''
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: aaa726ac90fd75a12054c18be6ec08a1372c1128
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794207"
---
# <a name="walkthrough-host-a-3d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="48579-102">Przewodnik: hostowanie złożonego formantu 3D WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="48579-102">Walkthrough: Host a 3D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="48579-103">W tym instruktażu pokazano, jak można utworzyć formant złożony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i hostować go w Windows Forms kontrolkach i formularzach za pomocą kontrolki <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="48579-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in Windows Forms controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="48579-104">W tym instruktażu zaimplementowano <xref:System.Windows.Controls.UserControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], który zawiera dwie kontrolki podrzędne.</span><span class="sxs-lookup"><span data-stu-id="48579-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="48579-105"><xref:System.Windows.Controls.UserControl> wyświetla stożkowy wymiar trójwymiarowy (3W).</span><span class="sxs-lookup"><span data-stu-id="48579-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3D) cone.</span></span> <span data-ttu-id="48579-106">Renderowanie obiektów 3W jest znacznie łatwiejsze dzięki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niż z Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="48579-106">Rendering 3D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with Windows Forms.</span></span> <span data-ttu-id="48579-107">W związku z tym warto hostować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasę <xref:System.Windows.Controls.UserControl> w celu utworzenia grafiki 3D w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="48579-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3D graphics in Windows Forms.</span></span>

<span data-ttu-id="48579-108">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="48579-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="48579-109">Tworzenie <xref:System.Windows.Controls.UserControl>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48579-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

- <span data-ttu-id="48579-110">Tworzenie projektu hosta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="48579-110">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="48579-111">Hostowanie <xref:System.Windows.Controls.UserControl>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48579-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48579-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="48579-112">Prerequisites</span></span>

<span data-ttu-id="48579-113">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="48579-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="48579-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="48579-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="48579-115">Tworzenie obiektu UserControl</span><span class="sxs-lookup"><span data-stu-id="48579-115">Create the UserControl</span></span>

1. <span data-ttu-id="48579-116">Utwórz projekt **biblioteki formantów użytkownika WPF** o nazwie `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="48579-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="48579-117">Otwórz UserControl1. XAML w projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="48579-117">Open UserControl1.xaml in the WPF Designer.</span></span>

3. <span data-ttu-id="48579-118">Zastąp wygenerowany kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="48579-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="48579-119">Ten kod definiuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>, który zawiera dwa kontrolki podrzędne.</span><span class="sxs-lookup"><span data-stu-id="48579-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="48579-120">Pierwszy formant podrzędny jest formantem <xref:System.Windows.Controls.Label?displayProperty=nameWithType>; drugim jest formant <xref:System.Windows.Controls.Viewport3D>, który wyświetla stożkowy 3W.</span><span class="sxs-lookup"><span data-stu-id="48579-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="48579-121">Utwórz projekt hosta</span><span class="sxs-lookup"><span data-stu-id="48579-121">Create the host project</span></span>

1. <span data-ttu-id="48579-122">Dodaj projekt **aplikacji Windows Forms (.NET Framework)** o nazwie `WpfUserControlHost` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="48579-122">Add a **Windows Forms App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span>

2. <span data-ttu-id="48579-123">W **Eksplorator rozwiązań**Dodaj odwołanie do zestawu WindowsFormsIntegration o nazwie WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="48579-123">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="48579-124">Dodaj odwołania do następujących zestawów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="48579-124">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    - <span data-ttu-id="48579-125">'Presentationcore</span><span class="sxs-lookup"><span data-stu-id="48579-125">PresentationCore</span></span>

    - <span data-ttu-id="48579-126">Platformie docelowej</span><span class="sxs-lookup"><span data-stu-id="48579-126">PresentationFramework</span></span>

    - <span data-ttu-id="48579-127">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="48579-127">WindowsBase</span></span>

4. <span data-ttu-id="48579-128">Dodaj odwołanie do projektu `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="48579-128">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="48579-129">W Eksplorator rozwiązań Ustaw projekt `WpfUserControlHost` jako projekt startowy.</span><span class="sxs-lookup"><span data-stu-id="48579-129">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="48579-130">Hostowanie elementu UserControl</span><span class="sxs-lookup"><span data-stu-id="48579-130">Host the UserControl</span></span>

1. <span data-ttu-id="48579-131">W Projektant formularzy systemu Windows otwórz formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="48579-131">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="48579-132">W okno Właściwości kliknij pozycję **zdarzenia**, a następnie kliknij dwukrotnie zdarzenie <xref:System.Windows.Forms.Form.Load>, aby utworzyć procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="48579-132">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="48579-133">Zostanie otwarty Edytor kodu dla nowo wygenerowanego programu obsługi zdarzeń `Form1_Load`.</span><span class="sxs-lookup"><span data-stu-id="48579-133">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="48579-134">Zastąp kod w Form1.cs następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="48579-134">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="48579-135">Program obsługi zdarzeń `Form1_Load` tworzy wystąpienie `UserControl1` i dodaje je kontrolki podrzędnej formantu <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="48579-135">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="48579-136">Kontrolka <xref:System.Windows.Forms.Integration.ElementHost> jest dodawana do kolekcji formantów podrzędnych formularza.</span><span class="sxs-lookup"><span data-stu-id="48579-136">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="48579-137">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="48579-137">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="48579-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48579-138">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="48579-139">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="48579-139">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="48579-140">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="48579-140">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="48579-141">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="48579-141">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="48579-142">Hostowanie złożonego formantu WPF w Windows Forms przykładzie</span><span class="sxs-lookup"><span data-stu-id="48579-142">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)
