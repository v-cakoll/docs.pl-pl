---
title: 'Porady: użycie szablonu wiersza do dostosowania wierszy w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 2bde9b3f6934833804866e29c18f3636c65ba069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539181"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Porady: użycie szablonu wiersza do dostosowania wierszy w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Formant używa szablonu wiersza jako podstawa dla wszystkich wierszy, które są dodawane do formantu za pomocą powiązania danych lub po wywołaniu <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metody bez określania istniejącego wiersza do użycia.  
  
 Szablon wiersza zapewnia większą kontrolę nad wyglądem i zachowaniem wierszy niż <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> zawiera właściwości. Przy użyciu szablonu wiersza można ustawić dowolną <xref:System.Windows.Forms.DataGridViewRow> właściwości, w tym <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Istnieje kilka sytuacji, gdy w przypadku użycia szablonu wiersza do osiągnięcia określonej efekt. Na przykład, nie mogą być przechowywane informacje o wysokości wiersza <xref:System.Windows.Forms.DataGridViewCellStyle>, trzeba używać szablonu wiersza, aby zmienić wysokość domyślne używane przez wszystkie wiersze. Szablon wiersza jest również przydatne podczas tworzenia własnych klas pochodnych <xref:System.Windows.Forms.DataGridViewRow> i chcesz, aby Twoje typ niestandardowy używany, gdy nowe wiersze są dodawane do formantu.  
  
> [!NOTE]
>  Szablon wiersza jest używana tylko wtedy, gdy zostaną dodane wierszy. Istniejących wierszy nie można zmienić, zmieniając szablon wiersza.  
  
### <a name="to-use-the-row-template"></a>Aby użyć szablonu wiersza  
  
-   Ustawianie właściwości w obiekcie pobierane z <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>  
 [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Style komórki w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
