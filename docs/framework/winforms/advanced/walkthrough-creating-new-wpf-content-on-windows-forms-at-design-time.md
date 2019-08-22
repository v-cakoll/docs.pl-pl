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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e3fb6e42270cc0a530646b656470ec99fcfc7f1f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666243"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="fc805-102">Przewodnik: Utwórz nową zawartość WPF na Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="fc805-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="fc805-103">W tym artykule pokazano, jak utworzyć formant Windows Presentation Foundation (WPF) do użycia w aplikacjach opartych na Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fc805-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc805-104">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fc805-104">Prerequisites</span></span>

<span data-ttu-id="fc805-105">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fc805-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="fc805-106">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="fc805-106">Create the project</span></span>

<span data-ttu-id="fc805-107">Pierwszym krokiem jest utworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fc805-107">The first step is to create the Windows Forms project.</span></span> <span data-ttu-id="fc805-108">Otwórz program Visual Studio i Utwórz nowy projekt **aplikacji Windows Forms (.NET Framework)** w Visual Basic lub wizualizacji `HostingWpf` C# o nazwie.</span><span class="sxs-lookup"><span data-stu-id="fc805-108">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="fc805-109">W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fc805-109">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="fc805-110">Utwórz nową kontrolkę WPF</span><span class="sxs-lookup"><span data-stu-id="fc805-110">Create a new WPF control</span></span>

<span data-ttu-id="fc805-111">Utworzenie nowej kontrolki WPF i dodanie jej do projektu jest tak proste jak dodanie innego elementu do projektu.</span><span class="sxs-lookup"><span data-stu-id="fc805-111">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="fc805-112">Projektant formularzy systemu Windows działa z określonym rodzajem kontrolki o nazwie *formant złożony*lub *kontrolka użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="fc805-112">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="fc805-113">Aby uzyskać więcej informacji na temat kontrolek użytkownika <xref:System.Windows.Controls.UserControl>WPF, zobacz.</span><span class="sxs-lookup"><span data-stu-id="fc805-113">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="fc805-114">Typ dla WPF jest różny od typu kontrolki użytkownika dostarczonej przez Windows Forms, która jest również nazywana <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fc805-114">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fc805-115">Aby utworzyć nową kontrolkę WPF:</span><span class="sxs-lookup"><span data-stu-id="fc805-115">To create a new WPF control:</span></span>

1. <span data-ttu-id="fc805-116">W **Eksplorator rozwiązań**Dodaj nowy projekt **biblioteki formantów użytkownika WPF (.NET Framework)** do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fc805-116">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="fc805-117">Użyj domyślnej nazwy biblioteki `WpfControlLibrary1`kontrolek.</span><span class="sxs-lookup"><span data-stu-id="fc805-117">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="fc805-118">Domyślna nazwa kontrolki to `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="fc805-118">The default control name is `UserControl1.xaml`.</span></span>

   <span data-ttu-id="fc805-119">Dodanie nowej kontrolki ma następujące skutki:</span><span class="sxs-lookup"><span data-stu-id="fc805-119">Adding the new control has the following effects:</span></span>

   - <span data-ttu-id="fc805-120">Plik UserControl1. XAML został dodany.</span><span class="sxs-lookup"><span data-stu-id="fc805-120">File UserControl1.xaml is added.</span></span>

   - <span data-ttu-id="fc805-121">Dodano plik UserControl1.xaml.cs (lub UserControl1. XAML. vb).</span><span class="sxs-lookup"><span data-stu-id="fc805-121">File UserControl1.xaml.cs (or UserControl1.xaml.vb) is added.</span></span> <span data-ttu-id="fc805-122">Ten plik zawiera kod związany z obsługą zdarzeń oraz inne implementacje.</span><span class="sxs-lookup"><span data-stu-id="fc805-122">This file contains the code-behind for event handlers and other implementation.</span></span>

   - <span data-ttu-id="fc805-123">Dodano odwołania do zestawów WPF.</span><span class="sxs-lookup"><span data-stu-id="fc805-123">References to WPF assemblies are added.</span></span>

   - <span data-ttu-id="fc805-124">Plik UserControl1. XAML zostanie otwarty w projektancie WPF dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fc805-124">File UserControl1.xaml opens in the WPF Designer for Visual Studio.</span></span>

