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
ms.openlocfilehash: 251c53a8665d2eae7c3b5bb23b0a388009362dcc
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960115"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Jak włączyć style Visual w aplikacji hybrydowej
W tym temacie przedstawiono sposób włączania stylów wizualnych w formancie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hostowanym w aplikacji opartej na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Jeśli aplikacja wywołuje metodę <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, większość kontrolek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] będzie automatycznie używać stylów wizualnych. Aby uzyskać więcej informacji, zobacz [renderowanie formantów przy użyciu stylów wizualnych](../../winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Aby uzyskać pełną listę kodów zadań przedstawionych w tym temacie, zobacz [Włączanie stylów wizualnych w przykładowej aplikacji hybrydowej](https://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Włączanie Windows Forms stylów wizualnych  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Aby włączyć Windows Forms style wizualizacji  
  
1. Utwórz projekt aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o nazwie `HostingWfWithVisualStyles`.  
  
2. W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. W przyborniku kliknij dwukrotnie ikonę <xref:System.Windows.Controls.Grid>, aby umieścić element <xref:System.Windows.Controls.Grid> na powierzchni projektowej.  
  
4. W okno Właściwości ustaw wartości właściwości <xref:System.Windows.FrameworkElement.Height%2A> i **<xref:System.Windows.FrameworkElement.Width%2A> na wartość**Auto.  
  
5. W widoku widok Projekt lub XAML wybierz <xref:System.Windows.Window>.  
  
6. W okno Właściwości kliknij kartę **zdarzenia** .  
  
7. Kliknij dwukrotnie zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.
  
8. W MainWindow. XAML. vb lub MainWindow.xaml.cs Wstaw następujący kod, aby obsłużyć zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     Formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest malowany przy użyciu stylów wizualnych.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Wyłączanie Windows Forms stylów wizualnych  
 Aby wyłączyć style wizualne, po prostu usuń wywołanie metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Aby wyłączyć Windows Forms style wizualizacji  
  
1. Otwórz MainWindow. XAML. vb lub MainWindow.xaml.cs w edytorze kodu.  
  
2. Dodaj komentarz do wywołania metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
3. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     Formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest malowany przy użyciu domyślnego stylu systemowego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Renderowanie kontrolek przy użyciu stylów wizualnych](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [Przewodnik: hosting kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
