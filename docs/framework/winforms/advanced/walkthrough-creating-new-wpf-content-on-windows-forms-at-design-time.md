---
title: 'Wskazówki: tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: dc72b86a69d44ad282e30b000313b73211cad09c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45653279"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="21103-102">Wskazówki: tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="21103-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>

<span data-ttu-id="21103-103">W tym temacie dowiesz się, jak utworzyć formant Windows Presentation Foundation (WPF) do użytku w aplikacjach opartych na formularzach Windows.</span><span class="sxs-lookup"><span data-stu-id="21103-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

<span data-ttu-id="21103-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="21103-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="21103-105">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="21103-105">Create the project.</span></span>

- <span data-ttu-id="21103-106">Utwórz nową kontrolkę WPF.</span><span class="sxs-lookup"><span data-stu-id="21103-106">Create a new WPF control.</span></span>

- <span data-ttu-id="21103-107">Dodawanie nowej kontrolki WPF do formularza Windows.</span><span class="sxs-lookup"><span data-stu-id="21103-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="21103-108">Kontrolki WPF znajduje się w <xref:System.Windows.Forms.Integration.ElementHost> kontroli.</span><span class="sxs-lookup"><span data-stu-id="21103-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21103-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="21103-109">Prerequisites</span></span>

<span data-ttu-id="21103-110">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="21103-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="21103-111">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="21103-111">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="21103-112">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="21103-112">Creating the Project</span></span>

<span data-ttu-id="21103-113">Pierwszym krokiem jest utworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="21103-113">The first step is to create the Windows Forms project.</span></span> <span data-ttu-id="21103-114">Otwórz program Visual Studio i Utwórz nowy **aplikacji programu Windows Forms (.NET Framework)** projektu w języku Visual Basic lub Visual C# o nazwie `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="21103-114">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="21103-115">Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="21103-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="21103-116">Utworzenie nowej kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="21103-116">Creating a New WPF Control</span></span>

<span data-ttu-id="21103-117">Utworzenie nowej kontrolki WPF, a następnie dodanie go do projektu jest bardzo proste — wystarczy dodanie innych elementów do projektu.</span><span class="sxs-lookup"><span data-stu-id="21103-117">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="21103-118">Windows Forms Designer współpracuje z określonego rodzaju formantu o nazwie *złożonej kontrolki*, lub *kontrolki użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="21103-118">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="21103-119">Aby uzyskać więcej informacji dotyczących kontrolek użytkownika WPF, zobacz <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="21103-119">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="21103-120"><xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> Wpisz WPF różni się od typu formantu użytkownika, dostarczone przez Windows Forms, który jest również określany <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21103-120">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="21103-121">Aby utworzyć nowe kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="21103-121">To create a new WPF control</span></span>

