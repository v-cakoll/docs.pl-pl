---
title: Określ wartości domyślne dla nowych wierszy w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742929"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Porady: określanie wartości domyślnych dla nowych wierszy w formancie DataGridView formularzy systemu Windows
Wprowadzanie danych może być wygodniejsze, gdy aplikacja wypełnia wartości domyślne dla nowo dodanych wierszy. Za pomocą klasy <xref:System.Windows.Forms.DataGridView> można wypełnić wartości domyślne za pomocą zdarzenia <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>. To zdarzenie jest zgłaszane, gdy użytkownik wprowadzi wiersz dla nowych rekordów. Gdy kod obsługuje to zdarzenie, można wypełniać odpowiednie komórki wybranymi wartościami.  
  
 Poniższy przykład kodu demonstruje sposób określania wartości domyślnych dla nowych wierszy przy użyciu zdarzenia <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Funkcja `NewCustomerId` do generowania unikatowych wartości `CustomerID`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
