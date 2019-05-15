---
title: 'Przewodnik: Nadawanie stylu zawartości WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: b689bb7299d541708db7ae786bff62a1007608e5
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557890"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="82c80-102">Przewodnik: Stylu zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="82c80-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="82c80-103">W tym instruktażu pokazano, jak stosowanie stylów do formantu Windows Presentation Foundation (WPF) hostowanych w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="82c80-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="82c80-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="82c80-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="82c80-105">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="82c80-105">Create the project.</span></span>

- <span data-ttu-id="82c80-106">Utwórz typ formantu WPF.</span><span class="sxs-lookup"><span data-stu-id="82c80-106">Create the WPF control type.</span></span>

- <span data-ttu-id="82c80-107">Zastosuj styl do WPF control.a</span><span class="sxs-lookup"><span data-stu-id="82c80-107">Apply a style to the WPF control.a</span></span>

## <a name="prerequisites"></a><span data-ttu-id="82c80-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="82c80-108">Prerequisites</span></span>

<span data-ttu-id="82c80-109">Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="82c80-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="82c80-110">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="82c80-110">Create the project</span></span>

<span data-ttu-id="82c80-111">Otwórz program Visual Studio i Utwórz nowy projekt Windows Forms aplikacji w Visual Basic lub Visual C# o nazwie `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="82c80-111">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="82c80-112">Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82c80-112">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="82c80-113">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="82c80-113">Create the WPF control types</span></span>

<span data-ttu-id="82c80-114">Po dodaniu typu formantu WPF do projektu, można umieścić go w <xref:System.Windows.Forms.Integration.ElementHost> kontroli.</span><span class="sxs-lookup"><span data-stu-id="82c80-114">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="82c80-115">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="82c80-115">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="82c80-116">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="82c80-116">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="82c80-117">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="82c80-117">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="82c80-118">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="82c80-118">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="82c80-119">Aby uzyskać więcej informacji, zobacz [jak: Wybierz i Przesuń elementy na powierzchni projektowej](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="82c80-119">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="82c80-120">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="82c80-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="82c80-121">Dodaj <xref:System.Windows.Controls.Button?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **anulować**.</span><span class="sxs-lookup"><span data-stu-id="82c80-121">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="82c80-122">Dodaj drugą <xref:System.Windows.Controls.Button?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **OK**.</span><span class="sxs-lookup"><span data-stu-id="82c80-122">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="82c80-123">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="82c80-123">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="82c80-124">Zastosuj styl do kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="82c80-124">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="82c80-125">Można stosować różne style do formantu WPF, aby zmienić wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="82c80-125">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="82c80-126">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="82c80-126">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="82c80-127">W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="82c80-127">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="82c80-128">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="82c80-128">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="82c80-129">W panelu tagi inteligentne dla `elementHost1`, kliknij przycisk **Edytuj hostowana zawartość** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="82c80-129">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

     <span data-ttu-id="82c80-130">`UserControl1` zostanie otwarty w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82c80-130">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

1. <span data-ttu-id="82c80-131">W widoku XAML, Wstaw następujące XAML po `<UserControl>` tagu początkowego.</span><span class="sxs-lookup"><span data-stu-id="82c80-131">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>

     <span data-ttu-id="82c80-132">Ta XAML tworzy gradient kontrastujące obramowaniem gradientu.</span><span class="sxs-lookup"><span data-stu-id="82c80-132">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="82c80-133">Po kliknięciu formantu gradientów zostały zmienione, aby wygenerować się po naciśnięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="82c80-133">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="82c80-134">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="82c80-134">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

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

1. <span data-ttu-id="82c80-135">Zastosuj `SimpleButton` style zdefiniowane w poprzednim kroku, aby przycisk Anuluj, wstawiając następujące XAML w `<Button>` tag przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="82c80-135">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="82c80-136">Twoje zgłoszenie przycisk będzie przypominał następujące XAML:</span><span class="sxs-lookup"><span data-stu-id="82c80-136">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="82c80-137">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="82c80-137">Build the project.</span></span>

1. <span data-ttu-id="82c80-138">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="82c80-138">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="82c80-139">Nowy styl jest stosowany do kontrolki przycisku.</span><span class="sxs-lookup"><span data-stu-id="82c80-139">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="82c80-140">Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82c80-140">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="82c80-141">Kliknij przycisk OK lub Anuluj i wyświetlać różnice.</span><span class="sxs-lookup"><span data-stu-id="82c80-141">Click the OK and Cancel buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="82c80-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82c80-142">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="82c80-143">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="82c80-143">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="82c80-144">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="82c80-144">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="82c80-145">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="82c80-145">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="82c80-146">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="82c80-146">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="82c80-147">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="82c80-147">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
