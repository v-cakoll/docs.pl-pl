---
title: Zmiana kolejności kolumn w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 2aef196e9544a81f42a563783ce6c357869aa247
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746545"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows
Gdy używasz <xref:System.Windows.Forms.DataGridView> do wyświetlania danych ze źródła danych, kolumny w schemacie źródła danych czasami nie są wyświetlane w kolejności, w jakiej chcesz je wyświetlić. Można zmienić kolejność wyświetlania kolumn za pomocą właściwości <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> klasy <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 Poniższy przykład kodu zmienia położenie niektórych kolumn generowanych automatycznie podczas tworzenia powiązania z tabelą Customers w przykładowej bazie danych Northwind. Aby uzyskać więcej informacji o sposobie powiązania formantu <xref:System.Windows.Forms.DataGridView> z tabelą bazy danych, zobacz [How to: bind Data to the Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 To zadanie jest obsługiwane w programie Visual Studio.  Zapoznaj się również z tematem [: zmiana kolejności kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `customersDataGridView`, która jest powiązana z tabelą ze wskazanymi nazwami kolumn, takimi jak tabela `Customers` w przykładowej bazie danych Northwind.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>i <xref:System.Xml?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: wiązanie danych z kontrolką DataGridView formularzy Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
