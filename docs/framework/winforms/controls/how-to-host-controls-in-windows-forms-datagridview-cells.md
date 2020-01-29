---
title: Kontrolki hosta w komórkach DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a64521a15a272ca8140302f39d15e7f17e0c423b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736539"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Porady: formanty hosta w komórkach DataGridView formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.DataGridView> zawiera kilka typów kolumn, umożliwiając użytkownikom wprowadzanie i edytowanie wartości na różne sposoby. Jeśli te typy kolumn nie spełniają wymagań związanych z wprowadzaniem danych, można jednak utworzyć własne typy kolumn z komórkami, które obsługują wybrane przez siebie kontrolki. W tym celu należy zdefiniować klasy, które pochodzą od <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewCell>. Należy również zdefiniować klasę, która pochodzi od <xref:System.Windows.Forms.Control> i implementuje interfejs <xref:System.Windows.Forms.IDataGridViewEditingControl>.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć kolumnę kalendarza. Komórki tej kolumny wyświetlają daty w zwykłych komórkach pól tekstowych, ale gdy użytkownik edytuje komórkę, zostanie wyświetlona kontrolka <xref:System.Windows.Forms.DateTimePicker>. Aby uniknąć konieczności ponownego wdrożenia funkcji wyświetlania pól tekstowych, Klasa `CalendarCell` dziedziczy z klasy <xref:System.Windows.Forms.DataGridViewTextBoxCell>, a nie dziedziczy bezpośrednio klasy <xref:System.Windows.Forms.DataGridViewCell>.  
  
> [!NOTE]
> Gdy dziedziczysz z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodasz nowe właściwości do klasy pochodnej, pamiętaj, aby zastąpić metodę `Clone`, aby skopiować nowe właściwości podczas klonowania operacji. Należy również wywołać metodę `Clone` klasy bazowej, aby właściwości klasy bazowej były kopiowane do nowej komórki lub kolumny.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższy przykład wymaga:  
  
- Odwołania do zestawów system i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
