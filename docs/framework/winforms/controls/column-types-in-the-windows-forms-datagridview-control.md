---
title: Typy kolumn w formancie DataGridView formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e45ddcec4459e376a5dab4eec36e51cc2e5e49c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Typy kolumn w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Kontrola korzysta kilka typów kolumn do wyświetlania jego informacji i umożliwiają użytkownikom modyfikowanie lub dodawanie informacji.  
  
 Po powiązaniu <xref:System.Windows.Forms.DataGridView> kontroli oraz ustawić <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> właściwości `true`, kolumny są generowane automatycznie przy użyciu domyślnych typów kolumn odpowiednie dla typów danych zawartych w źródle powiązania danych.  
  
 Możesz również samodzielnie utworzyć wystąpienia klasy kolumny i dodaj je do kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridView.Columns%2A> właściwości. Można utworzyć wystąpienia te do użycia jako niepowiązanych kolumn, lub ręcznie można powiązać. Ręcznie powiązane kolumny są przydatne, na przykład, jeśli chcesz zastąpić automatycznie wygenerowaną kolumny jednego typu kolumny innego typu.  
  
 W poniższej tabeli opisano dostępne w różnych klas kolumny <xref:System.Windows.Forms.DataGridView> formantu.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Używane z wartości tekstowych. Generowane automatycznie podczas wiązania z liczb i ciągów.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Używane z <xref:System.Boolean> i <xref:System.Windows.Forms.CheckState> wartości. Generowane automatycznie podczas wiązania z następujących typów wartości.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Umożliwia wyświetlanie obrazów. Generowane automatycznie podczas wiązania z tablic bajtowych <xref:System.Drawing.Image> obiektów, lub <xref:System.Drawing.Icon> obiektów.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Umożliwia wyświetlanie przycisków w komórkach. Automatycznie generowane podczas wiązania. Zwykle używane jako niepowiązanych kolumn.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Umożliwia wyświetlenie listy rozwijane w komórkach. Automatycznie generowane podczas wiązania. Zwykle powiązane z danymi ręcznie.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Umożliwia wyświetlenie łącza w komórkach. Automatycznie generowane podczas wiązania. Zwykle powiązane z danymi ręcznie.|  
