---
title: 'Instrukcje: ukrywanie kontrolki ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: 64c0f093063357c1e8db5933c035cc8295ad4f1e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623041"
---
# <a name="how-to-hide-toolstripmenuitems"></a>Instrukcje: ukrywanie kontrolki ToolStripMenuItems
Ukrywanie elementów menu jest możliwość sterowania interfejsem użytkownika aplikacji i ograniczyć polecenia użytkownika. Często chcesz ukryć całe menu, gdy wszystkie elementy menu na nim są niedostępne. Przedstawia informacje o przeszkadzał dla użytkownika. Ponadto warto ukryć i Wyłącz menu lub elementu menu, jak samodzielnie ukrywanie nie uniemożliwia użytkownikowi dostęp do poleceń menu przy użyciu klawisza skrótu.  
  
### <a name="to-hide-any-menu-item-programmatically"></a>Aby ukryć programowo dowolny element menu  
  
- W metodzie można ustawić właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość `false`.  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
- [Instrukcje: Wyłączanie kontrolki ToolStripMenuItems](how-to-disable-toolstripmenuitems.md)
