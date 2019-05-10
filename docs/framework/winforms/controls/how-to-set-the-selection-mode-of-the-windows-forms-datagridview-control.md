---
title: 'Instrukcje: ustawianie trybu zaznaczania kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
ms.openlocfilehash: 22db5c1438405fc830202ec7baac6b6fcd631b41
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620796"
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a>Instrukcje: ustawianie trybu zaznaczania kontrolki DataGridView formularzy systemu Windows
Poniższy przykład kodu demonstruje sposób konfigurowania <xref:System.Windows.Forms.DataGridView> kontroli tak, aby kliknięcie dowolnym miejscu w wierszu automatycznie wybiera cały wiersz, i tak aby tylko jeden wiersz jednocześnie można wybrać.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
- Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Tryby wyboru w kontrolce DataGridView formularzy Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
