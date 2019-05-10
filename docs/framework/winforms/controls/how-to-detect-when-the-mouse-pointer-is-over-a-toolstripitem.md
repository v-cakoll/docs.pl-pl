---
title: 'Instrukcje: wykrywanie, kiedy wskaźnik myszy znajduje się nad elementem ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: f01a9acb3a566be40d65fb075c8487d4e9cb6e73
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623642"
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
