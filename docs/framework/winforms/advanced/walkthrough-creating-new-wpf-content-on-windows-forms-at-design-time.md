---
title: 'Wskazówki: tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: dd68911abfa6bd6315091fb4630134532053efa1
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999874"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a>Wskazówki: tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania

W tym temacie dowiesz się, jak utworzyć formant Windows Presentation Foundation (WPF) do użytku w aplikacjach opartych na formularzach Windows.

W tym przewodniku należy wykonać następujące zadania:

- Utwórz projekt.

- Utwórz nową kontrolkę WPF.

- Dodawanie nowej kontrolki WPF do formularza Windows. Kontrolki WPF znajduje się w <xref:System.Windows.Forms.Integration.ElementHost> kontroli.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2017

## <a name="creating-the-project"></a>Tworzenie projektu

Pierwszym krokiem jest utworzenie projektu Windows Forms. Otwórz program Visual Studio i Utwórz nowy **aplikacji programu Windows Forms (.NET Framework)** projektu w języku Visual Basic lub Visual C# o nazwie `HostingWpf`.

> [!NOTE]
> Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.

## <a name="creating-a-new-wpf-control"></a>Utworzenie nowej kontrolki WPF

Utworzenie nowej kontrolki WPF, a następnie dodanie go do projektu jest bardzo proste — wystarczy dodanie innych elementów do projektu. Windows Forms Designer współpracuje z określonego rodzaju formantu o nazwie *złożonej kontrolki*, lub *kontrolki użytkownika*. Aby uzyskać więcej informacji dotyczących kontrolek użytkownika WPF, zobacz <xref:System.Windows.Controls.UserControl>.

> [!NOTE]
> <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> Wpisz WPF różni się od typu formantu użytkownika, dostarczone przez Windows Forms, który jest również określany <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.

### <a name="to-create-a-new-wpf-control"></a>Aby utworzyć nowe kontrolki WPF

1. W **Eksploratora rozwiązań**, Dodaj nowy **Biblioteka kontrolek użytkownika WPF (.NET Framework)** projektu do rozwiązania. Użyj domyślnej nazwy dla Biblioteka kontrolek `WpfControlLibrary1`. Domyślną nazwą formantu jest `UserControl1.xaml`.

     Dodawanie nowej kontrolki ma następujące skutki:

    - UserControl1.xaml plik zostanie dodany.

    - Plik UserControl1.xaml.cs lub UserControl1.xaml.vb są dodawane. Ten plik zawiera kodem procedury obsługi zdarzeń i innych implementacji.

    - Dodaje odwołania do zestawów WPF.

    - UserControl1.xaml plik zostanie otwarty w [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].

2. W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Select i Przesuń elementy na powierzchni projektowej](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).

3. W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości **200**.

4. Z **przybornika**, przeciągnij <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolki na powierzchnię projektu.

5. W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanej zawartości**.

    > [!NOTE]
    > Ogólnie rzecz biorąc należy obsługiwać bardziej złożone zawartości WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontroli jest tu używany wyłącznie w celach opisowy.

6. Skompiluj projekt.

## <a name="adding-a-wpf-control-to-a-windows-form"></a>Dodawanie kontrolki WPF do postaci Windows

Nowe kontrolki WPF jest gotowy do użycia w formularzu. Formularze Windows używa <xref:System.Windows.Forms.Integration.ElementHost> kontrolki hosta zawartości WPF.

### <a name="to-add-a-wpf-control-to-a-windows-form"></a>Aby dodać kontrolki WPF do postaci Windows

1. Otwórz `Form1` w programie Windows Forms Designer.

2. W **przybornika**, Znajdź kartę **kontrolek użytkownika WPF WPFUserControlLibrary**.

3. Przeciągnij wystąpienie `UserControl1` na formularz.

    - <xref:System.Windows.Forms.Integration.ElementHost> Kontrolki jest tworzona automatycznie na formularzu do hostowania kontrolki WPF.

    - <xref:System.Windows.Forms.Integration.ElementHost> Nosi nazwę kontrolki `elementHost1` i **właściwości** okna, możesz zobaczyć jego <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl1**.

    - Odwołania do zestawów WPF są dodawane do projektu.

    - `elementHost1` Kontrolkę panelu tagu inteligentnego, który przedstawia dostępne opcje hostingu.

4. W **zadania ElementHost** panelu tagi inteligentne, wybierz opcję **Zadokuj w kontenerze nadrzędnym**.

5. Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

## <a name="next-steps"></a>Następne kroki

Windows Forms i WPF są różne technologie, ale są one przeznaczone do ściśle współpracować. Aby zapewnić bardziej rozbudowane wygląd i zachowanie w swoich aplikacjach, spróbuj wykonać następujące czynności:

- Hostowanie kontrolki Windows Forms na stronie programu WPF. Aby uzyskać więcej informacji, zobacz [wskazówki: Hosting formantu Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).

- Stosowanie stylów wizualnych Windows Forms do zawartości WPF. Aby uzyskać więcej informacji, zobacz [porady: Włączanie stylów wizualnych w aplikacji hybrydowej](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).

- Zmiana stylu zawartości WPF. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie stylów zawartości WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)