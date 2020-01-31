---
title: Typy kolumn w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: e918394cca6350854074d4c1567890138b2a1462
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743855"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Typy kolumn w formancie DataGridView formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.DataGridView> używa kilku typów kolumn do wyświetlania informacji i umożliwia użytkownikom modyfikowanie lub Dodawanie informacji.  
  
 Po powiązaniu formantu <xref:System.Windows.Forms.DataGridView> i ustawieniu właściwości <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> na `true`kolumny są generowane automatycznie przy użyciu domyślnych typów kolumn odpowiednich dla typów danych zawartych w powiązanym źródle danych.  
  
 Możesz również utworzyć wystąpienia dowolnej klasy kolumn i dodać je do kolekcji zwróconej przez właściwość <xref:System.Windows.Forms.DataGridView.Columns%2A>. Te wystąpienia można utworzyć do użycia jako kolumny niepowiązane lub można je ręcznie powiązać. Kolumny powiązane ręcznie są przydatne, na przykład gdy chcesz zastąpić automatycznie wygenerowaną kolumnę jednego typu kolumną innego typu.  
  
 W poniższej tabeli opisano różne klasy kolumn dostępne do użycia w kontrolce <xref:System.Windows.Forms.DataGridView>.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Używany z wartościami tekstowymi. Generowane automatycznie podczas wiązania z liczbami i ciągami.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Używany z wartościami <xref:System.Boolean> i <xref:System.Windows.Forms.CheckState>. Generowane automatycznie podczas wiązania z wartościami tych typów.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Używane do wyświetlania obrazów. Generowane automatycznie podczas tworzenia powiązań z tablicami bajtowymi, obiektami <xref:System.Drawing.Image> lub obiektami <xref:System.Drawing.Icon>.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Używane do wyświetlania przycisków w komórkach. Nie generowane automatycznie podczas tworzenia powiązania. Zwykle używane jako kolumny niepowiązane.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Służy do wyświetlania list rozwijanych w komórkach. Nie generowane automatycznie podczas tworzenia powiązania. Zwykle są one powiązane z danymi ręcznie.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Służy do wyświetlania linków w komórkach. Nie generowane automatycznie podczas tworzenia powiązania. Zwykle są one powiązane z danymi ręcznie.|  
