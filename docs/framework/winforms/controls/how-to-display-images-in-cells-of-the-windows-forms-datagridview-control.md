---
title: 'Instrukcje: wyświetlanie obrazów w komórkach kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: 90aaff419ecc2c890a8b3802f3aaf12092febb73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083000"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Instrukcje: wyświetlanie obrazów w komórkach kontrolki DataGridView formularzy systemu Windows
Obraz lub element graficzny jest jedną z wartości, które można wyświetlić w wierszu danych. Często te grafiki formę fotografii pracownika lub logo firmy.  
  
 Dołączanie obrazów jest proste, podczas wyświetlania danych w ramach <xref:System.Windows.Forms.DataGridView> kontroli. <xref:System.Windows.Forms.DataGridView> Kontroli natywnie obsługuje format obrazu, wszystkie obsługiwane przez <xref:System.Drawing.Image> klasy, a także OLE obraz format używany przez niektóre bazy danych.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView> swojego źródła danych zawiera kolumnę obrazów, zostaną one wyświetlone automatycznie przez <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 Poniższy przykład kodu demonstruje sposób wyodrębniania ikony z zasobu osadzonego i przekonwertować go do mapy bitowej do wyświetlenia w każdej komórce kolumny obrazu. Inny przykład zastępuje wartości tekstowej komórek przy użyciu odpowiedniego obrazów, zobacz [jak: Dostosowywanie formatowania danych w formancie DataGridView formularzy Windows](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Zasób osadzony ikony o nazwie `tree.ico`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Drawing?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Instrukcje: Dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
