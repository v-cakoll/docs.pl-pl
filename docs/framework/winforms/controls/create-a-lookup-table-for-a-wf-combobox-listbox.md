---
title: 'Instrukcje: Tworzenie tabeli wyszukiwania dla Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka'
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
ms.openlocfilehash: 264a50cb2f9346ea164cedfbe5ced5e231e246ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516528"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Instrukcje: Tworzenie tabeli wyszukiwania dla Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka
Czasami warto wyświetlić dane w formacie przyjazny dla użytkownika w formularzu Windows, ale przechowywać dane w formacie, który jest bardziej zrozumiały dla programu. Na przykład formularz zamówienia ds może wyświetlić elementy menu według nazwy w polu listy. Jednak w tabeli danych rejestrowania kolejność zawierałoby unikatowe numery identyfikacyjne reprezentujący żywności. W poniższej tabeli przedstawiono przykład sposobu przechowywania i wyświetlania danych w formularzu zamówienia ds.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|Identyfikator elementu|Ilość|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|Nazwa|  
|--------|----------|  
|12|Ziemniaczanej|  
|13|Kurczaka|  
  
 W tym scenariuszu jedna tabela **OrderDetailsTable**, przechowuje dotyczy wyświetlanie i zapisywanie informacji. Jednak aby zaoszczędzić przestrzeń, odbywa się to w sposób dość tajemnicze. Drugiej tabeli **ItemTable**, zawiera tylko informacje związane z wygląd o identyfikatorze, który odpowiada numer, którego food nazwy i nic o zamówieniach rzeczywiste żywności.  
  
 **ItemTable** jest podłączony do <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, lub <xref:System.Windows.Forms.CheckedListBox> kontrolki za pomocą trzech właściwości. `DataSource` Właściwość zawiera nazwę tej tabeli. `DisplayMember` Właściwość zawiera kolumny danych tej tabeli, która ma być wyświetlany w kontrolce (nazwa żywności). `ValueMember` Właściwość zawiera kolumny danych tej tabeli przy użyciu przechowywanych informacji (numer identyfikacyjny).  
  
 **OrderDetailsTable** jest podłączony do formantu przez jego kolekcję powiązań, dostępne za pośrednictwem <xref:System.Windows.Forms.Control.DataBindings%2A> właściwości. Po dodaniu obiektu wiązania w kolekcji, możesz nawiązać właściwości kontrolki określony element członkowski danych (kolumna numery identyfikatorów) w źródle danych ( **OrderDetailsTable**). Po dokonaniu wyboru w kontrolce, ta tabela to, gdzie są zapisywane w formularzu danych wejściowych.  
  
### <a name="to-create-a-lookup-table"></a>Można utworzyć tabeli odnośników  
  
1.  Dodaj <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, lub <xref:System.Windows.Forms.CheckedListBox> formantu do formularza.  
  
2.  Łączenie ze źródłem danych.  
  
3.  Ustanów relację danych między dwiema tabelami. Zobacz [wprowadzenie do obiektów DataRelation](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
4.  Ustaw następujące właściwości. Mogą być ustawiane w kodzie lub w projektancie.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Tabela, która zawiera informacje o identyfikatorze, który numer jest odpowiednikiem elementu. W poprzednim scenariuszu jest to `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Kolumna tabeli źródła danych, który ma być wyświetlany w formancie. W poprzednim scenariuszu jest to `"Name"` (można ustawić w kodzie, użyj znaków cudzysłowu).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Kolumna tabeli źródła danych, która zawiera zapisane informacje. W poprzednim scenariuszu jest to `"ID"` (można ustawić w kodzie, użyj znaków cudzysłowu).|  
  
5.  W procedurze, należy wywołać <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody <xref:System.Windows.Forms.ControlBindingsCollection> klasy do wiązania kontrolki <xref:System.Windows.Forms.ListControl.SelectedValue%2A> właściwości do tabeli, rejestrowanie danych wejściowych z formularza. Użytkownik może to zrobić również w Projektancie zamiast w kodzie, uzyskując dostęp do formantu <xref:System.Windows.Forms.Control.DataBindings%2A> właściwość **właściwości** okna. W poprzednim scenariuszu jest to `OrderDetailsTable`, a kolumna jest `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Wiązanie danych i formularzy Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)
- [ListBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)
- [ComboBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)
- [CheckedListBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
