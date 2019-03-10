---
title: 'Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: a0ef450559a1106de635c6d3b16891c23c41b050
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725054"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms
W <xref:System.Windows.Forms.DataGridView> kontrolka, tekst pola kolumny używać automatycznego sortowania domyślnie, podczas gdy inne typy kolumn nie są sortowane automatycznie. Czasami chcesz przesłonić te ustawienia domyślne. Na przykład można wyświetlić obrazów zamiast tekstu, liczby lub wartości komórki wyliczenia. Gdy obrazy nie można sortować, podstawowej wartości, które reprezentują one można sortować.  
  
 W <xref:System.Windows.Forms.DataGridView> kontroli <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> wartość właściwości kolumny określa jego zachowanie sortowania.  
  
 Poniższej procedury `Priority` kolumny z [jak: Dostosowywanie formatowania danych w formancie DataGridView formularzy Windows](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Ta kolumna jest kolumną obrazu i nie jest sortowanie domyślne. Zawiera wartości rzeczywiste komórki, które są ciągami, jednak, więc może być sortowana automatycznie.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Aby ustawić tryb sortowania dla kolumny  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawierającą kolumnę o nazwie `Priority`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Dostosowywanie sortowania w kontrolce DataGridView formularzy Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
