---
title: 'Przewodnik: Tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 889e81053d4e2264755468446a4e1681216ae22e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040373"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="8f36b-102">Przewodnik: Utwórz nową zawartość WPF na Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="8f36b-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="8f36b-103">W tym artykule pokazano, jak utworzyć formant Windows Presentation Foundation (WPF) do użycia w aplikacjach opartych na Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8f36b-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

<span data-ttu-id="8f36b-104">W tym instruktażu wykonasz następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="8f36b-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="8f36b-105">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="8f36b-105">Create the project.</span></span>

- <span data-ttu-id="8f36b-106">Utwórz nową kontrolkę WPF.</span><span class="sxs-lookup"><span data-stu-id="8f36b-106">Create a new WPF control.</span></span>

- <span data-ttu-id="8f36b-107">Dodaj nową kontrolkę WPF do formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8f36b-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="8f36b-108">Kontrolka WPF jest hostowana w <xref:System.Windows.Forms.Integration.ElementHost> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="8f36b-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8f36b-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8f36b-109">Prerequisites</span></span>

<span data-ttu-id="8f36b-110">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="8f36b-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="8f36b-111">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8f36b-111">Visual Studio</span></span>

## <a name="create-the-project"></a><span data-ttu-id="8f36b-112">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="8f36b-112">Create the project</span></span>

<span data-ttu-id="8f36b-113">Pierwszym krokiem jest utworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8f36b-113">The first step is to create the Windows Forms project.</span></span> <span data-ttu-id="8f36b-114">Otwórz program Visual Studio i Utwórz nowy projekt **aplikacji Windows Forms (.NET Framework)** w Visual Basic lub wizualizacji `HostingWpf` C# o nazwie.</span><span class="sxs-lookup"><span data-stu-id="8f36b-114">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="8f36b-115">W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8f36b-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="8f36b-116">Utwórz nową kontrolkę WPF</span><span class="sxs-lookup"><span data-stu-id="8f36b-116">Create a new WPF control</span></span>

<span data-ttu-id="8f36b-117">Utworzenie nowej kontrolki WPF i dodanie jej do projektu jest tak proste jak dodanie innego elementu do projektu.</span><span class="sxs-lookup"><span data-stu-id="8f36b-117">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="8f36b-118">Projektant formularzy systemu Windows działa z określonym rodzajem kontrolki o nazwie *formant złożony*lub *kontrolka użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="8f36b-118">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="8f36b-119">Aby uzyskać więcej informacji na temat kontrolek użytkownika <xref:System.Windows.Controls.UserControl>WPF, zobacz.</span><span class="sxs-lookup"><span data-stu-id="8f36b-119">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="8f36b-120">Typ dla WPF jest różny od typu kontrolki użytkownika dostarczonej przez Windows Forms, która jest również nazywana <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8f36b-120">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8f36b-121">Aby utworzyć nową kontrolkę WPF:</span><span class="sxs-lookup"><span data-stu-id="8f36b-121">To create a new WPF control:</span></span>

