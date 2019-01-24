---
title: Dostosowywanie formantu DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 901b221f74fa76221ed3f19e9eb4c5f17c6534fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559557"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Dostosowywanie formantu DataGridView formularzy systemu Windows
`DataGridView` Kontrola zapewnia kilka właściwości, których można dostosować wygląd i zachowanie podstawowe (wygląd i działanie), jej komórek, wierszy i kolumn. Jeśli masz specjalne potrzeby, które wykraczają poza możliwości <xref:System.Windows.Forms.DataGridViewCellStyle> klasy, można jednak również zaimplementować rysowanie formantu przez właściciela lub rozszerzyć jej możliwości, tworząc niestandardowe komórek, kolumn i wierszy.  
  
 Aby rysować komórek i wierszy, samodzielnie, może obsługiwać różnych `DataGridView` zdarzenia rysowania. Aby zmodyfikować istniejące funkcje lub zapewniają nowe funkcje, można utworzyć własne typy pochodzące z istniejących `DataGridViewCell`, `DataGridViewColumn`, i `DataGridViewRow` typów. Możesz także podać nowe możliwości edytowania przez tworzenie typów pochodnych, które wyświetlają kontroli wybrane gdy komórka jest w trybie edycji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 W tym artykule opisano sposób obsługi <xref:System.Windows.Forms.DataGridView.CellPainting> zdarzeń w celu rysowania komórek ręcznie.  
  
 [Instrukcje: Dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 W tym artykule opisano sposób obsługi <xref:System.Windows.Forms.DataGridView.RowPrePaint> i <xref:System.Windows.Forms.DataGridView.RowPostPaint> zdarzenia w celu rysowania wiersze z niestandardowych, gradientu tła i zawartością, która obejmuje wiele kolumn.  
  
 [Instrukcje: Dostosowywanie komórek i kolumn w kontrolce DataGridView formularzy Windows Forms przez rozszerzanie ich zachowania i wyglądu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 W tym artykule opisano sposób tworzenia niestandardowych typów pochodnych typu `DataGridViewCell` i `DataGridViewColumn` celu Wyróżnij komórki, gdy wskaźnik myszy znajduje się na nich.  
  
 [Instrukcje: Wyłączanie przycisków w kolumnie przycisków w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 W tym artykule opisano sposób tworzenia niestandardowych typów pochodnych typu <xref:System.Windows.Forms.DataGridViewButtonCell> i <xref:System.Windows.Forms.DataGridViewButtonColumn> w celu wyświetlenia wyłączone przycisków w kolumnie przycisków.  
  
 [Instrukcje: Kontrolki hosta w komórkach kontrolki DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Opisuje sposób implementacji `IDataGridViewEditingControl` interfejs i tworzenie niestandardowych typów pochodnych typu `DataGridViewCell` i `DataGridViewColumn` w celu wyświetlenia <xref:System.Windows.Forms.DateTimePicker> kontroli, gdy komórka jest w trybie edycji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DataGridView>  
 Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewCell> klasy.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewRow> klasy.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewColumn> klasy.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy, które opisują sposób modyfikowania wyglądu podstawowego formantu i formatowania wyświetlania danych komórki.  
  
## <a name="see-also"></a>Zobacz także
- [DataGridView, kontrolka](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
