---
title: 'Porady: konfigurowanie automatycznego scalania menu dla aplikacji MDI'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e99aed38ed6c3af3424c264631f0eaf27e46af7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a>Porady: konfigurowanie automatycznego scalania menu dla aplikacji MDI
Poniższa procedura zawiera podstawowe kroki konfigurowania automatycznego scalania w aplikacji interfejsu wielu dokumentów (MDI) z <xref:System.Windows.Forms.MenuStrip>.  
  
### <a name="to-set-up-automatic-menu-merging"></a>Aby skonfigurować automatycznego scalania menu  
  
1.  Tworzenie formularza nadrzędnego MDI przez ustawienie jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`.  
  
2.  Dodaj <xref:System.Windows.Forms.MenuStrip> aby element nadrzędny MDI ustawienie jej <xref:System.Windows.Forms.Form.MainMenuStrip%2A> właściwości, do którego <xref:System.Windows.Forms.MenuStrip>.  
  
3.  Utwórz formularz podrzędny MDI i ustaw jej <xref:System.Windows.Forms.Form.MdiParent%2A> właściwość na nazwę formularza nadrzędnego.  
  
4.  Dodaj <xref:System.Windows.Forms.MenuStrip> do formularz podrzędny MDI.  
  
5.  W formularzu podrzędnym ustawić <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `false`.  
  
6.  Dodawanie elementów menu do formularza podrzędnego <xref:System.Windows.Forms.MenuStrip> , które chcesz scalić formularza nadrzędnego <xref:System.Windows.Forms.MenuStrip> po aktywowaniu formularza podrzędnego.  
  
7.  Użyj <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> elementów właściwości w menu w formularzu podrzędnym <xref:System.Windows.Forms.MenuStrip> do kontrolowania sposobu scalania do formularza nadrzędnego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Informacje o formancie MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
