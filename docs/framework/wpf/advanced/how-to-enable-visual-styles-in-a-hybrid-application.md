---
title: Jak włączyć style Visual w aplikacji hybrydowej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 2d714ad020f2f7b6a6343c8f8e3901b59dfd23a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Jak włączyć style Visual w aplikacji hybrydowej
W tym temacie przedstawiono sposób włączania [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual style na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli hostowanych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.  
  
 Jeśli aplikacja wymaga <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody, większość z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty będą automatycznie używać stylów wizualnych, gdy aplikacja jest uruchamiana na [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]. Aby uzyskać więcej informacji, zobacz [renderowanie formantów przy użyciu stylów wizualnych](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Kompletny kod listę zadań przedstawione w tym temacie, można znaleźć [włączenie style wizualne w przykładowej aplikacji hybrydowych](http://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Włączanie Windows Forms style wizualne  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Aby włączyć style wizualne formularzy systemu Windows  
  
1.  Utwórz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt aplikacji o nazwie `HostingWfWithVisualStyles`.  
  
2.  W Eksploratorze rozwiązań Dodaj odwołania do następujących zestawów.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Przybornik, kliknij dwukrotnie <xref:System.Windows.Controls.Grid> ikonę, aby umieścić <xref:System.Windows.Controls.Grid> elementu na powierzchnię projektu.  
  
4.  W oknie właściwości można ustawić wartości właściwości <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości **automatycznie**.  
  
5.  W widoku projektu lub XAML, wybierz <xref:System.Windows.Window>.  
  
6.  Kliknij w oknie właściwości **zdarzenia** kartę.  
  
7.  Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.
  
8.  W MainWindow.xaml.vb lub MainWindow.xaml.cs, Wstaw następujący kod, aby obsłużyć <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Kontroli jest rysowane przy użyciu stylów wizualnych.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Wyłączanie Windows Forms style wizualne  
 Aby wyłączyć stylów wizualnych, po prostu usuń wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Aby wyłączyć style wizualne formularzy systemu Windows  
  
1.  Otwórz MainWindow.xaml.vb lub MainWindow.xaml.cs w edytorze kodu.  
  
2.  Komentarz wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.  
  
3.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Kontroli jest rysowane przy użyciu domyślnego systemu stylu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Renderowanie kontrolek przy użyciu stylów wizualnych](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [Przewodnik: hosting kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
