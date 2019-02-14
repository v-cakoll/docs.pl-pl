---
title: 'Instrukcje: Kontrolki hosta w komórkach kontrolki DataGridView formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 86a1577174c12e55b23dd8bce2cf00ac0e780abb
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261261"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Instrukcje: Kontrolki hosta w komórkach kontrolki DataGridView formularzy Windows
<xref:System.Windows.Forms.DataGridView> Control oferuje kilka typów kolumn, aby umożliwić użytkownikom wprowadzanie i edytowanie wartości w na różne sposoby. Te typy kolumn nie odpowiadają Twoim potrzebom wprowadzanie danych, można jednak utworzyć swój własny typ kolumny, wraz z komórkami, które hostują formantów wybrane. Aby to zrobić, należy zdefiniować klas, które wynikają z <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewCell>. Należy także zdefiniować klasę, która pochodzi od klasy <xref:System.Windows.Forms.Control> i implementuje <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu.  
  
 Poniższy przykład kodu pokazuje sposób tworzenia kolumny kalendarza. Komórki w tej kolumnie wyświetlanie dat w komórkach pola zwykły tekst, ale w przypadku, gdy użytkownik edytuje komórkę, <xref:System.Windows.Forms.DateTimePicker> formant jest widoczny. Aby uniknąć konieczności implementowania funkcji wyświetlania pola tekstowego ponownie `CalendarCell` klasa pochodzi od <xref:System.Windows.Forms.DataGridViewTextBoxCell> klasy, a nie dziedziczy <xref:System.Windows.Forms.DataGridViewCell> klasy bezpośrednio.  
  
> [!NOTE]
>  Po utworzeniu klasy pochodnej z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, pamiętaj zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas operacji klonowania. Należy także wywołać klasy bazowej `Clone` metody, aby właściwości klasy bazowej są kopiowane do nowej komórce lub kolumnie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższy przykład wymaga:  
  
-   Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [DataGridView, kontrolka — architektura](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
