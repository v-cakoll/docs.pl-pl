---
title: "Porady: dodawanie elementu ToolTips do pojedynczych komórek w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a533f4cbf5000489e774ba8661c3ab03cea4948a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Porady: dodawanie elementu ToolTips do pojedynczych komórek w formancie DataGridView formularzy systemu Windows
Domyślnie etykietki narzędzi są używane do wyświetlania wartości <xref:System.Windows.Forms.DataGridView> komórki, które są zbyt małe, aby wyświetlić ich całą zawartość. Można jednak zmienić to zachowanie, można ustawić wartości tekst etykietki narzędzia dla pojedynczych komórek. Jest to przydatne do wyświetlenia użytkownikom dodatkowe informacje na temat komórki lub w celu zapewnienia użytkownikom alternatywny opis zawartości komórki. Na przykład jeśli masz wiersza, który wyświetla stan ikony, można podać tekst objaśnienia używanie etykietek narzędzi.  
  
 Wyświetlanie podpowiedzi poziomie komórki można również wyłączyć, ustawiając <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> właściwości `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Aby dodać etykietkę narzędzia do komórki  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawiera kolumny o nazwie `Rating` do wyświetlania wartości ciągu z jednego do czterech gwiazdki ("*") symboli. <xref:System.Windows.Forms.DataGridView.CellFormatting> Zdarzeń formantu musi być skojarzony z metoda obsługi zdarzeń pokazano w przykładzie.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Po powiązaniu <xref:System.Windows.Forms.DataGridView> sterowania do zewnętrznego źródła danych lub podaj źródła danych przez Implementowanie trybu wirtualnego, mogą wystąpić problemy z wydajnością. Aby uniknąć spadek wydajności podczas pracy z dużą ilością danych, obsługa <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> zdarzeń, a nie ustawienia <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> właściwości wielu komórek. Podczas obsługi tego zdarzenia pobierania wartości komórki <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> właściwość wywołuje zdarzenie i zwraca wartość <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> właściwość jako określonych w zdarzeniu programu obsługi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
