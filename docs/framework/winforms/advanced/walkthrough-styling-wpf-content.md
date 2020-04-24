---
title: 'Instruktaż: Styl zawartości WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07241d41e3fbf270a76bd241765bfa369ee265d5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646331"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="b2140-102">Instruktaż: Styl zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="b2140-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="b2140-103">W tym artykule pokazano, jak zastosować styl do formantu Windows Presentation Foundation (WPF) hostowanego w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b2140-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2140-104">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b2140-104">Prerequisites</span></span>

<span data-ttu-id="b2140-105">Program Visual Studio musi ukończyć ten instruktaż.</span><span class="sxs-lookup"><span data-stu-id="b2140-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="b2140-106">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="b2140-106">Create the project</span></span>

<span data-ttu-id="b2140-107">Otwórz program Visual Studio i utwórz nowy projekt aplikacji `StylingWpfContent`formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie .</span><span class="sxs-lookup"><span data-stu-id="b2140-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="b2140-108">Podczas hostowania zawartości WPF obsługiwane są tylko projekty języka C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b2140-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="b2140-109">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="b2140-109">Create the WPF control types</span></span>

<span data-ttu-id="b2140-110">Po dodaniu typu formantu WPF do projektu, <xref:System.Windows.Forms.Integration.ElementHost> można hostować go w formancie.</span><span class="sxs-lookup"><span data-stu-id="b2140-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="b2140-111">Dodaj nowy projekt <xref:System.Windows.Controls.UserControl> WPF do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b2140-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="b2140-112">Użyj domyślnej nazwy typu `UserControl1.xaml`formantu, .</span><span class="sxs-lookup"><span data-stu-id="b2140-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="b2140-113">Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF w formularzach systemu Windows w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="b2140-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="b2140-114">W widoku Projekt upewnij `UserControl1` się, że jest zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="b2140-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="b2140-115">W oknie **Właściwości** ustaw wartość i <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> właściwości na **200**.</span><span class="sxs-lookup"><span data-stu-id="b2140-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="b2140-116">Dodaj <xref:System.Windows.Controls.Button?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> do i ustaw <xref:System.Windows.Controls.ContentControl.Content%2A> wartość właściwości **anuluj**.</span><span class="sxs-lookup"><span data-stu-id="b2140-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="b2140-117">Dodaj drugi <xref:System.Windows.Controls.Button?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> do i ustaw <xref:System.Windows.Controls.ContentControl.Content%2A> wartość właściwości na **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2140-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="b2140-118">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="b2140-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="b2140-119">Stosowanie stylu do formantu WPF</span><span class="sxs-lookup"><span data-stu-id="b2140-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="b2140-120">Można zastosować różne stylizacje do formantu WPF, aby zmienić jego wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="b2140-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="b2140-121">Otwórz `Form1` w Projektancie formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b2140-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="b2140-122">W **przyborniku**kliknij `UserControl1` dwukrotnie, aby `UserControl1` utworzyć wystąpienie w formularzu.</span><span class="sxs-lookup"><span data-stu-id="b2140-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="b2140-123">Wystąpienie `UserControl1` jest hostowane w <xref:System.Windows.Forms.Integration.ElementHost> nowym `elementHost1`formancie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="b2140-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="b2140-124">W panelu `elementHost1`tagów inteligentnych kliknij pozycję **Edytuj zawartość hostowana** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="b2140-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="b2140-125">`UserControl1`otwiera się w Projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="b2140-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="b2140-126">W widoku XAML wstaw następujący kod `<UserControl>` XAML po znaczniku otwierającym.</span><span class="sxs-lookup"><span data-stu-id="b2140-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="b2140-127">Ten kod XAML tworzy gradient z kontrastującymi obramowaniem gradientu.</span><span class="sxs-lookup"><span data-stu-id="b2140-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="b2140-128">Po kliknięciu formantu gradienty są zmieniane w celu wygenerowania wyglądu naciśnięty przycisk.</span><span class="sxs-lookup"><span data-stu-id="b2140-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="b2140-129">Aby uzyskać więcej informacji, zobacz [Stylowanie i tworzenie szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b2140-129">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

1. <span data-ttu-id="b2140-130">Zastosuj `SimpleButton` styl zdefiniowany w poprzednim kroku do przycisku Anuluj, `<Button>` wstawiając następujący kod XAML w tagu przycisku **Anuluj.**</span><span class="sxs-lookup"><span data-stu-id="b2140-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="b2140-131">Deklaracja przycisków będzie przypominać następujący kod XAML:</span><span class="sxs-lookup"><span data-stu-id="b2140-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="b2140-132">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="b2140-132">Build the project.</span></span>

1. <span data-ttu-id="b2140-133">Otwórz `Form1` w Projektancie formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b2140-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="b2140-134">Nowy styl jest stosowany do formantu przycisku.</span><span class="sxs-lookup"><span data-stu-id="b2140-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="b2140-135">Z menu **Debugowanie** wybierz polecenie **Rozpocznij debugowanie,** aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b2140-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="b2140-136">Kliknij przyciski **OK** i **Anuluj** i wyświetl różnice.</span><span class="sxs-lookup"><span data-stu-id="b2140-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2140-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2140-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="b2140-138">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="b2140-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="b2140-139">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="b2140-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="b2140-140">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2140-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="b2140-141">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="b2140-141">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="b2140-142">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="b2140-142">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
