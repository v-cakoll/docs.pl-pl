---
title: 'Porady: dodawanie przycisków do formantu ToolBar przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: b96f112c83d2296356e3eb566a24315bcefeff1f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563748"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Porady: dodawanie przycisków do formantu ToolBar przy użyciu narzędzia Projektant
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
 Integralną częścią <xref:System.Windows.Forms.ToolBar> formant jest przyciski, Dodaj do niej. Mogą one być używane do zapewniają łatwy dostęp do poleceń menu lub też mogą być umieszczane w innym obszarze interfejsu użytkownika aplikacji do udostępnienia poleceń dla użytkowników, które nie są dostępne w strukturze menu.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.ToolBar> kontroli. Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-buttons-at-design-time"></a>Aby dodać przyciski w czasie projektowania  
  
1.  Wybierz <xref:System.Windows.Forms.ToolBar> kontroli.  
  
2.  W **właściwości** okna, kliknij przycisk <xref:System.Windows.Forms.ToolBar.Buttons%2A> właściwość, aby go zaznaczyć, a następnie kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) przycisk, aby otworzyć **ToolBarButton — Edytor kolekcji**.  
  
3.  Użyj **Dodaj** i **Usuń** przycisków, aby dodawać i usuwać przycisków z <xref:System.Windows.Forms.ToolBar> kontroli.  
  
4.  Konfigurowanie właściwości poszczególnych przycisków w **właściwości** okna, w którym jest wyświetlana w okienku po prawej stronie edytora. W poniższej tabeli przedstawiono niektóre ważne właściwości do uwzględnienia.  
  
    |Właściwość|Opis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Określa menu, które mają być wyświetlane w przycisk na pasku narzędzi listy rozwijanej. Przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> właściwość musi być równa <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>. Ta właściwość przyjmuje wystąpienie klasy <xref:System.Windows.Forms.ContextMenu> klasy jako odwołanie.|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Określa, czy częściowo wypchnięciach Przełącz styl przycisku paska narzędzi. Przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> właściwość musi być równa <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Określa, czy Przełącz styl przycisku paska narzędzi jest obecnie w stanie wypchnięcia. Przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> właściwość musi być równa <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> lub <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Ustawia styl przycisku paska narzędzi. Musi mieć jedną z wartości w <xref:System.Windows.Forms.ToolBarButtonStyle> wyliczenia.|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Ciąg tekstowy wyświetlany przez przycisk.|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Tekst, który jest wyświetlany jako etykietka narzędzia dla przycisku.|  
  
5.  Kliknij przycisk **OK** aby zamknąć okno dialogowe i utworzyć panele określony.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolBar>  
 [Instrukcje: określanie ikony dla przycisku kontrolki ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [ToolBar, kontrolka](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
