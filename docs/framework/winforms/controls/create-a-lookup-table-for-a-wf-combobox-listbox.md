---
title: "Porady: tworzenie tabeli wyszukiwania dla formantów ComboBox, ListBox i CheckedListBox formularzy systemu Windows"
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
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb7ffb8a7f20c1e53b24a1db8bda326d73743a93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Porady: tworzenie tabeli wyszukiwania dla formantów ComboBox, ListBox i CheckedListBox formularzy systemu Windows
Czasami jest przydatne do wyświetlania danych w formacie przyjazną dla użytkownika na formularzu systemu Windows, ale przechowywania danych w formacie, który jest bardziej zrozumiałej do programu. Na przykład w formularzu zamówienia ds może być wyświetlany elementów menu według nazwy w polu listy. Jednak w tabeli danych rejestrowania kolejność może zawierać unikatowe numery identyfikacyjne reprezentujący żywności. W poniższej tabeli przedstawiono przykład sposobu przechowywania i wyświetlania danych formularza zamówienia ds.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|Identyfikator elementu|Ilość|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|Nazwa|  
|--------|----------|  
|12|Ziemniaka|  
|13|Kurczaka|  
  
 W tym scenariuszu, w jednej tabeli, **OrderDetailsTable**, są przechowywane informacje dotyczy wyświetlanie i zapisywanie. Jednak aby zaoszczędzić miejsce, robi to w sposób dość one niezrozumiałe. Drugiej tabeli **ItemTable**, zawiera tylko informacje związane z wygląd o identyfikator, z którym odpowiada liczba, która nazwa żywności i nic o żywności rzeczywistej zleceń.  
  
 **ItemTable** jest podłączony do <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, lub <xref:System.Windows.Forms.CheckedListBox> sterowanie za pośrednictwem trzech właściwości. `DataSource` Właściwość zawiera nazwę tej tabeli. `DisplayMember` Właściwość zawiera kolumny danych tej tabeli, które mają być wyświetlane w formancie (nazwa żywności). `ValueMember` Właściwość zawiera kolumny danych tej tabeli z przechowywanych informacji (numer identyfikacyjny).  
  
 **OrderDetailsTable** jest podłączony do formantu przez jego kolekcję powiązań, dostępne za pośrednictwem <xref:System.Windows.Forms.Control.DataBindings%2A> właściwości. Po dodaniu obiektu powiązania w kolekcji właściwości formantu nawiązywane określony element członkowski danych (kolumna identyfikatorów) w źródle danych ( **OrderDetailsTable**). Po dokonaniu wyboru w formancie, ta tabela jest lokalizacji zapisywania danych wejściowych z formularza.  
  
### <a name="to-create-a-lookup-table"></a>Można utworzyć tabeli odnośników  
  
1.  Dodaj <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, lub <xref:System.Windows.Forms.CheckedListBox> sterowania do formularza.  
  
2.  Połączenie ze źródłem danych.  
  
3.  Należy ustanowić relację danych między dwiema tabelami. Zobacz [wprowadzenie do obiektów DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
4.  Ustaw następujące właściwości. Można można ustawić w kodzie, lub w projektancie.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Tabela, która zawiera informacje o identyfikator, z którym jest odpowiednikiem elementu numer. W poprzednim scenariuszu jest to `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Kolumna tabeli źródła danych, który ma być wyświetlany w formancie. W poprzednim scenariuszu jest to `"Name"` (można ustawić w kodzie, użyj cudzysłowów).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Kolumna tabeli źródła danych, który zawiera informacje przechowywane. W poprzednim scenariuszu jest to `"ID"` (można ustawić w kodzie, użyj cudzysłowów).|  
  
5.  W procedurze, wywołaj <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody <xref:System.Windows.Forms.ControlBindingsCollection> klasy do wiązania kontrolki <xref:System.Windows.Forms.ListControl.SelectedValue%2A> właściwości do tabeli rejestrowania danych wejściowych z formularza. Możesz również to zrobić w Projektancie zamiast w kodzie, uzyskując dostęp do formantu <xref:System.Windows.Forms.Control.DataBindings%2A> właściwości w **właściwości** okna. W poprzednim scenariuszu jest to `OrderDetailsTable`, a kolumna jest `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych i formularze systemu Windows](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Informacje o formancie ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [Informacje o formancie ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [CheckedListBox — informacje o formancie](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Formanty używane do obsługi opcji List formularzy systemu Windows](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
