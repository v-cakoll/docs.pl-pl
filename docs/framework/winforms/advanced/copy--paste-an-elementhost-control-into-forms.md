---
title: 'Wskazówki: kopiowanie i wklejanie formantu ElementHost w oddzielnych formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 55b426fbe95bac269183a649ecd839175a8cbdda
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037256"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>Wskazówki: kopiowanie i wklejanie formantu ElementHost w oddzielnych formularzach systemu Windows
W tym instruktażu pokazano, jak kopiowanie kontrolki Windows Presentation Foundation (WPF) z jednego formularza Windows na inny.  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Utwórz projekt.  
  
-   Kopiowanie kontrolki WPF.  
  
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
  
-   Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `CopyElementHost`.  
  
## <a name="copying-a-wpf-control"></a>Kopiowanie kontrolki WPF  
 Po dodaniu kontrolki WPF do projektu, skopiuj go do innych formularzy w projekcie.  
  
#### <a name="to-copy-a-wpf-control"></a>Aby skopiować kontrolki WPF  
  
1.  Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania. Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Skompiluj projekt.  
  
3.  Otwórz `Form1` w programie Windows Forms Designer.  
  
4.  Z **przybornika**, przeciągnij wystąpienie `UserControl1` na formularz.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
5.  Za pomocą `elementHost1` zaznaczone, naciśnij klawisze CTRL + C, aby skopiować go do Schowka.  
  
6.  Dodaj nowy formularz Windows do projektu. Użyj domyślnej nazwy dla typu formularza `Form2`.  
  
7.  Za pomocą `Form2` Otwórz w programie Windows Forms Designer, naciśnij klawisze CTRL + V, aby wkleić kopię `elementHost1` na formularz.  
  
     Kontrolki skopiowane jest również określany `elementHost1`, ponieważ jest prywatny pola `Form2` klasy. Nie ma żadnych kolizji nazw za pomocą `elementHost1` w `Form1` klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Korzystanie z kontrolek WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
