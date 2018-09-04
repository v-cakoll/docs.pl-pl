---
title: 'Porady: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: f97c622719c0f76fe8ce7ea34b9324110508b6e9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523297"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Porady: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant
Można ograniczyć lub rozszerzenia poleceń, które użytkownik może wprowadzić, włączanie i wyłączanie elementów menu w odpowiedzi na działania użytkownika. Elementy menu są włączone domyślnie, gdy są one tworzone, ale to może być regulowany poprzez <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości. Tę właściwość można manipulować w czasie projektowania w **właściwości** okna lub ustawiając je programowo w kodzie. Aby uzyskać więcej informacji, zobacz [porady: wyłączanie kontrolki ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>Aby wyłączyć element menu w czasie projektowania  
  
1.  W menu elementu wybranego w formularzu, ustawiać <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość `false`.  
  
    > [!TIP]
    >  Wyłączanie elementu menu pierwszy lub najwyższego poziomu w menu powoduje wyłączenie wszystkich elementów menu zawartych w menu. Podobnie wyłączenie element menu, który zawiera elementy podmenu powoduje wyłączenie elementów podmenu. Jeśli wszystkie polecenia w danym menu są dostępne dla użytkownika, uważa się dobrą praktyką programowania, aby ukryć i wyłączyć całe menu, jak to stanowi interfejs użytkownika czyste. Należy zarówno ukryć i Wyłącz menu, zgodnie z ukrywanie samodzielnie nie uniemożliwia dostępu do polecenia menu za pomocą klawisza skrótu. Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwości elementu menu najwyższego poziomu do `false` ukryć całe menu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Instrukcje: ukrywanie kontrolki ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
