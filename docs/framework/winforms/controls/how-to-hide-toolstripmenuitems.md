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
ms.workload: dotnet
ms.openlocfilehash: 6f5491cfbfc312b2ce3e35170ddc4edc8ee39a61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 [MenuStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [Instrukcje: wyłączanie kontrolki ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
