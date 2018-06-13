---
title: 'Wskazówki: hosting formantu Windows Forms w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 515135893c0d6cf251977bbddc13241e8b6b60bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546832"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Wskazówki: hosting formantu Windows Forms w WPF
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia wiele formantów z zestawem funkcji zaawansowanych. Jednak czasami warto użyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stron. Na przykład może mieć znaczne inwestycji w istniejących [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, lub może być [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który udostępnia funkcje unikatowy.  
  
 W tym przewodniku przedstawiono sposób obsługi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> kontrolować na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony przy użyciu kodu.  
  
 Kompletny kod lista zadań wyświetlane w tym przewodniku, zobacz [hostowanie kontrolki formularza systemu Windows w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=160057).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="hosting-the-windows-forms-control"></a>Hostowanie kontrolki formularza systemu Windows  
  
#### <a name="to-host-the-maskedtextbox-control"></a>Na hoście maskedtextbox — formant  
  
1.  Utwórz projekt aplikacji WPF o nazwie `HostingWfInWpf`.  
  
2.  Dodaj odwołania do następujących zestawów.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Otwórz MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  Nazwa <xref:System.Windows.Controls.Grid> elementu `grid1`.  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  W widoku projektu lub XAML, wybierz <xref:System.Windows.Window> elementu.  
  
6.  Kliknij w oknie właściwości **zdarzenia** kartę.  
  
7.  Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.  
  
8.  Wstaw następujący kod, aby obsłużyć <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. W górnej części pliku, Dodaj następujący `Imports` lub `using` instrukcji.  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Przewodnik: hosting kontrolki Windows Form w WPF z wykorzystaniem XAML](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Kontrolki formularzy Windows Forms i równoważne kontrolki WPF](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [Hostowanie kontrolki formularza systemu Windows w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=160057)
