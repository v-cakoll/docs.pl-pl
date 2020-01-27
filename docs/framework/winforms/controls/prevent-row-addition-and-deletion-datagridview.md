---
title: Zapobiegaj dodawaniu i usuwaniu wierszy w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: de8e0412faf8c3731f9356771b35a4a5d31b6ec7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728722"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a>Porady: zapobiegaj dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows
Czasami chcesz uniemożliwić użytkownikom wprowadzanie nowych wierszy danych lub usuwanie istniejących wierszy w kontrolce <xref:System.Windows.Forms.DataGridView>. Właściwość <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> wskazuje, czy wiersz dla nowych rekordów znajduje się u dołu kontrolki, natomiast Właściwość <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> wskazuje, czy można usunąć wiersze. Poniższy przykład kodu używa tych właściwości, a także ustawia właściwość <xref:System.Windows.Forms.DataGridView.ReadOnly%2A>, aby kontrolka była całkowicie tylko do odczytu.  
  
 To zadanie jest obsługiwane w programie Visual Studio. Zobacz również [instrukcje: Zapobieganie dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