2. <span data-ttu-id="fc805-125">W widok Projekt upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="fc805-125">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="fc805-126">W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="fc805-126">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="fc805-127">Z **przybornika**przeciągnij <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolkę na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="fc805-127">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="fc805-128">W oknie **Właściwości** ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości na **hostowana zawartość**.</span><span class="sxs-lookup"><span data-stu-id="fc805-128">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="fc805-129">Ogólnie rzecz biorąc, należy hostować bardziej zaawansowaną zawartość WPF.</span><span class="sxs-lookup"><span data-stu-id="fc805-129">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="fc805-130"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontrolka jest używana w tym miejscu tylko do celów informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="fc805-130">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="fc805-131">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="fc805-131">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="fc805-132">Dodawanie formantu WPF do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fc805-132">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="fc805-133">Nowa kontrolka WPF jest gotowa do użycia w formularzu.</span><span class="sxs-lookup"><span data-stu-id="fc805-133">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="fc805-134">Windows Forms używa <xref:System.Windows.Forms.Integration.ElementHost> kontrolki do hostowania zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="fc805-134">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="fc805-135">Aby dodać formant WPF do formularza systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="fc805-135">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="fc805-136">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fc805-136">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="fc805-137">W przyborniku Znajdź kartę z **WPFUserControlLibraryą formantów użytkownika WPF**.</span><span class="sxs-lookup"><span data-stu-id="fc805-137">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="fc805-138">Przeciągnij wystąpienie do `UserControl1` formularza.</span><span class="sxs-lookup"><span data-stu-id="fc805-138">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="fc805-139"><xref:System.Windows.Forms.Integration.ElementHost> Formant jest automatycznie tworzony w formularzu, aby hostować formant WPF.</span><span class="sxs-lookup"><span data-stu-id="fc805-139">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="fc805-140">`elementHost1` <xref:System.Windows.Forms.Integration.ElementHost.Child%2A>Kontrolka ma nazwę i w oknie właściwości można zobaczyć, że jej właściwość jest ustawiona na UserControl1. <xref:System.Windows.Forms.Integration.ElementHost></span><span class="sxs-lookup"><span data-stu-id="fc805-140">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="fc805-141">Odwołania do zestawów WPF są dodawane do projektu.</span><span class="sxs-lookup"><span data-stu-id="fc805-141">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="fc805-142">`elementHost1` Kontrolka zawiera Panel tagów inteligentnych, który zawiera dostępne opcje hostingu.</span><span class="sxs-lookup"><span data-stu-id="fc805-142">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="fc805-143">W panelu Tagi inteligentne **ElementHost zadania** wybierz pozycję Zadokuj **w kontenerze nadrzędnym**.</span><span class="sxs-lookup"><span data-stu-id="fc805-143">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="fc805-144">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fc805-144">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fc805-145">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fc805-145">Next steps</span></span>

<span data-ttu-id="fc805-146">Windows Forms i WPF są różnymi technologiami, ale są one tak zaprojektowane, aby ściśle współpracować.</span><span class="sxs-lookup"><span data-stu-id="fc805-146">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="fc805-147">Aby zapewnić bogatszy wygląd i zachowanie aplikacji, spróbuj wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fc805-147">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="fc805-148">Hostowanie kontrolki Windows Forms na stronie WPF.</span><span class="sxs-lookup"><span data-stu-id="fc805-148">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="fc805-149">Aby uzyskać więcej informacji, [zobacz Przewodnik: Hostowanie formantu Windows Forms w WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="fc805-149">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="fc805-150">Zastosuj Windows Forms style wizualne do zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="fc805-150">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="fc805-151">Aby uzyskać więcej informacji, zobacz [jak: Włącz style wizualne w aplikacji](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="fc805-151">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="fc805-152">Zmień styl zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="fc805-152">Change the style of your WPF content.</span></span> <span data-ttu-id="fc805-153">Aby uzyskać więcej informacji, [zobacz Przewodnik: Style zawartości](walkthrough-styling-wpf-content.md)WPF.</span><span class="sxs-lookup"><span data-stu-id="fc805-153">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc805-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc805-154">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="fc805-155">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="fc805-155">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="fc805-156">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="fc805-156">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="fc805-157">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc805-157">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
