---
title: 'Wskazówki: zmienianie właściwości hostowanego elementu WPF w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
ms.openlocfilehash: d17273f52d0cef118b79fef03af72522f6677073
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a>Wskazówki: zmienianie właściwości hostowanego elementu WPF w czasie projektowania
W tym przewodniku przedstawiono sposób zmiany wartości właściwości kontrolki Windows Presentation Foundation (WPF) obsługiwanych na formularzu systemu Windows.  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Tworzenie projektu.  
  
-   Tworzenie formantu WPF.  
  
-   Host formantów WPF w formularzach systemu Windows.  
  
-   Aby zmienić wartości właściwości za pomocą projektanta WPF dla programu Visual Studio.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.  
  
> [!NOTE]
>  Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `WpfHost`.  
  
## <a name="creating-the-wpf-control"></a>Tworzenie formantu WPF  
 Po dodaniu formantu WPF do projektu można rozmieścić go w formularzu.  
  
#### <a name="to-create-wpf-controls"></a>Aby utworzyć formantów WPF  
  
1.  Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> do projektu. Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości `Blue`.  
  
3.  Skompiluj projekt.  
  
## <a name="changing-property-values-on-the-wpf-control"></a>Zmiana wartości właściwości w kontrolce WPF  
 <xref:System.Windows.Forms.Integration.ElementHost> Tagów inteligentnych można łatwo zmienić właściwości WPF hostowanej zawartości przy użyciu narzędzia Projektant WPF.  
  
#### <a name="to-host-a-wpf-control"></a>Do hostowania formantu WPF  
  
1.  Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.  
  
2.  W **przybornika**w **formanty użytkownika WPF** karcie, kliknij dwukrotnie `UserControl1` można utworzyć wystąpienia `UserControl1` w formularzu.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
3.  W **zadania ElementHost** panelu tagów inteligentnych, wybierz opcję **Edytuj hostowana zawartość**.  
  
     UserControl1.xaml zostanie otwarty w Projektancie WPF.  
  
4.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości `Red`.  
  
5.  Skompiluj ponownie projekt.  
  
6.  Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.  
  
     Wystąpienie `UserControl1` ma red tło.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Korzystanie z kontrolek WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
