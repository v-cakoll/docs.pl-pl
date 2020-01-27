---
title: Dostęp do obiektów na liście rozwijanej DataGridViewComboBoxCell
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 7e76ab1ac9089778e4371f4ee65b06d5ebc570bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746310"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Porady: uzyskiwanie dostępu do obiektów na liście rozwijanej DataGridViewComboBoxCell formularzy systemu Windows
Podobnie jak w przypadku kontrolki <xref:System.Windows.Forms.ComboBox>, typy <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i <xref:System.Windows.Forms.DataGridViewComboBoxCell> umożliwiają dodawanie dowolnych obiektów do ich list rozwijanych. Za pomocą tej funkcji można reprezentować złożone Stany na liście rozwijanej bez konieczności przechowywania odpowiednich obiektów w oddzielnej kolekcji.  
  
 W przeciwieństwie do kontrolki <xref:System.Windows.Forms.ComboBox> typy <xref:System.Windows.Forms.DataGridView> nie mają właściwości <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> do pobrania aktualnie zaznaczonego obiektu. Zamiast tego należy ustawić właściwość <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> na nazwę właściwości w obiekcie biznesowym. Gdy użytkownik dokonuje wyboru, wskazana właściwość obiektu biznesowego ustawia właściwość <xref:System.Windows.Forms.DataGridViewCell.Value%2A> komórki.  
  
 Aby można było pobrać obiekt biznesowy za pomocą wartości komórki, właściwość `ValueMember` musi wskazywać właściwość, która zwraca odwołanie do obiektu biznesowego. W związku z tym, jeśli typ obiektu biznesowego nie znajduje się w kontrolce, należy dodać taką właściwość, rozszerzając typ przez dziedziczenie.  
  
 W poniższych procedurach pokazano, jak wypełnić listę rozwijaną z obiektami biznesowymi i pobrać obiekty za pomocą właściwości <xref:System.Windows.Forms.DataGridViewCell.Value%2A> komórki.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Aby dodać obiekty biznesowe do listy rozwijanej  
  
1. Utwórz nowy <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i wypełnij jego kolekcję <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>. Alternatywnie możesz ustawić Właściwość Column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> na kolekcję obiektów biznes. W takim przypadku nie można jednak dodać "nieprzypisane" do listy rozwijanej bez tworzenia odpowiedniego obiektu biznesowego w kolekcji.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. Ustaw właściwości <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> i <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> wskazuje właściwość obiektu biznesowego do wyświetlenia na liście rozwijanej. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> wskazuje właściwość, która zwraca odwołanie do obiektu biznesowego.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. Upewnij się, że typ obiektu biznesowego zawiera właściwość zwracającą odwołanie do bieżącego wystąpienia. Ta właściwość musi mieć nazwę z wartością przypisaną do <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> w poprzednim kroku.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Aby pobrać aktualnie wybrany obiekt biznesowy  
  
- Pobierz Właściwość <xref:System.Windows.Forms.DataGridViewCell.Value%2A> komórki i przerzutj ją na typ obiektu biznesowego.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Przykład  
 Kompletny przykład ilustruje użycie obiektów biznesowych na liście rozwijanej. W przykładzie formant <xref:System.Windows.Forms.DataGridView> jest powiązany z kolekcją obiektów `Task`. Każdy obiekt `Task` ma właściwość `AssignedTo`, która wskazuje obiekt `Employee` aktualnie przypisany do tego zadania. Kolumna `Assigned To` wyświetla wartość właściwości `Name` dla każdego przypisanego pracownika lub "UNASSIGNED", jeśli wartość właściwości `Task.AssignedTo` jest `null`.  
  
 Aby wyświetlić zachowanie tego przykładu, wykonaj następujące czynności:  
  
1. Zmień przypisania w kolumnie `Assigned To`, wybierając różne wartości z listy rozwijanej lub naciskając kombinację klawiszy CTRL + 0 w komórce pola kombi.  
  
2. Kliknij przycisk `Generate Report`, aby wyświetlić bieżące przypisania. Pokazuje to, że zmiana w kolumnie `Assigned To` automatycznie aktualizuje kolekcję `tasks`.  
  
3. Kliknij przycisk `Request Status`, aby wywołać metodę `RequestStatus` bieżącego obiektu `Employee` dla tego wiersza. Pokazuje to, że wybrany obiekt został pomyślnie pobrany.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