1. <span data-ttu-id="21103-122">W **Eksploratora rozwiązań**, Dodaj nowy **Biblioteka kontrolek użytkownika WPF (.NET Framework)** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="21103-122">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="21103-123">Użyj domyślnej nazwy dla Biblioteka kontrolek `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="21103-123">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="21103-124">Domyślną nazwą formantu jest `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="21103-124">The default control name is `UserControl1.xaml`.</span></span>

     <span data-ttu-id="21103-125">Dodawanie nowej kontrolki ma następujące skutki:</span><span class="sxs-lookup"><span data-stu-id="21103-125">Adding the new control has the following effects:</span></span>

    - <span data-ttu-id="21103-126">UserControl1.xaml plik zostanie dodany.</span><span class="sxs-lookup"><span data-stu-id="21103-126">File UserControl1.xaml is added.</span></span>

    - <span data-ttu-id="21103-127">Plik UserControl1.xaml.cs lub UserControl1.xaml.vb są dodawane.</span><span class="sxs-lookup"><span data-stu-id="21103-127">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="21103-128">Ten plik zawiera kodem procedury obsługi zdarzeń i innych implementacji.</span><span class="sxs-lookup"><span data-stu-id="21103-128">This file contains the code-behind for event handlers and other implementation.</span></span>

    - <span data-ttu-id="21103-129">Dodaje odwołania do zestawów WPF.</span><span class="sxs-lookup"><span data-stu-id="21103-129">References to WPF assemblies are added.</span></span>

    - <span data-ttu-id="21103-130">UserControl1.xaml plik zostanie otwarty w [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="21103-130">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>

2. <span data-ttu-id="21103-131">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="21103-131">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="21103-132">Aby uzyskać więcej informacji, zobacz [jak: Select i Przesuń elementy na powierzchni projektowej](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="21103-132">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>

3. <span data-ttu-id="21103-133">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości **200**.</span><span class="sxs-lookup"><span data-stu-id="21103-133">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="21103-134">Z **przybornika**, przeciągnij <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolki na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="21103-134">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="21103-135">W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanej zawartości**.</span><span class="sxs-lookup"><span data-stu-id="21103-135">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="21103-136">Ogólnie rzecz biorąc należy obsługiwać bardziej złożone zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="21103-136">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="21103-137"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontroli jest tu używany wyłącznie w celach opisowy.</span><span class="sxs-lookup"><span data-stu-id="21103-137">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="21103-138">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="21103-138">Build the project.</span></span>

## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="21103-139">Dodawanie kontrolki WPF do postaci Windows</span><span class="sxs-lookup"><span data-stu-id="21103-139">Adding a WPF Control to a Windows Form</span></span>

<span data-ttu-id="21103-140">Nowe kontrolki WPF jest gotowy do użycia w formularzu.</span><span class="sxs-lookup"><span data-stu-id="21103-140">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="21103-141">Formularze Windows używa <xref:System.Windows.Forms.Integration.ElementHost> kontrolki hosta zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="21103-141">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="21103-142">Aby dodać kontrolki WPF do postaci Windows</span><span class="sxs-lookup"><span data-stu-id="21103-142">To add a WPF control to a Windows Form</span></span>

1. <span data-ttu-id="21103-143">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="21103-143">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="21103-144">W **przybornika**, Znajdź kartę **kontrolek użytkownika WPF WPFUserControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="21103-144">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="21103-145">Przeciągnij wystąpienie `UserControl1` na formularz.</span><span class="sxs-lookup"><span data-stu-id="21103-145">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="21103-146"><xref:System.Windows.Forms.Integration.ElementHost> Kontrolki jest tworzona automatycznie na formularzu do hostowania kontrolki WPF.</span><span class="sxs-lookup"><span data-stu-id="21103-146">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="21103-147"><xref:System.Windows.Forms.Integration.ElementHost> Nosi nazwę kontrolki `elementHost1` i **właściwości** okna, możesz zobaczyć jego <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="21103-147">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="21103-148">Odwołania do zestawów WPF są dodawane do projektu.</span><span class="sxs-lookup"><span data-stu-id="21103-148">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="21103-149">`elementHost1` Kontrolkę panelu tagu inteligentnego, który przedstawia dostępne opcje hostingu.</span><span class="sxs-lookup"><span data-stu-id="21103-149">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="21103-150">W **zadania ElementHost** panelu tagi inteligentne, wybierz opcję **Zadokuj w kontenerze nadrzędnym**.</span><span class="sxs-lookup"><span data-stu-id="21103-150">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="21103-151">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="21103-151">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="21103-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="21103-152">Next Steps</span></span>

<span data-ttu-id="21103-153">Windows Forms i WPF są różne technologie, ale są one przeznaczone do ściśle współpracować.</span><span class="sxs-lookup"><span data-stu-id="21103-153">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="21103-154">Aby zapewnić bardziej rozbudowane wygląd i zachowanie w swoich aplikacjach, spróbuj wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="21103-154">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="21103-155">Hostowanie kontrolki Windows Forms na stronie programu WPF.</span><span class="sxs-lookup"><span data-stu-id="21103-155">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="21103-156">Aby uzyskać więcej informacji, zobacz [wskazówki: Hosting formantu Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="21103-156">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="21103-157">Stosowanie stylów wizualnych Windows Forms do zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="21103-157">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="21103-158">Aby uzyskać więcej informacji, zobacz [porady: Włączanie stylów wizualnych w aplikacji hybrydowej](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="21103-158">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="21103-159">Zmiana stylu zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="21103-159">Change the style of your WPF content.</span></span> <span data-ttu-id="21103-160">Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie stylów zawartości WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="21103-160">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21103-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21103-161">See Also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="21103-162">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="21103-162">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="21103-163">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="21103-163">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [<span data-ttu-id="21103-164">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="21103-164">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
