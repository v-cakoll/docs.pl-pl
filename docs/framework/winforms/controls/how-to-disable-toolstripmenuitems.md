---
title: 'Instrukcje: wyłączanie ToolStripMenuItems'
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
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046225"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Instrukcje: wyłączanie ToolStripMenuItems
Można ograniczyć lub rozszerzyć polecenia, które użytkownik może wprowadzić, włączając i wyłączając elementy menu w odpowiedzi na działania użytkownika. Elementy menu są domyślnie włączone, gdy są tworzone, ale można je dostosować za pomocą <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości. Tę właściwość można manipulować w czasie projektowania w oknie **Właściwości** lub programowo przez ustawienie jej w kodzie.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Aby programowo wyłączyć element menu  
  
- W metodzie, w której ustawiasz właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> `false`właściwość.  
  
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
    > Wyłączenie elementu menu pierwszy lub najwyższego poziomu w menu powoduje ukrycie wszystkich elementów menu zawartych w menu, ale nie powoduje ich wyłączenia. Analogicznie, wyłączenie elementu menu zawierającego elementy podmenu powoduje ukrycie elementów podmenu, ale nie powoduje ich wyłączenia. Jeśli wszystkie polecenia w danym menu są niedostępne dla użytkownika, jest on uznawany za dobry sposób programowania, aby ukryć i wyłączyć całe menu, ponieważ prezentuje to czysty interfejs użytkownika. Należy ukryć i wyłączyć menu, a następnie wyłączyć każdy element i podmenu w menu, ponieważ ukrywanie samo nie uniemożliwia dostępu do polecenia menu za pośrednictwem klawisza skrótu. Ustaw właściwość elementu menu najwyższego poziomu, aby `false` ukryć całe menu. <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Instrukcje: Ukryj kontrolki ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
