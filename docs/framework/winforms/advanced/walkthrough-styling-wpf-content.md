---
title: 'Przewodnik: Nadawanie stylu zawartości WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 287ed08db8a4266e5044a81d47a697949257e113
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658482"
---
# <a name="walkthrough-style-wpf-content"></a>Przewodnik: Styl zawartości WPF

W tym artykule pokazano, jak zastosować styl do formantu Windows Presentation Foundation (WPF) hostowanego w formularzu systemu Windows.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub C# wizualizacji `StylingWpfContent`o nazwie.

> [!NOTE]
> W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.

## <a name="create-the-wpf-control-types"></a>Tworzenie typów formantów WPF

Po dodaniu typu formantu WPF do projektu można hostować go w <xref:System.Windows.Forms.Integration.ElementHost> kontrolce.

1. Dodaj nowy projekt WPF <xref:System.Windows.Controls.UserControl> do rozwiązania. Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`. Aby uzyskać więcej informacji, [zobacz Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)projektowania.

2. W widok Projekt upewnij się, że `UserControl1` jest zaznaczone.

3. W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Dodaj kontrolkę <xref:System.Windows.Controls.UserControl> do i <xref:System.Windows.Controls.ContentControl.Content%2A> ustaw wartość właściwości na **Anuluj.** <xref:System.Windows.Controls.Button?displayProperty=nameWithType>

5. Dodaj drugą <xref:System.Windows.Controls.Button?displayProperty=nameWithType> kontrolkę <xref:System.Windows.Controls.UserControl> do i <xref:System.Windows.Controls.ContentControl.Content%2A> ustaw wartość właściwości na **OK**.

6. Skompiluj projekt.

## <a name="apply-a-style-to-a-wpf-control"></a>Zastosuj styl do kontrolki WPF

Możesz zastosować różne style do kontrolki WPF, aby zmienić jej wygląd i zachowanie.

1. Otwórz `Form1` w Projektant formularzy systemu Windows.

1. W **przyborniku**kliknij `UserControl1` dwukrotnie, aby utworzyć wystąpienie elementu `UserControl1` w formularzu.

   Wystąpienie `UserControl1` jest hostowane w nowym <xref:System.Windows.Forms.Integration.ElementHost> formancie o nazwie `elementHost1`.

1. W panelu tagów inteligentnych dla `elementHost1`kliknij pozycję **Edytuj hostowaną zawartość** z listy rozwijanej.

   `UserControl1`otwiera w projektancie WPF.

1. W widoku XAML Wstaw następujący kod XAML po `<UserControl>` tagu otwierającym. Ten kod XAML tworzy gradient z kontrastowym obramowaniem gradientu. Gdy formant zostanie kliknięty, gradienty są zmieniane w celu wygenerowania naciśniętego przycisku. Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](../../wpf/controls/styling-and-templating.md).

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

1. Zastosuj styl zdefiniowany w poprzednim kroku do przycisku Anuluj, wstawiając Poniższy kod XAML `<Button>` w tagu przycisku **Anuluj** . `SimpleButton`

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Deklaracja przycisku będzie wyglądać podobnie do następującego kodu XAML:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Skompiluj projekt.

1. Otwórz `Form1` w Projektant formularzy systemu Windows.

1. Nowy styl zostanie zastosowany do kontrolki Button.

1. Z menu **Debuguj** wybierz pozycję **Rozpocznij debugowanie** , aby uruchomić aplikację.

1. Kliknij przycisk **OK** i **Anuluj** , aby wyświetlić różnice.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przegląd XAML (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [Tworzenie szablonów i stylów](../../wpf/controls/styling-and-templating.md)
