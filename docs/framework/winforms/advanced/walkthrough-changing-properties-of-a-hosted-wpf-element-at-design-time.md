---
title: 'Wskazówki: zmienianie właściwości hostowanego elementu WPF w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
ms.openlocfilehash: 15cab9266af5840aa4b37a62b71bd5010b7a859a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741023"
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a>Wskazówki: zmienianie właściwości hostowanego elementu WPF w czasie projektowania
W tym instruktażu dowiesz się, jak zmienić wartości właściwości kontrolki Windows Presentation Foundation (WPF), hostowana w formularzu Windows.  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Utwórz projekt.  
  
-   Tworzenie formantu WPF.  
  
-   Hostowanie kontrolki WPF w formularzu Windows.  
  
-   Za pomocą projektanta WPF dla programu Visual Studio w celu zmiany wartości właściwości.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu Windows Forms.  
  
> [!NOTE]
>  Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `WpfHost`.  
  
## <a name="creating-the-wpf-control"></a>Tworzenie kontrolki WPF  
 Po dodaniu kontrolki WPF do projektu, można rozmieścić je na formularzu.  
  
#### <a name="to-create-wpf-controls"></a>Aby utworzyć formanty WPF  
  
1.  Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> do projektu. Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwość `Blue`.  
  
3.  Skompiluj projekt.  
  
## <a name="changing-property-values-on-the-wpf-control"></a>Zmiana wartości właściwości kontrolki WPF  
 <xref:System.Windows.Forms.Integration.ElementHost> Tagu inteligentnego ułatwia zmienianie właściwości hostowanego WPF zawartości przy użyciu projektanta WPF.  
  
#### <a name="to-host-a-wpf-control"></a>Do hostowania kontrolki WPF  
  
1.  Otwórz `Form1` w programie Windows Forms Designer.  
  
2.  W **przybornika**w **kontrolek użytkownika WPF** kartę, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w formularzu.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
3.  W **zadania ElementHost** panelu tagi inteligentne, wybierz opcję **Edytuj hostowana zawartość**.  
  
     UserControl1.xaml zostanie otwarty w Projektancie WPF.  
  
4.  W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwość `Red`.  
  
5.  Skompiluj ponownie projekt.  
  
6.  Otwórz `Form1` w programie Windows Forms Designer.  
  
     Wystąpienie `UserControl1` czerwony tłem.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Korzystanie z kontrolek WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
