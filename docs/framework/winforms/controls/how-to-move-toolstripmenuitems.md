---
title: 'Porady: przenoszenie ToolStripMenuItems'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc1cb718b3738ac93b284b0b438b08d1e721349
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-move-toolstripmenuitems"></a>Porady: przenoszenie ToolStripMenuItems
W czasie projektowania, można przenieść całej menu najwyższego poziomu i ich elementów menu w inne miejsce na <xref:System.Windows.Forms.MenuStrip>. Można również przenieść poszczególnych elementów menu między menu najwyższego poziomu lub zmienić jego położenie elementów menu w menu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Aby przenieść do innej lokalizacji najwyższego poziomu menu najwyższego poziomu i jego elementów menu  
  
1.  Kliknij i przytrzymaj lewy przycisk myszy w menu, które chcesz przenieść.  
  
2.  Przeciągnij punkt wstawiania do menu najwyższego poziomu, które jest przed zamierzone nowej lokalizacji i zwolnij lewego przycisku myszy.  
  
     Przenosi wybrane menu z prawej strony punktu wstawiania.  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Aby przenieść lokalizację z listy rozwijanej menu najwyższego poziomu i jej elementów menu  
  
1.  Lewym przyciskiem myszy menu, które chcesz przenieść i naciśnij klawisze CTRL + X, lub kliknij prawym przyciskiem myszy menu i wybierz **Wytnij** z menu skrótów.  
  
2.  W menu najwyższego poziomu docelowego lewym przyciskiem myszy element menu powyżej zamierzone nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu powyżej zamierzone nowej lokalizacji i wybierz **Wklej** z menu skrótów.  
  
     Menu Wycinanie są wstawiane po wybranego elementu menu.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Aby przenieść element menu w menu za pomocą edytora kolekcji elementy  
  
1.  Kliknij prawym przyciskiem myszy menu, które zawiera element menu, który chcesz przenieść.  
  
2.  Z menu skrótów wybierz **Edytuj elementy DropDownItems**.  
  
3.  W **edytora kolekcji elementy**, lewym przyciskiem myszy element menu, który chcesz przenieść.  
  
4.  Kliknij przycisk klawiszy strzałek w górę i w dół, można przenieść elementu menu w menu.  
  
5.  Kliknij przycisk **OK**.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Aby przenieść element menu w menu za pomocą klawiatury  
  
1.  Naciśnij i przytrzymaj klawisz ALT.  
  
2.  Kliknij i przytrzymaj lewym przyciskiem myszy element menu, który chcesz przenieść.  
  
3.  Przeciągnij element menu do nowej lokalizacji i zwolnij lewego przycisku myszy.  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>Aby przenieść element menu innym menu  
  
1.  Lewym przyciskiem myszy element menu, który chcesz przenieść i naciśnij klawisze CTRL + X, lub kliknij prawym przyciskiem myszy element menu i wybierz **Wytnij** z menu skrótów.  
  
2.  W lewym przyciskiem myszy menu, która będzie zawierać element menu, który Wycinanie.  
  
3.  Lewym przyciskiem myszy element menu, który jest przed zamierzone nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu, który jest przed zamierzone nowej lokalizacji, a następnie wybierz **Wklej** z menu skrótów.  
  
     Element menu, który Wycinanie są wstawiane po wybranego elementu menu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
