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
# <a name="walkthrough-style-wpf-content"></a>Przewodnik: zawartość w stylu WPF

W tym artykule pokazano, jak zastosować styl do formantu Windows Presentation Foundation (WPF) hostowanego w formularzu systemu Windows.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub wizualizacji C# o nazwie `StylingWpfContent`.

> [!NOTE]
> W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.

## <a name="create-the-wpf-control-types"></a>Tworzenie typów formantów WPF

Po dodaniu typu formantu WPF do projektu można hostować go w kontrolce <xref:System.Windows.Forms.Integration.ElementHost>.

1. Dodaj nowy projekt WPF <xref:System.Windows.Controls.UserControl> do rozwiązania. Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. W widok Projekt upewnij się, że wybrano pozycję `UserControl1`.

3. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Dodaj kontrolkę <xref:System.Windows.Controls.Button?displayProperty=nameWithType> do <xref:System.Windows.Controls.UserControl> i ustaw wartość właściwości <xref:System.Windows.Controls.ContentControl.Content%2A> na **Anuluj**.

5. Dodaj drugą kontrolkę <xref:System.Windows.Controls.Button?displayProperty=nameWithType> do <xref:System.Windows.Controls.UserControl> i ustaw wartość właściwości <xref:System.Windows.Controls.ContentControl.Content%2A> na **OK**.

6. Skompiluj projekt.

## <a name="apply-a-style-to-a-wpf-control"></a>Zastosuj styl do kontrolki WPF

Możesz zastosować różne style do kontrolki WPF, aby zmienić jej wygląd i zachowanie.

1. Otwórz `Form1` w Projektant formularzy systemu Windows.

1. W **przyborniku**kliknij dwukrotnie `UserControl1`, aby utworzyć wystąpienie `UserControl1` w formularzu.

   Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost1`.

1. W panelu tagów inteligentnych dla `elementHost1`kliknij pozycję **Edytuj hostowaną zawartość** z listy rozwijanej.

   `UserControl1` zostanie otwarty w projektancie WPF.

1. W widoku XAML Wstaw następujący kod XAML po tagu otwierającym `<UserControl>`. Ten kod XAML tworzy gradient z kontrastowym obramowaniem gradientu. Gdy formant zostanie kliknięty, gradienty są zmieniane w celu wygenerowania naciśniętego przycisku. Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](../../wpf/controls/styling-and-templating.md).

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

1. Zastosuj styl `SimpleButton` zdefiniowany w poprzednim kroku do przycisku Anuluj, wstawiając Poniższy kod XAML w tagu `<Button>` przycisku **Anuluj** .

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
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Przegląd XAML (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [Tworzenie szablonów i stylów](../../wpf/controls/styling-and-templating.md)
