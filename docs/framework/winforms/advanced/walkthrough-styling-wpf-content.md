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
# <a name="walkthrough-style-wpf-content"></a>Instruktaż: Styl zawartości WPF

W tym artykule pokazano, jak zastosować styl do formantu Windows Presentation Foundation (WPF) hostowanego w formularzu systemu Windows.

## <a name="prerequisites"></a>Wymagania wstępne

Program Visual Studio musi ukończyć ten instruktaż.

## <a name="create-the-project"></a>Tworzenie projektu

Otwórz program Visual Studio i utwórz nowy projekt aplikacji `StylingWpfContent`formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie .

> [!NOTE]
> Podczas hostowania zawartości WPF obsługiwane są tylko projekty języka C# i Visual Basic.

## <a name="create-the-wpf-control-types"></a>Tworzenie typów formantów WPF

Po dodaniu typu formantu WPF do projektu, <xref:System.Windows.Forms.Integration.ElementHost> można hostować go w formancie.

1. Dodaj nowy projekt <xref:System.Windows.Controls.UserControl> WPF do rozwiązania. Użyj domyślnej nazwy typu `UserControl1.xaml`formantu, . Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF w formularzach systemu Windows w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. W widoku Projekt upewnij `UserControl1` się, że jest zaznaczona.

3. W oknie **Właściwości** ustaw wartość i <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> właściwości na **200**.

4. Dodaj <xref:System.Windows.Controls.Button?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> do i ustaw <xref:System.Windows.Controls.ContentControl.Content%2A> wartość właściwości **anuluj**.

5. Dodaj drugi <xref:System.Windows.Controls.Button?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> do i ustaw <xref:System.Windows.Controls.ContentControl.Content%2A> wartość właściwości na **OK**.

6. Skompiluj projekt.

## <a name="apply-a-style-to-a-wpf-control"></a>Stosowanie stylu do formantu WPF

Można zastosować różne stylizacje do formantu WPF, aby zmienić jego wygląd i zachowanie.

1. Otwórz `Form1` w Projektancie formularzy systemu Windows.

1. W **przyborniku**kliknij `UserControl1` dwukrotnie, aby `UserControl1` utworzyć wystąpienie w formularzu.

   Wystąpienie `UserControl1` jest hostowane w <xref:System.Windows.Forms.Integration.ElementHost> nowym `elementHost1`formancie o nazwie .

1. W panelu `elementHost1`tagów inteligentnych kliknij pozycję **Edytuj zawartość hostowana** z listy rozwijanej.

   `UserControl1`otwiera się w Projektancie WPF.

1. W widoku XAML wstaw następujący kod `<UserControl>` XAML po znaczniku otwierającym. Ten kod XAML tworzy gradient z kontrastującymi obramowaniem gradientu. Po kliknięciu formantu gradienty są zmieniane w celu wygenerowania wyglądu naciśnięty przycisk. Aby uzyskać więcej informacji, zobacz [Stylowanie i tworzenie szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

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

1. Zastosuj `SimpleButton` styl zdefiniowany w poprzednim kroku do przycisku Anuluj, `<Button>` wstawiając następujący kod XAML w tagu przycisku **Anuluj.**

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Deklaracja przycisków będzie przypominać następujący kod XAML:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Skompiluj projekt.

1. Otwórz `Form1` w Projektancie formularzy systemu Windows.

1. Nowy styl jest stosowany do formantu przycisku.

1. Z menu **Debugowanie** wybierz polecenie **Rozpocznij debugowanie,** aby uruchomić aplikację.

1. Kliknij przyciski **OK** i **Anuluj** i wyświetl różnice.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
