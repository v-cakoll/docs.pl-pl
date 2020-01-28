---
title: Dodaj etykietki narzędzi do poszczególnych komórek w formancie DataGridView
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
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732183"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Porady: dodawanie elementu ToolTips do pojedynczych komórek w formancie DataGridView formularzy systemu Windows
Domyślnie etykietki narzędzi są używane do wyświetlania wartości <xref:System.Windows.Forms.DataGridView> komórek, które są zbyt małe, aby wyświetlić całą zawartość. Można jednak zastąpić to zachowanie, aby ustawić wartości tekstowe etykietki narzędzia dla poszczególnych komórek. Jest to przydatne w przypadku wyświetlania użytkownikom dodatkowych informacji o komórce lub zapewnienia użytkownikom alternatywnego opisu zawartości komórki. Na przykład jeśli masz wiersz, w którym są wyświetlane ikony stanu, możesz podać wyjaśnienie tekstu przy użyciu etykietek narzędzi.  
  
 Możesz również wyłączyć wyświetlanie etykietek na poziomie komórki, ustawiając właściwość <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> na `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Aby dodać etykietkę narzędzia do komórki  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`, która zawiera kolumnę o nazwie `Rating` do wyświetlania wartości ciągów jednego z czterech gwiazdek ("*"). Zdarzenie <xref:System.Windows.Forms.DataGridView.CellFormatting> formantu musi być skojarzone z metodą obsługi zdarzeń pokazaną w przykładzie.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Po powiązaniu formantu <xref:System.Windows.Forms.DataGridView> z zewnętrznym źródłem danych lub udostępnieniu własnego źródła danych przez implementację trybu wirtualnego mogą wystąpić problemy z wydajnością. Aby uniknąć pogorszenia wydajności podczas pracy z dużymi ilościami danych, należy obsłużyć <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> zdarzenia zamiast ustawiania właściwości <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> wielu komórek. Podczas obsługi tego zdarzenia pobieranie wartości właściwości <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> komórki wywołuje zdarzenie i zwraca wartość właściwości <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType>, jak określono w obsłudze zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](programming-with-cells-rows-and-columns-in-the-datagrid.md)
