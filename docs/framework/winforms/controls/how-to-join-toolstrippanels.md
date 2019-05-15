---
title: 'Instrukcje: łączenie ToolStripPanels'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
ms.openlocfilehash: d9cacddecdf3859a0fca4038481eeab417e22e6a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592385"
---
# <a name="how-to-join-toolstrippanels"></a>Instrukcje: łączenie ToolStripPanels
Możesz dołączyć <xref:System.Windows.Forms.ToolStrip> mające na celu <xref:System.Windows.Forms.ToolStripPanel> w czasie wykonywania, który zapewnia elastyczność aplikacji interfejsu wielu dokumentów (MDI).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak sprzęgać <xref:System.Windows.Forms.ToolStrip> mające na celu <xref:System.Windows.Forms.ToolStripPanel>.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- [Instrukcje: Używanie elementu ToolStripPanels dla MDI](how-to-use-toolstrippanels-for-mdi.md)
