---
title: 'Instrukcje: Konfigurowanie automatycznego scalania Menu dla aplikacji MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: 3aeaf9ee4818b6689905c10d2bd46fc887609c35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549827"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a>Instrukcje: Konfigurowanie automatycznego scalania Menu dla aplikacji MDI
Poniższa procedura zawiera podstawowe kroki konfiguracji automatycznego scalenia w aplikacji interfejsu wielu dokumentów (MDI) za pomocą <xref:System.Windows.Forms.MenuStrip>.  
  
### <a name="to-set-up-automatic-menu-merging"></a>Aby skonfigurować automatycznego scalania menu  
  
1.  Tworzenie formularza nadrzędnego MDI, ustawiając jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwość `true`.  
  
2.  Dodaj <xref:System.Windows.Forms.MenuStrip> nadrzędny MDI, ustawiając jego <xref:System.Windows.Forms.Form.MainMenuStrip%2A> właściwość, która <xref:System.Windows.Forms.MenuStrip>.  
  
3.  Utwórz formularz podrzędny MDI i ustaw jego <xref:System.Windows.Forms.Form.MdiParent%2A> właściwość na nazwę formularza nadrzędnego.  
  
4.  Dodaj <xref:System.Windows.Forms.MenuStrip> na formularz podrzędny MDI.  
  
5.  W formularzu podrzędnym ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `false`.  
  
6.  Dodawanie elementów menu do formularza podrzędnego <xref:System.Windows.Forms.MenuStrip> , którą chcesz scalić formularza nadrzędnego <xref:System.Windows.Forms.MenuStrip> po aktywowaniu formularza podrzędnego.  
  
7.  Użyj <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> właściwości w menu elementów w formularzu podrzędnym <xref:System.Windows.Forms.MenuStrip> do kontrolowania, jak scalania do formularza nadrzędnego.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
