---
title: Typy kolumn w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: a33cf4cd865921c04ef10c7fccf3a67c3d22de73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115677"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Typy kolumn w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Kontrola korzysta kilka typów kolumn w celu wyświetlania jej informacji i umożliwiają użytkownikom modyfikowanie lub dodawanie informacji.  
  
 Po powiązaniu <xref:System.Windows.Forms.DataGridView> i ustaw <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> właściwości `true`, kolumny są generowane automatycznie za pomocą typów kolumn domyślne odpowiednie dla typów danych znajdujących się w źródle danych powiązanych.  
  
 Możesz również samodzielnie utworzyć wystąpienia klasy kolumny i dodaj je do kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridView.Columns%2A> właściwości. Możesz utworzyć te wystąpienia do użycia jako niepowiązanych kolumn lub ręcznie można powiązać. Ręcznie powiązane kolumny są przydatne, na przykład, jeśli chcesz zastąpić automatycznie wygenerowaną kolumny jednego typu kolumnę innego typu.  
  
 W poniższej tabeli opisano dostępne do użycia w różnych zajęciach kolumny <xref:System.Windows.Forms.DataGridView> kontroli.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Używane z wartości tekstowych. Generowane automatycznie, podczas tworzenia wiązania do liczb i ciągów.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Używane z <xref:System.Boolean> i <xref:System.Windows.Forms.CheckState> wartości. Generowane automatycznie, podczas tworzenia wiązania do następujących typów wartości.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Umożliwia wyświetlanie obrazów. Generowane automatycznie, gdy powiązanie z tablic bajtowych <xref:System.Drawing.Image> obiektów, lub <xref:System.Drawing.Icon> obiektów.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Umożliwia wyświetlanie przycisków w komórkach. Automatycznie generowane podczas tworzenia powiązania. Zazwyczaj jest używane jako niepowiązanych kolumn.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Umożliwia wyświetlenie listy rozwijane w komórkach. Automatycznie generowane podczas tworzenia powiązania. Zazwyczaj powiązane z danymi ręcznie.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Umożliwia wyświetlenie łącza w komórkach. Automatycznie generowane podczas tworzenia powiązania. Zazwyczaj powiązane z danymi ręcznie.|  
