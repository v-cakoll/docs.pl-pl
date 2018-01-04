---
title: "Wskazówki: hosting formantu ActiveX w WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6980097c074e10efae7fc6ee77c6c9835c3b1b00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Wskazówki: hosting formantu ActiveX w WPF
Aby włączyć ulepszone interakcji z przeglądarki, można użyć [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] formantów w Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-aplikacji. W tym przewodniku pokazano, jak można hostować [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] jako formant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu.  
  
-   Tworzenie formantu ActiveX.  
  
-   Hostowanie kontrolki ActiveX na stronie WPF.  
  
 Po ukończeniu tego przewodnika, wiedzieć, jak używać [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] formantów w Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]zainstalowana na komputerze, którym [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] jest zainstalowany.  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].,  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Tworzenie i konfigurowanie projektu  
  
1.  Utwórz projekt aplikacji WPF o nazwie `HostingAxInWpf`.  
  
2.  Dodaj projekt Biblioteka formantów formularzy systemu Windows do rozwiązania, a nazwa projektu `WmpAxLib`.  
  
3.  W projekcie WmpAxLib Dodaj odwołanie do zestawu Windows Media Player, o nazwie wmp.dll.  
  
4.  Otwórz **przybornika**.  
  
5.  Kliknij prawym przyciskiem myszy **przybornika**, a następnie kliknij przycisk **wybierz elementy**.  
  
6.  Kliknij przycisk **składniki COM** wybierz opcję **Windows Media Player** kontroli, a następnie kliknij przycisk **OK**.  
  
     Program Windows Media Player formant został dodany do **przybornika**.  
  
7.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1** pliku, a następnie kliknij przycisk **zmienić**.  
  
8.  Zmień nazwę, aby `WmpAxControl.vb` lub `WmpAxControl.cs`, w zależności od języka.  
  
9. Jeśli zostanie wyświetlony monit, aby zmienić nazwę wszystkich odwołań, kliknij przycisk **tak**.  
  
## <a name="creating-the-activex-control"></a>Tworzenie formantu ActiveX  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]automatycznie generuje <xref:System.Windows.Forms.AxHost> klasy otoki dla [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] kontroli, gdy formant został dodany do powierzchni projektu. Poniższa procedura dotyczy tworzenia zarządzanego zestawu o nazwie AxInterop.WMPLib.dll.  
  
#### <a name="to-create-the-activex-control"></a>Można utworzyć formantu ActiveX  
  
1.  Otwórz WmpAxControl.vb lub WmpAxControl.cs w narzędziu Projektant dla formularzy systemu Windows.  
  
2.  Z **przybornika**, Dodaj formant programu Windows Media Player na powierzchnię projektu.  
  
3.  W oknie właściwości ustaw wartość formantu programu Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.  
  
4.  Tworzenie projektu biblioteki WmpAxLib formantu.  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hostowanie kontrolki ActiveX na stronie WPF  
  
#### <a name="to-host-the-activex-control"></a>Do hostowania kontrolki ActiveX  
  
1.  W projekcie HostingAxInWpf Dodaj odwołanie do wygenerowanego [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] współdziałanie zestawu.  
  
     Ten zestaw o nazwie AxInterop.WMPLib.dll i został dodany do folderu debugowania projektu WmpAxLib po zaimportowaniu formantu programu Windows Media Player.  
  
2.  Dodaj odwołanie do zestawu WindowsFormsIntegration, o nazwie WindowsFormsIntegration.dll.  
  
3.  Dodaj odwołanie do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zestawu o nazwie System.Windows.Forms.dll.  
  
4.  Otwórz MainWindow.xaml w Projektancie WPF.  
  
5.  Nazwa <xref:System.Windows.Controls.Grid> elementu `grid1`.  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  W widoku projektu lub XAML, wybierz <xref:System.Windows.Window> elementu.  
  
7.  Kliknij w oknie właściwości **zdarzenia** kartę.  
  
8.  Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.  
  
9. Wstaw następujący kod, aby obsłużyć <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.  
  
     Ten kod tworzy wystąpienie <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli i dodaje wystąpienie `AxWindowsMediaPlayer` formantu podrzędnej.  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Projektant WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
