---
title: Użycie szablonu wiersza do dostosowania wierszy w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 35cb95f22c0caa654bf149b5fc4fd0395696a411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728386"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Porady: użycie szablonu wiersza do dostosowania wierszy w formancie DataGridView formularzy systemu Windows
Formant <xref:System.Windows.Forms.DataGridView> używa szablonu wiersza jako podstawy dla wszystkich wierszy, które dodaje do formantu za pośrednictwem powiązania danych lub wywołania metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> bez określania istniejącego wiersza do użycia.  
  
 Szablon wiersza zapewnia większą kontrolę nad wyglądem i zachowaniem wierszy, niż zapewnia Właściwość <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>. Za pomocą szablonu wiersza można ustawić wszystkie <xref:System.Windows.Forms.DataGridViewRow> właściwości, w tym <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Istnieją sytuacje, w których należy użyć szablonu wiersza do osiągnięcia określonego efektu. Na przykład informacje o wysokości wiersza nie mogą być przechowywane w <xref:System.Windows.Forms.DataGridViewCellStyle>, więc musisz użyć szablonu wiersza, aby zmienić domyślną wysokość używaną przez wszystkie wiersze. Szablon wiersza jest również przydatny podczas tworzenia własnych klas pochodnych z <xref:System.Windows.Forms.DataGridViewRow> i chcesz, aby typ niestandardowy był używany podczas dodawania nowych wierszy do formantu.  
  
> [!NOTE]
> Szablon wiersza jest używany tylko po dodaniu wierszy. Nie można zmienić istniejących wierszy, zmieniając szablon wiersza.  
  
### <a name="to-use-the-row-template"></a>Aby użyć szablonu wiersza  
  
- Ustaw właściwości obiektu pobranego z właściwości <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
