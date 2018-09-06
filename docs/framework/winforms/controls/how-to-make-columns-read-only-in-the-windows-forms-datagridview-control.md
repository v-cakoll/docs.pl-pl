---
title: 'Porady: określanie kolumn jako tylko do odczytu w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: a8b5c0f9492941cf0e01e016d9fb097e1df44d2e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731978"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>Porady: określanie kolumn jako tylko do odczytu w formancie DataGridView formularzy systemu Windows
Nie wszystkie dane, jest przeznaczona do edycji. W <xref:System.Windows.Forms.DataGridView> kontrolować kolumny <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> wartość właściwości określa, czy użytkownicy mogą edytować komórek w tej kolumnie. Aby dowiedzieć się, jak sprawić, że formant całkowicie tylko do odczytu, zobacz [porady: zapobieganie Dodawanie wierszy i usuwanie w formancie DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).  
  
 Są obsługiwane dla tego zadania w programie Visual Studio.  Zobacz też [jak: utworzyć tylko do odczytu w kolumnach w Windows Forms DataGridView kontroli przy użyciu narzędzia Projektant](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).  
  
### <a name="to-make-a-column-read-only-programmatically"></a>Aby kolumnę tylko do odczytu programowe  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> właściwość `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` kolumnę o nazwie `CompanyName`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Instrukcje: zapobieganie dodawaniu i usuwaniu wierszy dla kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
