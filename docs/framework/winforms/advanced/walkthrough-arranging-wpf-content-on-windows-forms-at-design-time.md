---
title: 'Wskazówki: rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 373a7f977a9dad59cd40fd29fdd39c8fc6996ad0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529305"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>Wskazówki: rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania
W tym przewodniku przedstawiono możliwości korzystania z funkcji układ formularzy systemu Windows, takich jak Zakotwiczanie i linie przyciągania, ułożyć kontrolki Windows Presentation Foundation (WPF).  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Tworzenie projektu.  
  
-   Tworzenie formantu WPF.  
  
-   Host formantów WPF w panelu układu.  
  
-   Linie przyciągania Użyj, aby były wyrównane formantów WPF.  
  
-   Zakotwiczenie i dokowanie formantów WPF.  
  
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
  
-   Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `ArrangeElementHost`.  
  
## <a name="creating-the-wpf-control"></a>Tworzenie formantu WPF  
 Po dodaniu formantu WPF do projektu można rozmieścić go w formularzu.  
  
#### <a name="to-create-wpf-controls"></a>Aby utworzyć formantów WPF  
  
1.  Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> do projektu. Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone. Aby uzyskać więcej informacji, zobacz [porady: Wybierz i Przenieś elementy na powierzchnię projektu](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.  
  
4.  Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości `Blue`.  
  
5.  Skompiluj projekt.  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>Hosting formantów WPF w panelu układu  
 Używając formantów WPF w panele układu w taki sam sposób, jak używać inne formanty formularzy systemu Windows.  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>Na hoście formantów WPF w panelu układu  
  
1.  Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.  
  
2.  W **przybornika**, przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> sterowania do formularza.  
  
3.  Na <xref:System.Windows.Forms.TableLayoutPanel> kontrolki panelu tagów inteligentnych, wybierz opcję **Usuń ostatni wiersz**.  
  
4.  Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontroli większych szerokości i wysokości.  
  
5.  W **przybornika**, kliknij dwukrotnie `UserControl1` można utworzyć wystąpienia `UserControl1` w komórce pierwszy <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
6.  W **przybornika**, kliknij dwukrotnie `UserControl1` Aby utworzyć inne wystąpienie w komórce drugi <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
7.  W **konspekt dokumentu** wybierz `tableLayoutPanel1`. Aby uzyskać więcej informacji, zobacz [okno konspektu dokumentu](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).  
  
8.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwości `10, 10, 10, 10`.  
  
     Zarówno <xref:System.Windows.Forms.Integration.ElementHost> formanty są dopasowane do do nowego układu.  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>Aby wyrównać formantów WPF za pomocą linii przyciągania  
 Linie przyciągania umożliwiają łatwe wyrównanie kontrolek w formularzu. Linie przyciągania umożliwia wyrównywanie Twoich formantów WPF. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów na formularzach systemu Windows przy użyciu linie przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>Na potrzeby Dopasuj WPF linie przyciągania kontrolki  
  
1.  Z **przybornika**, przeciągnij wystąpienia `UserControl1` na formularz i umieść go w obszarze poniżej <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost3`.  
  
2.  Za pomocą linii przyciągania, wyrównanie do lewej krawędzi `elementHost3` lewej krawędzi <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
3.  Za pomocą linii przyciągania, rozmiar `elementHost3` do tej samej szerokości jako <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
4.  Przenieś `elementHost3` kierunku <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — center pojawi się między formantami.  
  
5.  W **właściwości** okna, ustaw wartość właściwości margines `20, 20, 20, 20`.  
  
6.  Przenieś `elementHost3` od <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — center pojawi się ponownie. Snapline — center wskazuje teraz margines 20.  
  
7.  Przenieś `elementHost3` z prawej strony, do momentu jego lewej krawędzi jest wyrównywany do lewej krawędzi `elementHost1`.  
  
8.  Zmień szerokość `elementHost3` do momentu jego prawej krawędzi wyrównuje do prawej krawędzi `elementHost2`.  
  
## <a name="anchoring-and-docking-wpf-controls"></a>Zakotwiczanie i dokowanie formantów WPF  
 Formant WPF hostowanych na formularzu ma tej samej Zakotwiczanie i dokowanie zachowanie jako inne formanty formularzy systemu Windows.  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>Aby zakotwiczenie i dokowanie formantów WPF  
  
1.  Wybierz `elementHost1`.  
  
2.  W **właściwości** ustaw <xref:System.Windows.Forms.Control.Anchor%2A> właściwości **górnej i dolnej lewe, prawe**.  
  
3.  Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> większy rozmiar formantu.  
  
     `elementHost1` Kontrolować zmienia rozmiar do wypełnienia komórki.  
  
4.  Wybierz `elementHost2`.  
  
5.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost2` Kontrolować zmienia rozmiar do wypełnienia komórki.  
  
6.  Wybierz <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
7.  Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Top>.  
  
8.  Wybierz `elementHost3`.  
  
9. Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost3` Kontrolować zmienia rozmiar w celu wypełnienia pozostałego miejsca na formularzu.  
  
10. Zmień rozmiar formularza.  
  
     Wszystkie trzy <xref:System.Windows.Forms.Integration.ElementHost> odpowiednio zmienić rozmiar kontrolki.  
  
     Aby uzyskać więcej informacji, zobacz [porady: zakotwiczenie i formantów podrzędnych Dock w formancie TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Korzystanie z kontrolek WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
