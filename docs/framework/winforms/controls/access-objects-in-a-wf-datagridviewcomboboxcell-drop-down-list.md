---
title: 'Instrukcje: Uzyskiwanie dostępu do obiektów na liście rozwijanej kontrolki DataGridViewComboBoxCell formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 8a4731e081b31f74b4f17c2796b56cdf6b95e3e2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705730"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Instrukcje: Uzyskiwanie dostępu do obiektów na liście rozwijanej kontrolki DataGridViewComboBoxCell formularzy Windows
Podobnie jak <xref:System.Windows.Forms.ComboBox> kontroli <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i <xref:System.Windows.Forms.DataGridViewComboBoxCell> typy umożliwiają dodać dowolne obiekty do listy rozwijanej. Dzięki tej funkcji może reprezentować złożonych stanów na liście rozwijanej bez konieczności przechowywania odpowiednimi obiektami w oddzielnych kolekcji.  
  
 W odróżnieniu od <xref:System.Windows.Forms.ComboBox> kontroli <xref:System.Windows.Forms.DataGridView> typy nie mają <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> właściwości do pobierania aktualnie zaznaczonego obiektu. Zamiast tego należy ustawić <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> Właściwość Nazwa właściwości w obiekcie Twojej firmy. Po dokonaniu wyboru wskazanej właściwości obiektu biznesowego ustawia komórki <xref:System.Windows.Forms.DataGridViewCell.Value%2A> właściwości.  
  
 Można pobrać obiektu biznesowych za pomocą wartości komórki `ValueMember` właściwość musi wskazywać, właściwość, która zwraca odwołanie do samego obiektu biznesowych. W związku z tym jeśli typ obiektu firmy nie jest pod kontrolą, należy dodać taką właściwość, rozszerzając typ poprzez dziedziczenie.  
  
 Poniższe procedury przedstawiają sposób wypełnienia listy rozwijanej, za pomocą obiektów biznesowych i pobieranie obiektów za pomocą komórki <xref:System.Windows.Forms.DataGridViewCell.Value%2A> właściwości.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Aby dodać obiekty biznesowych do listy rozwijanej  
  
1.  Utwórz nową <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i wypełnić jego <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> kolekcji. Alternatywnie, można ustawić kolumny <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> właściwości do kolekcji obiektów biznesowych. W takim przypadku należy jednak nie można dodać "nieprzypisane" do listy rozwijanej bez tworzenia odpowiedniego obiektu biznesowego z kolekcji.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  Ustaw <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> i <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> właściwości. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> Wskazuje właściwość obiektu biznesowych do wyświetlenia na liście rozwijanej. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> Wskazuje właściwość, która zwraca odwołanie do obiektu biznesowego.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  Upewnij się, że typ obiektu usługi biznesowe zawiera właściwość, która zwraca odwołanie do bieżącego wystąpienia. Ta właściwość musi mieć nazwę z wartością przypisaną do <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> w poprzednim kroku.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Można pobrać obiektu obecnie biznesową  
  
-   Pobierz komórki <xref:System.Windows.Forms.DataGridViewCell.Value%2A> właściwości i go rzutować na typ object biznesowych.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Przykład  
 Pełny przykład demonstruje użycie obiektów biznesowych na liście rozwijanej. W tym przykładzie <xref:System.Windows.Forms.DataGridView> kontrolka jest powiązana z kolekcją `Task` obiektów. Każdy `Task` obiekt ma `AssignedTo` właściwość, która wskazuje `Employee` obiektu aktualnie przypisane do tego zadania. `Assigned To` Kolumna Wyświetla `Name` wartości właściwości dla każdego przypisanych pracowników lub jeśli "nieprzypisane" `Task.AssignedTo` wartość właściwości jest `null`.  
  
 Aby wyświetlić zachowanie tego przykładu, wykonaj następujące czynności:  
  
1.  Zmień przypisania w `Assigned To` kolumny, wybierając różne wartości z listy rozwijanej lub naciskając klawisze CTRL + 0, w komórce pola kombi.  
  
2.  Kliknij przycisk `Generate Report` Aby wyświetlić bieżące przypisania. Oznacza to, że zmiana `Assigned To` kolumny automatycznie aktualizuje `tasks` kolekcji.  
  
3.  Kliknij przycisk `Request Status` przycisk, aby wywołać `RequestStatus` metoda bieżącego `Employee` obiektu dla tego wiersza. Oznacza to, że wybrany obiekt zostały pomyślnie pobrane.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
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
