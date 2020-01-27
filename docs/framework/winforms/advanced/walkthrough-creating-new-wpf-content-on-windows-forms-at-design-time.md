---
title: Utwórz nową zawartość WPF na Windows Forms
titleSuffix: ''
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 69a0598b05d1b2bff84b203317d6d5a166ce109d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746389"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="88ce8-102">Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="88ce8-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="88ce8-103">W tym artykule pokazano, jak utworzyć formant Windows Presentation Foundation (WPF) do użycia w aplikacjach opartych na Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="88ce8-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88ce8-104">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="88ce8-104">Prerequisites</span></span>

<span data-ttu-id="88ce8-105">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88ce8-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="88ce8-106">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="88ce8-106">Create the project</span></span>

<span data-ttu-id="88ce8-107">Otwórz program Visual Studio i Utwórz nowy projekt **aplikacji Windows Forms (.NET Framework)** w Visual Basic lub wizualizacji C# o nazwie `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="88ce8-107">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="88ce8-108">W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="88ce8-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="88ce8-109">Utwórz nową kontrolkę WPF</span><span class="sxs-lookup"><span data-stu-id="88ce8-109">Create a new WPF control</span></span>

<span data-ttu-id="88ce8-110">Utworzenie nowej kontrolki WPF i dodanie jej do projektu jest tak proste jak dodanie innego elementu do projektu.</span><span class="sxs-lookup"><span data-stu-id="88ce8-110">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="88ce8-111">Projektant formularzy systemu Windows działa z określonym rodzajem kontrolki o nazwie *formant złożony*lub *kontrolka użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="88ce8-111">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="88ce8-112">Aby uzyskać więcej informacji na temat kontrolek użytkownika WPF, zobacz <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="88ce8-112">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="88ce8-113">Typ <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> dla WPF jest różny od typu kontrolki użytkownika dostarczonej przez Windows Forms, która jest również nazywana <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="88ce8-113">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="88ce8-114">Aby utworzyć nową kontrolkę WPF:</span><span class="sxs-lookup"><span data-stu-id="88ce8-114">To create a new WPF control:</span></span>

1. <span data-ttu-id="88ce8-115">W **Eksplorator rozwiązań**Dodaj nowy projekt **biblioteki formantów użytkownika WPF (.NET Framework)** do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="88ce8-115">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="88ce8-116">Użyj domyślnej nazwy biblioteki formantów `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="88ce8-116">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="88ce8-117">Domyślna nazwa kontrolki to `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="88ce8-117">The default control name is `UserControl1.xaml`.</span></span>

   <span data-ttu-id="88ce8-118">Dodanie nowej kontrolki ma następujące skutki:</span><span class="sxs-lookup"><span data-stu-id="88ce8-118">Adding the new control has the following effects:</span></span>

   - <span data-ttu-id="88ce8-119">Plik UserControl1. XAML został dodany.</span><span class="sxs-lookup"><span data-stu-id="88ce8-119">File UserControl1.xaml is added.</span></span>

   - <span data-ttu-id="88ce8-120">Dodano plik UserControl1.xaml.cs (lub UserControl1. XAML. vb).</span><span class="sxs-lookup"><span data-stu-id="88ce8-120">File UserControl1.xaml.cs (or UserControl1.xaml.vb) is added.</span></span> <span data-ttu-id="88ce8-121">Ten plik zawiera kod związany z obsługą zdarzeń oraz inne implementacje.</span><span class="sxs-lookup"><span data-stu-id="88ce8-121">This file contains the code-behind for event handlers and other implementation.</span></span>

   - <span data-ttu-id="88ce8-122">Dodano odwołania do zestawów WPF.</span><span class="sxs-lookup"><span data-stu-id="88ce8-122">References to WPF assemblies are added.</span></span>

   - <span data-ttu-id="88ce8-123">Plik UserControl1. XAML zostanie otwarty w projektancie WPF dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88ce8-123">File UserControl1.xaml opens in the WPF Designer for Visual Studio.</span></span>

