---
title: 'Porady: ukrywanie formantu ToolStripMenuItems'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cb24fd36bdee76fa80a87d48f41b72f01c8f263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-toolstripmenuitems"></a>Porady: ukrywanie formantu ToolStripMenuItems
Ukrywanie elementów menu jest możliwość sterowania interfejsem użytkownika, aplikacji i ograniczyć poleceń użytkownika. Często chcesz ukryć całe menu, gdy wszystkich elementów menu na nim są niedostępne. Przedstawia informacje o tym przeszkadzał dla użytkownika. Ponadto możesz chcieć zarówno Ukryj i Wyłącz menu lub elementu menu, jak ukrywanie wyłącznie nie uniemożliwia użytkownikowi uzyskiwanie dostępu do polecenia menu za pomocą klawisza skrótu.  
  
### <a name="to-hide-any-menu-item-programmatically"></a>Aby programowo ukryć dowolny element menu  
  
-   W metodzie można ustawić właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwości `false`.  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [Informacje o formancie MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [Porady: wyłączanie ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
