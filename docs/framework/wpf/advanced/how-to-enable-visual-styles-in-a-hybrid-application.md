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
ms.openlocfilehash: f4684e277335a119d41d5bd79d504ed37a76d6fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179458"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Jak włączyć style Visual w aplikacji hybrydowej
W tym temacie przedstawiono sposób włączania [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual style na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowania hostowaną w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.  
  
 Jeśli Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody, większość swojej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek będzie automatycznie używać stylów wizualnych, gdy aplikacja jest uruchamiana na [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]. Aby uzyskać więcej informacji, zobacz [renderowanie kontrolek przy użyciu stylów wizualnych](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Aby uzyskać kompletny kod listę zadań przedstawionych w tym temacie, zobacz [Włączanie stylów wizualnych w przykładowej aplikacji hybrydowych](https://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Włączanie Windows Forms stylów wizualnych  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Aby włączyć stylów wizualnych Windows Forms  
  
1.  Tworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt aplikacji o nazwie `HostingWfWithVisualStyles`.  
  
2.  W Eksploratorze rozwiązań należy dodać odwołania do następujących zestawów.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  W przyborniku, kliknij dwukrotnie <xref:System.Windows.Controls.Grid> ikonę, aby umieścić <xref:System.Windows.Controls.Grid> element na powierzchni projektowej.  
  
4.  W oknie właściwości ustaw wartości <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości **automatycznie**.  
  
5.  W widoku projektu lub XAML, wybierz <xref:System.Windows.Window>.  
  
6.  W oknie dialogowym właściwości kliknij **zdarzenia** kartę.  
  
7.  Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.
  
8.  W MainWindow.xaml.vb lub MainWindow.xaml.cs, Wstaw następujący kod do obsługi <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Kontroli jest malowane przy użyciu stylów wizualnych.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Wyłączanie Windows Forms stylów wizualnych  
 Aby wyłączyć stylów wizualnych, po prostu usuń wywołanie funkcji <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Aby wyłączyć stylów wizualnych Windows Forms  
  
1.  Otwórz pliku MainWindow.xaml.vb lub MainWindow.xaml.cs w edytorze kodu.  
  
2.  Komentarz wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.  
  
3.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Kontroli jest malowany domyślnego stylu systemu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Renderowanie kontrolek przy użyciu stylów wizualnych](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [Przewodnik: hosting kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
