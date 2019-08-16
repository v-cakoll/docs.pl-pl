---
title: 'Przewodnik: Tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 889e81053d4e2264755468446a4e1681216ae22e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040373"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>Przewodnik: Utwórz nową zawartość WPF na Windows Forms w czasie projektowania

W tym artykule pokazano, jak utworzyć formant Windows Presentation Foundation (WPF) do użycia w aplikacjach opartych na Windows Forms.

W tym instruktażu wykonasz następujące zadania:

- Utwórz projekt.

- Utwórz nową kontrolkę WPF.

- Dodaj nową kontrolkę WPF do formularza systemu Windows. Kontrolka WPF jest hostowana w <xref:System.Windows.Forms.Integration.ElementHost> kontrolce.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio

## <a name="create-the-project"></a>Utwórz projekt

Pierwszym krokiem jest utworzenie projektu Windows Forms. Otwórz program Visual Studio i Utwórz nowy projekt **aplikacji Windows Forms (.NET Framework)** w Visual Basic lub wizualizacji `HostingWpf` C# o nazwie.

> [!NOTE]
> W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.

## <a name="create-a-new-wpf-control"></a>Utwórz nową kontrolkę WPF

Utworzenie nowej kontrolki WPF i dodanie jej do projektu jest tak proste jak dodanie innego elementu do projektu. Projektant formularzy systemu Windows działa z określonym rodzajem kontrolki o nazwie *formant złożony*lub *kontrolka użytkownika*. Aby uzyskać więcej informacji na temat kontrolek użytkownika <xref:System.Windows.Controls.UserControl>WPF, zobacz.

> [!NOTE]
> Typ dla WPF jest różny od typu kontrolki użytkownika dostarczonej przez Windows Forms, która jest również nazywana <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

Aby utworzyć nową kontrolkę WPF:

1. W **Eksplorator rozwiązań**Dodaj nowy projekt **biblioteki formantów użytkownika WPF (.NET Framework)** do rozwiązania. Użyj domyślnej nazwy biblioteki `WpfControlLibrary1`kontrolek. Domyślna nazwa kontrolki to `UserControl1.xaml`.

     Dodanie nowej kontrolki ma następujące skutki:

    - Plik UserControl1. XAML został dodany.

    - Dodano plik UserControl1.xaml.cs lub UserControl1. XAML. vb. Ten plik zawiera kod związany z obsługą zdarzeń oraz inne implementacje.

    - Dodano odwołania do zestawów WPF.

    - Plik UserControl1. XAML zostanie otwarty w [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].

2. W widok Projekt upewnij się, że `UserControl1` jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Wybierz i przenieś elementy na Powierzchnia projektowa](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).

3. W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Z **przybornika**przeciągnij <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolkę na powierzchnię projektu.

5. W oknie **Właściwości** ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości na **hostowana zawartość**.

    > [!NOTE]
    > Ogólnie rzecz biorąc, należy hostować bardziej zaawansowaną zawartość WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontrolka jest używana w tym miejscu tylko do celów informacyjnych.

6. Skompiluj projekt.

## <a name="add-a-wpf-control-to-a-windows-form"></a>Dodawanie formantu WPF do formularza systemu Windows

Nowa kontrolka WPF jest gotowa do użycia w formularzu. Windows Forms używa <xref:System.Windows.Forms.Integration.ElementHost> kontrolki do hostowania zawartości WPF.

Aby dodać formant WPF do formularza systemu Windows:

1. Otwórz `Form1` w Projektant formularzy systemu Windows.

2. W przyborniku Znajdź kartę z **WPFUserControlLibraryą formantów użytkownika WPF**.

3. Przeciągnij wystąpienie do `UserControl1` formularza.

    - <xref:System.Windows.Forms.Integration.ElementHost> Formant jest automatycznie tworzony w formularzu, aby hostować formant WPF.

    - `elementHost1` <xref:System.Windows.Forms.Integration.ElementHost.Child%2A>Kontrolka ma nazwę i w oknie właściwości można zobaczyć, że jej właściwość jest ustawiona na UserControl1. <xref:System.Windows.Forms.Integration.ElementHost>

    - Odwołania do zestawów WPF są dodawane do projektu.

    - `elementHost1` Kontrolka zawiera Panel tagów inteligentnych, który zawiera dostępne opcje hostingu.

4. W panelu Tagi inteligentne **ElementHost zadania** wybierz pozycję Zadokuj **w kontenerze nadrzędnym**.

5. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.

## <a name="next-steps"></a>Następne kroki

Windows Forms i WPF są różnymi technologiami, ale są one tak zaprojektowane, aby ściśle współpracować. Aby zapewnić bogatszy wygląd i zachowanie aplikacji, spróbuj wykonać następujące czynności:

- Hostowanie kontrolki Windows Forms na stronie WPF. Aby uzyskać więcej informacji, [zobacz Przewodnik: Hostowanie formantu Windows Forms w WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).

- Zastosuj Windows Forms style wizualne do zawartości WPF. Aby uzyskać więcej informacji, zobacz [jak: Włącz style wizualne w aplikacji](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)hybrydowej.

- Zmień styl zawartości WPF. Aby uzyskać więcej informacji, [zobacz Przewodnik: Style zawartości](walkthrough-styling-wpf-content.md)WPF.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