2. <span data-ttu-id="88ce8-124">W widok Projekt upewnij się, że wybrano pozycję `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="88ce8-124">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="88ce8-125">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="88ce8-125">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="88ce8-126">Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="88ce8-126">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="88ce8-127">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Controls.TextBox.Text%2A> na **hostowaną zawartość**.</span><span class="sxs-lookup"><span data-stu-id="88ce8-127">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="88ce8-128">Ogólnie rzecz biorąc, należy hostować bardziej zaawansowaną zawartość WPF.</span><span class="sxs-lookup"><span data-stu-id="88ce8-128">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="88ce8-129">Kontrolka <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> jest używana tutaj tylko do celów informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="88ce8-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="88ce8-130">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="88ce8-130">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="88ce8-131">Dodawanie formantu WPF do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="88ce8-131">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="88ce8-132">Nowa kontrolka WPF jest gotowa do użycia w formularzu.</span><span class="sxs-lookup"><span data-stu-id="88ce8-132">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="88ce8-133">Windows Forms używa kontrolki <xref:System.Windows.Forms.Integration.ElementHost> do hostowania zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="88ce8-133">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="88ce8-134">Aby dodać formant WPF do formularza systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="88ce8-134">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="88ce8-135">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="88ce8-135">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="88ce8-136">W **przyborniku**Znajdź kartę z **WPFUserControlLibraryą formantów użytkownika WPF**.</span><span class="sxs-lookup"><span data-stu-id="88ce8-136">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="88ce8-137">Przeciągnij wystąpienie `UserControl1` na formularz.</span><span class="sxs-lookup"><span data-stu-id="88ce8-137">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="88ce8-138">Formant <xref:System.Windows.Forms.Integration.ElementHost> jest automatycznie tworzony w formularzu, aby hostować formant WPF.</span><span class="sxs-lookup"><span data-stu-id="88ce8-138">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="88ce8-139">Kontrolka <xref:System.Windows.Forms.Integration.ElementHost> ma nazwę `elementHost1` i w oknie **Właściwości** można zobaczyć, że właściwość <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> jest ustawiona na **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="88ce8-139">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="88ce8-140">Odwołania do zestawów WPF są dodawane do projektu.</span><span class="sxs-lookup"><span data-stu-id="88ce8-140">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="88ce8-141">Kontrolka `elementHost1` ma panel tagu inteligentnego, który zawiera dostępne opcje hostingu.</span><span class="sxs-lookup"><span data-stu-id="88ce8-141">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="88ce8-142">W panelu Tagi inteligentne **ElementHost zadania** wybierz pozycję **Zadokuj w kontenerze nadrzędnym**.</span><span class="sxs-lookup"><span data-stu-id="88ce8-142">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="88ce8-143">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="88ce8-143">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="88ce8-144">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="88ce8-144">Next steps</span></span>

<span data-ttu-id="88ce8-145">Windows Forms i WPF są różnymi technologiami, ale są one tak zaprojektowane, aby ściśle współpracować.</span><span class="sxs-lookup"><span data-stu-id="88ce8-145">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="88ce8-146">Aby zapewnić bogatszy wygląd i zachowanie aplikacji, spróbuj wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="88ce8-146">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="88ce8-147">Hostowanie kontrolki Windows Forms na stronie WPF.</span><span class="sxs-lookup"><span data-stu-id="88ce8-147">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="88ce8-148">Aby uzyskać więcej informacji, zobacz [Przewodnik: hosting formantu Windows Forms w WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="88ce8-148">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="88ce8-149">Zastosuj Windows Forms style wizualne do zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="88ce8-149">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="88ce8-150">Aby uzyskać więcej informacji, zobacz [jak: włączyć style wizualne w aplikacji hybrydowej](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="88ce8-150">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="88ce8-151">Zmień styl zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="88ce8-151">Change the style of your WPF content.</span></span> <span data-ttu-id="88ce8-152">Aby uzyskać więcej informacji, zobacz [Przewodnik: style zawartości WPF](walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="88ce8-152">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88ce8-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88ce8-153">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="88ce8-154">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="88ce8-154">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="88ce8-155">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="88ce8-155">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="88ce8-156">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88ce8-156">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
