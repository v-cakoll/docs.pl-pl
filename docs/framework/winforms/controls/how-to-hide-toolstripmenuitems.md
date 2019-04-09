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
ms.openlocfilehash: dc9daa945f2a546548f2cc6ea033378bd9ceff93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127429"
---
# <a name="how-to-hide-toolstripmenuitems"></a>Instrukcje: ukrywanie kontrolki ToolStripMenuItems
Ukrywanie elementów menu jest możliwość sterowania interfejsem użytkownika aplikacji i ograniczyć polecenia użytkownika. Często chcesz ukryć całe menu, gdy wszystkie elementy menu na nim są niedostępne. Przedstawia informacje o przeszkadzał dla użytkownika. Ponadto warto ukryć i Wyłącz menu lub elementu menu, jak samodzielnie ukrywanie nie uniemożliwia użytkownikowi dostęp do poleceń menu przy użyciu klawisza skrótu.  
  
### <a name="to-hide-any-menu-item-programmatically"></a>Aby ukryć programowo dowolny element menu  
  
-   W metodzie można ustawić właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość `false`.  
  
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
- [Instrukcje: wyłączanie ToolStripMenuItems](how-to-disable-toolstripmenuitems.md)
