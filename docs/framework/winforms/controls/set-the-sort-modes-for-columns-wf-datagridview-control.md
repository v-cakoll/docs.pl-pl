---
title: 'Porady: ustawianie trybów sortowania kolumn w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 08d90bb45006af798b629f58821cbf50ee9ef089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535734"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Porady: ustawianie trybów sortowania kolumn w formancie DataGridView formularzy systemu Windows
W <xref:System.Windows.Forms.DataGridView> kolumny pole tekstowe kontroli, użyj automatyczne sortowanie domyślne, podczas gdy inne typy kolumn nie są automatycznie sortowane. Czasami można przesłonić te ustawienia domyślne. Na przykład można wyświetlić obrazy zamiast tekstu, liczby lub wartości wyliczenia komórki. Gdy nie można sortować obrazy, wartości podstawowych, które reprezentują można sortować.  
  
 W <xref:System.Windows.Forms.DataGridView> kontroli, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> wartość właściwości kolumny określa zachowanie sortowania.  
  
 Poniżej przedstawiono procedurę `Priority` kolumny z [porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Ta kolumna jest kolumną obrazu i nie jest sortowanie domyślne. Zawiera wartości rzeczywistych komórek, które są ciągami, jednak, mogą być sortowane automatycznie.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Aby ustawić tryb sortowania kolumny  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawiera kolumny o nazwie `Priority`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: dostosowywanie sortowania w kontrolce DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
