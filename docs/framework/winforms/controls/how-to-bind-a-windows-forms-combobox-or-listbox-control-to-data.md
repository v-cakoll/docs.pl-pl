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
ms.openlocfilehash: b869898a20008343b6c6cbe4bc7e399fc86fb232
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306056"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Instrukcje: powiązanie kontrolki ComboBox lub ListBox (Formularze systemu Windows) z danymi
Możesz powiązać <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> z danymi w celu wykonania zadania, takie jak przeglądanie danych w bazie danych, wprowadzając nowe dane lub edycji istniejących danych.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Do wiązania kontrolki ComboBox lub ListBox  
  
1. Ustaw `DataSource` właściwość do obiektu źródła danych. Źródła danych zawierają <xref:System.Windows.Forms.BindingSource> powiązany z danymi, tabeli danych, widoku danych, zestaw danych, dane widoku menedżera, tablicy lub dowolnej klasy, która implementuje <xref:System.Collections.IList> interfejsu. Aby uzyskać więcej informacji, zobacz [źródła danych obsługiwane przez formularze Windows](../data-sources-supported-by-windows-forms.md).  
  
2. Jeśli powiązania do tabeli `DisplayMember` właściwość na nazwę kolumny w źródle danych.  
  
     \- lub —  
  
     Jeśli dokonywane jest wiązanie <xref:System.Collections.IList>, ustaw członka wyświetlana właściwość publiczną typu na liście.  
  
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
    >  Jeśli jesteś zobowiązany do źródła danych, który nie implementuje <xref:System.ComponentModel.IBindingList> interfejsu, takich jak <xref:System.Collections.ArrayList>, powiązanej kontrolki danych nie zostanie zaktualizowany, gdy źródło danych zostanie zaktualizowane. Na przykład, jeśli masz pole kombi są powiązane z <xref:System.Collections.ArrayList> i dane są dodawane do <xref:System.Collections.ArrayList>, te nowe elementy nie będą wyświetlane w polu kombi. Jednak można wymusić pola kombi do zaktualizowania przez wywołanie metody <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> i <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metod w wystąpieniu programu <xref:System.Windows.Forms.BindingContext> klasy, do którego formantem.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
- [Wiązanie danych i formularzy Windows Forms](../data-binding-and-windows-forms.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
