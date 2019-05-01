---
title: 'Przewodnik: hostowanie kontrolki złożonej 3-D WPF w Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: e5b98a33f29759a81ba1cbc1fefbd45c0e5bf736
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007152"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="f7e4f-102">Przewodnik: hostowanie kontrolki złożonej 3-D WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7e4f-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="f7e4f-103">W tym instruktażu przedstawiono sposób tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego sterowania, a następnie Hostuj go w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów i formularzy przy użyciu <xref:System.Windows.Forms.Integration.ElementHost> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="f7e4f-104">W tym przewodniku zostaną zaimplementowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> zawiera dwie kontrolki podrzędne.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="f7e4f-105"><xref:System.Windows.Controls.UserControl> Wyświetla trójwymiarowej stożek (3-).</span><span class="sxs-lookup"><span data-stu-id="f7e4f-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="f7e4f-106">Renderowanie 3-D obiektów jest o wiele łatwiejsze za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niż przy użyciu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7e4f-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="f7e4f-107">W związku z tym, dobrym pomysłem hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> klasy w celu utworzenia grafiki 3-w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7e4f-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

<span data-ttu-id="f7e4f-108">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="f7e4f-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="f7e4f-109">Tworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

- <span data-ttu-id="f7e4f-110">Tworząc projekt hosta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-110">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="f7e4f-111">Hosting [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7e4f-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f7e4f-112">Prerequisites</span></span>

<span data-ttu-id="f7e4f-113">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="f7e4f-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="f7e4f-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f7e4f-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="f7e4f-115">Utworzyć elementu UserControl</span><span class="sxs-lookup"><span data-stu-id="f7e4f-115">Create the UserControl</span></span>

1. <span data-ttu-id="f7e4f-116">Tworzenie **Biblioteka kontrolek użytkownika WPF** projektu o nazwie `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="f7e4f-117">Otwórz UserControl1.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7e4f-117">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

3. <span data-ttu-id="f7e4f-118">Zastąp wygenerowany kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="f7e4f-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="f7e4f-119">Ten kod definiuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> zawiera dwie kontrolki podrzędne.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="f7e4f-120">Pierwszy formant podrzędny jest <xref:System.Windows.Controls.Label?displayProperty=nameWithType> formantu; druga jest <xref:System.Windows.Controls.Viewport3D> kontrolkę wyświetlającą stożek 3-D.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="f7e4f-121">Utwórz projekt hosta</span><span class="sxs-lookup"><span data-stu-id="f7e4f-121">Create the host project</span></span>

1. <span data-ttu-id="f7e4f-122">Dodaj **aplikacja WPF (.NET Framework)** projektu o nazwie `WpfUserControlHost` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-122">Add a **WPF App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="f7e4f-123">Aby uzyskać więcej informacji, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="f7e4f-123">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="f7e4f-124">W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu WindowsFormsIntegration, która nosi nazwę WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-124">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="f7e4f-125">Dodaj odwołania do następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów:</span><span class="sxs-lookup"><span data-stu-id="f7e4f-125">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    - <span data-ttu-id="f7e4f-126">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="f7e4f-126">PresentationCore</span></span>

    - <span data-ttu-id="f7e4f-127">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="f7e4f-127">PresentationFramework</span></span>

    - <span data-ttu-id="f7e4f-128">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="f7e4f-128">WindowsBase</span></span>

4. <span data-ttu-id="f7e4f-129">Dodaj odwołanie do `HostingWpfUserControlInWf` projektu.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-129">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="f7e4f-130">W Eksploratorze rozwiązań ustaw `WpfUserControlHost` projekt jako projekt startowy.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-130">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="f7e4f-131">Host UserControl</span><span class="sxs-lookup"><span data-stu-id="f7e4f-131">Host the UserControl</span></span>

1. <span data-ttu-id="f7e4f-132">Windows Forms Designer Otwórz formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-132">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="f7e4f-133">W oknie dialogowym właściwości kliknij **zdarzenia**, a następnie kliknij dwukrotnie <xref:System.Windows.Forms.Form.Load> zdarzenie, aby utworzyć program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-133">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="f7e4f-134">Zostanie otwarty Edytor kodu, aby nowo wygenerowane `Form1_Load` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-134">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="f7e4f-135">Zastąp kod w Form1.cs z następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-135">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="f7e4f-136">`Form1_Load` Programu obsługi zdarzeń tworzy wystąpienie `UserControl1` i dodaje itto <xref:System.Windows.Forms.Integration.ElementHost> kontrolki zbiór kontrolek podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-136">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="f7e4f-137"><xref:System.Windows.Forms.Integration.ElementHost> Formant jest dodawany do kolekcji formularza formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-137">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="f7e4f-138">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-138">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7e4f-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7e4f-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f7e4f-140">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f7e4f-140">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="f7e4f-141">Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7e4f-141">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="f7e4f-142">Przewodnik: Hostowanie kontrolki złożonej Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="f7e4f-142">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="f7e4f-143">Hosting złożonego formantu WPF w Windows Forms próbki</span><span class="sxs-lookup"><span data-stu-id="f7e4f-143">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)