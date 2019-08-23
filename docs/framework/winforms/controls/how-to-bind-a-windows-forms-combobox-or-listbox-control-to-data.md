---
title: 'Instrukcje: powiązanie kontrolki ComboBox lub ListBox (Formularze systemu Windows) z danymi'
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
ms.openlocfilehash: f361526c44f8fbb9ab282fe15ae109b67e8f01dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922755"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Instrukcje: powiązanie kontrolki ComboBox lub ListBox (Formularze systemu Windows) z danymi
Można powiązać <xref:System.Windows.Forms.ComboBox> dane i <xref:System.Windows.Forms.ListBox> z danymi, aby wykonywać zadania, takie jak przeglądanie danych w bazie danych, wprowadzanie nowych danych lub edytowanie istniejących danych.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Aby powiązać formant ComboBox lub ListBox  
  
1. `DataSource` Ustaw właściwość na obiekt źródła danych. Możliwe źródła danych obejmują <xref:System.Windows.Forms.BindingSource> powiązanie z danymi, tabelą danych, widokiem danych, zestawem danych, menedżerem widoku dane, tablicą lub dowolną klasą, która <xref:System.Collections.IList> implementuje interfejs. Aby uzyskać więcej informacji, zobacz [źródła danych obsługiwane przez Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Jeśli tworzysz powiązanie z tabelą, ustaw `DisplayMember` właściwość na nazwę kolumny w źródle danych.  
  
     \- lub —  
  
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
    > Jeśli masz powiązanie ze źródłem danych, które nie implementuje <xref:System.ComponentModel.IBindingList> interfejsu, takiego <xref:System.Collections.ArrayList>jak, dane kontrolki powiązanej nie zostaną zaktualizowane po aktualizacji źródła danych. Na przykład jeśli masz pole kombi powiązane z <xref:System.Collections.ArrayList> <xref:System.Collections.ArrayList>, a dane są dodawane do, te nowe elementy nie pojawią się w polu kombi. Można jednak wymusić aktualizację pola kombi, wywołując <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> metody i <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> <xref:System.Windows.Forms.BindingContext> w wystąpieniu klasy, do której jest powiązany formant.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
- [Wiązanie danych i formularzy Windows Forms](../data-binding-and-windows-forms.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
