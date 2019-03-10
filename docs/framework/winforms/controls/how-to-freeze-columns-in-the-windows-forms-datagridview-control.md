---
title: 'Instrukcje: Zablokuj kolumny w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: 640b6a9128758edfc22b5c9be971034c9e45fc70
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723871"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Instrukcje: Zablokuj kolumny w kontrolce DataGridView formularzy Windows Forms
Gdy użytkownicy wyświetlają dane wyświetlane w formularzach Windows <xref:System.Windows.Forms.DataGridView> kontrolki, czasami muszą odwoływać się do pojedynczej kolumny lub zestaw kolumn, często. Na przykład wyświetlając tabelę informacje o kliencie, który zawiera wiele kolumn, jest przydatne do wyświetlania nazwy klientów przez cały czas podczas włączania innych kolumn w celu przewiń poza regionem widoczne.  
  
 Aby uzyskać takie zachowanie, można zablokować kolumn w formancie. Po zablokowaniu kolumny, również są zablokowane wszystkie kolumny po lewej stronie (lub po jego prawej stronie skrypty języka od prawej do lewej). Zamrożone kolumny pozostaną w miejscu, a wszystkie pozostałe kolumny można przewijać.  
  
> [!NOTE]
>  Jeśli zmiany układu kolumn jest włączona, Zablokowane kolumny są traktowane jako różne od kolumny grupy. Użytkownicy mogą zmienić położenie kolumn w każdej grupie, ale kolumna nie może przenieść z jednej grupy do drugiego.  
  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Właściwość kolumny określa, czy kolumna jest zawsze widoczny w obrębie siatki.  
  
 Są obsługiwane dla tego zadania w programie Visual Studio.  Zobacz też [jak: Blokowanie kolumn w Windows Forms formantu DataGridView za pomocą projektanta](freeze-columns-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-freeze-a-column-programmatically"></a>Aby programowo Zablokuj kolumnę  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> właściwość `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawierającą kolumnę o nazwie `AddToCartButton`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Instrukcje: Włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
