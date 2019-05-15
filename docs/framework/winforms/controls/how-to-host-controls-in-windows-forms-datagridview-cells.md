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
ms.openlocfilehash: 20b9f33b31df9145205a13b8649153e51d840a6c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592437"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Instrukcje: kontrolki hosta w komórkach DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Control oferuje kilka typów kolumn, aby umożliwić użytkownikom wprowadzanie i edytowanie wartości w na różne sposoby. Te typy kolumn nie odpowiadają Twoim potrzebom wprowadzanie danych, można jednak utworzyć swój własny typ kolumny, wraz z komórkami, które hostują formantów wybrane. Aby to zrobić, należy zdefiniować klas, które wynikają z <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewCell>. Należy także zdefiniować klasę, która pochodzi od klasy <xref:System.Windows.Forms.Control> i implementuje <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu.  
  
 Poniższy przykład kodu pokazuje sposób tworzenia kolumny kalendarza. Komórki w tej kolumnie wyświetlanie dat w komórkach pola zwykły tekst, ale w przypadku, gdy użytkownik edytuje komórkę, <xref:System.Windows.Forms.DateTimePicker> formant jest widoczny. Aby uniknąć konieczności implementowania funkcji wyświetlania pola tekstowego ponownie `CalendarCell` klasa pochodzi od <xref:System.Windows.Forms.DataGridViewTextBoxCell> klasy, a nie dziedziczy <xref:System.Windows.Forms.DataGridViewCell> klasy bezpośrednio.  
  
> [!NOTE]
>  Po utworzeniu klasy pochodnej z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, pamiętaj zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas operacji klonowania. Należy także wywołać klasy bazowej `Clone` metody, aby właściwości klasy bazowej są kopiowane do nowej komórce lub kolumnie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższy przykład wymaga:  
  
- Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
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
