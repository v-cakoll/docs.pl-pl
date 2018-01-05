---
title: "Porady: wyłączanie ToolStripMenuItems"
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
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0432c59979f8f595b481154f5b339e448ee66b06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-toolstripmenuitems"></a>Porady: wyłączanie ToolStripMenuItems
Można ograniczyć lub rozszerzyć poleceń, które mogą spowodować, że użytkownik, włączanie i wyłączanie elementów menu w odpowiedzi na działania użytkownika. Elementy menu są włączone domyślnie, gdy są one tworzone, ale to można dostosować za pomocą <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości. Tej właściwości można manipulować w czasie projektowania w **właściwości** okna lub programowo przez ustawienie dla niego w kodzie.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Aby wyłączyć programowo elementu menu.  
  
-   W metodzie można ustawić właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości `false`.  
  
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
    >  Wyłączenie elementu menu pierwszy lub najwyższego poziomu w menu powoduje ukrycie wszystkich elementów menu zawartych w menu, ale nie je wyłączyć. Podobnie wyłączenie elementu menu, który zawiera elementy podmenu ukrywa elementy podmenu, ale nie je wyłączyć. Jeśli wszystkie polecenia w danym menu są niedostępne dla użytkownika, jest uznawany dobrze programowania zarówno Ukryj i Wyłącz całe menu, za stwarza czystą interfejs. Należy Ukryj i Wyłącz menu i wyłączyć każdego elementu, a element podmenu w menu, ponieważ ukrywanie samodzielnie nie uniemożliwia dostępu do polecenia menu za pomocą klawisza skrótu. Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość element menu najwyższego poziomu do `false` ukrycia całego menu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Instrukcje: ukrywanie kontrolki ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