1. <span data-ttu-id="8f36b-122">W **Eksplorator rozwiązań**Dodaj nowy projekt **biblioteki formantów użytkownika WPF (.NET Framework)** do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8f36b-122">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="8f36b-123">Użyj domyślnej nazwy biblioteki `WpfControlLibrary1`kontrolek.</span><span class="sxs-lookup"><span data-stu-id="8f36b-123">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="8f36b-124">Domyślna nazwa kontrolki to `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="8f36b-124">The default control name is `UserControl1.xaml`.</span></span>

     <span data-ttu-id="8f36b-125">Dodanie nowej kontrolki ma następujące skutki:</span><span class="sxs-lookup"><span data-stu-id="8f36b-125">Adding the new control has the following effects:</span></span>

    - <span data-ttu-id="8f36b-126">Plik UserControl1. XAML został dodany.</span><span class="sxs-lookup"><span data-stu-id="8f36b-126">File UserControl1.xaml is added.</span></span>

    - <span data-ttu-id="8f36b-127">Dodano plik UserControl1.xaml.cs lub UserControl1. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="8f36b-127">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="8f36b-128">Ten plik zawiera kod związany z obsługą zdarzeń oraz inne implementacje.</span><span class="sxs-lookup"><span data-stu-id="8f36b-128">This file contains the code-behind for event handlers and other implementation.</span></span>

    - <span data-ttu-id="8f36b-129">Dodano odwołania do zestawów WPF.</span><span class="sxs-lookup"><span data-stu-id="8f36b-129">References to WPF assemblies are added.</span></span>

    - <span data-ttu-id="8f36b-130">Plik UserControl1. XAML zostanie otwarty w [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f36b-130">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>

2. <span data-ttu-id="8f36b-131">W widok Projekt upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="8f36b-131">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="8f36b-132">Aby uzyskać więcej informacji, zobacz [jak: Wybierz i przenieś elementy na Powierzchnia projektowa](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8f36b-132">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="8f36b-133">W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="8f36b-133">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="8f36b-134">Z **przybornika**przeciągnij <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolkę na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="8f36b-134">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="8f36b-135">W oknie **Właściwości** ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości na **hostowana zawartość**.</span><span class="sxs-lookup"><span data-stu-id="8f36b-135">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8f36b-136">Ogólnie rzecz biorąc, należy hostować bardziej zaawansowaną zawartość WPF.</span><span class="sxs-lookup"><span data-stu-id="8f36b-136">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="8f36b-137"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontrolka jest używana w tym miejscu tylko do celów informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="8f36b-137">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="8f36b-138">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="8f36b-138">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="8f36b-139">Dodawanie formantu WPF do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8f36b-139">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="8f36b-140">Nowa kontrolka WPF jest gotowa do użycia w formularzu.</span><span class="sxs-lookup"><span data-stu-id="8f36b-140">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="8f36b-141">Windows Forms używa <xref:System.Windows.Forms.Integration.ElementHost> kontrolki do hostowania zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="8f36b-141">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="8f36b-142">Aby dodać formant WPF do formularza systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="8f36b-142">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="8f36b-143">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8f36b-143">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="8f36b-144">W przyborniku Znajdź kartę z **WPFUserControlLibraryą formantów użytkownika WPF**.</span><span class="sxs-lookup"><span data-stu-id="8f36b-144">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="8f36b-145">Przeciągnij wystąpienie do `UserControl1` formularza.</span><span class="sxs-lookup"><span data-stu-id="8f36b-145">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="8f36b-146"><xref:System.Windows.Forms.Integration.ElementHost> Formant jest automatycznie tworzony w formularzu, aby hostować formant WPF.</span><span class="sxs-lookup"><span data-stu-id="8f36b-146">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="8f36b-147">`elementHost1` <xref:System.Windows.Forms.Integration.ElementHost.Child%2A>Kontrolka ma nazwę i w oknie właściwości można zobaczyć, że jej właściwość jest ustawiona na UserControl1. <xref:System.Windows.Forms.Integration.ElementHost></span><span class="sxs-lookup"><span data-stu-id="8f36b-147">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="8f36b-148">Odwołania do zestawów WPF są dodawane do projektu.</span><span class="sxs-lookup"><span data-stu-id="8f36b-148">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="8f36b-149">`elementHost1` Kontrolka zawiera Panel tagów inteligentnych, który zawiera dostępne opcje hostingu.</span><span class="sxs-lookup"><span data-stu-id="8f36b-149">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="8f36b-150">W panelu Tagi inteligentne **ElementHost zadania** wybierz pozycję Zadokuj **w kontenerze nadrzędnym**.</span><span class="sxs-lookup"><span data-stu-id="8f36b-150">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="8f36b-151">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8f36b-151">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8f36b-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8f36b-152">Next steps</span></span>

<span data-ttu-id="8f36b-153">Windows Forms i WPF są różnymi technologiami, ale są one tak zaprojektowane, aby ściśle współpracować.</span><span class="sxs-lookup"><span data-stu-id="8f36b-153">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="8f36b-154">Aby zapewnić bogatszy wygląd i zachowanie aplikacji, spróbuj wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8f36b-154">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="8f36b-155">Hostowanie kontrolki Windows Forms na stronie WPF.</span><span class="sxs-lookup"><span data-stu-id="8f36b-155">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="8f36b-156">Aby uzyskać więcej informacji, [zobacz Przewodnik: Hostowanie formantu Windows Forms w WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="8f36b-156">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="8f36b-157">Zastosuj Windows Forms style wizualne do zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="8f36b-157">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="8f36b-158">Aby uzyskać więcej informacji, zobacz [jak: Włącz style wizualne w aplikacji](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="8f36b-158">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="8f36b-159">Zmień styl zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="8f36b-159">Change the style of your WPF content.</span></span> <span data-ttu-id="8f36b-160">Aby uzyskać więcej informacji, [zobacz Przewodnik: Style zawartości](walkthrough-styling-wpf-content.md)WPF.</span><span class="sxs-lookup"><span data-stu-id="8f36b-160">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f36b-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f36b-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="8f36b-162">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="8f36b-162">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="8f36b-163">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="8f36b-163">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="8f36b-164">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8f36b-164">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