|Typ kolumny niestandardowej|Można utworzyć własną klasę kolumn przez dziedziczenie klasy <xref:System.Windows.Forms.DataGridViewColumn> lub dowolnej z jej klas pochodnych w celu zapewnienia niestandardowego wyglądu, zachowania lub formantów hostowanych. Aby uzyskać więcej informacji, zobacz [How to: dostosowywanie komórek i kolumn w kontrolce DataGridView Windows Forms przez rozszerzenie ich zachowania i wyglądu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Te typy kolumn są opisane bardziej szczegółowo w poniższych sekcjach.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> to typ kolumny ogólnego przeznaczenia do użycia z wartościami tekstowymi, takimi jak liczby i ciągi. W trybie edycji w aktywnej komórce zostanie wyświetlony formant <xref:System.Windows.Forms.TextBox>, co umożliwia użytkownikom modyfikowanie wartości komórki.  
  
 Wartości komórek są automatycznie konwertowane na ciągi na potrzeby wyświetlania. Wartości wprowadzone lub zmodyfikowane przez użytkownika są automatycznie analizowane w celu utworzenia wartości komórki odpowiedniego typu danych. Można dostosować te konwersje poprzez obsługę zdarzeń <xref:System.Windows.Forms.DataGridView.CellFormatting> i <xref:System.Windows.Forms.DataGridView.CellParsing> kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
 Typ danych wartości komórki kolumny jest określony we właściwości <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> kolumny.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> jest używany z wartościami <xref:System.Boolean> i <xref:System.Windows.Forms.CheckState>. wartości <xref:System.Boolean> są wyświetlane jako dwa lub trzy stany, w zależności od wartości właściwości <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>. Gdy kolumna jest powiązana z wartościami <xref:System.Windows.Forms.CheckState>, domyślnie `true` wartość właściwości <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>.  
  
 Zazwyczaj wartości komórek pola wyboru są przeznaczone dla magazynu, podobnie jak inne dane, lub do wykonywania operacji zbiorczych. Jeśli chcesz odpowiedzieć natychmiast po kliknięciu komórki pola wyboru, możesz obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.CellClick>, ale to zdarzenie występuje przed zaktualizowaniem wartości komórki. Jeśli potrzebujesz nowej wartości w momencie kliknięcia, jedną z opcji jest obliczenie wartości oczekiwanej na podstawie bieżącej wartości. Innym rozwiązaniem jest natychmiastowe zatwierdzenie zmiany i obsłużenie zdarzenia <xref:System.Windows.Forms.DataGridView.CellValueChanged>, aby odpowiedzieć na to zdarzenie. Aby zatwierdzić zmianę po kliknięciu komórki, należy obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>. W programie obsługi, jeśli bieżąca komórka jest komórką pola wyboru, wywołaj metodę <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> i przekaż wartość <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit>.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> jest używany do wyświetlania obrazów. Kolumny obrazu mogą być wypełniane automatycznie ze źródła danych, wypełniane ręcznie w przypadku kolumn niepowiązanych lub wypełniane dynamicznie w programie obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting>.  
  
 Automatyczne wypełnianie kolumny obrazu ze źródła danych współpracuje z tablicami bajtowymi w różnych formatach obrazu, w tym na wszystkich formatach obsługiwanych przez klasę <xref:System.Drawing.Image> i formacie obrazu OLE używanego przez program Microsoft® Access i przykładową bazę danych Northwind.  
  
 Ręczne wypełnienie kolumny obrazu jest przydatne, gdy chcesz zapewnić funkcjonalność <xref:System.Windows.Forms.DataGridViewButtonColumn>, ale z niestandardowym wyglądem. Możesz obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>, aby reagować na kliknięcia w komórce obrazu.  
  
 Zapełnianie komórek kolumny obrazu w procedurze obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting> jest przydatne, gdy chcesz udostępnić obrazy dla obliczonych wartości lub wartości w formatach bez obrazu. Na przykład może istnieć kolumna "ryzyko" z wartościami ciągu, takimi jak `"high"`, `"middle"`i `"low"`, które mają być wyświetlane jako ikony. Alternatywnie można mieć kolumnę "Image" zawierającą lokalizacje obrazów, które muszą zostać załadowane zamiast zawartości binarnej obrazów.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 Za pomocą <xref:System.Windows.Forms.DataGridViewButtonColumn>można wyświetlić kolumnę komórek zawierających przyciski. Jest to przydatne, gdy chcesz, aby użytkownicy mogli w łatwy sposób wykonywać działania dotyczące konkretnych rekordów, takich jak umieszczanie zamówienia lub wyświetlanie rekordów podrzędnych w osobnym oknie.  
  
 Kolumny przycisków nie są generowane automatycznie, gdy dane są powiązane z formantem <xref:System.Windows.Forms.DataGridView>. Aby użyć kolumn przycisków, należy je utworzyć ręcznie i dodać do kolekcji zwróconej przez właściwość <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>.  
  
 Możesz odpowiedzieć na kliknięcia przez użytkownika w komórkach przycisków przez obsługę zdarzenia <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 Za pomocą <xref:System.Windows.Forms.DataGridViewComboBoxColumn>można wyświetlić kolumnę komórek zawierających pola listy rozwijanej. Jest to przydatne w przypadku wprowadzania danych w polach, które mogą zawierać tylko określone wartości, takie jak kolumna Category tabeli Products w przykładowej bazie danych Northwind.  
  
 Można wypełnić listę rozwijaną używaną dla wszystkich komórek w taki sam sposób, jak w przypadku <xref:System.Windows.Forms.ComboBox> listę rozwijaną ręcznie za pomocą kolekcji zwróconej przez właściwość <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> lub przez powiązanie jej ze źródłem danych za pomocą właściwości <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>i <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>. Aby uzyskać więcej informacji, zobacz [kontrolka ComboBox](combobox-control-windows-forms.md).  
  
 Rzeczywiste wartości komórek można powiązać ze źródłem danych używanym przez formant <xref:System.Windows.Forms.DataGridView> przez ustawienie właściwości <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Kolumny pól kombi nie są generowane automatycznie, gdy dane są powiązane z formantem <xref:System.Windows.Forms.DataGridView>. Aby użyć kolumn pola kombi, należy je utworzyć ręcznie i dodać do kolekcji zwróconej przez właściwość <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 Za pomocą <xref:System.Windows.Forms.DataGridViewLinkColumn>można wyświetlić kolumnę komórek zawierających hiperłącza. Jest to przydatne w przypadku wartości adresu URL w źródle danych lub jako alternatywy dla kolumny Button dla zachowań specjalnych, takich jak otwieranie okna z rekordami podrzędnymi.  
  
 Kolumny łączy nie są generowane automatycznie podczas wiązania <xref:System.Windows.Forms.DataGridView> formantu z danymi. Aby użyć kolumn łączy, należy je utworzyć ręcznie i dodać do kolekcji zwróconej przez właściwość <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
 Możesz odpowiedzieć na kliknięcia przez użytkowników w łączach, obsługując zdarzenia <xref:System.Windows.Forms.DataGridView.CellContentClick>. To zdarzenie jest odrębne względem zdarzeń <xref:System.Windows.Forms.DataGridView.CellClick> i <xref:System.Windows.Forms.DataGridView.CellMouseClick>, które pojawiają się, gdy użytkownik kliknie gdziekolwiek w komórce.  
  
 Klasa <xref:System.Windows.Forms.DataGridViewLinkColumn> udostępnia kilka właściwości do modyfikowania wyglądu linków przed, w trakcie i po kliknięciu.  
  
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
- [Instrukcje: wyświetlanie obrazów w komórkach kontrolki DataGridView formularzy Windows Forms](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [Instrukcje: praca z kolumnami obrazów w kontrolce DataGridView formularzy Windows Forms](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
