---
title: 'Przewodnik: Nadawanie stylu zawartości WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: 887a157494c2992c1ae5868229c442f31fafb276
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781306"
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="761c0-102">Przewodnik: Nadawanie stylu zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="761c0-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="761c0-103">W tym instruktażu pokazano, jak stosowanie stylów do formantu Windows Presentation Foundation (WPF) hostowanych w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="761c0-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="761c0-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="761c0-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="761c0-105">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="761c0-105">Create the project.</span></span>

- <span data-ttu-id="761c0-106">Utwórz typ formantu WPF.</span><span class="sxs-lookup"><span data-stu-id="761c0-106">Create the WPF control type.</span></span>

- <span data-ttu-id="761c0-107">Zastosuj styl do kontrolki WPF.</span><span class="sxs-lookup"><span data-stu-id="761c0-107">Apply a style to the WPF control.</span></span>

> [!NOTE]
>  <span data-ttu-id="761c0-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="761c0-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="761c0-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="761c0-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="761c0-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="761c0-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="761c0-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="761c0-111">Prerequisites</span></span>  
 <span data-ttu-id="761c0-112">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="761c0-112">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="761c0-113">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="761c0-113">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="761c0-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="761c0-114">Creating the Project</span></span>  
 <span data-ttu-id="761c0-115">Pierwszym krokiem jest utworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="761c0-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="761c0-116">Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="761c0-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="761c0-117">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="761c0-117">To create the project</span></span>  
  
- <span data-ttu-id="761c0-118">Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="761c0-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="761c0-119">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="761c0-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="761c0-120">Po dodaniu typu formantu WPF do projektu, można umieścić go w <xref:System.Windows.Forms.Integration.ElementHost> kontroli.</span><span class="sxs-lookup"><span data-stu-id="761c0-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="761c0-121">Aby utworzyć typy kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="761c0-121">To create WPF control types</span></span>  
  
1. <span data-ttu-id="761c0-122">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="761c0-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="761c0-123">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="761c0-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="761c0-124">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="761c0-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2. <span data-ttu-id="761c0-125">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="761c0-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="761c0-126">Aby uzyskać więcej informacji, zobacz [jak: Wybierz i Przesuń elementy na powierzchni projektowej](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="761c0-126">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3. <span data-ttu-id="761c0-127">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="761c0-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4. <span data-ttu-id="761c0-128">Dodaj <xref:System.Windows.Controls.Button?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **anulować**.</span><span class="sxs-lookup"><span data-stu-id="761c0-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5. <span data-ttu-id="761c0-129">Dodaj drugą <xref:System.Windows.Controls.Button?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **OK**.</span><span class="sxs-lookup"><span data-stu-id="761c0-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6. <span data-ttu-id="761c0-130">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="761c0-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="761c0-131">Zastosować styl do kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="761c0-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="761c0-132">Można stosować różne style do formantu WPF, aby zmienić wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="761c0-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="761c0-133">Aby zastosować styl do kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="761c0-133">To apply a style to a WPF control</span></span>  
  
1. <span data-ttu-id="761c0-134">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="761c0-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2. <span data-ttu-id="761c0-135">W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="761c0-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="761c0-136">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="761c0-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3. <span data-ttu-id="761c0-137">W panelu tagi inteligentne dla `elementHost1`, kliknij przycisk **Edytuj hostowana zawartość** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="761c0-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="761c0-138">`UserControl1` zostanie otwarty w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="761c0-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4. <span data-ttu-id="761c0-139">W widoku XAML, Wstaw następujące XAML po `<UserControl>` tagu początkowego.</span><span class="sxs-lookup"><span data-stu-id="761c0-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="761c0-140">Ta XAML tworzy gradient kontrastujące obramowaniem gradientu.</span><span class="sxs-lookup"><span data-stu-id="761c0-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="761c0-141">Po kliknięciu formantu gradientów zostały zmienione, aby wygenerować się po naciśnięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="761c0-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="761c0-142">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="761c0-142">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>  
  
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
  
1. <span data-ttu-id="761c0-143">Zastosuj `SimpleButton` style zdefiniowane w poprzednim kroku, aby przycisk Anuluj, wstawiając następujące XAML w `<Button>` tag przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="761c0-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="761c0-144">Twoje zgłoszenie przycisk będzie przypominał następujące XAML.</span><span class="sxs-lookup"><span data-stu-id="761c0-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1. <span data-ttu-id="761c0-145">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="761c0-145">Build the project.</span></span>  
  
2. <span data-ttu-id="761c0-146">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="761c0-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3. <span data-ttu-id="761c0-147">Nowy styl jest stosowany do kontrolki przycisku.</span><span class="sxs-lookup"><span data-stu-id="761c0-147">The new style is applied to the button control.</span></span>  
  
4. <span data-ttu-id="761c0-148">Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="761c0-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5. <span data-ttu-id="761c0-149">Kliknij przycisk OK lub Anuluj i wyświetlać różnice.</span><span class="sxs-lookup"><span data-stu-id="761c0-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761c0-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="761c0-150">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="761c0-151">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="761c0-151">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="761c0-152">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="761c0-152">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="761c0-153">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="761c0-153">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="761c0-154">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="761c0-154">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="761c0-155">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="761c0-155">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
