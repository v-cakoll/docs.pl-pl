---
title: "Porady: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f704e99622900d8c37c8ddd5054a3c5ad920bc6b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Porady: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant
Można ograniczyć lub rozszerzyć poleceń, które mogą spowodować, że użytkownik, włączanie i wyłączanie elementów menu w odpowiedzi na działania użytkownika. Elementy menu są włączone domyślnie, gdy są one tworzone, ale to można dostosować za pomocą <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości. Tej właściwości można manipulować w czasie projektowania w **właściwości** okna lub programowo przez ustawienie dla niego w kodzie. Aby uzyskać więcej informacji, zobacz [porady: wyłączanie ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>Aby wyłączyć element menu w czasie projektowania  
  
1.  Z elementem menu wybranego w formularzu, należy ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości `false`.  
  
    > [!TIP]
    >  Wyłączenie elementu menu pierwszy lub najwyższego poziomu w menu powoduje wyłączenie wszystkich elementów menu zawartych w menu. Podobnie wyłączenie elementu menu, który zawiera elementy podmenu wyłącza elementów podmenu. Jeśli wszystkie polecenia w danym menu są niedostępne dla użytkownika, jest uznawany dobrze programowania zarówno Ukryj i Wyłącz całe menu, za stwarza czystą interfejs. Należy zarówno Ukryj i Wyłącz menu, jak ukrywanie wyłącznie nie uniemożliwia dostępu do polecenia menu za pomocą klawisza skrótu. Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość element menu najwyższego poziomu do `false` ukrycia całego menu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Instrukcje: ukrywanie kontrolki ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
