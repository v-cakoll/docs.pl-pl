---
title: Tworzenie tabeli odnośników dla kontrolki ComboBox, ListBox lub CheckedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737370"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Porady: tworzenie tabeli wyszukiwania dla formantów ComboBox, ListBox i CheckedListBox formularzy systemu Windows
Czasami warto wyświetlać dane w formacie przyjaznym dla użytkownika w formularzu systemu Windows, ale przechowywać dane w formacie, który jest bardziej zrozumiały dla programu. Na przykład formularz zamówienia dla żywności może wyświetlać elementy menu według nazwy w polu listy. Jednak tabela danych, która rejestruje zamówienie, będzie zawierać unikatowe numery IDENTYFIKACYJNe reprezentujące żywność. W poniższych tabelach przedstawiono przykład przechowywania i wyświetlania danych formularza zamówienia dla żywności.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|Wartooć|Elementów|Liczba|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>Element  
  
|ID|Nazwa|  
|--------|----------|  
|12|Ziemniaczan|  
|13|Kury|  
  
 W tym scenariuszu w jednej tabeli, **OrderDetailsTable**przechowywane są rzeczywiste informacje, które są potrzebne do wyświetlania i zapisywania. Jednak aby zaoszczędzić miejsce, robi to w dość tajemnicze sposób. Druga tabela, **element Items**, zawiera tylko informacje dotyczące wyglądu, na których numer identyfikacyjny jest równoważny z nazwą żywności, a nic nie dotyczy rzeczywistych zamówień żywności.  
  
 **Element Item** jest połączony z <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>lub kontroli <xref:System.Windows.Forms.CheckedListBox> przez trzy właściwości. Właściwość `DataSource` zawiera nazwę tej tabeli. Właściwość `DisplayMember` zawiera kolumnę danych tej tabeli, która ma być wyświetlana w formancie (nazwa żywności). Właściwość `ValueMember` zawiera kolumnę danych tej tabeli zawierającą przechowywane informacje (numer IDENTYFIKACYJNy).  
  
 **OrderDetailsTable** jest połączona z kontrolką przez kolekcję powiązań, do której można uzyskać dostęp za pomocą właściwości <xref:System.Windows.Forms.Control.DataBindings%2A>. Po dodaniu obiektu powiązania do kolekcji, należy połączyć właściwość kontrolki z określonym członkiem danych (kolumna numerów IDENTYFIKACYJNych) w źródle danych ( **OrderDetailsTable**). Po dokonaniu wyboru w kontrolce, w tej tabeli jest zapisywane dane wejściowe formularza.  
  
### <a name="to-create-a-lookup-table"></a>Aby utworzyć tabelę odnośników  
  
1. Dodaj kontrolkę <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>lub <xref:System.Windows.Forms.CheckedListBox> do formularza.  
  
2. Nawiąż połączenie ze źródłem danych.  
  
3. Ustanów relację danych między dwiema tabelami. Zobacz [wprowadzenie do obiektów DataRelations](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).  
  
4. Ustaw następujące właściwości. Można je ustawić w kodzie lub w projektancie.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Tabela zawierająca informacje o IDENTYFIKATORze odpowiadającym elementowi. W poprzednim scenariuszu jest to `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Kolumna tabeli źródła danych, która ma być wyświetlana w formancie. W poprzednim scenariuszu jest to `"Name"` (aby ustawić w kodzie, używać cudzysłowów).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Kolumna tabeli źródła danych zawierająca przechowywane informacje. W poprzednim scenariuszu jest to `"ID"` (aby ustawić w kodzie, używać cudzysłowów).|  
  
5. W procedurze należy wywołać metodę <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> klasy <xref:System.Windows.Forms.ControlBindingsCollection>, aby powiązać Właściwość <xref:System.Windows.Forms.ListControl.SelectedValue%2A> kontrolki z tabelą, która rejestruje dane wejściowe formularza. Można to również zrobić w projektancie zamiast w kodzie, uzyskując dostęp do właściwości <xref:System.Windows.Forms.Control.DataBindings%2A> formantu w oknie **Właściwości** . W poprzednim scenariuszu jest `OrderDetailsTable`, a kolumna jest `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Wiązanie danych i formularzy Windows Forms](../data-binding-and-windows-forms.md)
- [ListBox, kontrolka — omówienie](listbox-control-overview-windows-forms.md)
- [ComboBox, kontrolka — omówienie](combobox-control-overview-windows-forms.md)
- [CheckedListBox, kontrolka — omówienie](checkedlistbox-control-overview-windows-forms.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
