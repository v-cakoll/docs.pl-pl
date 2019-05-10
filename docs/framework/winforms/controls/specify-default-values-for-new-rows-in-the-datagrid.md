---
title: 'Instrukcje: określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: 879c035366c4686ceff3250a63c6ae8d8d3cfec4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651960"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Instrukcje: określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView formularzy systemu Windows
Wprowadzanie danych można wprowadzić bardziej wygodne, gdy aplikacja domyślnie wypełnia wartości dla nowo dodanych wierszy. Za pomocą <xref:System.Windows.Forms.DataGridView> klasy, możesz wpisać w domyślnych wartości za pomocą <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik wprowadzi wiersza dla nowych rekordów. Kod, obsługując to zdarzenie, możesz wypełnić żądane komórki o wartości wybrane.  
  
 Poniższy przykład kodu demonstruje sposób określania wartości domyślne dla nowych wierszy przy użyciu <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
- A `NewCustomerId` funkcji do generowania unikatowych `CustomerID` wartości.  
  
- Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
