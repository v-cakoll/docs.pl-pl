---
title: 'Instrukcje: Ustawianie tła panelu formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: be0359e13bcab868374189c6b42df392327b8eb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645075"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Instrukcje: Ustawianie tła panelu formularzy Windows przy użyciu narzędzia Projektant
Formularze Windows <xref:System.Windows.Forms.Panel> formant może wyświetlić kolor tła i obraz tła. <xref:System.Windows.Forms.Control.BackColor%2A> Właściwość ustawia kolor tła kontrolki, które są zawarte w panelu, takich jak etykiety i przycisków radiowych. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie ustawiono właściwości <xref:System.Windows.Forms.Control.BackColor%2A> wypełni wszystkie panelu wyboru. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obraz, który pojawi się za zaporą formantów, które są zawarte w panelu.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą formularza, który zawiera <xref:System.Windows.Forms.Panel> kontroli. Aby dowiedzieć się, jak skonfigurować taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [jak: Dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Aby ustawić tło w programie Windows Forms Designer  
  
1.  Wybierz <xref:System.Windows.Forms.Panel> kontroli.  
  
2.  W **właściwości** , kliknij strzałkę znajdujący się obok <xref:System.Windows.Forms.Control.BackColor%2A> właściwość, aby wyświetlić okno z trzema kartami.  
  
3.  Wybierz **niestandardowe** kartę, aby wyświetlić paletę kolorów.  
  
4.  Wybierz **Web** lub **systemu** kartę, aby wyświetlić listę nazw wstępnie zdefiniowanych kolorów, a następnie wybierz kolor.  
  
5.  W **właściwości** , kliknij strzałkę znajdujący się obok <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości.  
  
6.  W **Otwórz** oknie dialogowym Wybierz plik który chcesz wyświetlić.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel, kontrolka](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [Panel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [Instrukcje: Grupowanie formantów z formantem panelu formularzy Windows przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
