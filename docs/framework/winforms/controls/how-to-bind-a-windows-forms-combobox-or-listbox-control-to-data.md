---
title: Powiąż kontrolkę ComboBox lub ListBox z danymi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: 99d9b53b32d6faae888b134d4ed486980c05a75b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742036"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Porady: powiązanie formantu ComboBox lub ListBox (Formularze systemu Windows) z danymi
Można powiązać <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> z danymi, aby wykonywać zadania, takie jak przeglądanie danych w bazie danych, wprowadzanie nowych danych lub edytowanie istniejących danych.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Aby powiązać formant ComboBox lub ListBox  
  
1. Ustaw właściwość `DataSource` na obiekt źródła danych. Możliwe źródła danych obejmują <xref:System.Windows.Forms.BindingSource> powiązane z danymi, tabelą danych, widokiem danych, zestawem danych, menedżerem widoku dane, tablicą lub dowolną klasą, która implementuje interfejs <xref:System.Collections.IList>. Aby uzyskać więcej informacji, zobacz [źródła danych obsługiwane przez Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Jeśli tworzysz powiązanie z tabelą, ustaw właściwość `DisplayMember` na nazwę kolumny w źródle danych.  
  
     \- lub-  
  
     Jeśli tworzysz powiązanie z <xref:System.Collections.IList>, Ustaw element członkowski wyświetlania na publiczną właściwość typu na liście.  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    > Jeśli masz powiązanie ze źródłem danych, które nie implementuje interfejsu <xref:System.ComponentModel.IBindingList>, takiego jak <xref:System.Collections.ArrayList>, dane kontrolki powiązanej nie zostaną zaktualizowane po aktualizacji źródła danych. Na przykład jeśli masz pole kombi powiązane z <xref:System.Collections.ArrayList>em, a dane są dodawane do <xref:System.Collections.ArrayList>, te nowe elementy nie będą wyświetlane w polu kombi. Można jednak wymusić aktualizację pola kombi, wywołując <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> i <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metody w wystąpieniu klasy <xref:System.Windows.Forms.BindingContext>, do której jest powiązany formant.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
- [Wiązanie danych i formularzy Windows Forms](../data-binding-and-windows-forms.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
