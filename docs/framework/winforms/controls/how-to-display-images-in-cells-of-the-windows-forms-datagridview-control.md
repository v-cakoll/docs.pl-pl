---
title: Wyświetlanie obrazów w komórkach kontrolki DataGridView
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
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740285"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Porady: wyświetlanie obrazów w komórkach formantu DataGridView formularzy systemu Windows
Obraz lub grafika to jedna z wartości, które można wyświetlić w wierszu danych. Często te grafiki przyjmują formę Zdjęcia pracownika lub logo firmy.  
  
 Dołączanie obrazów jest proste, gdy wyświetlasz dane w kontrolce <xref:System.Windows.Forms.DataGridView>. Formant <xref:System.Windows.Forms.DataGridView> natywnie obsługuje dowolny format obrazu obsługiwany przez klasę <xref:System.Drawing.Image>, a także format obrazu OLE używany przez niektóre bazy danych.  
  
 Jeśli źródło danych kontrolki <xref:System.Windows.Forms.DataGridView> ma kolumnę obrazów, zostaną one automatycznie wyświetlone przez kontrolkę <xref:System.Windows.Forms.DataGridView>.  
  
 Poniższy przykład kodu demonstruje, jak wyodrębnić ikonę z osadzonego zasobu i przekonwertować ją na mapę bitową do wyświetlania w każdej komórce kolumny obrazu. Aby uzyskać inny przykład, który zastępuje wartości komórki tekstowej odpowiednimi obrazami, zobacz [How to: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Osadzony zasób ikon o nazwie `tree.ico`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>i <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
