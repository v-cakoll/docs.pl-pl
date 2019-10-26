---
title: 'Wskazówki: hosting formantu ActiveX w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 395081640815f00ce4ae8e83f25b37de567adc01
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920197"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Wskazówki: hosting formantu ActiveX w WPF
Aby umożliwić lepszą interakcję z przeglądarkami, możesz użyć kontrolek ActiveX firmy Microsoft w aplikacji opartej na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. W tym instruktażu pokazano, jak można hostować [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] jako kontrolkę na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stronie.

 Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie projektu.

- Tworzenie kontrolki ActiveX.

- Hostowanie kontrolki ActiveX na stronie WPF.

 Po ukończeniu tego przewodnika dowiesz się, jak używać kontrolek ActiveX firmy Microsoft w aplikacji opartej na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] zainstalowany na komputerze, na którym jest zainstalowany program Visual Studio.

- Program Visual Studio 2010.

## <a name="creating-the-project"></a>Tworzenie projektu

### <a name="to-create-and-set-up-the-project"></a>Aby utworzyć i skonfigurować projekt

1. Utwórz projekt aplikacji WPF o nazwie `HostingAxInWpf`.

2. Dodaj projekt biblioteki formantów Windows Forms do rozwiązania i nadaj nazwę projektowi `WmpAxLib`.

3. W projekcie WmpAxLib Dodaj odwołanie do zestawu Media Player systemu Windows o nazwie WMP. dll.

4. Otwórz **Przybornik**.

5. Kliknij prawym przyciskiem myszy w **przyborniku**, a następnie kliknij pozycję **Wybierz elementy**.

6. Kliknij kartę **składniki com** , wybierz formant **Media Player systemu Windows** , a następnie kliknij przycisk **OK**.

     Kontrolka Media Player systemu Windows jest dodawana do **przybornika**.

7. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy plik **UserControl1** , a następnie kliknij polecenie **Zmień nazwę**.

8. Zmień nazwę na `WmpAxControl.vb` lub `WmpAxControl.cs`, w zależności od języka.

9. Jeśli zostanie wyświetlony monit o zmianę nazwy wszystkich odwołań, kliknij przycisk **tak**.

## <a name="creating-the-activex-control"></a>Tworzenie kontrolki ActiveX
Program Visual Studio automatycznie generuje klasę otoki <xref:System.Windows.Forms.AxHost> dla kontrolki ActiveX firmy Microsoft po dodaniu kontrolki do powierzchni projektowej. Poniższa procedura tworzy zarządzany zestaw o nazwie AxInterop. WMPLib. dll.

### <a name="to-create-the-activex-control"></a>Aby utworzyć kontrolkę ActiveX

1. Otwórz WmpAxControl. vb lub WmpAxControl.cs w Projektant formularzy systemu Windows.

2. Z **przybornika**dodaj formant Media Player systemu Windows do powierzchni projektowej.

3. W okno Właściwości ustaw wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> kontrolki Windows Media Player na <xref:System.Windows.Forms.DockStyle.Fill>.

4. Kompiluj projekt biblioteki formantów WmpAxLib.

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hostowanie kontrolki ActiveX na stronie WPF

### <a name="to-host-the-activex-control"></a>Aby hostować formant ActiveX

1. W projekcie HostingAxInWpf Dodaj odwołanie do wygenerowanego zestawu współdziałania ActiveX.

     Ten zestaw ma nazwę AxInterop. WMPLib. dll i został dodany do folderu debugowania projektu WmpAxLib podczas importowania formantu Media Player systemu Windows.

2. Dodaj odwołanie do zestawu WindowsFormsIntegration o nazwie WindowsFormsIntegration. dll.

3. Dodaj odwołanie do zestawu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] o nazwie System. Windows. Forms. dll.

4. Otwórz MainWindow. XAML w projektancie WPF.

5. Nadaj nazwę elementowi <xref:System.Windows.Controls.Grid> `grid1`.

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. W widoku widok Projekt lub XAML wybierz element <xref:System.Windows.Window>.

7. W okno Właściwości kliknij kartę **zdarzenia** .

8. Kliknij dwukrotnie zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.

9. Wstaw poniższy kod, aby obsłużyć zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.

     Ten kod tworzy wystąpienie formantu <xref:System.Windows.Forms.Integration.WindowsFormsHost> i dodaje wystąpienie formantu `AxWindowsMediaPlayer` jako jego element podrzędny.

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
