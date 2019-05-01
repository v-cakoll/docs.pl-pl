---
title: 'Instrukcje: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 9965825458afcd50b29699c3b89ed506078e04d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954248"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Instrukcje: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant
Można ograniczyć lub rozszerzenia poleceń, które użytkownik może wprowadzić, włączanie i wyłączanie elementów menu w odpowiedzi na działania użytkownika. Elementy menu są włączone domyślnie, gdy są one tworzone, ale to może być regulowany poprzez <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości. Tę właściwość można manipulować w czasie projektowania w **właściwości** okna lub ustawiając je programowo w kodzie. Aby uzyskać więcej informacji, zobacz [jak: Wyłączanie kontrolki ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>Aby wyłączyć element menu w czasie projektowania  
  
1. W menu elementu wybranego w formularzu, ustawiać <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość `false`.  
  
    > [!TIP]
    >  Wyłączanie elementu menu pierwszy lub najwyższego poziomu w menu powoduje wyłączenie wszystkich elementów menu zawartych w menu. Podobnie wyłączenie element menu, który zawiera elementy podmenu powoduje wyłączenie elementów podmenu. Jeśli wszystkie polecenia w danym menu są dostępne dla użytkownika, uważa się dobrą praktyką programowania, aby ukryć i wyłączyć całe menu, jak to stanowi interfejs użytkownika czyste. Należy zarówno ukryć i Wyłącz menu, zgodnie z ukrywanie samodzielnie nie uniemożliwia dostępu do polecenia menu za pomocą klawisza skrótu. Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwości elementu menu najwyższego poziomu do `false` ukryć całe menu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Instrukcje: Ukrywanie kontrolki ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
