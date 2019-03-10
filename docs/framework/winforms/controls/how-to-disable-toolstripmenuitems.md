---
title: 'Instrukcje: Wyłączanie kontrolki ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: 3c18935239a4355d5416a0a79d0fa9f5c504cc7e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720217"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Instrukcje: Wyłączanie kontrolki ToolStripMenuItems
Można ograniczyć lub rozszerzenia poleceń, które użytkownik może wprowadzić, włączanie i wyłączanie elementów menu w odpowiedzi na działania użytkownika. Elementy menu są włączone domyślnie, gdy są one tworzone, ale to może być regulowany poprzez <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości. Tę właściwość można manipulować w czasie projektowania w **właściwości** okna lub ustawiając je programowo w kodzie.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Aby programowo wyłączyć element menu  
  
-   W metodzie można ustawić właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość `false`.  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  Wyłączanie elementu menu pierwszy lub najwyższego poziomu w menu powoduje ukrycie wszystkich elementów menu zawartych w menu, ale nie je wyłączyć. Podobnie wyłączenie element menu, który zawiera elementy podmenu ukrywa elementy podmenu, ale nie je wyłączyć. Jeśli wszystkie polecenia w danym menu są dostępne dla użytkownika, uważa się dobrą praktyką programowania, aby ukryć i wyłączyć całe menu, jak to stanowi interfejs użytkownika czyste. Należy ukrywać i Wyłącz menu i wyłączyć każdego elementu i elementu podmenu w menu, ponieważ ukrycie samodzielnie nie uniemożliwia dostęp do polecenia menu za pomocą klawisza skrótu. Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwości elementu menu najwyższego poziomu do `false` ukryć całe menu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Instrukcje: Ukrywanie kontrolki ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
