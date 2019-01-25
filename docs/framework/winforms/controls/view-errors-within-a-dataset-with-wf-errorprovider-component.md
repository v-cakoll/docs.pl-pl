---
title: 'Instrukcje: Wyświetl błędy w zestawie danych za pomocą składnika ErrorProvider formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 48f333fbae816748813b370bccc559cea2714fa5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694051"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Instrukcje: Wyświetl błędy w zestawie danych za pomocą składnika ErrorProvider formularzy Windows
Można używać formularzy Windows <xref:System.Windows.Forms.ErrorProvider> składnika, aby wyświetlić błędy kolumny w ramach zestawu danych lub innego źródła danych. Aby uzyskać <xref:System.Windows.Forms.ErrorProvider> składnika, aby wyświetlić błędy danych na formularzu, nie musi być bezpośrednio powiązany z kontrolką. Gdy jest powiązany ze źródłem danych, ona wyświetlona ikona błędu obok żadnego formantu, który jest powiązany z tego samego źródła danych.  
  
> [!NOTE]
>  Jeśli zmienisz dostawcy błąd <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> i <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> właściwości w czasie wykonywania, należy użyć <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> metody w celu uniknięcia konfliktów.  
  
### <a name="to-display-data-errors"></a>Aby wyświetlić błędy danych  
  
1.  Powiąż składnik do określonej kolumny w tabeli danych.  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
    ```  
  
2.  Ustaw <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> właściwości formularza.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  Ustaw pozycję bieżącego rekordu do wiersza, który zawiera błąd kolumny.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [ErrorProvider, składnik — omówienie](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)
- [Instrukcje: Wyświetlanie ikon błędów weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
