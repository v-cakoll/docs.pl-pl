---
title: 'Przewodnik: hostowanie kontrolki ActiveX w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 0181093de1c40889110ab7eae75a3847a17845a9
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859935"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Przewodnik: hostowanie kontrolki ActiveX w WPF
Aby włączone ulepszone współdziałanie z przeglądarki, można użyć kontrolek ActiveX firmy Microsoft w usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji. W tym instruktażu pokazano, jak możesz hostować [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] jako formant na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony.

 Zadania zilustrowane w tym przewodniku obejmują:

- Tworzenie projektu.

- Tworzenie kontrolki ActiveX.

- Hosting kontrolki ActiveX na stronie WPF.

 Po ukończeniu tego przewodnika, będzie zrozumienie, jak użyć kontrolek ActiveX firmy Microsoft w swojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] zainstalowana na komputerze, na którym jest zainstalowany program Visual Studio.

- Visual Studio 2010.

## <a name="creating-the-project"></a>Tworzenie projektu

### <a name="to-create-and-set-up-the-project"></a>Aby utworzyć i skonfigurować projekt

1. Utwórz projekt aplikacji WPF, o nazwie `HostingAxInWpf`.

2. Dodaj projekt Biblioteka kontrolek formularzy Windows do rozwiązania, a następnie nadaj projektowi nazwę `WmpAxLib`.

3. W projekcie WmpAxLib Dodaj odwołanie do zestawu Windows Media Player, która nosi nazwę wmp.dll.

4. Otwórz **przybornika**.

5. Kliknij prawym przyciskiem myszy **przybornika**, a następnie kliknij przycisk **wybierz elementy**.

6. Kliknij przycisk **składników COM** zaznacz **Windows Media Player** sterowania, a następnie kliknij przycisk **OK**.

     Formant programu Windows Media Player jest dodawany do **przybornika**.

7. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1** pliku, a następnie kliknij przycisk **Zmień nazwę**.

8. Zmień nazwę na `WmpAxControl.vb` lub `WmpAxControl.cs`, w zależności od języka.

9. Jeśli zostanie wyświetlony monit o zmianę nazwy wszystkich odwołań, kliknij przycisk **tak**.

## <a name="creating-the-activex-control"></a>Tworzenie kontrolki ActiveX
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] automatycznie generuje <xref:System.Windows.Forms.AxHost> klasy otoki kontrolki ActiveX firmy Microsoft, gdy formant został dodany do powierzchni projektowej. Poniższa procedura tworzy zestaw zarządzany o nazwie AxInterop.WMPLib.dll.

### <a name="to-create-the-activex-control"></a>Aby utworzyć formant ActiveX

1. Otwórz WmpAxControl.vb lub WmpAxControl.cs w programie Windows Forms Designer.

2. Z **przybornika**, dodawanie formantu programu Windows Media Player do powierzchni projektowej.

3. W oknie dialogowym właściwości ustawić wartość kontrolki Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.

4. Tworzenie projektu biblioteki kontrolek WmpAxLib.

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hostowanie kontrolki ActiveX na stronie WPF

### <a name="to-host-the-activex-control"></a>Do hostowania kontrolki ActiveX

1. W projekcie HostingAxInWpf Dodaj odwołanie do wygenerowanego zestawu współdziałania ActiveX.

     Ten zestaw o nazwie AxInterop.WMPLib.dll i został dodany do folderu debugowania projektu WmpAxLib po zaimportowaniu formantu programu Windows Media Player.

2. Dodaj odwołanie do zestawu WindowsFormsIntegration, która nosi nazwę WindowsFormsIntegration.dll.

3. Dodaj odwołanie do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zestawu, która nosi nazwę System.Windows.Forms.dll.

4. Otwórz pliku MainWindow.xaml w Projektancie WPF.

5. Nazwa <xref:System.Windows.Controls.Grid> elementu `grid1`.

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. W widoku projektu lub XAML, wybierz <xref:System.Windows.Window> elementu.

7. W oknie dialogowym właściwości kliknij **zdarzenia** kartę.

8. Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.

9. Wstaw następujący kod do obsługi <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.

     Ten kod tworzy wystąpienie <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli i dodaje instancję `AxWindowsMediaPlayer` formant jako jego podrzędny.

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: Hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
