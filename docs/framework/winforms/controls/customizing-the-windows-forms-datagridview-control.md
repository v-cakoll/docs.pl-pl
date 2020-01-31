---
title: Dostosuj formant DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744023"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Dostosowywanie formantu DataGridView formularzy systemu Windows
Kontrolka `DataGridView` zawiera kilka właściwości, których można użyć do dostosowania wyglądu i podstawowego zachowania (wyglądu i działania) jego komórek, wierszy i kolumn. W przypadku specjalnych potrzeb, które wykraczają poza możliwości klasy <xref:System.Windows.Forms.DataGridViewCellStyle>, można również zaimplementować rysowanie właściciela dla kontrolki lub zwiększyć jej możliwości przez utworzenie niestandardowych komórek, kolumn i wierszy.  
  
 Aby samodzielnie malować komórki i wiersze, możesz obsłużyć różne `DataGridView`ych zdarzeń rysowania. Aby zmodyfikować istniejące funkcje lub udostępnić nowe funkcje, można utworzyć własne typy pochodne na podstawie istniejących typów `DataGridViewCell`, `DataGridViewColumn`i `DataGridViewRow`. Możesz również udostępnić nowe możliwości edytowania, tworząc typy pochodne, które wyświetlają formant wyboru, gdy komórka jest w trybie edycji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
 Opisuje sposób obsługi zdarzenia <xref:System.Windows.Forms.DataGridView.CellPainting> w celu ręcznego malowania komórek.  
  
 [Instrukcje: dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
 Opisuje sposób obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.RowPrePaint> i <xref:System.Windows.Forms.DataGridView.RowPostPaint> w celu malowania wierszy z niestandardowym tłem gradientu i zawartością obejmującą wiele kolumn.  
  
 [Instrukcje: dostosowywanie komórek i kolumn w kontrolce DataGridView formularzy Windows Forms przez rozszerzanie ich zachowania i wyglądu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Opisuje sposób tworzenia typów niestandardowych pochodnych dla `DataGridViewCell` i `DataGridViewColumn` w celu wyróżnienia komórek, gdy wskaźnik myszy zatrzyma się na nich.  
  
 [Instrukcje: wyłączanie przycisków w kolumnie przycisków w kontrolce DataGridView formularzy Windows Forms](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Opisuje sposób tworzenia typów niestandardowych pochodnych dla <xref:System.Windows.Forms.DataGridViewButtonCell> i <xref:System.Windows.Forms.DataGridViewButtonColumn> w celu wyświetlenia wyłączonych przycisków w kolumnie przycisków.  
  
 [Instrukcje: kontrolki hosta w komórkach kontrolki DataGridView formularzy Windows Forms](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Opisuje, jak zaimplementować interfejs `IDataGridViewEditingControl` i utworzyć niestandardowe typy pochodne od `DataGridViewCell` i `DataGridViewColumn` w celu wyświetlenia kontrolki <xref:System.Windows.Forms.DateTimePicker>, gdy komórka jest w trybie edycji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DataGridView>  
 Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewCell>.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewRow>.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Zawiera dokumentację referencyjną dla interfejsu <xref:System.Windows.Forms.IDataGridViewEditingControl>.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy opisujące sposób modyfikowania podstawowego wyglądu kontrolki i formatowania wyświetlania danych komórek.  
  
## <a name="see-also"></a>Zobacz także

- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
