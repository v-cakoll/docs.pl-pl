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
ms.openlocfilehash: 0dba318e6aa35761f4e9471fdb13b65644747b57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966505"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Instrukcje: użycie szablonu wiersza do dostosowania wierszy w kontrolce DataGridView formularzy systemu Windows
Kontrolka używa szablonu wiersza jako podstawy dla wszystkich wierszy, które dodaje do kontrolki przez powiązanie danych lub podczas <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> wywoływania metody bez określania istniejącego wiersza do użycia. <xref:System.Windows.Forms.DataGridView>  
  
 Szablon wiersza zapewnia większą kontrolę nad wyglądem i zachowaniem wierszy, niż <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> zapewnia właściwość. Za pomocą szablonu wiersza można ustawić wszystkie <xref:System.Windows.Forms.DataGridViewRow> właściwości, w tym. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>  
  
 Istnieją sytuacje, w których należy użyć szablonu wiersza do osiągnięcia określonego efektu. Na przykład informacje o wysokości wiersza nie mogą być przechowywane w <xref:System.Windows.Forms.DataGridViewCellStyle>, dlatego należy użyć szablonu wiersza, aby zmienić domyślną wysokość używaną przez wszystkie wiersze. Szablon wiersza jest również przydatny podczas tworzenia własnych klas pochodnych z <xref:System.Windows.Forms.DataGridViewRow> i chcesz, aby typ niestandardowy był używany podczas dodawania nowych wierszy do formantu.  
  
> [!NOTE]
> Szablon wiersza jest używany tylko po dodaniu wierszy. Nie można zmienić istniejących wierszy, zmieniając szablon wiersza.  
  
### <a name="to-use-the-row-template"></a>Aby użyć szablonu wiersza  
  
- Ustaw właściwości obiektu pobranego ze <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka o `dataGridView1`nazwie. <xref:System.Windows.Forms.DataGridView>  
  
- Odwołania do <xref:System?displayProperty=nameWithType>zestawów, <xref:System.Drawing?displayProperty=nameWithType>i. <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
