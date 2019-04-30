---
title: 'Przewodnik: Rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 306c042fe432f0c087ceb1b5ff6b5aec0fe0bbc7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748255"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>Przewodnik: Rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania
W tym instruktażu przedstawiono sposób korzystania z funkcji układu formularzy Windows, takich jak Zakotwiczanie i linii przyciągania, aby rozmieścić formanty Windows Presentation Foundation (WPF).

 W tym przewodniku należy wykonać następujące zadania:

- Utwórz projekt.

- Tworzenie formantu WPF.

- Host formantów WPF w panelu układu.

- Linii przyciągania użycia do wyrównania kontrolek WPF.

- Zakotwiczenie i dokowanie kontrolek WPF.

> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
- Visual Studio 2012.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu Windows Forms.  
  
> [!NOTE]
>  Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
- Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `ArrangeElementHost`.  
  
## <a name="creating-the-wpf-control"></a>Tworzenie kontrolki WPF  
 Po dodaniu kontrolki WPF do projektu, można rozmieścić je na formularzu.  
  
#### <a name="to-create-wpf-controls"></a>Aby utworzyć formanty WPF  
  
1. Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> do projektu. Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2. W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Wybierz i Przesuń elementy na powierzchni projektowej](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).  
  
3. W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.  
  
4. Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwość `Blue`.  
  
5. Skompiluj projekt.  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>Hosting kontrolek WPF w panelu układu  
 Umożliwia kontrolek WPF w panele układów w taki sam sposób, jak używać innych kontrolek Windows Forms.  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>Host formantów WPF w panelu układu  
  
1. Otwórz `Form1` w programie Windows Forms Designer.  
  
2. W **przybornika**, przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> formant na formularzu.  
  
3. Na <xref:System.Windows.Forms.TableLayoutPanel> kontrolki panelu tagi inteligentne, wybierz **Usuń ostatni wiersz**.  
  
4. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki większych szerokość i wysokość.  
  
5. W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w pierwszej komórki z <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
6. W **przybornika**, kliknij dwukrotnie `UserControl1` Aby utworzyć inną instancję w drugiej komórce <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
7. W **konspekt dokumentu** wybierz `tableLayoutPanel1`. Aby uzyskać więcej informacji, zobacz [okno konspektu dokumentu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).  
  
8. W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwość `10, 10, 10, 10`.  
  
     Zarówno <xref:System.Windows.Forms.Integration.ElementHost> formanty są dopasowane do do nowego układu.  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>Aby wyrównać formanty WPF za pomocą linii przyciągania  
 Linii przyciągania umożliwiają łatwe wyrównanie kontrolek w formularzu. Za pomocą linii przyciągania do wyrównania Twoich kontrolek WPF. Aby uzyskać więcej informacji, zobacz [instruktażu: Rozmieszczanie formantów Windows Forms za pomocą linii przyciągania](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>Wyrównaj WPF za pomocą linii przyciągania kontrolki  
  
1. Z **przybornika**, przeciągnij wystąpienie `UserControl1` na formularz i umieść go w miejsce poniżej <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost3`.  
  
2. Za pomocą linii przyciągania, Wyrównaj do lewej krawędzi `elementHost3` lewej krawędzi <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
3. Za pomocą linii przyciągania, rozmiar `elementHost3` mają taką samą szerokość jako <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
4. Przenieś `elementHost3` kierunku <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — Centrum pojawi się między formantami.  
  
5. W **właściwości** okna, ustaw wartość właściwości marginesów `20, 20, 20, 20`.  
  
6. Przenieś `elementHost3` opuszczenie <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — Centrum pojawi się ponownie. Snapline — Centrum wskazuje teraz margines 20.  
  
7. Przenieś `elementHost3` z prawej strony, do momentu jego lewej krawędzi jest wyrównywany do lewej krawędzi `elementHost1`.  
  
8. Zmień szerokość `elementHost3` do momentu jego prawej krawędzi wyrównuje do prawej krawędzi `elementHost2`.  
  
## <a name="anchoring-and-docking-wpf-controls"></a>Zakotwiczanie i dokowanie kontrolek WPF  
 Kontrolki WPF w serwisie formularza ma, które ten sam Zakotwiczanie i dokowanie zachowanie, jak inne kontrolki Windows Forms.  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>Aby zakotwiczenie i dokowanie kontrolek WPF  
  
1. Wybierz `elementHost1`.  
  
2. W **właściwości** oknie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości **górnej, dolnej, lewe, prawe**.  
  
3. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki o większym rozmiarze.  
  
     `elementHost1` Kontrolować zmiany rozmiaru w celu wypełnienia komórki.  
  
4. Wybierz `elementHost2`.  
  
5. W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost2` Kontrolować zmiany rozmiaru w celu wypełnienia komórki.  
  
6. Wybierz <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
7. Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Top>.  
  
8. Wybierz `elementHost3`.  
  
9. Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost3` Kontrolować zmiany rozmiaru w celu wypełnienia pozostałego miejsca w formularzu.  
  
10. Zmień rozmiar formularza.  
  
     Wszystkie trzy <xref:System.Windows.Forms.Integration.ElementHost> odpowiednio zmień rozmiar kontrolki.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Instrukcje: Wyrównywanie formantu z krawędziami formularzy w czasie projektowania](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
