---
title: "Wskazówki: tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7731456cfcf35cd16b1df304fee4f4c138db84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a>Wskazówki: tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania
W tym temacie przedstawiono sposób tworzenia formantu Windows Presentation Foundation (WPF) do użycia w aplikacjach opartych na formularzach systemu Windows.  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Tworzenie projektu.  
  
-   Utwórz nową kontrolkę WPF.  
  
-   Dodaj nowy formant WPF do formularza systemu Windows. Formant WPF znajduje się w <xref:System.Windows.Forms.Integration.ElementHost> formantu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].,  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.  
  
> [!NOTE]
>  Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `HostingWpf`.  
  
## <a name="creating-a-new-wpf-control"></a>Tworzenie nowego formantu WPF  
 Tworzenie nowego formantu WPF i dodanie go do projektu jest tak proste, jak dodać innego elementu do projektu. Projektant formularzy systemu Windows współdziała z określonego rodzaju formantu o nazwie *formantu złożonego*, lub *kontrolki użytkownika*. Aby uzyskać więcej informacji na temat formanty użytkownika WPF, zobacz <xref:System.Windows.Controls.UserControl>.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> Wpisz WPF różni się od typu formantu użytkownika udostępniane przez formularze systemu Windows o nazwie <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.  
  
#### <a name="to-create-a-new-wpf-control"></a>Aby utworzyć nową kontrolkę WPF  
  
1.  W **Eksploratora rozwiązań**, Dodaj nową **Biblioteka kontrolek użytkownika WPF** projektu do rozwiązania. Użyj nazwy domyślnej biblioteki formantu `WpfControlLibrary1`. Domyślna nazwa formantu to `UserControl1.xaml`.  
  
     Dodawanie nowego formantu ma następujące skutki.  
  
    -   Dodawany jest UserControl1.xaml pliku.  
  
    -   Plik UserControl1.xaml.cs lub UserControl1.xaml.vb jest dodawany. Ten plik zawiera kodem obsługi zdarzeń i innych implementacji.  
  
    -   Odwołania do zestawów WPF zostaną dodane.  
  
    -   Otworzy się w pliku UserControl1.xaml [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].  
  
2.  W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone. Aby uzyskać więcej informacji, zobacz [porady: Wybierz i Przenieś elementy na powierzchnię projektu](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.  
  
4.  Z **przybornika**, przeciągnij <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> sterowania na powierzchnię projektu.  
  
5.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanego zawartości**.  
  
    > [!NOTE]
    >  Ogólnie rzecz biorąc należy udostępnić dokładniejsze zawartości WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontroli jest tu używany wyłącznie w celach ilustracyjnych.  
  
6.  Skompiluj projekt.  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a>Dodawanie formantu WPF do formularza systemu Windows  
 Nowego formantu WPF jest gotowy do użycia w formularzu. Formularze systemu Windows używa <xref:System.Windows.Forms.Integration.ElementHost> formantu do hosta zawartości WPF  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a>Aby dodać kontrolkę WPF do formularza systemu Windows  
  
1.  Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.  
  
2.  W **przybornika**, Znajdź kartę **formanty użytkownika WPF WPFUserControlLibrary**.  
  
3.  Przeciągnij wystąpienia `UserControl1` na formularzu.  
  
    -   <xref:System.Windows.Forms.Integration.ElementHost> Kontroli jest tworzony automatycznie w formularzu kontrolki WPF hosta.  
  
    -   <xref:System.Windows.Forms.Integration.ElementHost> Nosi nazwę formantu `elementHost1` i w **właściwości** okna, można wyświetlić jego <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl1**.  
  
    -   Odwołania do zestawów WPF zostaną dodane do projektu.  
  
    -   `elementHost1` Formantem panelu tag inteligentny pokazujący dostępne opcje hostingu.  
  
4.  W **zadania ElementHost** panelu tagów inteligentnych, wybierz opcję **Zadokuj w kontenerze nadrzędnym**.  
  
5.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 Formularze systemu Windows i WPF są różnych technologii, ale są one przeznaczone do ściśle współpracować. Aby zapewnić bardziej rozbudowane wygląd i zachowanie w aplikacji, należy spróbować wykonać następujące czynności.  
  
-   Hostowanie kontrolki formularza systemu Windows, na stronie programu WPF. Aby uzyskać więcej informacji, zobacz [wskazówki: hostowanie kontrolki formularza systemu Windows na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).  
  
-   Style wizualne formularzy systemu Windows stosowane do zawartości WPF. Aby uzyskać więcej informacji, zobacz [porady: Włączanie style wizualne w aplikacji hybrydowych](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
-   Zmienianie stylu zawartości WPF. Aby uzyskać więcej informacji, zobacz [wskazówki: nadawanie stylu zawartości WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Korzystanie z kontrolek WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Projektant WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
