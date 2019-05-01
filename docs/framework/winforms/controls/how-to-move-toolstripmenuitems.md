---
title: 'Instrukcje: przenoszenie ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: 2203511e91254c270c59b5d298dd87a5b3737109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913630"
---
# <a name="how-to-move-toolstripmenuitems"></a>Instrukcje: przenoszenie ToolStripMenuItems
W czasie projektowania, można przenieść cały menu najwyższego poziomu i ich elementów menu w inne miejsce na <xref:System.Windows.Forms.MenuStrip>. Możesz również przenieść elementy menu poszczególnych między menu najwyższego poziomu lub zmiana położenia elementów menu w menu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Aby przenieść jej elementy menu i menu najwyższego poziomu do innej lokalizacji najwyższego poziomu  
  
1. Kliknij i przytrzymaj naciśnięty przycisk myszy po lewej stronie, w menu, które chcesz przenieść.  
  
2. Przeciągnij kursor do menu najwyższego poziomu, które jest wcześniejsza niż zamierzony nowej lokalizacji, a następnie zwolnij przycisk myszy po lewej stronie.  
  
     Przenosi wybrane menu z prawej strony punktu wstawiania.  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Aby przenieść menu najwyższego poziomu i jego elementów menu w lokalizacji z listy rozwijanej  
  
1. Kliknij lewym przyciskiem myszy menu, który chcesz przenieść i naciśnij klawisze CTRL + X lub kliknij prawym przyciskiem myszy menu i wybierz **Wytnij** z menu skrótów.  
  
2. W menu najwyższego poziomu docelowego kliknij lewym przyciskiem myszy element menu powyżej zamierzony nowej lokalizacji naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu powyżej zamierzony nowej lokalizacji i wybierz pozycję **Wklej** z menu skrótów.  
  
     Menu, które można wyciąć dodaje się po wybranego elementu menu.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Aby przenieść element menu w menu przy użyciu edytora kolekcji elementów  
  
1. Kliknij prawym przyciskiem myszy menu, który zawiera element menu, który chcesz przenieść.  
  
2. Z menu skrótów wybierz polecenie **Edytuj vlastnost DropDownItems**.  
  
3. W **Edytor kolekcji elementów**, kliknij lewym przyciskiem myszy element menu, którą chcesz przenieść.  
  
4. Kliknij przycisk klawiszy strzałek w górę i w dół, aby przenieść element menu w menu.  
  
5. Kliknij przycisk **OK**.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Aby przenieść element menu w menu za pomocą klawiatury  
  
1. Naciśnij i przytrzymaj naciśnięty klawisz ALT.  
  
2. Kliknij i przytrzymaj lewym przyciskiem myszy element menu, który chcesz przenieść.  
  
3. Przeciągnij element menu do nowej lokalizacji, a następnie zwolnij przycisk myszy po lewej stronie.  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>Aby przenieść element menu do menu inny  
  
1. Kliknij lewym przyciskiem myszy element menu, który chcesz przenieść i naciśnij klawisze CTRL + X lub kliknij prawym przyciskiem myszy element menu i wybrać **Wytnij** z menu skrótów.  
  
2. Kliknij lewym przyciskiem myszy menu, który będzie zawierać element menu, który można wyciąć.  
  
3. Kliknij lewym przyciskiem myszy element menu, który jest wcześniejsza niż zamierzony nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu, który jest wcześniejsza niż zamierzony nową lokalizację i wybierz pozycję **Wklej** z menu skrótów.  
  
     Element menu, który można wyciąć dodaje się po wybranego elementu menu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
