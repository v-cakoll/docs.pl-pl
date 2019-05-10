---
title: 'Instrukcje: dodawanie elementu ToolTips do pojedynczych komórek w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: d0e9b3ad742633b135a2fe1c00af3fa72af7b44a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663456"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Instrukcje: dodawanie elementu ToolTips do pojedynczych komórek w kontrolce DataGridView formularzy systemu Windows
Domyślnie, etykietki narzędzi są używane do wyświetlania wartości <xref:System.Windows.Forms.DataGridView> komórki, które są zbyt małe, aby wyświetlić jego całą zawartość. Można jednak zmienić to zachowanie, można ustawić wartości tekst etykietki narzędzia dla poszczególnych komórek. Jest to przydatne, mają być wyświetlane użytkownikom dodatkowe informacje na temat komórki lub w celu zapewnienia użytkownikom alternatywny opis zawartości komórki. Na przykład w przypadku wiersza, który wyświetla ikony stanu może być zapewnienie tekst wyjaśnienia przy użyciu etykietek narzędzi.  
  
 Wyświetlanie etykietek narzędzi w komórce poziomu można również wyłączyć, ustawiając <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> właściwość `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Aby dodać etykietka narzędzia komórki  
  
- Ustaw <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Ten przykład wymaga:  
  
- A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawierającą kolumnę o nazwie `Rating` do wyświetlania wartości ciągu o jeden przez cztery gwiazdki ("*") symboli. <xref:System.Windows.Forms.DataGridView.CellFormatting> Zdarzeń formantu musi być skojarzony z metody obsługi zdarzeń, jak pokazano w przykładzie.  
  
- Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Po powiązaniu <xref:System.Windows.Forms.DataGridView> sterowania do zewnętrznego źródła danych lub zapewnić źródła danych, implementowanie trybu wirtualnego, mogą wystąpić problemy z wydajnością. Aby uniknąć spadek wydajności, podczas pracy z dużymi ilościami danych, obsługa <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> zdarzeń, a nie ustawienie <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> właściwości wielu komórek. Podczas obsługi tego zdarzenia pobierania wartości komórki <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> właściwość wywołuje zdarzenie i zwraca wartość <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> właściwość jako określonych w zdarzeniu programu obsługi.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](programming-with-cells-rows-and-columns-in-the-datagrid.md)
