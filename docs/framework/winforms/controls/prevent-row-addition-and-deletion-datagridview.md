---
title: 'Instrukcje: Zapobieganie dodawaniu i usuwaniu w Windows formantu DataGridView formularzy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: 9f579720b4f3ff561ecd807e09db8d464abc9001
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664591"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a>Instrukcje: Zapobieganie dodawaniu i usuwaniu w Windows formantu DataGridView formularzy
Czasami można uniemożliwić użytkownikom wprowadzanie nowych wierszy danych lub usunięcie istniejących wierszy w swojej <xref:System.Windows.Forms.DataGridView> kontroli. <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> Właściwość wskazuje, czy wiersza dla nowych rekordów jest obecny w dolnej części kontrolki, podczas gdy <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> właściwość wskazuje, czy można usunąć wierszy. Poniższy przykład kodu używa tych właściwości, a także ustawia <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> właściwość, aby sprawić, że formant całkowicie tylko do odczytu.  
  
 Są obsługiwane dla tego zadania w programie Visual Studio. Zobacz też [jak: Zapobieganie dodawaniu i usuwaniu rzędów Windows do formantu DataGridView przy użyciu narzędzia Projektant formularzy](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