|Typu kolumny niestandardowej|Można utworzyć klasy kolumny przez dziedziczenie <xref:System.Windows.Forms.DataGridViewColumn> klasy lub dowolny z jej klas pochodnych zapewnienie niestandardowy wygląd, zachowanie lub hostowanej kontrolki. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie komórek i kolumn w kontrolce DataGridView formularzy Windows Forms przez rozszerzanie ich zachowania i wyglądu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Te typy kolumn są opisane bardziej szczegółowo w poniższych sekcjach.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> Jest typu ogólnego przeznaczenia kolumny do użytku z wartości tekstowych, takie jak liczb i ciągów. W trybie edycji <xref:System.Windows.Forms.TextBox> formant jest wyświetlany w aktywnej komórce, umożliwiając użytkownikom zmodyfikować wartość komórki.  
  
 Wartości komórek są automatycznie konwertowane na ciągi do wyświetlenia. Wartości wprowadzone lub zmodyfikowany przez użytkownika są automatycznie przeanalizować w celu utworzenia wartości komórki odpowiedni typ danych. Można dostosować te konwersje obsługi <xref:System.Windows.Forms.DataGridView.CellFormatting> i <xref:System.Windows.Forms.DataGridView.CellParsing> zdarzenia <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 Typ danych wartości komórek kolumny jest określona w <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> właściwości kolumny.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> Jest używana z <xref:System.Boolean> i <xref:System.Windows.Forms.CheckState> wartości. <xref:System.Boolean> wartości są wyświetlane jako dwustanowy lub trójstanowych pól wyboru, w zależności od wartości <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> właściwości. Jeśli kolumna jest powiązany z <xref:System.Windows.Forms.CheckState> wartości <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> wartość właściwości jest `true` domyślnie.  
  
 Zazwyczaj pole wartości komórek są przeznaczone dla magazynu, takich jak inne dane, lub do wykonywania operacji zbiorczej. Jeśli chcesz odpowiedzieć natychmiast, gdy użytkownik kliknie komórki pole wyboru, które ułatwią Ci obsługę <xref:System.Windows.Forms.DataGridView.CellClick> zdarzenia, ale to zdarzenie występuje przed zaktualizowaniem wartość komórki. Jeśli potrzebujesz nową wartość w czasie kliknij jedną z opcji jest do obliczania, co będzie oczekiwanej wartości na podstawie bieżącej wartości. Innym rozwiązaniem jest natychmiastowe Zatwierdź zmianę i obsłużyć <xref:System.Windows.Forms.DataGridView.CellValueChanged> zdarzenie, aby odpowiedzieć na. Aby zatwierdzić zmiany, po kliknięciu komórki, musi obsługiwać <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> zdarzeń. W procedurze obsługi Jeśli bieżąca komórka jest pole wyboru, wywołaj <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> metody i przekaż <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> wartość.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> Służy do wyświetlania obrazów. Obraz kolumny mogą być wypełniane automatycznie ze źródła danych, wypełnieniu ręcznie niepowiązanych kolumn lub dynamicznie wypełnione w obsłudze dla <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń.  
  
 Automatyczne populacji kolumny obrazów ze źródła danych współpracuje z tablic bajtowych w różnych formatach obrazu, w tym wszystkie formaty obsługiwane przez <xref:System.Drawing.Image> klasy i format obrazu OLE, używany przez Microsoft® Access i bazie danych Northwind.  
  
 Wypełnianie ręcznie kolumnę obrazu jest przydatne, gdy chcesz zapewnić funkcjonalność <xref:System.Windows.Forms.DataGridViewButtonColumn>, ale z dostosowanego wyglądu. Może obsługiwać <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> zdarzenie, aby odpowiadanie na kliknięcia w obrębie obrazu komórki.  
  
 Wypełnianie komórek kolumny obrazu w obsłudze dla <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń jest przydatne w przypadku, gdy chcesz udostępnić obrazy obliczone wartości lub wartości w formatach-image. Na przykład masz kolumnę "Ryzyko" z wartościami ciągów takich jak `"high"`, `"middle"`, i `"low"` , którą chcesz wyświetlić jako ikony. Alternatywnie możesz mieć kolumnę "Image", która zawiera lokalizacje obrazów, które muszą być ładowane zamiast zawartość binarną obrazów.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 Za pomocą <xref:System.Windows.Forms.DataGridViewButtonColumn>, można wyświetlić kolumny komórek zawierających przycisków. Jest to przydatne, gdy chcesz zapewnić łatwą metodę dla użytkowników do wykonywania akcji względem określonego rekordów, takich jak złożeniu zamówienia lub wyświetlanie rekordów podrzędnych w osobnym oknie.  
  
 Przycisk kolumny nie są generowane automatycznie, gdy powiązanie danych <xref:System.Windows.Forms.DataGridView> kontroli. Aby użyć kolumnach przycisków, należy ręcznie utworzyć i dodać je do kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> właściwości.  
  
 Można odpowiedzieć użytkownik kliknie przycisk komórek, obsługując <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> zdarzeń.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 Za pomocą <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, można wyświetlić kolumny komórki, które zawierają pola listy rozwijanej. Jest to przydatne do wprowadzania danych w polach, które mogą zawierać tylko określonej wartości, takich jak kolumna kategorii produktów tabeli w bazie danych Northwind.  
  
 Można wypełnić listy rozwijanej, używany dla wszystkich komórek w taki sam sposób, może wypełnić <xref:System.Windows.Forms.ComboBox> listy rozwijanej, albo ręcznie za pomocą kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> właściwości lub tworząc powiązanie ze źródłem danych za pośrednictwem <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, i <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> właściwości. Aby uzyskać więcej informacji, zobacz [ComboBox, kontrolka](combobox-control-windows-forms.md).  
  
 Można powiązać wartości komórek rzeczywistego źródła danych używanego przez <xref:System.Windows.Forms.DataGridView> kontroli przez ustawienie <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> właściwość <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Kolumny pola kombi nie są generowane automatycznie, gdy powiązanie danych <xref:System.Windows.Forms.DataGridView> kontroli. Aby użyć kolumny pola kombi, należy ręcznie utworzyć i dodać je do kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridView.Columns%2A> właściwości.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 Za pomocą <xref:System.Windows.Forms.DataGridViewLinkColumn>, można wyświetlić kolumny komórki, które zawierają hiperłącza. Jest to przydatne w przypadku wartości adresu URL w źródle danych lub jako alternatywa kolumnie przycisków dla zachowania specjalnych, takich jak otwieranie okna podrzędne rekordy.  
  
 Link kolumny nie są generowane automatycznie, gdy powiązanie danych <xref:System.Windows.Forms.DataGridView> kontroli. Aby użyć linku kolumn, należy ręcznie utworzyć i dodać je do kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridView.Columns%2A> właściwości.  
  
 Można odpowiedzieć użytkownik kliknie w łączach, obsługując <xref:System.Windows.Forms.DataGridView.CellContentClick> zdarzeń. To zdarzenie różni się od <xref:System.Windows.Forms.DataGridView.CellClick> i <xref:System.Windows.Forms.DataGridView.CellMouseClick> zdarzenia, które występują, gdy użytkownik kliknie w dowolnym miejscu w komórce.  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> Klasa udostępnia kilka właściwości do modyfikowania wyglądu łączy przed, podczas i po ich kliknięciu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewButtonColumn>
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewImageColumn>
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>
- <xref:System.Windows.Forms.DataGridViewLinkColumn>
- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [Instrukcje: Wyświetlanie obrazów w komórkach kontrolki DataGridView formularzy Windows Forms](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [Instrukcje: Praca z kolumnami obrazów w kontrolce DataGridView formularzy Windows Forms](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
