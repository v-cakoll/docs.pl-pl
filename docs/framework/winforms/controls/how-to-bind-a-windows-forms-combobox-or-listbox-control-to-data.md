---
title: Powiąż kontrolkę ComboBox lub ListBox z danymi
description: Dowiedz się, jak powiązać Windows Forms ComboBox i ListBox z danymi, aby wykonywać zadania, takie jak przeglądanie danych w bazie danych, wprowadzanie nowych danych lub edytowanie istniejących danych.
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
ms.openlocfilehash: 0c07dc90ddc91061c5f34b5a237082cb444e89d9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324074"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Porady: powiązanie formantu ComboBox lub ListBox (Formularze systemu Windows) z danymi
Można powiązać <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ListBox> dane i z danymi, aby wykonywać zadania, takie jak przeglądanie danych w bazie danych, wprowadzanie nowych danych lub edytowanie istniejących danych.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Aby powiązać formant ComboBox lub ListBox  
  
1. Ustaw `DataSource` Właściwość na obiekt źródła danych. Możliwe źródła danych obejmują <xref:System.Windows.Forms.BindingSource> powiązanie z danymi, tabelą danych, widokiem danych, zestawem danych, menedżerem widoku dane, tablicą lub dowolną klasą, która implementuje <xref:System.Collections.IList> interfejs. Aby uzyskać więcej informacji, zobacz [źródła danych obsługiwane przez Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Jeśli tworzysz powiązanie z tabelą, ustaw `DisplayMember` Właściwość na nazwę kolumny w źródle danych.  
  
     \-oraz  
  
     Jeśli tworzysz powiązanie z <xref:System.Collections.IList> , Ustaw element członkowski wyświetlania na publiczną właściwość typu na liście.  
  
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
    > Jeśli masz powiązanie ze źródłem danych, które nie implementuje <xref:System.ComponentModel.IBindingList> interfejsu, takiego jak <xref:System.Collections.ArrayList> , dane kontrolki powiązanej nie zostaną zaktualizowane po aktualizacji źródła danych. Na przykład jeśli masz pole kombi powiązane z <xref:System.Collections.ArrayList> , a dane są dodawane do <xref:System.Collections.ArrayList> , te nowe elementy nie pojawią się w polu kombi. Można jednak wymusić aktualizację pola kombi, wywołując <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metody i w wystąpieniu <xref:System.Windows.Forms.BindingContext> klasy, do której jest powiązany formant.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Powiązywanie danych formularzy systemu Windows](../windows-forms-data-binding.md)
- [Wiązanie danych i formularze systemu Windows](../data-binding-and-windows-forms.md)
- [Formanty formularzy systemu Windows używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
