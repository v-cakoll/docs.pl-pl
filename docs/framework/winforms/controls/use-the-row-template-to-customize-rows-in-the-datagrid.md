---
title: 'Instrukcje: użycie szablonu wiersza do dostosowania wierszy w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: cb3a826262a49a8653e3a344bd126d434f2522dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073062"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Instrukcje: użycie szablonu wiersza do dostosowania wierszy w kontrolce DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Kontroli używa szablonu wiersza jako podstawy dla wszystkich wierszy, które są dodawane do formantu za pomocą powiązania danych lub po wywołaniu <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metody bez określania istniejącego wiersza do użycia.  
  
 Szablon wiersza zapewnia większą kontrolę nad wyglądem i zachowaniem wierszy niż <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> zawiera właściwość. Za pomocą szablonu wiersza można ustawić dowolny <xref:System.Windows.Forms.DataGridViewRow> właściwości, w tym <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Istnieją sytuacje, w którym musi użycie szablonu wiersza do osiągnięcia określonej efekt. Na przykład, nie mogą być przechowywane informacje o wysokości wiersza <xref:System.Windows.Forms.DataGridViewCellStyle>, więc musisz można zmienić wysokość domyślna używana przez wszystkie wiersze, używając szablonu wiersza. Szablon wiersza jest przydatna podczas tworzenia własnych klas pochodnych <xref:System.Windows.Forms.DataGridViewRow> i chcesz, aby używany, gdy nowe wiersze są dodawane do formantu niestandardowego typu.  
  
> [!NOTE]
>  Szablon wiersza jest używana tylko wtedy, gdy zostaną dodane wiersze. Nie można zmienić istniejące wiersze, zmieniając szablonu wiersza.  
  
### <a name="to-use-the-row-template"></a>Użycie szablonu wiersza  
  
-   Ustawianie właściwości w obiekcie pobierane <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Podstawowe formatowanie i style w formancie DataGridView formularzy systemu Windows](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w formancie DataGridView formularzy systemu Windows](cell-styles-in-the-windows-forms-datagridview-control.md)
