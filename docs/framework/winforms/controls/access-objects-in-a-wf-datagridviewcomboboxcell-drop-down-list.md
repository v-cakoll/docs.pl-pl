---
title: "Porady: uzyskiwanie dostępu do obiektów na liście rozwijanej DataGridViewComboBoxCell formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0fac2e73e76ad49a5b1ce6942f3ae2b4c0584e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Porady: uzyskiwanie dostępu do obiektów na liście rozwijanej DataGridViewComboBoxCell formularzy systemu Windows
Podobnie jak <xref:System.Windows.Forms.ComboBox> kontroli, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i <xref:System.Windows.Forms.DataGridViewComboBoxCell> typy umożliwiają dodanie dowolne obiekty do listy rozwijanej. W przypadku tej funkcji może reprezentować złożonych stany na liście rozwijanej bez konieczności przechowywania odpowiednimi obiektami w oddzielnych kolekcji.  
  
 W odróżnieniu od <xref:System.Windows.Forms.ComboBox> kontroli, <xref:System.Windows.Forms.DataGridView> typy nie mają <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> właściwości pobierania obecnie wybranego obiektu. Zamiast tego należy ustawić <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> właściwości do nazwy właściwości na obiekt biznesowy. Po dokonaniu wyboru wskazanej właściwości powiązania obiektu biznesowego ustawia komórki <xref:System.Windows.Forms.DataGridViewCell.Value%2A> właściwości.  
  
 Można pobrać obiektu biznesowego przez wartość komórki `ValueMember` właściwości musi wskazywać właściwość, która zwraca odwołanie do samego obiektu biznesowego. W związku z tym jeśli typ powiązania obiektu biznesowego nie jest pod kontrolą, należy dodać takie właściwości przez rozszerzenie typu za pomocą dziedziczenia.  
  
 Poniższe procedury pokazują, jak do wypełnienia listy rozwijanej z obiektów biznesowych i pobrać obiektów za pomocą komórki <xref:System.Windows.Forms.DataGridViewCell.Value%2A> właściwości.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Aby dodać obiekty biznesowych do listy rozwijanej  
  
1.  Utwórz nową <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i wypełnić jego <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> kolekcji. Alternatywnie, można ustawić kolumny <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> właściwości do kolekcji obiektów biznesowych. W takim przypadku jednak nie można dodać "nieprzypisane" do listy rozwijanej bez tworzenia odpowiedniego obiektu biznesowego z kolekcji.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  Ustaw <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> i <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> właściwości. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>Wskazuje właściwość powiązania obiektu biznesowego do wyświetlenia na liście rozwijanej. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>Wskazuje właściwość, która zwraca odwołanie do obiektu biznesowego.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  Upewnij się, że danego typu obiektu biznesowa zawiera właściwość, która zwraca odwołanie do bieżącego wystąpienia. Ta właściwość musi mieć nazwę z wartością przypisaną do <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> w poprzednim kroku.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Pobiera obiekt obecnie biznesową  
  
-   Pobierz komórki <xref:System.Windows.Forms.DataGridViewCell.Value%2A> właściwości i rzutować go do typu obiektu biznesowego.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Przykład  
 Pełny przykład ilustruje obiektów biznesowe na liście rozwijanej. W tym przykładzie <xref:System.Windows.Forms.DataGridView> kontrolka jest powiązana z kolekcją `Task` obiektów. Każdy `Task` obiekt ma `AssignedTo` właściwość, która wskazuje `Employee` obiektu aktualnie przypisane do tego zadania. `Assigned To` Wyświetla kolumny `Name` przypisane wartości właściwości dla każdego pracownika lub, jeśli "nieprzypisane" `Task.AssignedTo` wartość właściwości jest `null`.  
  
 Aby wyświetlić zachowanie w tym przykładzie, wykonaj następujące czynności:  
  
1.  Zmienić przypisania w `Assigned To` kolumny, wybierając różne wartości z listy rozwijanej lub naciskając klawisz CTRL + 0 w komórce pola kombi.  
  
2.  Kliknij przycisk `Generate Report` Aby wyświetlić bieżące przypisania. Oznacza to, że zmiana `Assigned To` kolumny automatycznie aktualizuje `tasks` kolekcji.  
  
3.  Kliknij przycisk `Request Status` przycisk, aby wywołać `RequestStatus` metody bieżącego `Employee` obiekt dla tego wiersza. Oznacza to, że wybrany obiekt zostały pomyślnie pobrane.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu i System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [Wyświetlanie danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
