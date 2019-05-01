---
title: 'Instrukcje: wykrywanie, kiedy wskaźnik myszy znajduje się nad elementem ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 09fd9f2f9b8cc44b6c04b829bf2854bea4aa8cf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054266"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>Instrukcje: wykrywanie, kiedy wskaźnik myszy znajduje się nad elementem ToolStripItem
Użyj poniższej procedury, aby wykryć, kiedy wskaźnik myszy znajduje się nad <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>Aby wykryć, gdy wskaźnik znajduje się za pośrednictwem elementu ToolStripItem  
  
- Użyj <xref:System.Windows.Forms.ToolStripItem.Selected%2A> właściwości dla elementów, w którym <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> jest `true`.  
  
     To uniemożliwi konieczności synchronizacji <xref:System.Windows.Forms.ToolStripItem.MouseEnter> i <xref:System.Windows.Forms.ToolStripItem.MouseLeave> zdarzenia.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
