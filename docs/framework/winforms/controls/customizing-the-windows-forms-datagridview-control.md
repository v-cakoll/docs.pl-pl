---
title: Dostosowywanie formantu DataGridView formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 348651784ef2b4d99679038a1875fc6650688a6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Dostosowywanie formantu DataGridView formularzy systemu Windows
`DataGridView` Kontrola zapewnia kilka właściwości, które można dostosować wygląd i zachowanie podstawowe (wyglądu i działania), jego komórek, wierszy i kolumn. Jeśli masz specjalnymi potrzebami, które wykraczają poza możliwości <xref:System.Windows.Forms.DataGridViewCellStyle> klasy, jednak można zaimplementować rysowanie formantu przez właściciela lub rozszerzyć jej możliwości, tworząc niestandardowe komórek, kolumn i wierszy.  
  
 Namalować komórek i wierszy samodzielnie, może obsługiwać różne `DataGridView` zdarzenia rysowania. Aby zmodyfikować istniejące funkcje lub udostępnia nowych funkcji, można utworzyć własne typy pochodzące z istniejącego `DataGridViewCell`, `DataGridViewColumn`, i `DataGridViewRow` typów. Można też podać nowe możliwości edytowania przez tworzenie typów pochodnych zawierających formantu użytkownika wybrać, gdy komórka jest w trybie edycji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 Opisuje sposób obsługi <xref:System.Windows.Forms.DataGridView.CellPainting> zdarzeń w celu rysowania komórek ręcznie.  
  
 [Instrukcje: dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 Opisuje sposób obsługi <xref:System.Windows.Forms.DataGridView.RowPrePaint> i <xref:System.Windows.Forms.DataGridView.RowPostPaint> zdarzeń w celu rysowania wiersze z niestandardowych, gradientu tła i zawartością, która obejmuje wielu kolumn.  
  
 [Instrukcje: dostosowywanie komórek i kolumn w kontrolce DataGridView formularzy Windows Forms przez rozszerzanie ich zachowania i wyglądu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Opisuje sposób tworzenia niestandardowych typów pochodnych `DataGridViewCell` i `DataGridViewColumn` aby wyróżnić komórki, gdy wskaźnik myszy znajduje się na nich.  
  
 [Instrukcje: wyłączanie przycisków w kolumnie przycisków w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Opisuje sposób tworzenia niestandardowych typów pochodnych <xref:System.Windows.Forms.DataGridViewButtonCell> i <xref:System.Windows.Forms.DataGridViewButtonColumn> w celu wyświetlenia wyłączone przycisków w kolumnie przycisków.  
  
 [Instrukcje: kontrolki hosta w komórkach kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Opisuje sposób wdrożenia `IDataGridViewEditingControl` interfejsu i tworzyć niestandardowych typów pochodnych `DataGridViewCell` i `DataGridViewColumn` w celu wyświetlenia <xref:System.Windows.Forms.DateTimePicker> kontroli, gdy komórka jest w trybie edycji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DataGridView>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridViewCell> klasy.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridViewRow> klasy.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridViewColumn> klasy.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Udostępnia tematach opisano sposób modyfikowania podstawowe wygląd formantu i formatowania wyświetlania danych komórki.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGridView, kontrolka](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
