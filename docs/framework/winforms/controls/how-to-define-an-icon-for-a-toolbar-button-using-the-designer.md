---
title: 'Porady: określanie ikony dla przycisku ToolBar przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: f26e21d824420fc4ff0480de21f260309c5c2e11
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456723"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Porady: określanie ikony dla przycisku ToolBar przy użyciu narzędzia Projektant
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
 <xref:System.Windows.Forms.ToolBar> przyciski będą mogli wyświetlać ikony w ich obrębie, ułatwiający identyfikację przez użytkowników. Jest to realizowane poprzez dodawanie obrazów do <xref:System.Windows.Forms.ImageList> składnika i kojarząc ją z <xref:System.Windows.Forms.ToolBar> kontroli.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.ToolBar> kontroli i <xref:System.Windows.Forms.ImageList> składnika. Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Aby ustawić ikony dla przycisku kontrolki toolbar w czasie projektowania  
  
1.  Dodawanie obrazów do <xref:System.Windows.Forms.ImageList> składnika. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2.  Wybierz <xref:System.Windows.Forms.ToolBar> kontrolkę w formularzu.  
  
3.  W **właściwości** oknie <xref:System.Windows.Forms.ToolBar> kontrolki <xref:System.Windows.Forms.ToolBar.ImageList%2A> właściwość <xref:System.Windows.Forms.ImageList> składnika.  
  
4.  Kliknij przycisk <xref:System.Windows.Forms.ToolBar> kontrolki <xref:System.Windows.Forms.ToolBar.Buttons%2A> właściwość, aby go zaznaczyć, a następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **ToolBarButton — Edytor kolekcji**.  
  
5.  Użyj **Dodaj** przycisk, aby dodać przyciski do <xref:System.Windows.Forms.ToolBar> kontroli.  
  
6.  W **właściwości** wyświetlone w okienku po prawej stronie okno **ToolBarButton — Edytor kolekcji**ustaw <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> właściwości przycisku paska narzędzi na jedną z wartości na liście, który jest rysowana od obrazy dodane do <xref:System.Windows.Forms.ImageList> składnika.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolBar>  
 [Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar, kontrolka](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [ImageList, składnik](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
