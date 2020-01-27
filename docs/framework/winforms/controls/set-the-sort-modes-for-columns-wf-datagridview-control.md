---
title: Ustawianie trybów sortowania kolumn w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742996"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Porady: ustawianie trybów sortowania kolumn w formancie DataGridView formularzy systemu Windows
W kontrolce <xref:System.Windows.Forms.DataGridView> kolumny pól tekstowych używają automatycznego sortowania domyślnie, natomiast inne typy kolumn nie są sortowane automatycznie. Czasami chcesz zastąpić te ustawienia domyślne. Na przykład można wyświetlić obrazy zamiast tekstu, liczb lub wartości komórek wyliczenia. Gdy obrazy nie mogą być sortowane, podstawowe wartości, które reprezentują, mogą być sortowane.  
  
 W formancie <xref:System.Windows.Forms.DataGridView> wartość właściwości <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> kolumny określa zachowanie sortowania.  
  
 Poniższa procedura przedstawia `Priority` kolumnie z [: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Ta kolumna jest kolumną obrazu i domyślnie nie jest sortowany. Zawiera rzeczywiste wartości komórek, które są ciągami, jednak można je posortować automatycznie.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Aby ustawić tryb sortowania dla kolumny  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`, która zawiera kolumnę o nazwie `Priority`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: dostosowywanie sortowania w kontrolce DataGridView Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
