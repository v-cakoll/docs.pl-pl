---
title: 'Wskazówki: nadawanie stylu zawartości WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 581fcbfdfd7806b8f0f70347ac96f1bf09fa9098
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460947"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="248ea-102">Przewodnik: zawartość w stylu WPF</span><span class="sxs-lookup"><span data-stu-id="248ea-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="248ea-103">W tym artykule pokazano, jak zastosować styl do formantu Windows Presentation Foundation (WPF) hostowanego w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="248ea-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="248ea-104">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="248ea-104">Prerequisites</span></span>

<span data-ttu-id="248ea-105">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="248ea-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="248ea-106">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="248ea-106">Create the project</span></span>

<span data-ttu-id="248ea-107">Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub wizualizacji C# o nazwie `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="248ea-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="248ea-108">W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="248ea-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="248ea-109">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="248ea-109">Create the WPF control types</span></span>

<span data-ttu-id="248ea-110">Po dodaniu typu formantu WPF do projektu można hostować go w kontrolce <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="248ea-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="248ea-111">Dodaj nowy projekt WPF <xref:System.Windows.Controls.UserControl> do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="248ea-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="248ea-112">Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="248ea-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="248ea-113">Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="248ea-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="248ea-114">W widok Projekt upewnij się, że wybrano pozycję `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="248ea-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="248ea-115">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="248ea-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="248ea-116">Dodaj kontrolkę <xref:System.Windows.Controls.Button?displayProperty=nameWithType> do <xref:System.Windows.Controls.UserControl> i ustaw wartość właściwości <xref:System.Windows.Controls.ContentControl.Content%2A> na **Anuluj**.</span><span class="sxs-lookup"><span data-stu-id="248ea-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="248ea-117">Dodaj drugą kontrolkę <xref:System.Windows.Controls.Button?displayProperty=nameWithType> do <xref:System.Windows.Controls.UserControl> i ustaw wartość właściwości <xref:System.Windows.Controls.ContentControl.Content%2A> na **OK**.</span><span class="sxs-lookup"><span data-stu-id="248ea-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="248ea-118">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="248ea-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="248ea-119">Zastosuj styl do kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="248ea-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="248ea-120">Możesz zastosować różne style do kontrolki WPF, aby zmienić jej wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="248ea-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="248ea-121">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="248ea-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="248ea-122">W **przyborniku**kliknij dwukrotnie `UserControl1`, aby utworzyć wystąpienie `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="248ea-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="248ea-123">Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="248ea-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="248ea-124">W panelu tagów inteligentnych dla `elementHost1`kliknij pozycję **Edytuj hostowaną zawartość** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="248ea-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="248ea-125">`UserControl1` zostanie otwarty w projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="248ea-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="248ea-126">W widoku XAML Wstaw następujący kod XAML po tagu otwierającym `<UserControl>`.</span><span class="sxs-lookup"><span data-stu-id="248ea-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="248ea-127">Ten kod XAML tworzy gradient z kontrastowym obramowaniem gradientu.</span><span class="sxs-lookup"><span data-stu-id="248ea-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="248ea-128">Gdy formant zostanie kliknięty, gradienty są zmieniane w celu wygenerowania naciśniętego przycisku.</span><span class="sxs-lookup"><span data-stu-id="248ea-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="248ea-129">Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="248ea-129">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

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

1. <span data-ttu-id="248ea-130">Zastosuj styl `SimpleButton` zdefiniowany w poprzednim kroku do przycisku Anuluj, wstawiając Poniższy kod XAML w tagu `<Button>` przycisku **Anuluj** .</span><span class="sxs-lookup"><span data-stu-id="248ea-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="248ea-131">Deklaracja przycisku będzie wyglądać podobnie do następującego kodu XAML:</span><span class="sxs-lookup"><span data-stu-id="248ea-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="248ea-132">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="248ea-132">Build the project.</span></span>

1. <span data-ttu-id="248ea-133">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="248ea-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="248ea-134">Nowy styl zostanie zastosowany do kontrolki Button.</span><span class="sxs-lookup"><span data-stu-id="248ea-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="248ea-135">Z menu **Debuguj** wybierz pozycję **Rozpocznij debugowanie** , aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="248ea-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="248ea-136">Kliknij przycisk **OK** i **Anuluj** , aby wyświetlić różnice.</span><span class="sxs-lookup"><span data-stu-id="248ea-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="248ea-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="248ea-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="248ea-138">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="248ea-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="248ea-139">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="248ea-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="248ea-140">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="248ea-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="248ea-141">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="248ea-141">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="248ea-142">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="248ea-142">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
