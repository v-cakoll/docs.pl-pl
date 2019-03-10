---
title: 'Instrukcje: Włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: c34807cc1d2a569068ba82479e3a2bf230f4f2c5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704416"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a>Instrukcje: Włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms
Po włączeniu zmiany układu kolumn w <xref:System.Windows.Forms.DataGridView> kontrolki, użytkownicy mogą przechodzić kolumnę w nowe położenie przez przeciągnięcie nagłówka kolumny za pomocą myszy. W <xref:System.Windows.Forms.DataGridView> kontroli <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> wartość właściwości określa, czy użytkownicy mogą przechodzić do innej pozycji kolumn.  
  
 Są obsługiwane dla tego zadania w programie Visual Studio.  Zobacz też [jak: Włącz w Windows zmiany układu kolumn do formantu DataGridView przy użyciu narzędzia Projektant formularzy](enable-column-reordering-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-enable-column-reordering-programmatically"></a>Aby włączyć programowe Zmienianie kolejności kolumn  
  
-   Ustaw <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> właściwość `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Instrukcje: Zablokuj kolumny w kontrolce DataGridView formularzy Windows Forms](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
