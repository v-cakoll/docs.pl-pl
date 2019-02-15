---
title: 'Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 6343000b5060c3b1e98e68b1aa7e84bfb3e817b7
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303399"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows przy użyciu narzędzia Projektant
Proces dodawania elementu do formularzy Windows <xref:System.Windows.Forms.ListView> kontroli składa się przede wszystkim określenie elementu i przypisywanie właściwości do niego. Dodawanie lub usuwanie pozycji listy może odbywać się w dowolnym momencie.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.ListView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>Aby dodać lub usunąć elementy przy użyciu narzędzia Projektant  
  
1.  Wybierz <xref:System.Windows.Forms.ListView> kontroli.  
  
2.  W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Items%2A> właściwości.  
  
     **ListViewItem — Edytor kolekcji** pojawia się.  
  
3.  Aby dodać element, kliknij przycisk **Dodaj** przycisku. Następnie można ustawić właściwości nowego elementu, takie jak <xref:System.Windows.Forms.ListView.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.  
  
4.  Aby usunąć element, wybierz ją, a następnie kliknij przycisk **Usuń** przycisku.  
  
## <a name="see-also"></a>Zobacz także
- [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie ikon dla kontrolki ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Instrukcje: Grupowanie elementów w formancie ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