|Danego typu kolumny niestandardowe|Można utworzyć klasy kolumny dziedziczenie <xref:System.Windows.Forms.DataGridViewColumn> klasy lub dowolny z jej klas pochodnych zapewnienie wygląd niestandardowych, zachowanie lub hostowanej kontrolki. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie komórek i kolumn w formancie DataGridView formularzy systemu Windows przez rozszerzanie ich zachowania i wyglądu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Te typy kolumn są opisane bardziej szczegółowo w poniższych sekcjach.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> Jest typu ogólnego przeznaczenia kolumny do użytku z wartości tekstowych, takich jak liczb i ciągów. W trybie edycji <xref:System.Windows.Forms.TextBox> formant jest wyświetlany w komórce aktywnej umożliwiające użytkownikom na modyfikowanie wartość komórki.  
  
 Wartości komórek są konwertowane na ciągi do wyświetlenia. Wartości wprowadzone lub zmodyfikowany przez użytkownika jest automatycznie przekształcany do tworzenia wartości komórki odpowiedni typ danych. Obsługa można dostosować te konwersje <xref:System.Windows.Forms.DataGridView.CellFormatting> i <xref:System.Windows.Forms.DataGridView.CellParsing> zdarzenia <xref:System.Windows.Forms.DataGridView> formantu.  
  
 Typ danych wartości komórki kolumny jest określona w <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> właściwości kolumny.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> Jest używany z <xref:System.Boolean> i <xref:System.Windows.Forms.CheckState> wartości. <xref:System.Boolean>Wyświetl wartości jako dwa lub trzy stanu pola wyboru, w zależności od wartości <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> właściwości. Jeśli kolumna jest powiązany z <xref:System.Windows.Forms.CheckState> wartości, <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> wartość właściwości jest `true` domyślnie.  
  
 Zazwyczaj wartości komórek pola wyboru są przeznaczone dla magazynu, takich jak innych danych, lub dla operacji zbiorczej. Jeśli chcesz odpowiedzieć natychmiast po kliknięciu komórki pola wyboru, może obsługiwać <xref:System.Windows.Forms.DataGridView.CellClick> zdarzeń, ale to zdarzenie występuje przed zaktualizowaniem wartość komórki. Jeśli potrzebujesz nowej wartości w czasie kliknij jedną z opcji jest można obliczyć, co będzie oczekiwanej wartości na podstawie bieżącej wartości. Innym rozwiązaniem jest natychmiast Zatwierdź zmiany i obsługiwać <xref:System.Windows.Forms.DataGridView.CellValueChanged> zdarzeń odpowiedzieć. Aby zatwierdzić zmiany po kliknięciu komórki, musi obsługiwać <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> zdarzeń. W obsłudze, jeśli bieżąca komórka jest pole wyboru, wywołanie <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> — metoda i przekaż <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> wartość.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> Służy do wyświetlania obrazów. Kolumny obrazu mogą być wypełniane automatycznie ze źródła danych, wypełnione ręcznie niepowiązanych kolumn lub dynamicznie wypełnione obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń.  
  
 Automatyczne wypełnianie kolumny obrazu ze źródła danych współpracuje z tablic bajtowych w różnych formatach obrazu, w tym wszystkie formatów obsługiwanych przez <xref:System.Drawing.Image> klasy i obraz OLE format używany przez program Microsoft® dostępu i przykładowej bazy danych Northwind.  
  
 Wypełnianie ręcznie kolumnę obrazu jest przydatne, gdy chcesz zapewnić funkcjonalność <xref:System.Windows.Forms.DataGridViewButtonColumn>, ale z dostosowanego wyglądu. Może obsłużyć <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> zdarzeń na odpowiadanie na kliknięcia w komórce obrazu.  
  
 Wypełnianie komórek w kolumnie obrazu programu obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń jest przydatne, gdy chcesz zapewnić obrazy obliczone wartości lub wartości w formatach z systemem innym niż obraz. Na przykład może być kolumną "Ryzyka" z ciągami takich jak `"high"`, `"middle"`, i `"low"` , który ma być wyświetlany jako ikony. Alternatywnie może mieć kolumnę "Obrazu", która zawiera lokalizacje obrazów, które muszą zostać załadowane zamiast zawartość binarną obrazów.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 Z <xref:System.Windows.Forms.DataGridViewButtonColumn>, można wyświetlić kolumny komórek zawierających przycisków. Jest to przydatne, gdy chcesz zapewnić łatwą metodę dla użytkowników do wykonywania działań w szczególności rekordów, takich jak kolejność wprowadzania lub wyświetlanie podrzędne rekordy w osobnym oknie.  
  
 Przycisk kolumn nie są generowane automatycznie podczas wiązania z danymi <xref:System.Windows.Forms.DataGridView> formantu. Aby użyć kolumnach przycisków, należy ręcznie utworzyć i dodać je do kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> właściwości.  
  
 Obsługa może odpowiedzieć użytkownik klika przycisk w komórkach przycisk <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> zdarzeń.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 Z <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, można wyświetlić kolumny komórek zawierających pola listy rozwijanej. Jest to przydatne w przypadku wprowadzania danych w polach, które mogą zawierać tylko określonej wartości, takich jak kolumny kategorii produktów tabeli w bazie danych Northwind.  
  
 Można go wypełnić listy rozwijanej używane dla wszystkich komórek w taki sam sposób czy wypełnić <xref:System.Windows.Forms.ComboBox> listy rozwijanej, albo ręcznie za pomocą kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> właściwości, lub przez jego powiązanie ze źródłem danych za pośrednictwem <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, i <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> właściwości. Aby uzyskać więcej informacji, zobacz [formantu ComboBox](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md).  
  
 Źródło danych używane przez można powiązać wartości rzeczywistych komórek <xref:System.Windows.Forms.DataGridView> kontroli przez ustawienie <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> właściwość <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Kolumny pola kombi nie są generowane automatycznie podczas wiązania z danymi <xref:System.Windows.Forms.DataGridView> formantu. Aby użyć kolumny pola kombi, należy ręcznie utworzyć i dodaj je do kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridView.Columns%2A> właściwości.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 Z <xref:System.Windows.Forms.DataGridViewLinkColumn>, można wyświetlić kolumny komórek zawierających hiperłącza. Jest to przydatne dla wartości adres URL źródła danych lub zamiast kolumnie przycisków dla specjalnych zachowań, takich jak otwarcie okna z podrzędne rekordy.  
  
 Łącze kolumn nie są generowane automatycznie podczas wiązania z danymi <xref:System.Windows.Forms.DataGridView> formantu. Używanie kolumn łączy, należy ręcznie utworzyć i dodać je do kolekcji zwróconej przez <xref:System.Windows.Forms.DataGridView.Columns%2A> właściwości.  
  
 Obsługa może odpowiedzieć użytkownik klika przycisk łącza <xref:System.Windows.Forms.DataGridView.CellContentClick> zdarzeń. To zdarzenie różni się od <xref:System.Windows.Forms.DataGridView.CellClick> i <xref:System.Windows.Forms.DataGridView.CellMouseClick> zdarzenia, które występują, gdy użytkownik kliknie w dowolnym miejscu w komórce.  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> Klasa udostępnia kilka właściwości modyfikowania wyglądu łączy przed, podczas i po kliknięciu ich.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewImageColumn>  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>  
 [DataGridView — formant](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Porady: wyświetlanie obrazów w komórkach systemu Windows do formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 [Porady: Praca z kolumnami obrazów w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 [Dostosowywanie formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
