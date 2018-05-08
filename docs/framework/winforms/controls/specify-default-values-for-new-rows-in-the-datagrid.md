---
title: 'Porady: określanie wartości domyślnych dla nowych wierszy w formancie DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: c28d969f9d4976c7432e7293afb13e7f340f7e97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Porady: określanie wartości domyślnych dla nowych wierszy w formancie DataGridView formularzy systemu Windows
Istnieje możliwość wprowadzania danych wygodniejsze podczas aplikacji wypełnia w domyślnych wartości dla nowo dodanych wierszy. Z <xref:System.Windows.Forms.DataGridView> klasy, możesz wpisać w domyślnej wartości z <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik wprowadzi wiersz dla nowych rekordów. Gdy swój kod obsługi tego zdarzenia, można wypełnić żądaną komórek zawierających wartości wybrane.  
  
 Poniższy przykład kodu pokazuje sposób określania wartości domyślne dla nowych wierszy za pomocą <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   A `NewCustomerId` funkcja generowania unikatowych `CustomerID` wartości.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
