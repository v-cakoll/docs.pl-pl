---
title: 'Wskazówki: nadawanie stylu zawartości WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: ad98c2da32084122dab529b8cf3a8fe7ef506b99
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489906"
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="7869c-102">Wskazówki: nadawanie stylu zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="7869c-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="7869c-103">W tym instruktażu pokazano, jak stosowanie stylów do formantu Windows Presentation Foundation (WPF) hostowanych w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="7869c-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="7869c-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="7869c-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="7869c-105">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="7869c-105">Create the project.</span></span>  
  
-   <span data-ttu-id="7869c-106">Utwórz typ formantu WPF.</span><span class="sxs-lookup"><span data-stu-id="7869c-106">Create the WPF control type.</span></span>  
  
-   <span data-ttu-id="7869c-107">Zastosuj styl do kontrolki WPF.</span><span class="sxs-lookup"><span data-stu-id="7869c-107">Apply a style to the WPF control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7869c-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="7869c-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7869c-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="7869c-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7869c-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7869c-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7869c-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7869c-111">Prerequisites</span></span>  
 <span data-ttu-id="7869c-112">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="7869c-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="7869c-113">.</span><span class="sxs-lookup"><span data-stu-id="7869c-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="7869c-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="7869c-114">Creating the Project</span></span>  
 <span data-ttu-id="7869c-115">Pierwszym krokiem jest utworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7869c-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7869c-116">Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7869c-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="7869c-117">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="7869c-117">To create the project</span></span>  
  
-   <span data-ttu-id="7869c-118">Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="7869c-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="7869c-119">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="7869c-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="7869c-120">Po dodaniu typu formantu WPF do projektu, można umieścić go w <xref:System.Windows.Forms.Integration.ElementHost> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7869c-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="7869c-121">Aby utworzyć typy kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="7869c-121">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="7869c-122">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7869c-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="7869c-123">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7869c-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="7869c-124">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7869c-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="7869c-125">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="7869c-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="7869c-126">Aby uzyskać więcej informacji, zobacz [jak: Select i Przesuń elementy na powierzchni projektowej](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="7869c-126">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="7869c-127">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="7869c-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="7869c-128">Dodaj <xref:System.Windows.Controls.Button?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **anulować**.</span><span class="sxs-lookup"><span data-stu-id="7869c-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5.  <span data-ttu-id="7869c-129">Dodaj drugą <xref:System.Windows.Controls.Button?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **OK**.</span><span class="sxs-lookup"><span data-stu-id="7869c-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6.  <span data-ttu-id="7869c-130">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="7869c-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="7869c-131">Zastosować styl do kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="7869c-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="7869c-132">Można stosować różne style do formantu WPF, aby zmienić wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="7869c-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="7869c-133">Aby zastosować styl do kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="7869c-133">To apply a style to a WPF control</span></span>  
  
1.  <span data-ttu-id="7869c-134">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="7869c-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="7869c-135">W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7869c-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="7869c-136">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="7869c-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="7869c-137">W panelu tagi inteligentne dla `elementHost1`, kliknij przycisk **Edytuj hostowana zawartość** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="7869c-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="7869c-138">`UserControl1` zostanie otwarty w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7869c-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="7869c-139">W widoku XAML, Wstaw następujące XAML po `<UserControl>` tagu początkowego.</span><span class="sxs-lookup"><span data-stu-id="7869c-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="7869c-140">Ta XAML tworzy gradient kontrastujące obramowaniem gradientu.</span><span class="sxs-lookup"><span data-stu-id="7869c-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="7869c-141">Po kliknięciu formantu gradientów zostały zmienione, aby wygenerować się po naciśnięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="7869c-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="7869c-142">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="7869c-142">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
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
  
1.  <span data-ttu-id="7869c-143">Zastosuj `SimpleButton` style zdefiniowane w poprzednim kroku, aby przycisk Anuluj, wstawiając następujące XAML w `<Button>` tag przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="7869c-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="7869c-144">Twoje zgłoszenie przycisk będzie przypominał następujące XAML.</span><span class="sxs-lookup"><span data-stu-id="7869c-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  <span data-ttu-id="7869c-145">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="7869c-145">Build the project.</span></span>  
  
2.  <span data-ttu-id="7869c-146">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="7869c-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="7869c-147">Nowy styl jest stosowany do kontrolki przycisku.</span><span class="sxs-lookup"><span data-stu-id="7869c-147">The new style is applied to the button control.</span></span>  
  
4.  <span data-ttu-id="7869c-148">Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7869c-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5.  <span data-ttu-id="7869c-149">Kliknij przycisk OK lub Anuluj i wyświetlać różnice.</span><span class="sxs-lookup"><span data-stu-id="7869c-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7869c-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7869c-150">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="7869c-151">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="7869c-151">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="7869c-152">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="7869c-152">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="7869c-153">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7869c-153">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="7869c-154">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="7869c-154">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="7869c-155">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="7869c-155">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
