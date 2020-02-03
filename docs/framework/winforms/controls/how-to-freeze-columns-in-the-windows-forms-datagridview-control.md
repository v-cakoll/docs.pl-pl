---
title: Zablokuj kolumny w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: 6d1a98e5c4332078c6012cb7c9ed836108abd86c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736743"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows
Gdy użytkownicy będą wyświetlać dane wyświetlane w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms, czasami muszą odwoływać się do pojedynczej kolumny lub zestawu kolumn często. Na przykład podczas wyświetlania tabeli informacji o kliencie zawierającej wiele kolumn warto wyświetlić nazwę klienta przez cały czas, jednocześnie włączając inne kolumny przewijane poza widocznym regionem.  
  
 Aby osiągnąć takie zachowanie, można zablokować kolumny w kontrolce. Po zablokowaniu kolumny wszystkie kolumny po lewej stronie (lub po prawej stronie w skrypcie języka od prawej do lewej) również są zamrożone. Zablokowane kolumny pozostają na miejscu, gdy wszystkie inne kolumny można przewijać.  
  
> [!NOTE]
> W przypadku włączenia zmiany kolejności kolumn zablokowane kolumny są traktowane jako odrębne dla grupy z odblokowanych kolumn. Użytkownicy mogą zmieniać położenie kolumn w jednej grupie, ale nie mogą przenosić kolumn z jednej grupy do drugiej.  
  
 Właściwość <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> kolumny określa, czy kolumna jest zawsze widoczna w obrębie siatki.  
  
 To zadanie jest obsługiwane w programie Visual Studio.  Zobacz również [instrukcje: zamrażanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](freeze-columns-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-freeze-a-column-programmatically"></a>Aby programowo zablokować kolumnę  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> na `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`, która zawiera kolumnę o nazwie `AddToCartButton`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
