---
title: 'Przewodnik: hostowanie kontrolki Windows Forms w WPF z wykorzystaniem języka XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 10554145de9725bb4cfc655ed88195dce28d739c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032113"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>Przewodnik: hostowanie kontrolki Windows Forms w WPF z wykorzystaniem języka XAML
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia wiele kontrolek z rozbudowanym zestawie funkcji. Jednak czasami warto użyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów na Twoje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stron. Na przykład może mieć znaczne inwestycje w istniejących [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, lub może być [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który oferuje unikatową funkcję.  
  
 W tym instruktażu dowiesz się, jak hostować formularzy Windows <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> kontrolować na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Aby uzyskać kompletny kod listę zadań przedstawione w niniejszym instruktażu, zobacz [Hosting kontrolki Windows Forms w WPF próbki przy użyciu XAML](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).
  
## <a name="prerequisites"></a>Wymagania wstępne  

Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.  
  
## <a name="hosting-the-windows-forms-control"></a>Hostowanie kontrolki formularza Windows  
  
#### <a name="to-host-the-maskedtextbox-control"></a>Do hostowania maskedtextbox — formant  
  
1. Utwórz projekt aplikacji WPF, o nazwie `HostingWfInWpfWithXaml`.  
  
2. Dodaj odwołania do następujących zestawów.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. Otwieranie pliku MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4. W <xref:System.Windows.Window> elementu, Dodaj następujące mapowanie przestrzeni nazw. `wf` Mapowanie przestrzeni nazw ustanawia odwołanie do zestawu, który zawiera kontrolki Windows Forms.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. W <xref:System.Windows.Controls.Grid> elementu Dodawanie następujące XAML.  
  
     <xref:System.Windows.Forms.MaskedTextBox> Formant zostanie utworzony jako element podrzędny elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli.  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: Hosting kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Przewodnik: Hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Kontrolki formularzy Windows Forms i równoważne kontrolki WPF](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hosting kontrolki Windows Forms w WPF za pomocą przykładowych XAML](https://go.microsoft.com/fwlink/?LinkID=160000)
