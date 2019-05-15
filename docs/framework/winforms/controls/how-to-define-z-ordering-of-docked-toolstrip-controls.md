---
title: 'Instrukcje: definiowanie porządku osi Z zadokowanych kontrolek ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: 514c9dd1c91adcadf6f5d383ba734886dec3151d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591907"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a>Instrukcje: definiowanie porządku osi Z zadokowanych kontrolek ToolStrip
Położenie <xref:System.Windows.Forms.ToolStrip> kontroli poprawnie za pomocą dokowania, należy umieścić formant poprawnie w kolejności z formularza.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób rozmieszczenia <xref:System.Windows.Forms.ToolStrip> kontroli i zadokowany <xref:System.Windows.Forms.MenuStrip> kontroli przez określenie porządku osi z.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 Kolejność jest określana przez kolejność, w której <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.MenuStrip>  
  
 Formanty są dodawane do formularza <xref:System.Windows.Forms.Control.Controls%2A> kolekcji.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 Odwracanie kolejności tych wywołań <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metody i widoku. wpływa na układ.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>
- <xref:System.Windows.Forms.Control.Controls%2A>
- <xref:System.Windows.Forms.Control.Dock%2A>
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
