---
title: 'Wskazówki: nadawanie stylu zawartości WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: bd056bb9d5ad429e35e0b2625dee99ae5f18b527
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780144"
---
# <a name="walkthrough-styling-wpf-content"></a>Wskazówki: nadawanie stylu zawartości WPF
W tym instruktażu pokazano, jak stosowanie stylów do formantu Windows Presentation Foundation (WPF) hostowanych w formularzu Windows.

 W tym przewodniku należy wykonać następujące zadania:

-   Utwórz projekt.

-   Utwórz typ formantu WPF.

-   Zastosuj styl do kontrolki WPF.

> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Visual Studio 2012.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu Windows Forms.  
  
> [!NOTE]
>  Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `StylingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>Tworzenie typów formantów WPF  
 Po dodaniu typu formantu WPF do projektu, można umieścić go w <xref:System.Windows.Forms.Integration.ElementHost> kontroli.  
  
#### <a name="to-create-wpf-control-types"></a>Aby utworzyć typy kontrolek WPF  
  
1.  Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania. Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Select i Przesuń elementy na powierzchni projektowej](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.  
  
4.  Dodaj <xref:System.Windows.Controls.Button?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **anulować**.  
  
5.  Dodaj drugą <xref:System.Windows.Controls.Button?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości **OK**.  
  
6.  Skompiluj projekt.  
  
## <a name="applying-a-style-to-a-wpf-control"></a>Zastosować styl do kontrolki WPF  
 Można stosować różne style do formantu WPF, aby zmienić wygląd i zachowanie.  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a>Aby zastosować styl do kontrolki WPF  
  
1.  Otwórz `Form1` w programie Windows Forms Designer.  
  
2.  W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w formularzu.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
3.  W panelu tagi inteligentne dla `elementHost1`, kliknij przycisk **Edytuj hostowana zawartość** z listy rozwijanej.  
  
     `UserControl1` zostanie otwarty w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  W widoku XAML, Wstaw następujące XAML po `<UserControl>` tagu początkowego.  
  
     Ta XAML tworzy gradient kontrastujące obramowaniem gradientu. Po kliknięciu formantu gradientów zostały zmienione, aby wygenerować się po naciśnięciu przycisku. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
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
  
1.  Zastosuj `SimpleButton` style zdefiniowane w poprzednim kroku, aby przycisk Anuluj, wstawiając następujące XAML w `<Button>` tag przycisk Anuluj.  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     Twoje zgłoszenie przycisk będzie przypominał następujące XAML.  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  Skompiluj projekt.  
  
2.  Otwórz `Form1` w programie Windows Forms Designer.  
  
3.  Nowy styl jest stosowany do kontrolki przycisku.  
  
4.  Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** do uruchomienia aplikacji.  
  
5.  Kliknij przycisk OK lub Anuluj i wyświetlać różnice.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Korzystanie z kontrolek WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
