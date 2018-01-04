---
title: "Wskazówki: Hosting złożonego formantu 3D WPF w Windows Forms"
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
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2b64cacea48bbc8855cdb9ce451a13d4ad729bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Wskazówki: Hosting złożonego formantu 3D WPF w Windows Forms
W tym przewodniku przedstawiono sposób tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego kontroli i udostępnić go w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów i formularzy przy użyciu <xref:System.Windows.Forms.Integration.ElementHost> formantu.  
  
 W tym przewodniku zostaną zaimplementowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> zawiera dwa formantów podrzędnych. <xref:System.Windows.Controls.UserControl> Wyświetla trójwymiarowy stożkowy (3-). Renderowanie 3-obiektów jest znacznie łatwiejsze w przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niż z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. W związku z tym warto hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> klasy w celu utworzenia grafiki 3-w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.  
  
-   Tworzenie projektu hosta formularzy systemu Windows.  
  
-   Hosting [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.  
  
 Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [Hosting 3-formantu złożonego WPF w przykładowym formularzy systemu Windows](http://go.microsoft.com/fwlink/?LinkID=160001).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].,  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a>Tworzenie kontrolki użytkownika  
  
#### <a name="to-create-the-usercontrol"></a>Można utworzyć elementu UserControl  
  
1.  Tworzenie projektu Biblioteka formantów WPF użytkownika o nazwie `HostingWpfUserControlInWf`.  
  
2.  Otwórz UserControl1.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
3.  Zastąp następujący kod wygenerowany kod.  
  
     Ten kod definiuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> zawiera dwa formantów podrzędnych. Pierwszy formant podrzędny ma <xref:System.Windows.Controls.Label?displayProperty=nameWithType> formantu; druga jest <xref:System.Windows.Controls.Viewport3D> kontrolkę wyświetlającą stożkowy 3-w.  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a>Tworzenie projektu hosta formularzy systemu Windows  
  
#### <a name="to-create-the-host-project"></a>Aby utworzyć projekt z hosta  
  
1.  Dodaj projekt aplikacji systemu Windows o nazwie `WpfUserControlHost` do rozwiązania. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  W Eksploratorze rozwiązań Dodaj odwołanie do zestawu WindowsFormsIntegration, o nazwie WindowsFormsIntegration.dll.  
  
3.  Dodaj odwołania do następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów:  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
4.  Dodaj odwołanie do `HostingWpfUserControlInWf` projektu.  
  
5.  W Eksploratorze rozwiązań, ustaw `WpfUserControlHost` projekt jako projekt startowy.  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a>Hosting kontrolki systemu Windows Presentation Foundation użytkownika  
  
#### <a name="to-host-the-usercontrol"></a>Na hoście UserControl  
  
1.  W narzędziu Projektant dla formularzy systemu Windows otwórz Form1.  
  
2.  Kliknij w oknie właściwości **zdarzenia**, a następnie kliknij dwukrotnie <xref:System.Windows.Forms.Form.Load> zdarzeń, aby utworzyć program obsługi zdarzeń.  
  
     Otwiera edytora kodu do nowo utworzonego `Form1_Load` obsługi zdarzeń.  
  
3.  Zastąp kod w pliku Form1.cs następującym kodem.  
  
     `Form1_Load` Obsługi zdarzeń tworzy wystąpienie `UserControl1` i dodaje je <xref:System.Windows.Forms.Integration.ElementHost> kolekcja formantów podrzędnych formantu. <xref:System.Windows.Forms.Integration.ElementHost> Formant został dodany do formularza kolekcja formantów podrzędnych.  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Projektant WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Hostowanie formantu złożonego WPF w przykładowym formularzy systemu Windows](http://go.microsoft.com/fwlink/?LinkID=160001)
