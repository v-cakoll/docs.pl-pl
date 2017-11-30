---
title: "Wskazówki: nadawanie stylu zawartości WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ae28df17e17e81814cb8cba8b2630751707f354
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="89f80-102">Wskazówki: nadawanie stylu zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="89f80-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="89f80-103">W tym przewodniku opisano sposób stosowanie stylów do formantu Windows Presentation Foundation (WPF) obsługiwanych na formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="89f80-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="89f80-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="89f80-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="89f80-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="89f80-105">Create the project.</span></span>  
  
-   <span data-ttu-id="89f80-106">Utwórz WPF — typ formantu.</span><span class="sxs-lookup"><span data-stu-id="89f80-106">Create the WPF control type.</span></span>  
  
-   <span data-ttu-id="89f80-107">Zastosuj styl do kontrolki WPF.</span><span class="sxs-lookup"><span data-stu-id="89f80-107">Apply a style to the WPF control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89f80-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="89f80-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="89f80-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="89f80-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="89f80-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="89f80-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="89f80-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="89f80-111">Prerequisites</span></span>  
 <span data-ttu-id="89f80-112">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="89f80-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="89f80-113">.</span><span class="sxs-lookup"><span data-stu-id="89f80-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="89f80-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="89f80-114">Creating the Project</span></span>  
 <span data-ttu-id="89f80-115">Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="89f80-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89f80-116">Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.</span><span class="sxs-lookup"><span data-stu-id="89f80-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="89f80-117">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="89f80-117">To create the project</span></span>  
  
-   <span data-ttu-id="89f80-118">Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="89f80-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="89f80-119">Tworzenie typy formantów WPF</span><span class="sxs-lookup"><span data-stu-id="89f80-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="89f80-120">Po dodaniu typu WPF do projektu, można hostować w <xref:System.Windows.Forms.Integration.ElementHost> formantu.</span><span class="sxs-lookup"><span data-stu-id="89f80-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="89f80-121">Aby utworzyć typy formantów WPF</span><span class="sxs-lookup"><span data-stu-id="89f80-121">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="89f80-122">Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="89f80-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="89f80-123">Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="89f80-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="89f80-124">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="89f80-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="89f80-125">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="89f80-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="89f80-126">Aby uzyskać więcej informacji, zobacz [porady: Wybierz i Przenieś elementy na powierzchnię projektu](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="89f80-126">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="89f80-127">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="89f80-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="89f80-128">Dodaj <xref:System.Windows.Controls.Button?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **anulować**.</span><span class="sxs-lookup"><span data-stu-id="89f80-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5.  <span data-ttu-id="89f80-129">Dodaj drugi <xref:System.Windows.Controls.Button?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **OK**.</span><span class="sxs-lookup"><span data-stu-id="89f80-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6.  <span data-ttu-id="89f80-130">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="89f80-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="89f80-131">Zastosowanie stylu formantu WPF</span><span class="sxs-lookup"><span data-stu-id="89f80-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="89f80-132">Możesz zastosować różne stylów formantu WPF i zmienić wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="89f80-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="89f80-133">Aby zastosować styl do kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="89f80-133">To apply a style to a WPF control</span></span>  
  
1.  <span data-ttu-id="89f80-134">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="89f80-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="89f80-135">W **przybornika**, kliknij dwukrotnie `UserControl1` można utworzyć wystąpienia `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="89f80-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="89f80-136">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="89f80-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="89f80-137">W panelu tagów inteligentnych dla `elementHost1`, kliknij przycisk **Edytuj hostowana zawartość** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="89f80-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="89f80-138">`UserControl1`zostanie otwarty w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89f80-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="89f80-139">W widoku XAML, Wstaw następujący XAML po `<UserControl>` tagu początkowego.</span><span class="sxs-lookup"><span data-stu-id="89f80-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="89f80-140">Ta XAML tworzy gradient kontrastujące obramowaniem gradientu.</span><span class="sxs-lookup"><span data-stu-id="89f80-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="89f80-141">Po kliknięciu formantu gradienty zostaną zmienione na generowanie wygląd naciśniętego przycisku.</span><span class="sxs-lookup"><span data-stu-id="89f80-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="89f80-142">Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="89f80-142">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
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
  
1.  <span data-ttu-id="89f80-143">Zastosuj `SimpleButton` zdefiniowanego w poprzednim kroku na przycisk Anuluj, wstawiając następujące XAML w stylu `<Button>` Etykieta przycisku Anuluj.</span><span class="sxs-lookup"><span data-stu-id="89f80-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="89f80-144">Twoje zgłoszenie przycisk będzie przypominać następujące XAML.</span><span class="sxs-lookup"><span data-stu-id="89f80-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  <span data-ttu-id="89f80-145">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="89f80-145">Build the project.</span></span>  
  
2.  <span data-ttu-id="89f80-146">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="89f80-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="89f80-147">Nowy styl jest stosowany do formantu przycisku.</span><span class="sxs-lookup"><span data-stu-id="89f80-147">The new style is applied to the button control.</span></span>  
  
4.  <span data-ttu-id="89f80-148">Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="89f80-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5.  <span data-ttu-id="89f80-149">Kliknij przycisk OK lub Anuluj i wyświetlanie różnic.</span><span class="sxs-lookup"><span data-stu-id="89f80-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f80-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89f80-150">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="89f80-151">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="89f80-151">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="89f80-152">Korzystanie z formantów WPF</span><span class="sxs-lookup"><span data-stu-id="89f80-152">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="89f80-153">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="89f80-153">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="89f80-154">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="89f80-154">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="89f80-155">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="89f80-155">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
