---
title: 'Instrukcje: kontrolki hosta w komórkach DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a97af9bf0ef4016e54f877d934ed401b8dde7d4e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966605"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Instrukcje: kontrolki hosta w komórkach DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Formant zawiera kilka typów kolumn, umożliwiając użytkownikom wprowadzanie i edytowanie wartości na różne sposoby. Jeśli te typy kolumn nie spełniają wymagań związanych z wprowadzaniem danych, można jednak utworzyć własne typy kolumn z komórkami, które obsługują wybrane przez siebie kontrolki. Aby to zrobić, należy zdefiniować klasy, które pochodzą z <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewCell>. Należy również zdefiniować klasę, która dziedziczy z <xref:System.Windows.Forms.Control> i <xref:System.Windows.Forms.IDataGridViewEditingControl> implementuje interfejs.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć kolumnę kalendarza. Komórki tej kolumny wyświetlają daty w zwykłych komórkach pól tekstowych, ale gdy użytkownik edytuje komórkę, <xref:System.Windows.Forms.DateTimePicker> zostanie wyświetlony formant. Aby uniknąć konieczności ponownego wdrożenia funkcji wyświetlania pól tekstowych, `CalendarCell` Klasa pochodzi <xref:System.Windows.Forms.DataGridViewTextBoxCell> od klasy, <xref:System.Windows.Forms.DataGridViewCell> a nie dziedziczy bezpośrednio klasy.  
  
> [!NOTE]
> Gdy pochodzą z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodajesz nowe właściwości do klasy pochodnej, pamiętaj, aby zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas klonowania operacji. Należy również wywołać `Clone` metodę klasy bazowej, aby właściwości klasy bazowej były kopiowane do nowej komórki lub kolumny.  
  
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
